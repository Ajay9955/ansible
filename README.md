# ansible

Ansible is a configuration management tool.


First we need to enusre that we have passwordless connection to our target server form our ansible server. It is achived by copying the public key(can be genarated by using ssh-keygen) of ansible server to the authorized keys file  of target
server.

we will use ansible adhoc commands(single line coomands) if there are one or two actions or tasks to be done on the target servers.

If there are multiple or more actions to be performed on target servers we use ansible playbook.

Ansible playbooks are written as yaml files.

We have so many modules in ansible like 

copy
file
shell
command
ping
service , etc....

" inventory file " ---- contains the ip address of target or remote servers. IP addresses can be grouped base on the req 

[group-name]
ip1 ------- address
ip1
[groupname2 ]
ip3
ip4


Ansible adhoc commands(single line commands) will be written as 

$ ansible -i inventory all/webservers or any_other_list_of_IP_u_want-that-are-in-inventory-file -m(represents module) "module-name" -a(represents arguments) "req_arguments"

eg : ansible -i inventory all -m "copy" -a "src=path-of-file-we-want-to-copy dest=path-we-want-to-copy-file"


For mutliple commands or tasks we write "ansibel playbook"

-these are written as yaml files

skeleton or structure of the playbook :

--- (these 3 dashes represents this is a yaml file)
- name : file-name (name of file)
  hosts : all or webservers or dbservers (any list of IP addresses in your inventory file "all"--- represents to include all IP addresses in inventory file )
  tasks:
    - name: name of task
      module-name:
        actions or commands
    - name: task2 name
      module-ame:
        actions or commands


you can write multipe tasks under tasks section.

$ ansible-playbook -i inventory playbook-name.yml -------- executing or running ansible playbook.
