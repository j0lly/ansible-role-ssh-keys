SSH Keys
=========

Simplest role to map users with provided ssh keys.

[![Ansible Role](https://img.shields.io/ansible/role/16211.svg)](https://galaxy.ansible.com/j0lly/ssh-keys/)
[![Build Status](https://travis-ci.org/j0lly/ansible-role-ssh-keys.svg?branch=master)](https://travis-ci.org/j0lly/ansible-role-ssh-keys)


Requirements
------------

User to distribute the key to need to be already present

Role Variables
--------------

Only two variables here:

```yml
# Default to clean
ssh_keys_clean: True

ssh_keys_user:
  root:
    - "{{ lookup('file', lookup('env','HOME') + '/.ssh/id_rsa.pub') }}"
```

Dependencies
------------

None

Example Playbook
----------------

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

    - hosts: bastions
      roles:
         - role: j0lly.ssh-keys
           ssh_keys_clean: False
           ssh_keys_user:
             user_a:
               - https://place.to-store/keys
               - "ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABAQDmttIEinXN5+2J8g3V3XnVRshX9qllMNbHqGNT9x7glW5PsG1XUAKIjIvD5GfTEbqjxHuCuxXUuoUi/LsrQAGUO1hEnamsDZtczhWmoHiK8gzLW83qKIzXLsGEexzi7POnroRvjKNy2/koeigjY3+GcRXsJzwv0P4IaJMLi/aDvOhzLe00yiNQ6X+9Fdyp3n589e3k5H+A9BqROanoxuAA7ko0TGW52AHxM51doEofy4ySKqOj3M+vV5VwQNFmUFqa8WEnBYZ6k5eUL4ixJxY5TMzZfzWcOpIhI8+8WrnTmsDIB3t54VO3BeVW5hrG8W6oiwDVDvSDTpqklY2gmwI7"
               - "ssh-rsa BBBBB3NzaC1yc2EAAAADAQABAAABAQDmttIEinXN5+2J8g3V3XnVRshX9qllMNbHqGNT9x7glW5PsG1XUAKIjIvD5GfTEbqjxHuCuxXUuoUi/LsrQAGUO1hEnamsDZtczhWmoHiK8gzLW83qKIzXLsGEexzi7POnroRvjKNy2/koeigjY3+GcRXsJzwv0P4IaJMLi/aDvOhzLe00yiNQ6X+9Fdyp3n589e3k5H+A9BqROanoxuAA7ko0TGW52AHxM51doEofy4ySKqOj3M+vV5VwQNFmUFqa8WEnBYZ6k5eUL4ixJxY5TMzZfzWcOpIhI8+8WrnTmsDIB3t54VO3BeVW5hrG8W6oiwDVDvSDTpqklY2gmwI7"
             admin_user:
               - https://another.place.to-store/keys
               - '{{ lookup("file", "path/to/keys") }}'

License
-------

BSD

Author Information
------------------

j0lly - jos.ferraris@gmail.com
