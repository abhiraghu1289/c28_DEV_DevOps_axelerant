# c28_DEV_DevOps
Ques:-Automate the process of granting / revoking SSH access to a group of servers instances to a new developer
sh-access

Grant/Revoke SSH access to a group of instances to a user

Case:-1
Use below given command to add new user and grant SSH access

ansible-playbook -i inventory/ -e "action=grant" playbooks/ssh.yml

Case:-2
Use below given command to grant SSH access to an existing user

ansible-playbook -i inventory/ -e "action=grant" playbooks/ssh.yml --skip-tags=add

Case:-3
Use below given command to revoke SSH access from a user

ansible-playbook -i inventory/ -e "action=revoke" playbooks/ssh.yml --skip-tags=remove

Case:-4
Use below given command to remove user, hence revoke SSH access as well

ansible-playbook -i inventory/ -e "action=revoke" playbooks/ssh.yml

Note : 

* Under instances group in inventory/host file --- please make sure to add IPs of target instances.
Update the varibale "user_name" and "user_des" as per requirements. You can add multiple values for mutiple users at a time.
* Make sure to create a directory under "sshkeys" directory of same name as user name and put its SSH pub key under it.
* I have tested this on AWS instances as target instances so I have used ec2-user. Please make sure to use appropriate user in "ssh.yml"   who has access to target servers and the machine from where you will run Ansible should have passwordless access to target servers.
