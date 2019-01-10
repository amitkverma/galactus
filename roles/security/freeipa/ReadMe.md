FreeIpa
	
Active Open Ports
	`netstat -tulpn`
IPA Status
	`ipactl status`

ansible-playbook -i ./hosts/production.yml  ./playbook/freeipa-client.yml   -e "env=production" --private-key=~/Dropbox/Keys/test.pem

ansible-playbook -i ./hosts/production.yml  ./playbook/freeipa-server.yml   -e "env=production" --private-key=~/Dropbox/Keys/test.pem

Get Host Name: `hostname --fqdn`

Setups 
	1. Get Granting ticket for Admin -> `kinit admin`
	2. See All the available tickets -> `klist`

Steps
	1. Create User Group of name `sudo_users`.
		a. Create User Group
			`ipa group-add sudo_users --desc="Users who have admin rights"`
		b. Check If User Group Created
			`ipa group-find sudo_users`
		c. Create User with group
			`ipa user-add suman --gidnumber=YOUR_GROUP_NUMBER`
			Login to server and do 
			`kinit suman`
		d. Add members to group
			`ipa group-add-member charcoal_admin --`
	2. Create Host Group of name `charcoal_hosts`
		a. Create A host group
			`ipa hostgroup-add charcoal_hosts --desc="Charcoal Production Servers"`
		b. Add Members to hostgroup
			`ipa hostgroup-add-member charcoal_hosts --`
			Now enter host name in the shell
	3. Create Sudo Role of root cmd `root_role`
		a. Rule for root user
			`ipa sudorule-add root_role --desc="Rule for root user group"`
		b. assign a user group to sudo role
			`ipa sudorule-add-user root_role --groups=sudo_users`
		c. assign a host group to sudo role
			`ipa sudorule-add-host root_role --hostgroups=charcoal_hosts`
		d. add sudo rules to rule group
			`ipa sudorule-mod root_role --cmdcat=all`
		e. Disable password
			`ipa sudorule-add-option root_role` -> add `!authenticate`
		f. Verify Sudo role
			`ipa sudorule-show root_role`

Ref: 
https://access.redhat.com/documentation/en-us/red_hat_enterprise_linux/6/html/identity_management_guide/defining-sudorules

