Vault
=========

Role for Hashicorp Vault installation. 

Role Variables
--------------

To do

Example Playbook
----------------
```
- hosts: servers
  become: yes
  gather_facts: yes

  vars:
    aerospike_version: 6.4.0.6
    aerospike_tools_version: 9.2.1
    aerospike_edition: community
    aerospike_cluster_name: test
    aerospike_tune_os: true
    aerospike_ip: "{{ private_ip }}"
    aerospike_node_id: "{{ labels.node_id }}"
    aerospike_namespaces: |
      namespace test_runtime {
              replication-factor 1
              memory-size 50M
              default-ttl 1h
              nsup-period 1m
              high-water-memory-pct 60
              stop-writes-pct 90
              storage-engine memory
      }

      namespace test {
              replication-factor 1
              memory-size 200M
              default-ttl 1h
              nsup-period 1m
              high-water-memory-pct 60
              stop-writes-pct 90
              high-water-disk-pct 50
              storage-engine device {
                      file /opt/aerospike/data/test.dat
                      filesize 15G
                      data-in-memory false
              }
      }
      
    aerospike_exporter_install: true
    aerospike_exporter_version: "1.13.0"

  roles:
    - aerospike
```

