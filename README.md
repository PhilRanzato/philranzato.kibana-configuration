plrr.kibana-configuration
=========

Configure Kibana.

Requirements
------------

- Kibana installed on target host.
- Elasticsearch masters in the inventory.
- CA and certificate if ssl enabled.
- A builtin password file for the `kibana_system` user

Role Variables
--------------

```yaml
---
# Server and certificates variables
server:
  port: 5601
  host: "{{ hostvars[inventory_hostname].ansible_default_ipv4.address }}"
  name: "{{ inventory_hostname_short }}"
  ssl:
    enabled: false
    certificate: ""
    key: ""
    key_passphrase: ""

# utility variables to set kibana.yml parameters
elasticsearch_hosts_group_name: "elasticsearch_master"
kibana_user: ""
kibana_password: ""
elasticsearch_ssl_certificate_authorities:
- ""

elasticsearch:
  username: "{{ kibana_user }}"
  password: "{{ kibana_password }}"
  ssl:
    certificateAuthorities: "{{ elasticsearch_ssl_certificate_authorities }}"
  http_port: 9200
```

Dependencies
------------

None.

Example Playbook
----------------

```yaml
- name: "Configure Kibana"
  hosts: kibana
  roles:
  - { role: plrr.kibana-configuration }
  vars_files:
  - vars/kibana-config.yml
```

License
-------

Apache-2

Author Information
------------------

Get in touch with me at:
- [LinkedIn](www.linkedin.com/in/phil-ranzato-47b8bb194)
- [GitHub](https://github.com/PhilRanzato)
- [Medium](https://medium.com/@philranzato)
