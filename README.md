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
    vault_cluster_name: "vault-test-cluster"
    vault_gcp_auto_unseal:
      project: "gcp-project-name"
      keyring_name: "keyring-name"
      keyring_region: "europe-west2"
      key_name: "vault-key"

  roles:
    - vault
```

