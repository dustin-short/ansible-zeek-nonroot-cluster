# ansible-zeek-nonroot-cluster

Ansible role that installs [Zeek](https://zeek.org/) (formerly Bro) and configures it to run as a non-root user

## Requirements

None.

## Encrypted with vault
        - roles/cluster/files/id.rsa
        - vault/geoip_vars.yml
            - contains the following variables for geo maxmind template
                - geoip_account
                - geoip_license

## Role Variables
Zeek Version
    
    zeek_ver: zeek-4.0.0
        -   Use the name of the zeek package minus the file extention
    repo_branch: release/4.0
        -   Use this variable to grab the correct branch from zeek GitHub Repository

Digest Salt

	- digest_salt: custom string

Enable json output ```set to yes to write logs as json instead of TSV```

	- enable_json: no

zkg packages to install

        - bzar
        - ja3

Zeek Directories

        - logdir: /zeek
        - zeekdir: /opt

Zeek Ports allowed on host base firewall ufw ```ssh and splunk ports added to ensure they are allowed```
        
        - port: ssh
        - port: 9997
          proto: tcp
        - port: 9996
          proto: tcp
        - port: 8000
          proto: tcp
        - port: 8089
          proto: tcp
        - port: 47760
          proto: tcp
        - port: 47761
          proto: tcp
        - port: 47762
          proto: tcp
        - port: 47763
          proto: tcp
        - port: 47764
          proto: tcp
        - port: 47765
          proto: tcp

Proxy Variables ```by setting use_proxy to yes all connections to the internet will use proxy```

        - use_proxy: yes
        - proxy_ip: x.x.x.x
        - proxy_port: 3128
