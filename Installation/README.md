* Configure Ansible Control Server *

* Steps to INSTALL Ansible on Ubuntu.18

-- Below steps assume you have connected / access to Linux machine already. Use Git Bash / Putty to Connect to your machine.

I have use AWS  EC2 instance with Uuntu 18.

### Step 1: change user to root
 ```
Sudo -i
```

### Step 2: enable password base authentication: 
```
vi /etc/ssh/sshd_config
```
change 'PasswordAuthentication no'
 to 'yes' press ESC
 type `:wq` to save 

### Step 3: restart SSHD service 
```
service sshd restart
``` 
then check status 
```
service sshd status
```

### Step 4: create user :
[adduser OR useradd](https://askubuntu.com/questions/345974/what-is-the-difference-between-adduser-and-useradd "adduser OR useradd")

I prefere ADDUSER type (ubuntu): 
```
adduser ansible
```
OR for Linux:
```
sudo useradd ansible
sudo passwd ansible
```

### Step 5: Give root privilage to ansible (Ubuntu): `visudo` 
under `# Allow members of group sudo to execute any command` add as following: 
```
ansible ALL=(ALL:ALL) NOPASSWD:ALL
``` 

OR For Linux:
```
## Allows people in group wheel to run all commands
%wheel  ALL=(ALL)       ALL
ansible ALL=(ALL:ALL) NOPASSWD:ALL
```

. Ctrl + X to exit, to save say `Y` and Enter. 

exit again to go back to your ubuntu@ip..... user

### Step 6: do 
```
su ansible
```
then check working directory for ansible `cd ~`. Should get something like:
`ansible@ip-1......112:~$ pwd /home/ansible`

### Step 7: Then check sudo previlage by updatting packages: 
```
ubuntu:sudo apt-get update
linux: sudo yum update
```

### Step 8: Run below command to install Ansible on Master node or (Ansible Control Server)
```
$ sudo apt update
$ sudo apt install software-properties-common
$ sudo apt-add-repository --yes --update ppa:ansible/ansible
$ sudo apt install ansible
```
### Step 9: Check Ansible version 
```
ansible --version
```
should see something like:
```
ansible@ip-1.......2:~$ ansible --version
ansible 2.9.6
  config file = /etc/ansible/ansible.cfg
  configured module search path = [u'/home/ansible/.ansible/plugins/modules', u'/usr/share/ansible/plugins/modules']
  ansible python module location = /usr/lib/python2.7/dist-packages/ansible
  executable location = /usr/bin/ansible
  python version = 2.7.17 (default, Nov  7 2019, 10:07:09) [GCC 7.4.0]
ansible@ip-1.......2:~$
```

Ansibel successfully installed on your machine.

### step 10. generate SSH_KEYGEN
type: ssh-keygen

```
ansible@ip-172-31-46-241:~$ ssh-keygen
Generating public/private rsa key pair.
Enter file in which to save the key (/home/ansible/.ssh/id_rsa):
Created directory '/home/ansible/.ssh'.
Enter passphrase (empty for no passphrase):
Enter same passphrase again:
Your identification has been saved in /home/ansible/.ssh/id_rsa.
Your public key has been saved in /home/ansible/.ssh/id_rsa.pub.
The key fingerprint is:
SHA256:aN5LRzXz2qLLz+SOCRS9UiZzutYsFggeQuu3Z4Bmn6I ansible@ip-172-31-46-241
The key's randomart image is:
+---[RSA 2048]----+
|  .              |
| . .     .       |
|  o o   + = +    |
| . + o o O o +   |
|  = + + S o   .  |
| o o * o B   o   |
|  . + + O + + .  |
| . . o + * B .   |
|E       . *+=    |
+----[SHA256]-----+
```
### Step 11 to list rsa run 'ls .ssh'
```
ansible@ip-172-31-46-241:~$ ls .ssh
id_rsa  id_rsa.pub
ansible@ip-172-31-46-241:~$
```

### What next... Configure Ansibel Node


#### To configure Ansible Node follow steps 1 to Step 7:

Then follow below steps:

### Step 1 : install python
```
$ sudo apt-get update
$ sudo apt-get install software-properties-common
$ sudo apt-add-repository --yes --update ppa:ansible/ansible

$ sudo apt-get install python
$ python --version
```
### step 2: Exit and exit again to login into Ansible Control Server (ACS).

```
ssh user@<<public_ip_of_AnsibleControlServer>>
```
so my looks like this:
```
ssh ansible@34.244.108.76
```
ls
now try connecting Node from Ansible Control Server (ACS). Use Private ip to connect as both this machcines on same VPC / network.

```
ansible@ip-172-31-26-112:~$ ssh ansible@172.31.22.124
The authenticity of host '172.31.22.124 (172.31.22.124)' can't be established.
ECDSA key fingerprint is SHA256:n30s4Izfnn5NVCSL6KatLDdgWw4f/KXOUZjSAHAacgE.
Are you sure you want to continue connecting (yes/no)? yes
Warning: Permanently added '172.31.22.124' (ECDSA) to the list of known hosts.
ansible@172.31.22.124's password:
```
### Step 3 : copy ssh file form ACS to node
```
ssh-copy-id ansible@ip-172-31-22-124.eu-west-1.compute.internal
```

### Step 4: login to Node / ssh into node using rsa 

ssh ansible@ip-172-31-22-124.eu-west-1.compute.internal

```
    ansible@ip-172-31-26-112:~$ history
    1  pwd
    2  cd
    3  sudo apt-get update
    4  clear
    5  visudo
    6  exit
    7  pws
    8  clear
    9  pwd
   10  exit
   11  cd ~
   12  pwd
   13  sudo apt update
   14  cls
   15  clear
   16  sudo apt install software-properties-common
   17  sudo apt-add-repository --yes --update ppa:ansible/ansible
   18  sudo apt install ansible
   19  ansible --version
   20  exit
   21  ssh ansible@172.31.22.124
   22  clear
   23  ssh-keygen: Generate on ACS
   24  ls .ssh: see two files 1. id.rsa, 2.id_rsa.pub
   ### Step $:  Copy id_rsa.pub to nodes. Use Private DNS of node as below.

     ssh-copy-id ansible@ip-172-31-22-124.eu-west-1.compute.internal

   ### then try login into node from ASC as below.

   ssh  ansible@ip-172-31-22-124.eu-west-1.compute.internal
   you should be logged into Node:

   ansible@ip-172-31-22-124:~$
```
