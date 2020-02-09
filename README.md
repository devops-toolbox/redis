Role Name
=========

redis: Redis

[![Build Status](https://travis-ci.org/cmihai-ansible/redis.svg?branch=master)](https://travis-ci.org/cmihai-ansible/redis)

Ansible galaxy:
---------------

[https://galaxy.ansible.com/devopstoolbox.redis](https://galaxy.ansible.com/devopstoolbox.redis)

```bash
ansible-galaxy install devopstoolbox.redis
```

Requirements
------------

- For RHEL, a Red Hat subscription or functional local repository.
- Ansible 2.4 or higher

Role Variables
--------------

```yaml
redis_packages_state: present
redis_remove_packages: true
redis_enable_service: true
redis_enable_selinux: true
redis_copy_templates: true
redis_firewall_configure: true
redis_firewall_rules:
  - service: ssh
  - port: 3389
redis_users:
  - user: devops
    group: docker
redis_selinux_booleans:
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
- name: Install redis on localhost
  hosts:
    - localhost
  connection: local

  tasks:
    - name: redis is configured
      import_role:
        name: devopstoolbox.redis
      vars:
        redis_packages_state: present
        redis_remove_packages: true
        redis_enable_service: true
        redis_enable_selinux: true
        redis_copy_templates: true
        redis_firewall_configure: true
        redis_firewall_rules:
          - service: ssh
          - port: 3389
        redis_users:
          - user: devops
            group: docker
        redis_selinux_booleans:
          - name: ftp_home_dir
            state: true
            persistent: true
      tags: redis
```

License
-------

MIT

Author Information
------------------

- [Mihai Criveti](https://www.linkedin.com/in/devopstoolbox.)
