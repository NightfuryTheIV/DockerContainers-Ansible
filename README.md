# I used WSL Ubuntu to make this so it might not work as intended on Debian

### There is a possibility that accessing venv is required. If it is, access with `source .venv/bin/activate` from the root (Dockeransible)
### If venv doesn't work, reinstall it by running succssively (from Dockeransible):
```
rm -rf .venv
sudo apt update
sudo apt install python3-venv python3-pip
source .venv/bin/activate
pip install ansible
```

### If necessary, the hosts are on a local folder outside of the project accessible (from Dockeransible, a.k.a. the folder root) like this: ./../../../etc/ansible/hosts
The SSH key id_rsa is to be referred with ./id_rsa
### You might also have to connect to the SSH first, with `ssh -i ./id_rsa admin@daif.moindjie.takima.school`

## To run the ansible playbook, run: `ansible-playbook -i ansible/inventories/setup.yml ansible/installdocker.yml`, playbook.yml is completely useless
## Finally, to access the server, navigate to http://daif.moindjie.takima.school (heavy emphasis on the http instead of https), the URL should resolve after a few seconds

I also did the docker installation in the installdocker.yml on Ubuntu instead of Debian because I'm using Ubuntu

3-1: The inventories folder is the folder that we use to put the setup.yml and it's also where ansible runs commands, and as for the commands, ansible all calls all the specified hosts, -i specifies the inventory and the -m flag specifies the module

3-2: I moved all of the tasks from installdocker.yml to main.yml in roles/docker/tasks and I added roles: - docker
