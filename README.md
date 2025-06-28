MariaDB
=======

This role installs and configures MariaDB, sets up a database, root password, and a power user, based on the environment variables.


Requirements
------------

Any pre-requisites that may not be covered by Ansible itself or the role should be mentioned here. For instance, if the role uses the EC2 module, it may be a good idea to mention in this section that the boto package is required.

- Ansible Core >= 2.16
- Tested Linux Distribution
  - Debian 12
  - Ubuntu 24.04
  - Fedora 40

> Note: Other (and/or newer) distributions likely to work but not been tested


Role Variables
--------------

- `MYSQL_DB_NAME`: Name of the database to create (default: `my_db`)
- `ROOT_PWD`: MariaDB root password (default: `changeme01`)
- `POWER_USER`: Power user name (default: `ceaser`)
- `PU_PWD`: Power user password (default: `changeme02`)
- `sql_script_path`: SQL Script Jinja2 Template for execution in new Mariradb Server (default: ``)

Dependencies
------------

A list of other roles hosted on Galaxy should go here, plus any details in regards to parameters that may need to be set for other roles, or variables that are used from other roles.

Test Locally using Lint, Ansible, Molecule and Tox (for Paralllel Threads)
--------------------------------------------------------------------------

```
rm -rf ~/.ansible/roles/
molecule test --all
molecule test --all --driver-name=podman
molecule test --all -d docker

yamllint -v . && ansible-lint -v . && molecule test --all

tox
tox -p auto   # Runs tox environments in parallel, depending on local cpu core count and depends clause.
tox -e lint   # Runs only lint tox environment
tox -e fedora40  # Runs only fedora40 tox environment, if it depends on another tox environment, that should also execute.

tox -e debug-debian12 -- converge   # Stops at Converge, for manual debugging of container image
tox -e debug-debian12 -- list
tox -e debug-debian12 -- login
tox -e debug-debian12 -- login --host instance-debian12
tox -e debug-debian12 -- destroy

```

> Note: debug-debian12, debug-fedora40, and debug-ubuntu2404 - are hidden from "tox" and "tox -p auto" view in [tox.ini](./tox.ini) configuration file.

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
