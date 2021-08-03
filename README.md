# ansible-zeek-nonroot-cluster

Ansible role that installs [Zeek](https://zeek.org/) (formerly Bro) and configures it to run as a non-root user

## Requirements

None.

## Encrypted with vault
        - roles/cluster/files/id.rsa
        - vault/geoip_vars.yml
            - contains the following variables for geo maxmind template
                - geoip_account: <account number>
                - geoip_license: <license number>

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
        - hassh

Zeek Directories

        - logdir: /zeeklogdir
        - spooldir: /zeekspooldir
        - zeekdir: /opt/zeek

Log Retention

        - LogExpireInterval: 14
        - StatsLogExpireInterval: 30
        - CrashExpireInterval: 30

Zeek Ports allowed on host base firewall ufw
        
        - port: ssh
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

        - use_proxy: no
        - proxy_ip: x.x.x.x
        - proxy_port: 3128

Node.cfg configuration ```node.cfg is built using a jinja2 for loop. This allows you to add as many nodes as needed in the format below to create the node configuration.```

        - node_configuration:
          - name: zeek-manager
            type: manager
            host: localhost
          - name: zeek-proxy
            type: proxy
            host: localhost
          - name: zeek-logger
            type: logger
            host: localhost
        - worker_node_configuration:
          - name: zeek-worker-1
            pfring_interface: enp1s0f0
            worker_threads: 3
            host: localhost
          - name: zeek-worker-2
            pfring_interface: enp1s0f0
            worker_threads: 3
            host: localhost

