Ansible Node PM2
================
Ansible playbook for deploying a NodeJS application to a set of VMs and running them using the PM2
process manager.

Assumptions
-----------
- The NodeJS project contains a main file entitled app.js.
- The target VMs are running Linux with Debian/Ubuntu.


Usage
-----
Any necessary authentication for SSHing into the target VMs must be specified in the ansible.cfg
file. For example, Ubuntu ec2 instances in AWS typically require a pem file in order to SSH into them.
They also require you to SSH using the user name 'ubuntu'. The corresponding ansible.cfg file will
look as follows:

```
[defaults]
host_key_checking = False
remote_user = ubuntu
private_key_file = /path/to/file.pem
```

Ensure that Ansible is installed on the machine in which the project will be run.
VMs can be specified in the inventory file. The git repo containing the NodeJS project must be
specified in roles/node/vars/main.yml.

Execute the command
```
ansible-playbook site.yml -i inventory
```

to run the Ansible playbook.
