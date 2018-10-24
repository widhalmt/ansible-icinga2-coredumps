# ansible-icinga2-coredumps
Enabling coredumps for Icinga 2

Usage
=====

If you know how to use Ansible Roles: fine.

If you don't, here's a quick start for just using this role:

Quickstart
----------

1. Install Ansible on a host where you have your private ssh key
2. Ensure that you can login via ssh to all hosts running Icinga 2
3. Ensure that you can use `sudo -i` without password (there are plenty of other options if you need to fulfil security policies)
4. Create a directory to house your ansible code
5. Clone this directory into `roles/ansible-icinga2-coredumps` within this ansible directory
6. Create a playbook file (see below)
7. Create a host list (see below)
8. Run the playbook (see below)

Playbook file
-------------

Let's call it `icinga2-coredumps.yml`

```
---
- hosts: all
  remote_user: yourusername
  become: yes
  roles:
    - ansible-icinga2-coredumps
```

Host list
---------

On your Icinga 2 config master you can use the following lines to create a host list file.

```
# echo '[icingahosts]' > production
# icinga2 object list --type host | grep " name " | cut -d\" -f2 >> production

```

Run the playbook
----------------

```
# ansible-playbook -i production icinga2-coredumps.yml
```
