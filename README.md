ansible-role-cosbench
=========

Ansible role to install and configure [COSBench](https://github.com/intel-cloud/cosbench) (Cloud Object Storage Benchmarking Tool)

Requirements
------------
Role [ksingh7.cosbench](https://galaxy.ansible.com/ksingh7/cosbench/) must be installed

Installation
------------
```$ ansible-galaxy install ksingh7.cosbench```

Customization
--------------
Variable file :  ``vars/main.yml``
If you want to install any other version of COSBench , update the following variable
```
cosbench_version: 0.4.2.c4
```
Dependencies
------------
- This role depends on a specific naming convention of hostgroups in your inventory file. So your ansible inventory file should look like this
```
[cosbench-controller]
client1

[cosbench-driver]
client1
client2
client3

[cosbench:children]
cosbench-controller
cosbench-driver

```
Example Playbook
----------------
Your playbook should look like this

    - hosts: cosbench
      roles:
         - { role: ansible-role-cosbench }

To install cosbench:

```
ansible-playbook -i cosbench-hosts  cosbench-playbook.yml
```

To uninstall it:

```
ansible-playbook -i cosbench-hosts  cosbench-playbook.yml -e "uninstall=True"
```

License
-------

Apache

Author Information
------------------

Originially created by created [Karan Singh](http://www.ksingh.co.in).


