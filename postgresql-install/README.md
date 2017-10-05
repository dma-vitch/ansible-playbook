## PostgreSQL 

---

Ansible role which installs and configures PostgreSQL, extensions, databases and users.


#### Installation

This has been tested on Ansible 2.2 and higher.

To install:

```
ansible-playbook ./postgresql.yml
```

#### Variables

```yaml
# Basic settings
postgresql_version: 9.3
postgresql_encoding: 'UTF-8'
postgresql_locale: 'en_US.UTF-8'
postgresql_ctype: 'en_US.UTF-8'

postgresql_admin_user: "postgres"
postgresql_default_auth_method: "trust"

# List of databases to be created (optional)
# Note: for more flexibility with extensions use the postgresql_database_extensions setting.
postgresql_databases:
  - name: exampledb
    owner: # default to '{{ postgresql_user }}' specify the owner of the database
    encoding: 'UTF-8'   # override global {{ postgresql_encoding }} variable per database
    lc_collate: 'en_GB.UTF-8'   # override global {{ postgresql_locale }} variable per database
    lc_ctype: 'en_GB.UTF-8'     # override global {{ postgresql_ctype }} variable per database
    template: # defaults to 'template0'
    login_host: # defaults to 'localhost'
    login_password: # defaults to not set
    login_user: # defaults to '{{ postgresql_user }}'
    login_unix_socket: # defaults to first of postgresql_unix_socket_directories
    port: # defaults to '{{ postgresql_server_port }}'
    state: # defaults to 'present'

# List of database extensions to be created (optional)
postgresql_database_extensions:
  - db: exampledb
    extensions:
      - dblink
      - citext

# List of users to be created (optional)
postgresql_users:
  - name: tech
    password: # defaults to not set
    encrypted: # denotes if the password is already encrypted defaults to not set.
    priv: # defaults to not set
    role_attr_flags: # defaults to not set
    db: # defaults to not set
    login_host: # defaults to 'localhost'
    login_password: # defaults to not set
    login_user: # defaults to '{{ postgresql_user }}'
    login_unix_socket: # defaults to 1st of postgresql_unix_socket_directories
    port: # defaults to '{{ postgresql_server_port }}'
    state: # defaults to 'present'

# List of user privileges to be applied (optional)
postgresql_user_privileges:
  - name: tech                   # user name
    db: exampledb                  # database
    priv: "ALL"                 # privilege string format: example: INSERT,UPDATE/table:SELECT/anothertable:ALL
    role_attr_flags: "CREATEDB" # role attribute flags
```

#### License

Licensed under the MIT License. 

#### Thanks

This playbooks based on [ANXS.PostgreSQL](https://github.com/ANXS/postgresql)
