# Copy Data to App Servers using Ansible
---
The Nautilus DevOps team needs to copy data from the jump host to all application servers in Stratos DC using Ansible. Execute the task with the following details:

 a. Create an inventory file /home/thor/ansible/inventory on jump\_host and add all application servers as managed nodes.
```
Cd ansible
```
```
touch  inventory 
```
```
Vi inventory 
```
```
\[app\_servers\]

stapp01 ansible\_host=172.16.238.10 ansible\_user=tony ansible\_ssh\_pass=Ir0nM@n

stapp02 ansible\_host=172.16.238.11 ansible\_user=steve ansible\_ssh\_pass=Am3ric@

stapp03 ansible\_host=172.16.238.12 ansible\_user=banner ansible\_ssh\_pass=BigGr33n
```
 b. Create a playbook /home/thor/ansible/playbook.yml on the jump host to copy the /usr/src/finance/index.html file to all application servers, placing it at /opt/finance. 
```
touch playbook.yml
```
```
vi playbook.yml
```
```
---

- name: Copy finance index file to application servers

  hosts: app_servers

  become: yes

  tasks:

    - name: Copy index.html to /opt/finance

      copy:

        src: /usr/src/finance/index.html

        dest: /opt/finance/index.html
```
```
ansible-playbook -i inventory playbook.yml
```
Note: Validation will run the playbook using the command ansible-playbook -i inventory playbook.yml. Ensure the playbook functions properly without any extra arguments