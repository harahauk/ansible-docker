ansible-docker
==============
```diff
# Project maturity (- Dev|@ Staging|+ Prod):
@ Staging
```

An [Ansible](https://www.ansible.com/)-role which install and configures `docker` and `docker-compose` on the target
host.


Requirements
------------

## Linux
Currently supports following distributions
- RHEL-based (RockyLinux, AlmaLinux)
- Debian-based (Kali, Debian, Ubuntu)

You need ansible [install-script](./install_ansible.sh), and the module "community general" (which often is pre-installed with your ansible-distribution) and the "community docker" module.
This role comes with a [script](./install_ansible.sh) that might or might not setup Ansible correctly for you depending
on your environment.

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
| docker_user | no        | Defines a user that you want to given access to docker, defaults to the user running the playbook if not set |
| docker.service.subnet | no | Allows you to override network-segments docker should use |

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
      - ansible-docker    # Change to the folder you checked this role out as
      vars:
        docker_user: "my_unprivileged_user"

Author Information
------------------

[Harald Hauknes](https://github.com/harahauk)

License
-------

MIT License

See [LICENSE](./LICENSE) for the full text.
