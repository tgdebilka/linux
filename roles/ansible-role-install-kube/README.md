Ansible Role: install-kube
=========

Ansible Role for preparing and installing kubernetes on multiple machines using Ansible.

Requirements
------------
No special requirements; note that this role requires root access, so either run it in a playbook with a global become: yes, or invoke the tasks in your playbook like:
```
- hosts: servers
  tasks:
    - name: install-kube
      import_role:
        name: ansible-role-install-kube
      become: yes
```
Installing
------------
Inside the same folder your playbook is in:
```
mkdir -p roles
cd roles
git clone https://github.com/hiitsmatan/ansible-role-install-kube.git
```
Example Playbook
----------------
Example of how to use your role in a playbook:
```
- hosts: all
  become: yes
  tasks:
    - name: install kube
      import_role:
        name: ansible-role-install-kube
```
Execution
----------------
Example of how to execute your role:
```
ansible-playbook -i inventory your-playbook-name.yaml
```
or with the `-K` option which prompts you for become password:
```
ansible-playbook -i inventory -K your-playbook-name.yaml
```
Available Tags
----------------
Example of how to execute this role with specific actions:
```
ansible-playbook -i inventory your-playbook-name.yaml --tags "tag-name1,tag-name2"
```
### Tags:
| Tag Name | Explanation |
| ------------- | ------------- |
| `update-packages`  | Equal to `apt-get update`  |
| `swapoff` | Cancels the usage of swapfile  |
| `ip-forward` | Activated ipv4 forwarding  |
| `install-docker`  | Installs only Docker |
| `install-kubernetes`  | Installs only Kubernetes and creates daemon.json service file |
| `restart-services`  | Restarts the Docker and daemon services |





