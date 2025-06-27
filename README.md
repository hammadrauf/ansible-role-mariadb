MariaDB
=======

This role installs and configures MariaDB, sets up a database, root password, and a power user, based on the environment variables.

Requirements
------------

Any pre-requisites that may not be covered by Ansible itself or the role should be mentioned here. For instance, if the role uses the EC2 module, it may be a good idea to mention in this section that the boto package is required.

Role Variables
--------------

- `MYSQL_DB_NAME`: Name of the database to create (default: `my_db`)
- `ROOT_PWD`: MariaDB root password (default: `changeme01`)
- `POWER_USER`: Power user name (default: `ceaser`)
- `PU_PWD`: Power user password (default: `changeme02`)

Dependencies
------------

A list of other roles hosted on Galaxy should go here, plus any details in regards to parameters that may need to be set for other roles, or variables that are used from other roles.

Example Usage
-------------

```yaml
- hosts: all
  become: yes
  roles:
    - role: hammadrauf/mariadb
      vars:
        MYSQL_DB_NAME: my_db
        ROOT_PWD: changeme01
        POWER_USER: ceaser
        PU_PWD: changeme02
```

License
-------

MIT

Author Information
------------------

- Hammad Rauf
