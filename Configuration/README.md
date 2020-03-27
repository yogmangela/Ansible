
   ```
   21  cd /etc/ansible : Ansible setup folder
   23  ls
   32  sudo vi hosts :add localhost to Hosts
   33  ansible -m ping all: it doesn't ping needs key
   34  ssh-copy-id ansible@localhost
   35  ansible -m ping all
   36  clear
   37  sudo vi hosts
   38  ansible -m ping all
```