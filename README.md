Role Name
=========

cloudcli: Cloudcli

[![Build Status](https://travis-ci.org/cmihai-ansible/cloudcli.svg?branch=master)](https://travis-ci.org/cmihai-ansible/cloudcli)

Ansible galaxy:
---------------

[https://galaxy.ansible.com/devopstoolbox.cloudcli](https://galaxy.ansible.com/devopstoolbox.cloudcli)

```bash
ansible-galaxy install devopstoolbox.cloudcli
```

Requirements
------------

- For RHEL, a Red Hat subscription or functional local repository.
- Ansible 2.4 or higher

Role Variables
--------------

```yaml
cloudcli_packages_state: present
cloudcli_remove_packages: true
cloudcli_enable_service: true
cloudcli_enable_selinux: true
cloudcli_copy_templates: true
cloudcli_firewall_configure: true
cloudcli_firewall_rules:
  - service: ssh
  - port: 3389
cloudcli_users:
  - user: devops
    group: docker
cloudcli_selinux_booleans:
  - name: ftp_home_dir
    state: true
    persistent: true
```

Dependencies
------------

- For Red Hat, subscription-manager.

Example Playbook
----------------

```yaml
---
- name: Install cloudcli on localhost
  hosts:
    - localhost
  connection: local

  tasks:
    - name: cloudcli is configured
      import_role:
        name: devopstoolbox.cloudcli
      vars:
        cloudcli_packages_state: present
        cloudcli_remove_packages: true
        cloudcli_enable_service: true
        cloudcli_enable_selinux: true
        cloudcli_copy_templates: true
        cloudcli_firewall_configure: true
        cloudcli_firewall_rules:
          - service: ssh
          - port: 3389
        cloudcli_users:
          - user: devops
            group: docker
        cloudcli_selinux_booleans:
          - name: ftp_home_dir
            state: true
            persistent: true
      tags: cloudcli
```

License
-------

MIT

Author Information
------------------

- [Mihai Criveti](https://www.linkedin.com/in/devopstoolbox.)
