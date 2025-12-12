# Create Ansible Inventory for App Server Testing
---
The Nautilus DevOps team is testing Ansible playbooks on various servers within their stack. They've placed some playbooks under /home/thor/playbook/ directory on the jump host and now intend to test them on app server 3 in Stratos DC. However, an inventory file needs creation for Ansible to connect to the respective app. Here are the requirements:

a. Create an ini type Ansible inventory file /home/thor/playbook/inventory on jump host.
```
cd playbook
touch inventory
```

b. Include App Server 3 in this inventory along with necessary variables for proper functionality.
```
vi inventory
```
```
stapp03 ansible_host=172.16.238.12 ansible_user=banner ansible_ssh_pass=BigGr33n
```
c. Ensure the inventory hostname corresponds to the server name as per the wiki, for example stapp01 for app server 1 in Stratos DC.

```
ansible-playbook -i inevntory playbook.yml
```

Note: Validation will execute the playbook using the command ansible-playbook -i inventory playbook.yml. Ensure the playbook functions properly without any extra arguments.