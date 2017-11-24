[![Travis CI](https://img.shields.io/travis/inofix/ansible-acme-service-apache.svg?style=flat)](http://travis-ci.org/inofix/ansible-acme-service-apache)


Acme Cron Service - Apache
==========================

This is an ansible role for reloading services using certificates from let's encrypt, after the certs were renewed.
For everything related to the creation of the certs see the inofix.acme-\* roles. The main rule which also
has the details in its README is inofix.ansible-acme-setup.

This role is meant to be run on any host that needs certificates.

Why we do not use one of the existing roles?

* For the first reason read the section "Promise" below. We need something reliable.
* This role will be used by [maestro](https://github.com/inofix/maestro) and must follow the logic used there. (Of course, the role can be used without maestro..)


State
-----

UNSTABLE!


Promise
-------

Sure, this role may change in the future, but we will only expand features to not break backwards compatibility.

If radical changes should become necessary, a new role will be created, probably with an 'ng' or version suffix...

Installation
------------

 # ansible-galaxy install inofix.acme-service-apache

Requirements
------------

* Ansible >2.0
* Python2/3 on target host
* Generic UNIX with FHS
* Sudo
* Systemd (per default)

Role Variables
--------------

* app\_\_acme\_\_user - optional, default='acme'
* app\_\_acme\_\_group - optional, default='acme'
* app\_\_acme\_\_config\_dir - optional, default='/etc/ssl/acme'
* app\_\_acme\_\_service\_dir - optional, default='{{ app\_\_acme\_\_config\_dir }}/service'
* app\_\_acme\_\_log\_dir - optional, default='/var/log/acme'

Dependencies
------------

* inofix.acme-setup

Example Playbook
----------------

    - hosts: servers
      roles:
         - inofix.acme-service-apache

License
-------

GPLv3


Author Information
------------------

* Michael Lustenberger at [inofix.ch](http://www.inofix.ch)
