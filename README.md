# ansible-zeek-nonroot-cluster

Ansible role that installs [Zeek](https://zeek.org/) (formerly Bro) and configures it to run as a non-root user
## Requirements

```None```

## Role Variables
```Zeek Version``` 

Zeek package version minus the file extention
    
    zeek_ver: zeek-3.2.3


```Zeek User```

User to be created and used to run zeek

    zeek_user: zeek


```Zeek paths```

Install and log path for zeek

        - logpath: /zeek
        - zeekpath: /opt/zeek

```CPU Cores```

Specify how many CPU cores you want to allow to be used for building zeek from source. Defaults to system cpu count

    cpu_cores: 4