# Ansible Role: Storj

[![Build Status](https://travis-ci.org/mtlynch/ansible-role-storj.svg?branch=master)](https://travis-ci.org/mtlynch/ansible-role-storj)
[![Ansible Galaxy](https://img.shields.io/badge/ansible--galaxy-storj-blue.svg?style=flat-square)](https://galaxy.ansible.com/mtlynch/storj)
[![License](http://img.shields.io/:license-mit-blue.svg?style=flat-square)](LICENSE)

The Storj Ansible role installs [Storj](https://storj.io/) on a node and automates its initial provisioning steps.

## Features

TODO

## Role Variables

Available variables are listed below, along with default values (see [defaults/main.yml](defaults/main.yml)):

TODO

## Dependencies

* [geerlingguy.nodejs](https://galaxy.ansible.com/geerlingguy/nodejs/)

## Example Playbook

#### `example.yml`

```yaml
- hosts: all
  roles:
    - { role: mtlynch.storj }
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
