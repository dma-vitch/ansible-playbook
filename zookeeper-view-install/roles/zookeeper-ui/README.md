ha-cluster-pacemaker
=========

Role for configuring zookeeper UI on CentOS/RHEL 6/7 systems.

Requirements
------------



Role Variables
--------------

  - user used for running zk-ui

    ```
    ZOOKEEPER_UI_USER: zookeper-ui
    ```

  - group to which zk-ui user belongs 

    ```
    ZOOKEEPER_UI_GROUP: zookeper-ui
    ```

  - port for zk-ui

    ```
    ZOOKEEPER_UI_PORT: 9090
    ```

#todo
  - configuration of firewall for clustering, NOTE in RHEL/Centos 6 this replaces iptables configuration file!
  
    ```
    enabled_firewall: true
    ```
    
    - zookeeper servers for view
    ```
    ZOOKEEPER_UI_SERVERS: "zk1:2181,zk2:2181,zk3:2181"
    ```
    
Example Playbook
----------------

Example playbook for install zk-ui enabled on boot, with port 9999

    - hosts: servers
      roles:
         - { role: zookeeper-ui, ZOOKEEPER_UI_PORT: 9999 }
