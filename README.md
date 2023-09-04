# mysql-ha-master-to-master
This role will install mysql on 2 node with replication master to master
# variables
```
db1_ip: 192.168.1.40
db2_ip: 192.168.1.41
db_name: test
db_user: tester
db_user_passwd: test123
```
# inventory example 
```
[db1]
db1 ansible_host=192.168.1.40  ansible_connection=ssh ansible_ssh_user=filex5 ansible_ssh_pass=test123 ansible_sudo_pass=test123 host_key_checking=false ansible_python_interpreter=/usr/bin/python3
[db2]
db2 ansible_host=192.168.1.41 ansible_connection=ssh ansible_ssh_user=filex5 ansible_ssh_pass=test123 ansible_sudo_pass=test123 host_key_checking=false ansible_python_interpreter=/usr/bin/python3
```
# example of use
``` 
ansible-playbook -i inventory mysql.yml -k --extra-vars "control_machine_ip=$ANSIBLE_CONTROL_MACHINE"
```
```
- name: Depoly website
  hosts: db1, db2
  become: yes
  gather_facts: yes
 # Roles
  roles:
    - mysql-ha
  vars:
    db1_ip: 192.168.1.40
    db2_ip: 192.168.1.41
    db_name: test
    db_user: tester
    db_user_passwd: test123
```
