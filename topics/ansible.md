# ansible
System management **Automation** with config manager application Ansible

* GUI: Semaphore

Consider ansible instll in manage-node machine.
That machine access to another remote machines(Nodes)
Ansible system can connect and run some task on them.
I use a newly installed Debian stable 12 as managed node.

## Ansible fast tutorial

* [source](https://itomation.ca/ansible-for-beginners-tutorial-part-3-hello-world-playbook/)


## Install 
```
sudo apt install ansible
```


Commands with tab completion
```
$ ansible
ansible             ansible-connection  ansible-galaxy      ansible-pull        
ansible-community   ansible-console     ansible-inventory   ansible-test        
ansible-config      ansible-doc         ansible-playbook    ansible-vault       
```


## Hello world
After install ansible on your machine run below commands.

Run ping module to test ansible can works on local machine.
```
$ ansible -m ping localhost
[WARNING]: No inventory was parsed, only implicit localhost is available
localhost | SUCCESS => {
    "changed": false,
    "ping": "pong"
}

```
# GH Tutorial

I write a tutiral [here](https://github.com/esmaeelE/ansible_tutorial)



