## Ambari

---

Ansible role which installs or upgrades Ambari server, agent, and metrics.

#### Installation

This has been tested on Ansible 2.3 and higher.

To install:

```
ansible-playbook ./ambari.yml
```

## Role Variables

### Main variables
* `ambari_version`: This is the version of ambari. Default: 2.5.2.0
* `ambari_repo_yum`: A list with Yum repository configuration.

### Ambari Server specific

* `ambari_backup_dir`: This is the directory to create backup db. Default: /tmp/ambari_bkp
* `ambari_dump_databases`: A list with database. Default: ambari
* `ambari_db_connection`: A list credentials of database server
  ```
    user: "ambari"
    password: "bigdata"
    host: "localhost"
  ```

### Ambari Metrics specific
* `ambari_cluster_name`: This name of clusters in ambari. Default HDP_CLUSTER
* `ambari_user`: This ambari user. Default admin
* `ambari_passwd`: This ambari user password. Default admin
* `ambari_server`: This host where installed ambari server. Default: first node in group ambari-nodes
* `ambari_server_port`: This is port what listen ambari server. Default: 8080

#### License

Licensed under the MIT License.
