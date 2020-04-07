### How to rum jinja template

Run below command to see all the variable outputs:

```
ansible -i hosts -m setup -a 'filter=*' all
```

should get something like:
>>
[output.json](/jinja2/output.json)

but i am only interested in displaying : [display.j2](/jinja2/display.j2)

Attributes :

{{ ansible_all_ipv4_addresses }}
{{ ansible_bios_version }}
{{ ansible_date_time.date }}
{{ ansible_default_ipv4.alias }}

make sure they all are undfer same folder.

to run 

```
ansible@ip-172-00-38-000:~/playbook$ ansible-playbook -i hosts jinjaDemo.yml
```

then run 
```
cat display.txt
```
 to see result

 you should see below output:

 ```
 ansible@ip-172-31-38-250:~/playbook$ cat display.txt
Hi root ,

your machine is Debian

I want to install git

this is your machine infor:

[u'172.31.38.250']
4.2.amazon
2020-04-07
Tuesday
172.31.38.250
eth0
172.31.47.255
172.31.32.1
eth0
0a:c5:7e:d7:2c:b2
9001
255.255.240.0
172.31.32.0
ether

ansible@ip-172-31-38-250:~/playbook$

```