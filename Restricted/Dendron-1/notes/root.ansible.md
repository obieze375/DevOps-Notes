---
id: bzrs8nw7tydr7yur1s1xir2
title: Ansible
desc: ''
updated: 1657662514477
created: 1657661877559
traitIds:
  - journalNote
---

ctrl + shift +V to enter test view

# Create Directory Module

~~~~

tasks:
- name: ansible create multiple directory example
ansible.builtin.file:
     path: " {{ directory }} / {{ item }}"
     state: directory
     recurse: yes
with_items:
      - '/tmp/devops_system1'
      - '/tmp/devops_system2'
      - '/tmp/devops_system3'
when: "hostname in group_names" # Searches for hostname group in inventory file specified under group vars dir
~~~~



# Delegate to 

~~~~
---
- hosts: webservers
  serial: 5

  tasks:
    - name: Take out of load balancer pool
      ansible.builtin.command: /usr/bin/take_out_of_pool {{ inventory_hostname }}
      delegate_to: 127.0.0.1
      run_once: true

    - name: Actual steps would go here
      ansible.builtin.yum:
        name: acme-web-stack
        state: latest

    - name: Add back to load balancer pool
      ansible.builtin.command: /usr/bin/add_back_to_pool {{ inventory_hostname }}
      delegate_to: 127.0.0.1
      run_once: true 

~~~~

~~~~ 
NOTE: Run ansible playbook without --limit to group in inventory file as this example will just run on localhost 
~~~~


# failed_when

~~~~

---
- hosts: all
  tasks:
  - name: "shut down Rhel 6 and Debian 7 systems"
    command: /sbin/shutdown -t now
    when: (ansible_distribution == "CentOS" and ansible_distribution_major_version == "6") or
          (ansible_distribution == "Debian" and ansible_distribution_major_version == "7") or
          (ansible_distribution == "Debian" and ansible_distribution_major_version == "8")


~~~~



# Shell Module

~~~~

--- 
- hosts: loc
  tasks: 
  - name: Ansible Shell chdir and executable parameters 
    shell: | 
      bash example
      bash example
      bash example
    args:
      chdir: /root/ansible/shell_chdir_example 
      executable: /bin/bash

  - name: Ansible Shell chdir and executable parameters 
    shell: | 
      bash example
      bash example
      bash example
    args:
      chdir: /root/ansible/shell_chdir_example 
      executable: /bin/bash

~~~~


# Uri module

~~~~
- name: Check page contents, return status 200 and fail if the page contents uri doesn’t contain the word Linux

uri:

  url: http://www.example.com
  validate_certs: no
  return_content: yes 
register: this
failed_when: "'Linux' not in this.content"
args:
  chdir: "<dir>"
~~~~

# get_url module 

~~~~
- hosts: all    

- name: Download File with authentication      

  become: yes      

  get_url:
      url: http://102.15.192.120/backups/database.tar.gz
      url_username: user
      url_password: '{{ pass }}'
      url_password: '{{ API_TOKEN }}' /* Token stored in vault as variable*/
      force_basic_auth: yes
      validate_certs:no
      mode: 0777
      timeout: 5
      dest: /backups
~~~~


# Copy Module


~~~~
- name: copy files to destination
  hosts: localhost
  connection: local
  tasks:
    - name: copy src.txt as dest.txt in the same dir 
      copy:
        src: files/src.txt
        dest: files/dest.txt
        remote_src: yes /*Use for copying to remote locations or servers*/
      tags:
        - simple_copy
~~~~


# Dynamic environment usage

~~~~

host: "{{ env_name }}"
vars: 
  env_name: ""


CLI USAGE: ansible-playbook .yml --extra-vars "env_name=<value>"

~~~~

# nohup & disown command usage
~~~~

nohup <bash_command> & disown

 -> If you use all three together, the process is running in the background, is removed from the shell's job control and is effectively disconnected from the terminal
~~~~

# Create file with content

~~~~
- name: create file and add context
  copy:
    dest: <filepath>/file name
    mode: 0755
    content: "value_to_add"
~~~~

# xml parser to grab secrets from xml file

~~~~
xmlint --xpath "jnlp/application-desc/arguement [1]/text()" file.jnlp > file.secrets
~~~~

## Ansible Vault commands 

# Check Vault version

~~~~
vault --version
~~~~

# Adding credentials into vault

~~~~
for env in env1 env2 env 3;
do
vault kv patch \
-address "web_link_to_vault" \
-tls-skip-verify=true secret/path/to/$env
api_token_var="value1" \
api_token_var="value2" ;
done
~~~~


