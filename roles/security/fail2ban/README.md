Fail2ban ReadMe

## What is fail2ban?

fail2ban is a service which parses specified log files and can perform configured actions when a given regexp is found. It's usually used to ban offending IP addresses using iptables rules (only IPv4 connections are supported at the moment).

### What problem does it solve and why is it useful?

Fail2ban scans log files (e.g. /var/log/apache/error_log) and bans IPs that show the malicious signs -- too many password failures, seeking for exploits, etc. Generally Fail2Ban is then used to update firewall rules to reject the IP addresses for a specified amount of time, although any arbitrary other action (e.g. sending an email) could also be configured. Out of the box Fail2Ban comes with filters for various services (apache, courier, ssh, etc).


Example inventory
-----------------

To enable ``fail2ban`` you can add a host or several hosts to
``[fail2ban]`` group::

    [fail2ban]
    hostname

If you have many hosts which you want to protect using ``fail2ban``, you can
instead create a child group and add it to the ``[fail2ban]`` parent
group::

    [fail2ban:children]
    protected_hosts

    [protected_hosts]
    host1
    host2
    host3


Let's say you want to edit a few values, you can do this by opening group_vars/all and then add the following::
    ---
      fail2ban_services:
        - name: ssh
          port: ssh
          filter: sshd
          logpath: /var/log/auth.log



Example playbook
----------------

Here's an example playbook which uses ``fail2ban`` role to install ``fail2ban``::

    ---

    - name: Install fail2ban
      hosts: fail2ban
      roles:
        - role: fail2ban
          tags: fail2ban