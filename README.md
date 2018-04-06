# Ansible Role: Storj

[![Build Status](https://travis-ci.org/mtlynch/ansible-role-storj.svg?branch=master)](https://travis-ci.org/mtlynch/ansible-role-storj)
[![Ansible Galaxy](https://img.shields.io/badge/ansible--galaxy-storj-blue.svg?style=flat-square)](https://galaxy.ansible.com/mtlynch/storj)
[![License](http://img.shields.io/:license-mit-blue.svg?style=flat-square)](LICENSE)

The Storj Ansible role installs [Storj](https://storj.io/) on a node and automates its initial provisioning steps.

## Features

* Automatically installs storjshare-daemon and all of its dependencies
* Supports version upgrades/downgrades
* Automatically creates Storj farmer nodes

## Role Variables

Available variables are listed below, along with default values (see [defaults/main.yml](defaults/main.yml)):

The version of Storj to install:

```yaml
storj_daemon_version: 5.3.1
```

Storj farmer configurations. You'll need to specify your Storj payment address (the address where you can receive Storj ERC20 Ethereum tokens) and a share size (e.g. 5GB). To set up multiple farmer configurations, simply add another config to the `storj_farmer_configs` list:

```yaml
storj_farmer_configs:
- payment_address: null
  share_size: null
  rpc_address: "127.0.0.1"
  rpc_port: 45015
```

Username and group to use for Storj daemon:

```yaml
storj_user: storj
storj_group: "{{ storj_user }}"
```

Directories for Storj files:

```yaml
storj_dir: /opt/storj
storj_farmer_config_dir: "{{ storj_dir }}/configs"
storj_farmer_share_dir: "{{ storj_dir }}/shared"
storj_logs_dir: "{{ storj_dir }}/logs"
```

## Dependencies

* [geerlingguy.nodejs](https://galaxy.ansible.com/geerlingguy/nodejs/)

## Example Playbook

#### `example.yml`

```yaml
---
- hosts: all
  become: True
  become_method: sudo
  become_user: root
  vars:
    storj_farmer_configs:
      # Change payment_address to your own Storj ERC20 address.
      - payment_address: "0x161441Efd42171687dd1468A9e23E74226541c38"
        rpc_address: "{{ ansible_host }}"
        rpc_port: 6000
        storage_dir: /mnt/path1
        share_size: 5GB
  roles:
    - role: mtlynch.storj
```

### Running Example Playbook

To run the example playbook, `example.yml` (above), run the following commands:

```shell
ansible-galaxy install mtlynch.storj
ansible-playbook example.yml
```

## License

MIT

## Author Information

This role was created in 2018 by [Michael Lynch](https://mtlynch.io).
