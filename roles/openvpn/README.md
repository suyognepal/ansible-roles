
Ansible Role: OpenVPN
=====================================

An ansible role to install and configure OpenVPN server.

Features
----------------
- clientlist: Enter the namer of the client you want to add.
- revokelist: Enter the names of the client you want to revoke.


Directory Layout
----------------
```
├── clientlist
├── vars
│   └── vars.yml
├── files
│   └── make_config.sh
├── handlers
│   └── main.yml
├── media
├── README.md
├── revokelist
├── tasks
│   ├── client_keys.yaml
│   ├── config.yaml
│   ├── easy-rsa.yaml
│   ├── firewall.yaml
│   ├── install.yaml
│   ├── main.yaml
│   ├── revoke.yaml
│   └── server_keys.yaml
└── templates
    ├── before.rules.j2
    ├── client.conf.j2
    └── server.conf.j2

7 directories, 18 files

```
Role Variables
--------------

|**Variables**| **Default Values**| **Description**| **Type**|
|----------|---------|---------------|-----------|
| server_name | server | OpenVPN server Name | Optional |
| PROTOCOL | udp | The protocaol on which the server will work | Mandatory |
| PORT | udp | The port on which the server will work | Mandatory |
| openvpn_server_network | 10.8.0.0 | CIDR range given to vpn network | Optional |
| base_directory | /etc/openvpn | Configuration path of openvpn server | Optional |
| easy_rsa_url | url | URL to download Easy RSA | Optional |
| block_all_connection | false | Block all communication for openvpn client | Optional |
| port_list | [80,443] | Allow specific ports for openvpn client & only applicable if block_all_connection == true | Optional |
| out_interface | eth0 | out interface of machine or instance where openvpn is configured | Mandatory |
| dns_resolver | 8.8.4.4 | dns has to be resolved then change value ( If you have to use private instances/ec2 from then change it to vpc cidr with dns resolver example vpc cidr is 172.31.0.0 then put value 172.31.0.2 ) | Optional |

Inventory
----------
An inventory should look like this:-
```ini
[server]                 
192.xxx.x.xxx    ansible_user=ubuntu 
```

Playbook Example 
----------------
```
---
- name: OpenVPN setup
  hosts: server
  become: true
  roles:
    - role: openvpn
...

$  ansible-playbook site.yml -i inventory

```


