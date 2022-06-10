Unimus Ansible Role
=========

This role install Unimus Network Automation by NetCore jsa.

Find out more about Unimus in https://unimus.net/

Requirements
------------

No special requirements

Role Variables
--------------

Variables are self explanatory. Examples are:

- unimus_version: '2.2.2'
- mysql_root_password: supersecret
- mysql_database: unimus
- mysql_user: unimus
- mysql_password: secret
- TZ: America/New_York
- java_xmx: 1024M
- java_xms: 256M

Dependencies
------------

This role does not have any external dependences. You can maybe require geerlingguy.mysql on your playbook, depending on your deployment.

Example Playbook
----------------

```
---
- hosts: unimus
  become: true

  vars:
    mysql_root_password: "{{mysql_root_password}}"
    mysql_databases:
      - name: "{{mysql_database}}"
    mysql_users:
      - name: "{{mysql_user}}"
        host: "%"
        password: "{{mysql_password}}"
        priv: "{{mysql_database}}.*:ALL"

  roles:
    - geerlingguy.mysql
    - baldoarturo.unimus
```

License
-------

BSD

Author Information
------------------

Feel free to reach out on GitHub or https://arturobaldo.com.ar
