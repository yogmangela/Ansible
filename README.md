* Steps to INSTALL Ansible on Ubuntu.18

-- Below steps assume you have connected / access to Linux machine already. Use Git Bash / Putty to Connect to your machine.

I have use AWS  EC2 instance with Uuntu 18.

Step 1: change user to root `Sudo -i`

Step 2: enable password base authentication: `vi /etc/ssh/sshd_config`
change 'PasswordAuthentication no'
 to 'yes'
 type `:wq` to save and exit

Step 3: restart SSHD rervice `service sshd restart` then check status `service sshd status`

Step 4: create user :
[adduser OR useradd](https://askubuntu.com/questions/345974/what-is-the-difference-between-adduser-and-useradd "adduser OR useradd")

I prefere ADDUSER type : `adduser ansible`

Step 5: Give root privilage to ansible: `visudo` under `Allow members of group sudo` add as following: `ansible ALL=(ALL:ALL) NOPASSWORD:ALL` 
. Ctrl + X to exit, to save say `Y` and Enter. 

Step 6: do `su ansible` then check working directory for ansible `cd ~`. Should get something like:
`ansible@ip-1......112:~$ pwd /home/ansible`

Step 7: Then check sudo previlage by updatting packages: `sudo apt-update`