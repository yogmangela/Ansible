
#### To configure Ansible Node follow steps 1 to Step 7:

Then follow below steps:

Step 1 : install python
```
$ sudo apt update
$ sudo apt install software-properties-common
$ sudo apt-add-repository --yes --update ppa:ansible/ansible

$ sudo apt-get install python
```
step 2: Exit and exit again to login into Ansible Control Server (ACS).

```
ssh user@<<public_ip_of_AnsibleControlServer>>
```
so my looks like this:
```
ssh ansible@34.244.108.76
```

now try connecting Node from Ansible Control Server (ACS). Use Private ip to connect as both this machcines on same VPC / network.

```
ansible@ip-172-31-26-112:~$ ssh ansible@172.31.22.124
The authenticity of host '172.31.22.124 (172.31.22.124)' can't be established.
ECDSA key fingerprint is SHA256:n30s4Izfnn5NVCSL6KatLDdgWw4f/KXOUZjSAHAacgE.
Are you sure you want to continue connecting (yes/no)? yes
Warning: Permanently added '172.31.22.124' (ECDSA) to the list of known hosts.
ansible@172.31.22.124's password:
```

Step 3: Make connection ACS and Node.

```
ssh-copy-id ansible@node_Private_DNS
```


then do
```
ssh ansible@ip-172-31-22-124.eu-west-1.compute.internal
```

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
   23  ssh-keygen
   24  ls .ssh
   25  ssh-copy-id ansible@ip-172-31-22-124.eu-west-1.compute.internal
   26  history

```