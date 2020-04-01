### How to add Nodes to Hosts life

step:  logon to ACS
```
ssh ansible@public_ip
```

```
   21  cd /etc/ansible : Ansible setup folder
   23  ls
   32  sudo vi hosts :add localhost to Hosts
   33  ansible -m ping all: it does need ssh_key
   34  ssh-copy-id ansible@localhost
   35  ansible -m ping all
   36  clear
      mkdir playbook
      cd playbook
   37  sudo vi hosts: add private.DNS to hosts
   38  ansible -m ping all/appservers/dbservers/webserver
```