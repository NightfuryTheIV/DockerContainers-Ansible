There is a possibility that accessing venv is required. If it is, access with `source .venv/bin/activate` from the root (Dockeransible)
I also did the docker installation in the installdocker.yml on Ubuntu instead of Debian because I'm using Ubuntu

3-1: The inventories folder is the folder that we use to put the setup.yml and it's also where ansible runs commands, and as for the commands, ansible all calls all the specified hosts, -i specifies the inventory and the -m flag specifies the module

3-2: I moved all of the tasks from installdocker.yml to main.yml in roles/docker/tasks and I added roles: - docker


# commande pour aide: ansible-playbook -i inventories/setup.yml installdocker.yml (depuis le dossier ansible et à run sur ubuntu pas debian)