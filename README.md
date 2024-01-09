# This is an Ansible repository for AlmaLinux8 and 9
<br >

# What this plyabook contains below(# If you don't need all modules, please comment out unnecessary ones)
0. access_test
1. common(yum_update,hostname,firewalld,selinux,swap,timezone,tools,kernel,file_descriptor,history_date,postfix,user_add,user_add/sudoers) 
2. httpd
4. MySQL(including mysql_log)
5. PHP(including httpd_php-fpm)
6. Zabbix-agent(including zabbix_agent_mysql)
7. WordPress

# How to run
<br >
(Before running middleware playbooks, You should run access_test playbook to check the target server is correct)
1. Copy private key to the keys/user.key
2. Modify group_vars/all.yml(ex. user_name,user_password,host_name,domain_name and so on)
3. Move to the directory where playbook.yml locates
3. Dry run command {{ ansible-playbook --private-key keys/user.key -i hosts playbook.yml -C }}
4. Run command {{ ansible-playbook --private-key keys/user.key -i hosts playbook.yml -C }}

# Caution!
You need create a user for exectuing Ansible on AlamLinux9 if you use vagrant machine

# How to create an ansible exec user
1. useradd ansible-user
2. vi /etc/sudoers.d/ansible-user
3. ansible-user ALL=(ALL) NOPASSWD:ALL
4. su - ansible-user
5. ssh-keygen -t rsa -b 2048
6. cd ~/.ssh
7. ssh-keygen -p -m PEM -f id_rsa 
8. cat ./id_rsa.pub > ./authorized_keys
9. chmod 600 ./authorized_keys