# VM Setup:

controller = 192.168.56.10
web1 = 192.168.56.11
web2 = 192.168.56.12
web3 = 192.168.56.13

* Create ssh key on controller 
```
ssh-keygen -t rsa -b 4096 -f ansible
```
* Copy SSH keys to web1,web2,web3 VMs
```
ssh-copy-id -i ansiblekey vagrant@192.168.56.11
ssh-copy-id -i ansiblekey vagrant@192.168.56.12
ssh-copy-id -i ansiblekey vagrant@192.168.56.13
```
* Edit sudoers file for NOPASSWD for vagrant user on all slave VMS
```
sudo visudo
```
Add in no password
```
%wheel  ALL=(ALL:ALL)   NOPASSWD: ALL
```

Edit ssh config file and uncomment PubkeyAuthentication
```
sudo visudo
```

```
PubkeyAuthentication yes
```

cd project and test connection
```
cd project

ansible -m ping webservers
```