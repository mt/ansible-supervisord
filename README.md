Supervisor for Ansible
======================
A role for deploying and configuring [Supervisor](http://supervisord.org) and extensions on unix hosts using [Ansible](http://www.ansibleworks.com).

It can additionally be used as a playbook for quickly provisioning hosts.

Vagrant machines are provided to produce VMs for integration testing.


Supports
--------
Supported Supervisor versions:
- Supervisor 3+

Supported targets:
- Ubuntu 14.04 LTS "Trusty Tahr"
- Ubuntu 12.04 LTS "Precise Pangolin"
- Debian (untested)

Installation methods:
- Binary packages from the system repos.


Usage
-----
Clone this repo into your roles directory:

    $ git clone https://github.com/zenoamaro/ansible-supervisord.git roles/supervisord

And add it to your play's roles:

    - hosts: ...
      roles:
        - supervisord
        - ...

This roles comes preloaded with almost every available default. You can override each one in your hosts/group vars, in your inventory, or in your play. See the annotated defaults in `defaults/main.yml` for help in configuration. All provided variables start with `supervisord_` or `supervisorctl_`.

You can also use the role as a playbook. You will be asked which hosts to provision, and you can further configure the play by using `--extra-vars`.

    $ ansible-playbook -i inventory --extra-vars='{...}' main.yml

Run the tests by provisioning the appropriate VM:

    $ vagrant up test-ubuntu-trusty

At the moment, the following test boxes are available:

- `test-ubuntu-precise`
- `test-ubuntu-trusty`


Still to do
-----------
- Add tasks for quickly creating supervisor programs
- Support for fastcgi programs, event listeners, ...


Changelog
---------

### 0.3.0
- Revised the INIT script's restart sequence.
- Added a test box for Ubuntu Trusty 14.04.
- Sleep time between daemon restarts is now configurable.

### 0.2.0
- Delegated installation of supervisord to the OS package manager.

### 0.1.0
Initial version.

