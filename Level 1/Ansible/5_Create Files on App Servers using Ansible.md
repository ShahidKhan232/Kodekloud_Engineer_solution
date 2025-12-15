# Create Files on App Servers using Ansible
---
The Nautilus DevOps team is testing various Ansible modules on servers in Stratos DC. They're currently focusing on file creation on remote hosts using Ansible. Here are the details:


a. Create an inventory file ~/playbook/inventory on jump host and include all app servers.

```
[app_servers]
stapp01 ansible_host=172.16.238.10 ansible_user=tony ansible_ssh_pass=Ir0nM@n
stapp02 ansible_host=172.16.238.11 ansible_user=steve ansible_ssh_pass=Am3ric@
stapp03 ansible_host=172.16.238.12 ansible_user=banner ansible_ssh_pass=BigGr33n
```
b. Create a playbook ~/playbook/playbook.yml to create a blank file /opt/code.txt on all app servers.


c. Set the permissions of the /opt/code.txt file to 0777.


d. Ensure the user/group owner of the /opt/code.txt file is tony on app server 1, steve on app server 2 and banner on app server 3.

```
---
- name: Create /opt/code.txt on all app servers
  hosts: app_servers
  become: yes
  tasks:
    - name: Create blank file with correct permissions and ownership
      file:
        path: /opt/code.txt
        state: touch
        mode: '0777'
        owner: "{{ ansible_user }}"
        group: "{{ ansible_user }}"
```

Note: Validation will execute the playbook using the command ansible-playbook -i inventory playbook.yml, so ensure the playbook functions correctly without any additional arguments.