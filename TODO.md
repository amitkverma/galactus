FOR Password Based Login
https://github.com/ansible/ansible/issues/3564

1. Update the documetaion for ferm
2. Test sshd is working or not and update documetation
3. Test fail2ban is working or not and update documentation
4. Check whether Ansible can connect as admin_user in user.yml check trellis
5. Should have the option to remove default user like ubuntu or root.


Run Playbook
`ansible-playbook -i ./hosts/production.yml server.yml -e "env=staging"`