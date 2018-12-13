proxysql
========

A ProxySQL role capable proxying secure connections to a MySQL group replication cluster.

Login with Admin : `mysql -u admin -p -h 127.0.0.1 -P 6032 --prompt='ProxySQLAdmin> '`
Check host Status : `SELECT hostgroup_id, hostname, status FROM runtime_mysql_servers;`
Login with Client: `mysql -u charcoaleatsAdmin -p -h 127.0.0.1 -P 6033 --prompt='ProxySQLClient> '`
Check selected host: `SELECT @@hostname;`

Example Playbook
----------------

```
---
- name: Set up ProxySQL to balance group
  hosts: mysql_proxy
  vars:
    proxysql_admin_user: admin
    proxysql_admin_password: admin
    proxysql_mysql_backend_servers:
      - mysql-node-1
      - mysql-node-2
      - mysql-node-3
    proxysql_require_ssl: true
    proxysql_group_monitor_user: monitor
    proxysql_group_monitor_pass: monitorpassword
    proxysql_user_data:
        - user: "{{ proxysql_admin_user }}"
          password: "{{ proxysql_admin_password }}"
          filename: .my.cnf
          port: "{{ proxysql_admin_port }}"
          prompt: "ProxySQLAdmin> "
        - user: testuser
          password: testpass
          filename: "testuser.cnf"
          port: "{{ proxysql_mysql_port }}"
          default_hostgroup: 2
          prompt: "testuser> "

  roles:
    - role: proxysql
```