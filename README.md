ansible-docker
==============
```diff
# Project maturity (- Dev|@ Staging|+ Prod):
@ Staging
```

An [Ansible](https://www.ansible.com/)-role which installs and configures `docker` and `docker-compose` on the target
host.


Requirements
------------
### 1. Linux
This role is tested and expected to perform on the following Linux-distributions:
- Debian 12 "Bookworm"
- Red Hat Linux 9
- AlmaLinux 9
- Fedora 38

The role *might* work on the following distributions with no guarantees:
- RHEL-based (RockyLinux, AlmaLinux)
- Debian-based (Kali, Debian, Ubuntu)

### 2. Ansible
You need Ansible for a control-node. Either as a seperate computer/VM or on the intended target. You need the Ansible module-collection `community general` (which often is pre-installed with your Ansible-distribution). This is the basis of any Ansible-control node, additionally to operate this role you need  the `community docker` module.
I maintain a [script at Github](https://raw.githubusercontent.com/harahauk/ansible-help/refs/heads/main/install_ansible.sh) which can automate this in a way that do not interfere with system stability. The script installs the two module-packs as well.

On most systems these commands will lead to a working control node and is maintainable without the use of the script:
```
dnf install ansible-core
ansible-galaxy collection install community.general
ansible-galaxy collection install community.docker     # Only needed if you plan to automate Docker-deployments.
```
**Note**: Replace `dnf` with your package manager like `apt` for Ubuntu/Debian-based OS.


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

Useful Resources
----------------
Not really needed for this role but
- [this guide](https://docs.docker.com/reference/cli/docker/container/run/#env) was really useful for configuring containers

