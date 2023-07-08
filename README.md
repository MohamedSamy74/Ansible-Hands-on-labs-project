# Ansible-Hands-on-labs-project
Configuration management on cloud host using Ansible  

# INSTALLING ANSIBLE & PREPARING SSH
- Install Ansible
- Create a new user on the control machine and a new user on host 1
- Make sure you can ssh into host 1 (using a password)
- Generate SSH key pair on the control machine
- Copy the public key to host 1
- Make sure you can ssh into host 1 (using prv/pub)

# INVENTORY FILE
- Create the inventory file
- Put the IP of host 1 in the inventory file
- Use the inventory file path in your ad-hoc command instead of using the IP hard-coded
 Example:
ansible all -i inventory --private-key ~/.ssh/devops -u ubuntu -m ping

# CONFIGURATION FILE
- Create the configuration file
- Insert some values in the configuration file
- Run the minimized ad-hoc command
- Example: ansible all -m ping

# AD-HOC COMMAND ESCALATION USING ROOT USER
- Insert the correct values in the configuration file
- Example: ansible all -m command -a "whoami"
- What is the output of the command ?

# PLAYBOOK
- Write your first playbook file
- Stop gather_facts and update cache

# MODULES
- Explore some built-in modules like:
(apt, dnf, package, service, command, copy, user, group, lineinfile, authorized_key, etc.)
[ansible-builtin modules](https://docs.ansible.com/ansible/latest/collections/ansible/builtin/index.html)
- Update cache
- Install latest nginx
- Copy index.html from controller to host 1
- Restart nginx service
- Can you see your index.html file when you hit host 1 on port 80 ?

# TAGS
- Write simple playbook file
- Add two tasks (apt update – apt install nginx)
- Add tags to first task: update
- Add tags to second task: install
- Run only the (apt update) task
 Example: ansible-playbook my-playbook.yml --tags update
- Add one task with “tags: always” and run the previous command again

# VARIABLES
Define these variables (package_name, package_version)
- on playbook level
- on inventory level
- on command line level
Use apt module with the package name and version from your variables

# LOOPS
- Loop over a list of packages and install latest versions.
- Loop over a list of packages and perform different actions as per input.

# WHEN
- Install nginx or apache2 depending on distribution
- Restart nginx service if distribution is ubuntu and variable value is true

# REGISTER & WHEN
- View the value of your register variable using debug module
- Restart service if the installation task was changed or was not failed

# -------------------------------------------------------------------------

# ROLES
- Create your first role with name (web)

- The task book will include:
1. installing a package
(get the package name from vars)
2. copying a list of files from controller to host using loop
(get the list of file names from vars)
(the actual files will be stored in ./roles/web/files)
(will be executed only when the install task is in state: changed)

- Restart the service of the installed package
(will be executed only when the copy task is in state: changed)

# HANDLERS
- Create your first role with name (web)

- The task book will include:
1. installing a package
(get the package name from vars)
2. copying a list of files from controller to host using loop
(get the list of file names from vars)
(the actual files will be stored in ./roles/web/files)
(will be executed using Handlers)

- Restart the service of the installed package
(will be executed using Handlers chaining)

# TEMPLATES
- Create your first role with name (web)

- The task book will include:
1. installing a package
(get the package name from vars)
2. Copying a file from controller to host using template
(get the template name & template message from vars)
(the actual template file will be stored in ./roles/web/templates)
(will also notify the restart handler)
3. copying a list of files from controller to host using loop
(get the list of file names from vars)
(the actual files will be stored in ./roles/web/files)
(will be executed using Handlers)

- Restart the service of the installed package
(will be executed using Handlers chaining)

![Screenshot from 2023-07-08 18-27-56](https://github.com/MohamedSamy74/Ansible-Hands-on-labs-project/assets/44952687/9d36cec5-52e2-4d2e-963b-551690455988)
