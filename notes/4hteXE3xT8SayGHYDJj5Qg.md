### Report 

Below is a plain-text, copy-paste-friendly version of all 23 findings. I have kept the same structure for every issue.
============================================================
	1. ISSUE: Insufficient Kernel Module Hardening
SEVERITY: Low
============================================================ 
OBSERVATION:
The test team observed that unnecessary filesystem and removable-storage kernel modules were not disabled on the assessed endpoint, which increases the operating system attack surface by allowing support for filesystem types and device functionality that may not be required for normal business operations.
In the current scenario, the test team observed that:
	1. The cramfs kernel module was not disabled. 
	2. The freevxfs kernel module was not disabled. 
	3. The hfs kernel module was not disabled. 
	4. The hfsplus kernel module was not disabled. 
	5. The jffs2 kernel module was not disabled. 
	6. No configuration was identified to disable the squashfs kernel module. 
	7. The udf kernel module was not disabled. 
	8. No configuration was identified to disable the usb-storage kernel module. 
RISK IMPACT:
An attacker can leverage unnecessary kernel modules to increase the available attack surface of the endpoint and potentially interact with unsupported or unnecessary filesystem formats or removable-storage functionality. A vulnerable kernel module or malicious filesystem may increase the likelihood of endpoint compromise.
RECOMMENDATION:
It is recommended to disable unnecessary filesystem and removable-storage kernel modules that are not required for legitimate business operations by following the below mentioned steps:
	1. Create the kernel hardening configuration file: 
vi /etc/modprobe.d/99-filesystem-hardening.conf
	2. Add the following configuration: 
install cramfs /bin/false
blacklist cramfs
install freevxfs /bin/false
blacklist freevxfs
install hfs /bin/false
blacklist hfs
install hfsplus /bin/false
blacklist hfsplus
install jffs2 /bin/false
blacklist jffs2
install squashfs /bin/false
blacklist squashfs
install udf /bin/false
blacklist udf
install usb-storage /bin/false
blacklist usb-storage
	3. After confirming that the modules are not operationally required, unload currently loaded modules: 
modprobe -r cramfs
modprobe -r freevxfs
modprobe -r hfs
modprobe -r hfsplus
modprobe -r jffs2
modprobe -r squashfs
modprobe -r udf
modprobe -r usb-storage
	4. Update the initial RAM filesystem: 
update-initramfs -u
REFERENCE:
https://www.cisecurity.org/benchmark/ubuntu_linux
============================================================
2. ISSUE: Insufficient Filesystem Partition and Mount Hardening
SEVERITY: Low
OBSERVATION:
The test team observed that the assessed endpoint was not configured with adequate filesystem partitioning and restrictive mount options.
In the current scenario, the test team observed that:
	1. /tmp, /home, /var, /var/tmp, /var/log, and /var/log/audit were not configured as separate partitions or mount points. 
	2. /dev/shm did not have the noexec mount option configured. 
RISK IMPACT:
An attacker can leverage insufficient filesystem isolation after gaining access to increase the impact of a compromise. Disk exhaustion within one directory may affect other system functions, while executable content stored under /dev/shm may provide an additional location for malicious code execution.
RECOMMENDATION:
It is recommended to configure separate partitions or logical volumes for critical filesystem paths by following the below mentioned steps:
	1. Review the existing filesystem layout: 
lsblk
findmnt
df -h
	2. During an approved maintenance window, create dedicated partitions or logical volumes for: 
/tmp
/home
/var
/var/tmp
/var/log
/var/log/audit
	3. Configure the new filesystems in /etc/fstab using appropriate restrictive mount options. 
Additionally, it is recommended to configure the noexec, nodev, and nosuid options on /dev/shm:
	4. Edit /etc/fstab: 
vi /etc/fstab
	5. Add or update: 
tmpfs /dev/shm tmpfs defaults,nodev,nosuid,noexec 0 0
	6. Apply the configuration: 
mount -o remount,nodev,nosuid,noexec /dev/shm
	7. Verify the configuration: 
findmnt /dev/shm
REFERENCE:
https://www.cisecurity.org/benchmark/ubuntu_linux
============================================================
3. ISSUE: Insecure File and Directory Permission Configuration
SEVERITY: Low
OBSERVATION:
The test team observed that insecure file and directory permission conditions were present on the assessed endpoint.
In the current scenario, the test team observed that:
	1. World-writable directories without sticky-bit protection were identified. 
	2. A world-writable file was identified. 
	3. One or more files or directories without a valid associated group were identified. 
	4. User home-directory validation did not meet the required security baseline. 
RISK IMPACT:
An attacker can abuse excessive permissions to modify, replace, or delete files accessible to other users or processes. Improper ownership may also enable unauthorized access or manipulation of system or application files.
RECOMMENDATION:
It is recommended to restrict excessive file and directory permissions by following the below mentioned steps:
	1. Identify world-writable directories without sticky-bit protection: 
find / -xdev -type d -perm -0002 ! -perm -1000 -print
	2. Apply sticky-bit protection where required: 
chmod a+t <directory>
	3. Identify world-writable files: 
find / -xdev -type f -perm -0002 -print
	4. Remove unnecessary world-write permission: 
chmod o-w <file>
	5. Identify files or directories without a valid group: 
find / -xdev -nogroup -print
	6. Assign an approved group: 
chgrp <approved_group> <file_or_directory>
	7. Configure appropriate ownership and permissions on user home directories: 
chown <user>:<group> /home/<user>
chmod 750 /home/<user>
REFERENCE:
https://www.cisecurity.org/benchmark/ubuntu_linux
============================================================
4. ISSUE: Insufficient Mandatory Access Control Enforcement
SEVERITY: Medium
OBSERVATION:
The test team observed that AppArmor mandatory access controls were not fully enforced on the assessed endpoint.
In the current scenario, the test team observed that 91 AppArmor profiles were operating in unconfined mode and 37 running processes were unconfined despite having AppArmor profiles defined.
RISK IMPACT:
An attacker can exploit an application operating without effective AppArmor confinement to access system resources beyond the restrictions that would otherwise be applied, increasing the impact of an application compromise.
RECOMMENDATION:
It is recommended to ensure that applicable AppArmor profiles are configured in enforce mode by following the below mentioned steps:
	1. Review the current AppArmor status: 
aa-status
	2. Install AppArmor utilities if required: 
apt install apparmor-utils
	3. Review and test profiles operating in complain or unconfined mode. 
	4. Set approved profiles to enforce mode: 
aa-enforce /etc/apparmor.d/<profile_name>
	5. Reload AppArmor: 
systemctl reload apparmor
	6. Verify the configuration: 
aa-status
REFERENCE:
https://documentation.ubuntu.com/security/security-features/privilege-restriction/apparmor/
============================================================
5. ISSUE: Inadequate Bootloader Access Protection
SEVERITY: Low
OBSERVATION:
The test team observed that adequate bootloader access protection was not configured on the assessed endpoint.
In the current scenario, the test team observed that a valid GRUB superuser and password protection configuration could not be successfully validated.
RISK IMPACT:
An attacker can use physical or console access to modify boot parameters and attempt to bypass operating system security restrictions where bootloader authentication is not configured.
RECOMMENDATION:
It is recommended to configure GRUB bootloader authentication by following the below mentioned steps:
	1. Generate a PBKDF2 protected password: 
grub-mkpasswd-pbkdf2
	2. Edit the GRUB custom configuration: 
vi /etc/grub.d/40_custom
	3. Configure an authorized GRUB superuser: 
set superusers="grubadmin"
password_pbkdf2 grubadmin <generated_PBKDF2_hash>
	4. Regenerate the GRUB configuration: 
update-grub
	5. Reboot during an approved maintenance window and verify that protected GRUB changes require authentication. 
REFERENCE:
https://www.cisecurity.org/benchmark/ubuntu_linux
============================================================
6. ISSUE: Insufficient Core Dump Protection
SEVERITY: Low
OBSERVATION:
The test team observed that restrictions for core dump storage and backtrace generation were not adequately configured on the assessed endpoint.
In the current scenario, the test team observed that the configuration review failed the required core dump protection check.
RISK IMPACT:
An attacker can access sensitive information stored within process memory dumps, potentially exposing credentials, authentication tokens, cryptographic material, or application data.
RECOMMENDATION:
It is recommended to disable unnecessary core dump storage and processing by following the below mentioned steps:
	1. Create a systemd coredump hardening configuration: 
mkdir -p /etc/systemd/coredump.conf.d
vi /etc/systemd/coredump.conf.d/99-hardening.conf
	2. Add: 
[Coredump]
Storage=none
ProcessSizeMax=0
	3. Reload the systemd configuration: 
systemctl daemon-reload
	4. Verify the configuration: 
systemd-analyze cat-config systemd/coredump.conf
REFERENCE:
https://manpages.ubuntu.com/manpages/jammy/man8/systemd-coredump.8.html
============================================================
7. ISSUE: Insecure Graphical Login Configuration
SEVERITY: Low
OBSERVATION:
The test team observed that the graphical login configuration allowed user account information to be displayed on the login screen.
In the current scenario, the test team observed that GDM user-list hiding was not enabled.
RISK IMPACT:
An attacker can identify valid usernames from the login screen and use this information to support credential guessing or targeted authentication attacks.
RECOMMENDATION:
It is recommended to disable the GDM user list by following the below mentioned steps:
	1. Create or edit the GDM dconf profile: 
vi /etc/dconf/profile/gdm
	2. Add: 
user-db:user
system-db:gdm
file-db:/usr/share/gdm/greeter-dconf-defaults
	3. Create the login screen configuration: 
mkdir -p /etc/dconf/db/gdm.d
vi /etc/dconf/db/gdm.d/00-login-screen
	4. Add: 
[org/gnome/login-screen]
disable-user-list=true
	5. Apply the configuration: 
dconf update
REFERENCE:
https://help.gnome.org/system-admin-guide/login-userlist-disable.html
============================================================
8. ISSUE: Unnecessary Services and System Components Installed
SEVERITY: Low
OBSERVATION:
The test team observed that unnecessary services and system components were installed on the assessed endpoint.
In the current scenario, the test team observed that Avahi, CUPS, rsync, and X Server components were installed. Avahi, CUPS, and Xorg processes were also running during the assessment.
RISK IMPACT:
An attacker can target unnecessary services and software components to increase the available attack surface and potentially exploit vulnerabilities or insecure configurations within them.
RECOMMENDATION:
It is recommended to remove or disable unnecessary services by following the below mentioned steps:
	1. If Avahi is not operationally required: 
systemctl disable --now avahi-daemon
apt purge avahi-daemon
	2. If printing functionality is not required: 
systemctl disable --now cups
systemctl disable --now cups-browsed
apt purge cups cups-browsed
	3. If rsync is not required: 
apt purge rsync
	4. Review installed X Server components: 
dpkg -l | grep -E 'xserver|xorg'
	5. If the graphical interface is not required, remove unnecessary X Server packages: 
apt purge <unnecessary_X_server_packages>
REFERENCE:
https://www.cisecurity.org/benchmark/ubuntu_linux
============================================================
9. ISSUE: Legacy and Unnecessary Network Client Software Installed
SEVERITY: Low
OBSERVATION:
The test team observed that legacy and unnecessary network client software was installed on the assessed endpoint.
In the current scenario, the test team observed that FTP, Telnet, and LDAP client utilities were installed.
RISK IMPACT:
An attacker can leverage legacy network clients to facilitate insecure communications or connect to malicious services. Traditional FTP and Telnet communications may expose credentials or sensitive information when used without transport protection.
RECOMMENDATION:
It is recommended to remove unnecessary network client software by following the below mentioned steps:
	1. Remove the FTP client if not required: 
apt purge ftp
	2. Remove the Telnet client: 
apt purge telnet
	3. Remove LDAP utilities if not operationally required: 
apt purge ldap-utils
	4. Verify installed packages: 
dpkg -l | grep -E 'ftp|telnet|ldap-utils'
REFERENCE:
https://www.cisecurity.org/benchmark/ubuntu_linux
============================================================
10. ISSUE: Inadequate Time Synchronization Configuration
SEVERITY: Low
OBSERVATION:
The test team observed that an approved time synchronization service was not active on the assessed endpoint.
In the current scenario, the test team observed that chrony, systemd-timesyncd, and ntp were not detected as active time synchronization mechanisms.
RISK IMPACT:
An attacker can benefit from inaccurate system time because inconsistent timestamps can reduce the reliability of log correlation, authentication controls, certificate validation, and incident investigation.
RECOMMENDATION:
It is recommended to configure an approved time synchronization service by following the below mentioned steps:
	1. Install Chrony: 
apt update
apt install chrony
	2. Configure the approved NTP server: 
vi /etc/chrony/chrony.conf
	3. Add: 
server <approved_NTP_server> iburst
	4. Enable and start Chrony: 
systemctl enable --now chrony
	5. Verify synchronization: 
chronyc tracking
chronyc sources -v
REFERENCE:
https://www.cisecurity.org/benchmark/ubuntu_linux
============================================================
11. ISSUE: Inadequate Cron Access and Permission Hardening
SEVERITY: Low
OBSERVATION:
The test team observed that cron configuration files and directories were not configured with the required restrictive permissions and cron access was not explicitly restricted.
In the current scenario, the test team observed that /etc/crontab had permissions 644, multiple /etc/cron.* directories had permissions 755, and cron.allow was not present.
RISK IMPACT:
An attacker can benefit from insufficiently restricted scheduled-task configuration by gaining unnecessary visibility into scheduled jobs or attempting to misuse cron functionality for persistence or recurring command execution.
RECOMMENDATION:
It is recommended to set the permissions for time-based job schedulers properly by following the below mentioned steps:
	1. Set ownership and permissions on /etc/crontab: 
chown root:root /etc/crontab
chmod og-rwx /etc/crontab
	2. Set ownership and permissions on /etc/cron.hourly: 
chown root:root /etc/cron.hourly/
chmod og-rwx /etc/cron.hourly/
	3. Set ownership and permissions on /etc/cron.daily: 
chown root:root /etc/cron.daily/
chmod og-rwx /etc/cron.daily/
	4. Set ownership and permissions on /etc/cron.weekly: 
chown root:root /etc/cron.weekly/
chmod og-rwx /etc/cron.weekly/
	5. Set ownership and permissions on /etc/cron.monthly: 
chown root:root /etc/cron.monthly/
chmod og-rwx /etc/cron.monthly/
	6. Set ownership and permissions on /etc/cron.d: 
chown root:root /etc/cron.d/
chmod og-rwx /etc/cron.d/
Additionally, it is recommended to restrict cron access to approved users:
touch /etc/cron.allow
chown root:root /etc/cron.allow
chmod 640 /etc/cron.allow
Add only authorized usernames to /etc/cron.allow.
REFERENCE:
https://www.cisecurity.org/benchmark/ubuntu_linux
============================================================
12. ISSUE: Inadequate Network Protocol Module Hardening
SEVERITY: Low
OBSERVATION:
The test team observed that unnecessary network protocol kernel modules were not adequately disabled.
In the current scenario, the test team observed that DCCP, TIPC, RDS, and SCTP were not explicitly disabled.
RISK IMPACT:
An attacker can leverage unnecessary network protocol functionality to increase the available attack surface and potentially exploit vulnerabilities within unused protocol implementations.
RECOMMENDATION:
It is recommended to disable unnecessary network protocol modules by following the below mentioned steps:
	1. Create a configuration file: 
vi /etc/modprobe.d/99-network-protocol-hardening.conf
	2. Add: 
install dccp /bin/false
blacklist dccp
install tipc /bin/false
blacklist tipc
install rds /bin/false
blacklist rds
install sctp /bin/false
blacklist sctp
	3. After confirming the modules are not required, unload them: 
modprobe -r dccp
modprobe -r tipc
modprobe -r rds
modprobe -r sctp
	4. Update the initial RAM filesystem: 
update-initramfs -u
REFERENCE:
https://www.cisecurity.org/benchmark/ubuntu_linux
============================================================
13. ISSUE: Insecure Network Stack Configuration
SEVERITY: Medium
OBSERVATION:
The test team observed that multiple IPv4 and IPv6 network stack security parameters were not configured in accordance with the required endpoint hardening baseline.
In the current scenario, the test team observed that ICMP redirects were accepted and sent, source routing was insufficiently restricted, reverse-path filtering did not meet the baseline, IPv6 router advertisements and redirects were accepted, and martian packet logging was disabled.
RISK IMPACT:
An attacker can abuse insecure network stack behaviour to influence routing, attempt traffic redirection or spoofing attacks, and reduce visibility of suspicious network activity.
RECOMMENDATION:
It is recommended to harden the IPv4 and IPv6 network stack by following the below mentioned steps:
	1. Create the sysctl hardening file: 
vi /etc/sysctl.d/60-network-hardening.conf
	2. Add: 
net.ipv4.conf.all.accept_redirects = 0
net.ipv4.conf.default.accept_redirects = 0
net.ipv4.conf.all.secure_redirects = 0
net.ipv4.conf.default.secure_redirects = 0
net.ipv4.conf.all.send_redirects = 0
net.ipv4.conf.default.send_redirects = 0
net.ipv4.conf.all.accept_source_route = 0
net.ipv4.conf.default.accept_source_route = 0
net.ipv4.conf.all.rp_filter = 1
net.ipv4.conf.default.rp_filter = 1
net.ipv4.conf.all.log_martians = 1
net.ipv4.conf.default.log_martians = 1
net.ipv6.conf.all.accept_redirects = 0
net.ipv6.conf.default.accept_redirects = 0
net.ipv6.conf.all.accept_ra = 0
net.ipv6.conf.default.accept_ra = 0
	3. Apply: 
sysctl --system
	4. Verify relevant parameters: 
sysctl net.ipv4.conf.all.accept_redirects
sysctl net.ipv4.conf.all.send_redirects
sysctl net.ipv4.conf.all.rp_filter
sysctl net.ipv4.conf.all.log_martians
sysctl net.ipv6.conf.all.accept_ra
REFERENCE:
https://docs.kernel.org/networking/ip-sysctl.html
============================================================
14. ISSUE: Inadequate Host-Based Firewall Configuration
SEVERITY: Medium
OBSERVATION:
The test team observed that the host-based firewall was not securely configured on the assessed endpoint.
In the current scenario, the test team observed that the firewall status was inactive and INPUT, FORWARD, and OUTPUT policies were configured to ACCEPT.
RISK IMPACT:
An attacker can communicate directly with exposed network services where restrictive host-based firewall rules are absent, increasing the likelihood of service exploitation and lateral movement.
RECOMMENDATION:
It is recommended to enable and configure an approved host-based firewall by following the below mentioned steps:
	1. Install UFW if required: 
apt install ufw
	2. Before enabling the firewall, permit approved management access: 
ufw allow from <trusted_management_subnet> to any port <management_port> proto tcp
	3. Configure restrictive default policies: 
ufw default deny incoming
ufw default deny routed
ufw default allow outgoing
	4. Add explicit rules only for required services: 
ufw allow from <trusted_source> to any port <required_port> proto tcp
	5. Enable the firewall: 
ufw enable
	6. Verify: 
ufw status verbose
REFERENCE:
https://documentation.ubuntu.com/server/how-to/security/firewalls/
============================================================
15. ISSUE: Insufficient Privilege Escalation Controls
SEVERITY: Medium
OBSERVATION:
The test team observed that privilege escalation controls related to sudo and su were not adequately hardened.
In the current scenario, the test team observed that a dedicated sudo logfile was not configured, sudo authentication timeout was not explicitly restricted, and su access was not restricted through pam_wheel.
RISK IMPACT:
An attacker can benefit from weak privilege escalation controls by abusing cached administrative authentication or unrestricted privilege-changing mechanisms, while insufficient sudo logging can reduce audit visibility.
RECOMMENDATION:
It is recommended to strengthen sudo logging and authentication controls by following the below mentioned steps:
	1. Create a dedicated sudoers configuration: 
visudo -f /etc/sudoers.d/99-hardening
	2. Add: 
Defaults logfile="/var/log/sudo.log"
Defaults timestamp_timeout=15
	3. Set permissions: 
chmod 440 /etc/sudoers.d/99-hardening
Additionally, it is recommended to restrict su access:
	4. Create a dedicated group: 
groupadd sugroup
	5. Add approved administrators: 
usermod -aG sugroup <authorized_admin>
	6. Edit: 
vi /etc/pam.d/su
	7. Enable: 
auth required pam_wheel.so use_uid group=sugroup
REFERENCE:
https://www.sudo.ws/docs/
============================================================
16. ISSUE: Weak Password Authentication and Account Lockout Policy
SEVERITY: Medium
OBSERVATION:
The test team observed that password authentication and account lockout controls were not adequately configured.
In the current scenario, the test team observed deficiencies involving password length, password complexity, password history, failed-login lockout, unlock duration, pam_faillock, and the presence of the nullok option.
RISK IMPACT:
An attacker can perform password guessing and credential attacks more effectively when password strength, password history, and account lockout controls are weak or absent.
RECOMMENDATION:
It is recommended to configure a strong PAM password and account lockout policy by following the below mentioned steps:
	1. Back up the existing PAM files: 
cp -a /etc/pam.d/common-auth /etc/pam.d/common-auth.bak
cp -a /etc/pam.d/common-account /etc/pam.d/common-account.bak
cp -a /etc/pam.d/common-password /etc/pam.d/common-password.bak
	2. Install password quality support: 
apt install libpam-pwquality
	3. Edit: 
vi /etc/security/pwquality.conf
Configure:
minlen = 14
minclass = 4
	4. Configure account lockout: 
vi /etc/security/faillock.conf
Configure an approved policy, for example:
deny = 5
unlock_time = 900
	5. Configure password history: 
vi /etc/security/pwhistory.conf
Add:
remember = 24
	6. Ensure applicable PAM password-quality and password-history modules are enabled. 
	7. Configure pam_faillock in the PAM authentication and account stacks according to the approved security baseline. 
	8. Remove the nullok option from pam_unix.so authentication entries. 
	9. Test authentication functionality before terminating the existing administrative session. 
REFERENCE:
https://www.cisecurity.org/benchmark/ubuntu_linux
============================================================
17. ISSUE: Weak Account Defaults and Password Aging Configuration
SEVERITY: Low
OBSERVATION:
The test team observed that user account defaults and password aging parameters were not configured according to the required endpoint security baseline.
In the current scenario, the test team observed that PASS_MAX_DAYS was configured as 99999, PASS_MIN_DAYS was configured as 0, inactive-account locking was disabled, and the default UMASK was configured as 022.
RISK IMPACT:
An attacker can benefit from compromised credentials remaining valid for excessive periods, inactive accounts remaining accessible, and newly created files receiving broader permissions than necessary.
RECOMMENDATION:
It is recommended to configure secure password aging and account defaults by following the below mentioned steps:
	1. Edit: 
vi /etc/login.defs
	2. Configure: 
PASS_MAX_DAYS 365
PASS_MIN_DAYS 1
UMASK 027
	3. Configure new accounts to be disabled after the approved period of password inactivity: 
useradd -D -f 30
	4. Apply password aging settings to applicable existing accounts: 
chage --maxdays 365 --mindays 1 --inactive 30 <username>
	5. Verify: 
chage -l <username>
REFERENCE:
https://www.cisecurity.org/benchmark/ubuntu_linux
============================================================
18. ISSUE: Insufficient System Account Login Restrictions
SEVERITY: Low
OBSERVATION:
The test team observed that the system-account login restriction control did not successfully meet the required endpoint security baseline.
In the current scenario, the test team observed that the automated review did not confirm that all applicable system accounts were restricted to non-interactive shells.
RISK IMPACT:
An attacker can potentially misuse a system or service account for interactive access if that account has an interactive shell and valid authentication credentials.
RECOMMENDATION:
It is recommended to restrict interactive access for system and service accounts by following the below mentioned steps:
	1. Identify system accounts with interactive shells: 
awk -F: '($3 < 1000 && $1!="root" && $1!="sync" && $1!="shutdown" && $1!="halt" && $7 !~ /(nologin|false)$/){print $1 ":" $7}' /etc/passwd
	2. Review each account to determine whether interactive login is required. 
	3. Configure a non-interactive shell where appropriate: 
usermod -s /usr/sbin/nologin <service_account>
	4. Lock passwords for applicable service accounts: 
passwd -l <service_account>
REFERENCE:
https://www.cisecurity.org/benchmark/ubuntu_linux
============================================================
19. ISSUE: Inadequate Security Logging Configuration
SEVERITY: Low
OBSERVATION:
The test team observed that system logging controls were not fully configured according to the required security baseline.
In the current scenario, the test team observed deficiencies involving persistent journal storage, journal compression, remote rsyslog forwarding, and permissions of at least one log file.
RISK IMPACT:
An attacker can benefit from inadequate security logging because malicious activity may not be reliably retained, centrally collected, or protected against unauthorized access.
RECOMMENDATION:
It is recommended to configure persistent and protected system logging by following the below mentioned steps:
	1. Create the journald configuration: 
mkdir -p /etc/systemd/journald.conf.d
vi /etc/systemd/journald.conf.d/99-hardening.conf
	2. Add: 
[Journal]
Storage=persistent
Compress=yes
	3. Create the persistent journal directory if required: 
mkdir -p /var/log/journal
	4. Restart journald: 
systemctl restart systemd-journald
Additionally, it is recommended to configure centralized rsyslog forwarding:
	5. Create: 
vi /etc/rsyslog.d/60-remote.conf
	6. Configure the approved remote logging server: 
. @@<approved_log_server>:514
	7. Restart rsyslog: 
systemctl restart rsyslog
	8. Correct excessive permissions on identified log files: 
chown root:adm /var/log/apt/history.log.2.gz
chmod 640 /var/log/apt/history.log.2.gz
REFERENCE:
https://www.cisecurity.org/benchmark/ubuntu_linux
============================================================
20. ISSUE: System Auditing Not Enabled
SEVERITY: Medium
OBSERVATION:
The test team observed that the Linux auditing framework was not installed on the assessed endpoint.
In the current scenario, the test team observed that auditd was not installed.
RISK IMPACT:
An attacker can perform security-sensitive actions with reduced audit visibility when the operating system auditing framework is unavailable, making security monitoring and forensic investigation more difficult.
RECOMMENDATION:
It is recommended to install and configure the Linux auditing framework by following the below mentioned steps:
	1. Install audit packages: 
apt update
apt install auditd audispd-plugins
	2. Enable and start auditd: 
systemctl enable --now auditd
	3. Configure audit rules under: 
/etc/audit/rules.d/
For example:
vi /etc/audit/rules.d/50-identity.rules
Add:
-w /etc/passwd -p wa -k identity
-w /etc/group -p wa -k identity
-w /etc/shadow -p wa -k identity
-w /etc/sudoers -p wa -k scope
-w /etc/sudoers.d/ -p wa -k scope
	4. Load the rules: 
augenrules --load
	5. Verify: 
auditctl -l
systemctl status auditd
REFERENCE:
https://www.cisecurity.org/benchmark/ubuntu_linux
============================================================
21. ISSUE: File Integrity Monitoring Not Configured
SEVERITY: Low
OBSERVATION:
The test team observed that file integrity monitoring was not configured on the assessed endpoint.
In the current scenario, the test team observed that AIDE was not installed and a periodic AIDE integrity check was not configured.
RISK IMPACT:
An attacker can modify critical files, executables, or configuration files with a reduced likelihood of those changes being detected when file integrity monitoring is absent.
RECOMMENDATION:
It is recommended to implement file integrity monitoring by following the below mentioned steps:
	1. Install AIDE: 
apt update
apt install aide aide-common
	2. Initialize the AIDE database: 
aideinit
	3. Verify that AIDE can perform an integrity check: 
aide --check
	4. Configure a periodic integrity check: 
vi /etc/cron.d/aide-check
	5. Add an approved schedule, for example: 
0 5 * * * root /usr/bin/aide --check
	6. Secure the configuration: 
chown root:root /etc/cron.d/aide-check
chmod 600 /etc/cron.d/aide-check
REFERENCE:
https://aide.github.io/
============================================================
22. ISSUE: Unrestricted Exposure of Network Services
SEVERITY: Medium
OBSERVATION:
The test team observed that multiple application and backend services were configured to listen on all available network interfaces rather than being restricted to required interfaces or trusted network sources.
In the current scenario, the test team observed that the following services were listening on wildcard interfaces:
	1. Nginx on TCP port 80. 
	2. Erlang EPMD on TCP port 4369. 
	3. Erlang/RabbitMQ on TCP port 25672. 
	4. RabbitMQ on TCP port 5672. 
	5. MySQL on TCP port 3306. 
	6. OnlyOffice Node service on TCP port 8000. 
RISK IMPACT:
An attacker can directly interact with unnecessarily exposed backend services from reachable network segments. If one of these services contains a vulnerability, weak authentication, or insecure configuration, it may enable unauthorized access, information disclosure, denial of service, or lateral movement.
RECOMMENDATION:
It is recommended to restrict backend services to the minimum required network interfaces and trusted sources by following the below mentioned steps:
	1. Review all listening services: 
ss -lntup
	2. Where MySQL is required only locally, configure: 
bind-address = 127.0.0.1
	3. Configure RabbitMQ, Erlang, and internal OnlyOffice services to listen only on localhost or approved application interfaces where remote access is not required. 
Additionally, it is recommended to restrict backend ports through the host firewall:
	4. Deny unnecessary remote access: 
ufw deny 3306/tcp
ufw deny 5672/tcp
ufw deny 4369/tcp
ufw deny 25672/tcp
ufw deny 8000/tcp
	5. Where access is legitimately required, permit only trusted sources before applying restrictive rules: 
ufw allow from <trusted_application_subnet> to any port <required_port> proto tcp
	6. Review TCP port 80 and redirect HTTP traffic to HTTPS where HTTP is required only for redirection. 
	7. Verify: 
ss -lntup
ufw status numbered
REFERENCE:
https://documentation.ubuntu.com/server/how-to/security/firewalls/
============================================================
23. ISSUE: Vulnerable and Outdated Software Packages Installed
SEVERITY: High
OBSERVATION:
The test team observed that multiple installed software packages were running outdated versions for which security updates had been released. The identified packages were associated with known vulnerabilities that may affect the confidentiality, integrity, or availability of the endpoint.
In the current scenario, the test team reviewed the installed package inventory and identified the following vulnerable or outdated components:
	1. AccountsService / libaccountsservice0 - Version 23.13.9-2ubuntu6 - CVE-2026-61897, CVE-2026-61898. 
	2. OpenSSL / libssl3t64 - Version 3.0.13-0ubuntu3.11 - HollowByte denial-of-service vulnerability. 
	3. systemd / systemd-oomd - Version 255.4-1ubuntu8.16 - CVE-2026-16742, CVE-2026-15059. 
	4. Samba libraries - Version 2:4.19.5+dfsg-4ubuntu9.6 - CVE-2026-15779, CVE-2026-6949, CVE-2026-58216, CVE-2026-58218, CVE-2026-58221, CVE-2026-58222, CVE-2026-58224. 
	5. Yelp / libyelp0 - Version 42.2-1ubuntu0.24.04.1 - CVE-2026-13601. 
	6. libarchive13t64 - Version 3.7.2-2ubuntu0.7 - CVE-2026-14164, CVE-2026-5745. 
	7. Kerberos / libkrb5-3 - Version 1.20.1-6ubuntu2.6 - CVE-2026-11850, CVE-2026-40355, CVE-2026-40356. 
	8. GIFLIB / libgif7 - Version 5.2.2-1ubuntu1 - CVE-2026-26740, CVE-2026-23868. 
	9. HTML::Parser - Version 3.81-1build3 - CVE-2026-8829. 
	10. libgphoto2 - Version 2.5.31-2.1ubuntu1 - Multiple memory-handling vulnerabilities. 
	11. Linux Kernel - Version 6.17.0-40 - Multiple Linux kernel vulnerabilities. 
RISK IMPACT:
An attacker can exploit vulnerabilities within outdated software to compromise the confidentiality, integrity, or availability of the endpoint. Depending on the affected component and attack prerequisites, exploitation may result in privilege escalation, arbitrary command execution, information disclosure, denial of service, or further endpoint compromise.
RECOMMENDATION:
It is recommended to update all vulnerable and outdated software packages to the latest vendor-supported security versions by following the below mentioned steps:
	1. Refresh repository information: 
apt update
	2. Review pending upgrades: 
apt list --upgradable
	3. Install applicable updates during an approved maintenance window: 
apt full-upgrade
	4. Verify that the identified packages are updated: 
apt list --upgradable
	5. Reboot the endpoint after updating kernel and critical system packages: 
reboot
	6. Verify the active kernel after reboot: 
uname -r
	7. After confirming that the updated kernel is functioning correctly, remove obsolete packages: 
apt autoremove
	8. Re-run the vulnerability assessment and endpoint configuration review to verify remediation. 
REFERENCE:
AccountsService:
https://ubuntu.com/security/notices/USN-8580-1
OpenSSL:
https://ubuntu.com/security/notices/USN-8625-1
systemd:
https://ubuntu.com/security/notices/USN-8626-1
Samba:
https://ubuntu.com/security/notices/USN-8621-1
CIS Ubuntu Linux Benchmark:
https://www.cisecurity.org/benchmark/ubuntu_linux
