# Things to be done
- [x] Mysql Single Private Server
- [x] Mysql Master-Slave Setup
- [x] Mysql Master-Master Setup using group replication
- [x] Add ProxySql as reverse proxy for mysql server
- [x] Mysql Master-Master-Slave Topology 
- [ ] Mysql Import database
- [ ] Backup - Nightly on S3 and Live
- [ ] Edge Cases of replication setup

# Things to be refactored
- [ ] Database set should be selected dynamicaly
- [ ] Password should be saved in vault
- [ ] Define Replication section in `mysql.yml` 
- [ ] Adding New Member or Making live faulty node require restart of mysql

# Notes
- [ ] Require a admin user for ansible user `mysql_admin_user` to create slave replication user at master
- [ ] Replication user ( `mysql_replication_user` ) `host` should allow only ip range in which slaves are located