# RHEL7-Notes

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
    * 


2.  ##### SSSD Domain Status Information
        
        # sssctl domain-list
        # sssctl domain-status <domain>
        

3. ##### SSSD Configuration Check
   
        
        # sssctl config-check
        

4. ##### SSSD Logging
    
    * truncating SSSD logs can now be done with sssctl
  
        ```
        # sssctl logs-remove
        ```
    * Deleting logs entirely
        ```
        # sssctl logs-remove -d
        ```

5. ##### Cache management
  
    * Removing the SSSD cache is useful to ensure testing does not use stale cached information, and ensuring SSSD can remain in an online state.
    *  If SSSD is offline and cached credentials are being used, removing the SSSD cache will prevent SSSD users from logging in.
        ```
        # sssctl cache-remove
        SSSD must not be running. Stop SSSD now? (yes/no) [yes] yes
        Creating backup of local data...
        SSSD backup of local data already exist, override? (yes/no) [no] yes
        Removing cache files...
        SSSD needs to be running. Start SSSD now? (yes/no) [yes] yes

        ```
