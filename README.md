# ansible-zeek-nonroot-cluster

Ansible role that installs [Zeek] (https://zeek.org/) (formerly Bro) and configures it to run as a non-root user
## Requirements

None.

## Role Variables
Zeek Version
    
    zeek_ver: zeek-3.2.3
Use the name of the zeek package minus the file extention

Zeek paths

        - dir: /zeek
        - dir: /opt/zeek
