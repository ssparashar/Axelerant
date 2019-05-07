# Axelerant
## ssh access grant/revoke
Grant/Revoke SSH access to a group of instances to a new user

### Command to add new user and grant SSH access:
`ansible-playbook -i inventory/ -e "action=grant" sahil.yml`
### Command to grant SSH access to an existing user:
`ansible-playbook -i inventory/ -e "action=grant" sahil.yml --skip-tags=add`

### Command to revoke SSH access from a user:
`ansible-playbook -i inventory/ -e "action=revoke" sahil.yml`

## Notes
* Replace instance1,... under [instances] group in inventory/hosts files with IPs or DNS of target instances.
* The varibale "user_name" and "user_des" is the user-name of the user and an optional description as per requirements.
* Make sure to create a directory under "sshkeys" directory of same name as user name and put its SSH pub key under it.
* I have used ec2-user in the playbook "ssp.yml" as I have tested this on AWS instances. Please make sure to use appropriate user in "sahil.yml" who has access to target servers and the machine from where you will run Ansible should have passwordless access to target servers.
