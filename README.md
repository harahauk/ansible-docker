ansible-docker
==============
```diff
# Project maturity (- Dev|@ Staging|+ Prod):
- Dev
```

An [Ansible](https://www.ansible.com/)-role which creates a docker-host with traditional and docker-compose support.


Requirements
------------

## Linux
Currently supports following distributions
- RHEL-based (RockyLinux, AlmaLinux)
- Debian-based (Kali, Debian, Ubuntu)

You need ansible [installed](./install_ansible.sh), the "community general" modules which might or migh not be preinstalled with your ansible-distribution and the "community docker" modules.
This role comes with a [script](./install) that might or might not setup Ansible correctly for you.
On most systems this will do the same:
´´´
dnf install ansible-core
ansible-galaxy collection install community.general
ansible-galaxy collection install community.docker
´´´
Note: Replace `dnf` with your package manager like `apt` for Ubuntu/Debian-based OS.

Role Variables
--------------
| Variable    | Mandatory | Description |
| ----------- | --------- | ----------- |
| docker_user | no        | Defines a user that you want to given access to docker, defaults to the user running the
playbook if not set |

TODO:
A description of the settable variables for this role should go here, including any variables that are in defaults/main.yml, vars/main.yml, and any variables that can/should be set via parameters to the role. Any variables that are read from other roles and/or the global scope (ie. hostvars, group vars, etc.) should be mentioned here as well.

Dependencies
------------
This role might "work" on a wide range of Linux-distributions, but below are the distros that are actually tested.

xor:
  - Debian 12 "Bookworm"
  - Red Hat Linux 9
  - AlmaLinux 9
  - Fedora 38

Example Playbook
----------------

    - hosts: docker_hosts
      roles:
         - ansible-docker    #Change to the folder you checked this role out as

Author Information
------------------

[Harald Hauknes](https://github.com/harahauk)

License
-------

MIT License

See [LICENSE](./LICENSE) for the full text.


