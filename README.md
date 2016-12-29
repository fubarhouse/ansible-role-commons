# Ansible Role: Commons

[![Build Status](https://travis-ci.org/fubarhouse/ansible-role-commons.svg?branch=master)](https://travis-ci.org/fubarhouse/ansible-role-commons)
[![Ansible Galaxy](https://img.shields.io/badge/galaxy-fubarhouse--commons-13943.svg)](https://galaxy.ansible.com/fubarhouse/commons)

The purpose of this role is to consolidate all common behaviors/tasks used frequently by fubarhouse Ansible roles. Over time every role using a piece of this role will use this role. All functionality is segregated by logic.

* Sets `fubarhouse_user` for usage with Ansible roles authored by fubarhouse.
* Sets `apache2_is_installed` and `nginx_is_installed` for usage with Ansible roles authored by fubarhouse.
* Ensures `conf.d`, `sites-available` and `sites-enabled` folders are created for either `apache2` or `nginx` web servers.
* Creates virtual hosts fed through a proxy to localhost:port from a simple array.
* Makes sure apache2 proxy modules are enabled on RedHat/CentOS/REHL systems.
* Webserver roles `geerlingguy.apache` and `geerlinguy.nginx` are no longer included.

## Requirements

  * none

## Role Variables

Choose a webserver (only apache2 or nginx for now)
````
fubarhouse_webserver: nginx
````

To add proxy-based virtual hosts (web services on a port)
````
fubarhouse_vhosts:
  - name: myservice
    domain: "myservice.dev"
    docroot: /opt/myservice
    port: 3000
````

## Dependencies

  None.

## Example Playbook
````
- hosts: localhost
  roles:
    - fubarhouse.commons
````

## License

MIT / BSD

## Author Information

This role was created in 2016 by [Karl Hepworth](https://twitter.com/fubarhouse).