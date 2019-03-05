# RHEL7-Notes


## Troubleshooting

1. sssd daemon
   
   * start **sssd**(systems security services daemon) with debug level '7' in interactive mode:
     ```
     #sssd -d7 -i
     ```

    * Or set option 'debug_level = 9' in the sssd section of /etc/sssd/sssd.conf:
        ```
        [sssd]
        config_file_version = 2
        services = nss, pam
        domains = default
        debug_level = 9
        ```    
    * logs will be collected in /var/log/sss/sssd.log
  
    * ##### SSSD Domain Status Information
        ```
        # sssctl domain-list
        # sssctl domain-status <domain>
        ```


2. 