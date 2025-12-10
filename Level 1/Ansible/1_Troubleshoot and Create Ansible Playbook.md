# Troubleshoot and Create Ansible Playbook

An Ansible playbook needs completion on the jump host, where a team member left off. Below are the details:

1.  The inventory file /home/thor/ansible/inventory requires adjustments. The playbook must run on App Server 1 in Stratos DC. Update the inventory accordingly.
```
stapp02 ansible\_host=172.16.238.10 ansible\_user=tony ansible\_ssh\_pass=Ir0nM@n
```
    
2.  Create a playbook /home/thor/ansible/playbook.yml. Include a task to create an empty file /tmp/file.txt on App Server 1.
```
---   
    - name: Create file on App Server 1
    hosts: stapp01
    become: yes
    
    tasks:
    - name: Create an empty file at /tmp/file.txt
    file:
        path: /tmp/file.txt
        state: touch
``` 

Note: Validation will run the playbook using the command 
```ansible-playbook -i inventory playbook.yml```. Ensure the playbook works without any additional arguments.