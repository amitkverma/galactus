1. Check Number of replication users
    `SELECT * FROM performance_schema.replication_group_members;`
2. Setup replication
    `ansible-playbook -i ./hosts/development.yml  ./playbook/mysql-group-replication.yml    -e "env=dev" --private-key=~/Dropbox/Keys/test.pem`
3. If replication stopped in one or more servers ( Requires Restart  )
    `ansible-playbook -i ./hosts/development.yml  ./playbook/mysql-group-replication.yml    -e "env=dev" --private-key=~/Dropbox/Keys/test.pem`
4. if you need to add new server to replication
    `ansible-playbook -i ./hosts/development.yml  ./playbook/mysql-group-replication.yml    -e "env=dev" --private-key=~/Dropbox/Keys/test.pem`
5. if you need to add new slave server in replication group
    `ansible-playbook -i ./hosts/development.yml  ./playbook/mysql-mater-slave.yml    -e "env=dev" --private-key=~/Dropbox/Keys/test.pem`
6. if one or more slaves are not working in replication group
    `ansible-playbook -i ./hosts/development.yml  ./playbook/mysql-mater-slave.yml    -e "env=dev" --private-key=~/Dropbox/Keys/test.pem`


Example Mysql Server
----------------

```
mysql_server: 
   hosts:
     mysql-box:
   vars:
     ansible_ssh_user: root
     server_name: 'mysql'
```


Example Group Replication
----------------

```
mysql_replication: 
  hosts:
    mysql-role-1:
    mysql-role-2:
    mysql-role-3:
  vars:
    ansible_ssh_user: user
    server_name: 'name'
    mysql_group_replication: true
    mysql_group_replication_uuid: "unique-id"
```

Example Slave Server in Group Replication
----------------

```
mysql_slave: 
  hosts:
    mysql-role-1:
    mysql-role-2:
  vars:
    ansible_ssh_user: user
    server_name: 'name'
    mysql_replication_role: 'slave'
    mysql_replication_user: { name: slaveUser, host: '%', password: 'password' } 
    enable_mysql_slave_replication: true
```

# mysql_server:
