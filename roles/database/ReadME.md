1. Check Number of replication users
    `SELECT * FROM performance_schema.replication_group_members;`
2. Setup replication
    `ansible-playbook -i ./hosts/development.yml  ./playbook/mysql-group-replication.yml    -e "env=dev" --private-key=~/Dropbox/Keys/test.pem`
3. If replication stopped in one or more servers ( Requires Restart  )
    `ansible-playbook -i ./hosts/development.yml  ./playbook/mysql-group-replication.yml    -e "env=dev" --private-key=~/Dropbox/Keys/test.pem`
4. if you need to add new server to replication
    `ansible-playbook -i ./hosts/development.yml  ./playbook/mysql-group-replication.yml    -e "env=dev" --private-key=~/Dropbox/Keys/test.pem`
5. if you need to add new slave server in replication group
    `ansible-playbook -i ./hosts/development.yml  ./playbook/mysql-group-replication.yml    -e "env=dev" --private-key=~/Dropbox/Keys/test.pem`