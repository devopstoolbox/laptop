Role Name
=========

laptop: Laptop

[![Build Status](https://travis-ci.org/cmihai-ansible/laptop.svg?branch=master)](https://travis-ci.org/cmihai-ansible/laptop)

Ansible galaxy:
---------------

[https://galaxy.ansible.com/devops-toolbox.laptop](https://galaxy.ansible.com/devops-toolbox.laptop)

```bash
ansible-galaxy install devops-toolbox.laptop
```

Requirements
------------

- For RHEL, a Red Hat subscription or functional local repository.
- Ansible 2.4 or higher

Role Variables
--------------

```yaml
laptop_packages_state: present
laptop_remove_packages: true
laptop_enable_service: true
laptop_enable_selinux: true
laptop_copy_templates: true
laptop_firewall_configure: true
laptop_firewall_rules:
  - service: ssh
  - port: 3389
laptop_users:
  - user: devops
    group: docker
laptop_selinux_booleans:
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
- name: Install laptop on localhost
  hosts:
    - localhost
  connection: local

  tasks:
    - name: laptop is configured
      import_role:
        name: devops-toolbox.laptop
      vars:
        laptop_packages_state: present
        laptop_remove_packages: true
        laptop_enable_service: true
        laptop_enable_selinux: true
        laptop_copy_templates: true
        laptop_firewall_configure: true
        laptop_firewall_rules:
          - service: ssh
          - port: 3389
        laptop_users:
          - user: devops
            group: docker
        laptop_selinux_booleans:
          - name: ftp_home_dir
            state: true
            persistent: true
      tags: laptop
```

License
-------

MIT

Author Information
------------------

- [Mihai Criveti](https://www.linkedin.com/in/devops-toolbox.)
