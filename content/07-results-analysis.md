# Results Analysis

## The Initial
- SSH is tough, it resists brute force attacks heavily.
- When you install SSH on Arch, by default, root login is disabled as well as many other configurations.  
- There are many sshd configurations that stand directly in the way of brute force attacks out of the box (MaxAuthTries, MaxStartups, LoginGraceTime, PermitRootLogin, etc...)[@sshd_config_manpage]


![](images/network-confirmation.png)