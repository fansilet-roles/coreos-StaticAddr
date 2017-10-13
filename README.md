CoreOs Static Addr
=========

A simple way to add Static Address on CoreOS Machines

[![Build Status](https://travis-ci.org/isca0/coreos-StaticRoutes.svg?branch=master)](https://travis-ci.org/isca0/coreos-StaticAddr)

Requirements
------------

**None** (if you already has done the bootsrap on your coreos with python)  
If you need bootstrap your CoreOS and install python, run [coreos-bootstrap](https://galaxy.ansible.com/isca0/coreos-bootstrap/)
firstly... :smiley:

__This role will add static address to CoreOS on file /etc/systemd/10-static.networks, as a block at end of file.  


Role Variables
--------------

All you need is set interface, gateway and network addresses  
  
So the only variable you will need to set on this role is the addrs variable.  
The syntax is that:  

```
  addrs:
    - { inet: eth0, network: 10.0.0.0/8, gateway: 172.17.12.1 }
```

You can also set multiple addresses by dooing like this:
 
```
  addrs:
    - { inet: eth0, network: 10.0.0.0/8, gateway: 172.17.12.1 }
    - { inet: eth1, network: 192.168.125.0/28, gateway: 10.12.13.1 }
  ...
```

You must remember to set your python interpreter path.  
if you have bootstrapped with **isca0.coreos-bootstrap**, set your inventory vars with this python path:  
[coreos:vars]  
ansible_python_interpreter="/opt/python/bin/python"  


Dependencies
------------

None

Example Playbook
----------------


```
---
  - name: "Adding Static Address on CoreOS Machines"
    hosts: coreos
    remote_user: core
    become: true
    vars:
      addrs:
        - { inet: eth0, network: 10.0.0.0/8, gateway: 172.17.12.1 }
    roles:
      - coreos-StaticAddr
```

License
-------

BSD

Author Information
------------------

This role was create in 2017 by [Isca](https://isca.space)

