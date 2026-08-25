

















RHLHO02CC31-192.168.223.33




Below is the complete report for the 21 consolidated findings from the new endpoint. I have kept the format consistent with your earlier reports and used plain text for commands so the font size remains uniform.
============================================================
	1. ISSUE: Insufficient Kernel Module Hardening
SEVERITY: Low
============================================================
OBSERVATION:
The test team observed that unnecessary filesystem and removable-storage kernel modules were not disabled on the assessed endpoint, increasing the operating system attack surface.
In the current scenario, the test team observed that the following kernel modules were not appropriately disabled:
	1. cramfs
	2. freevxfs
	3. hfs
	4. hfsplus
	5. jffs2
	6. squashfs
	7. udf
	8. usb-storage
RISK IMPACT:
An attacker can leverage unnecessary kernel modules to increase the available attack surface and potentially interact with unsupported filesystem formats or removable-storage functionality. Exploitation of a vulnerable kernel module may result in unauthorized access or endpoint compromise.
RECOMMENDATION:
It is recommended to disable unnecessary filesystem and removable-storage kernel modules by following the below mentioned steps:
	1. Create a kernel module hardening configuration file:
vi /etc/modprobe.d/99-filesystem-hardening.conf
	2. Add the following entries:
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
	3. After confirming that the modules are not operationally required, unload any currently loaded modules:
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
CIS Ubuntu Linux Benchmark
============================================================
2. ISSUE: Insufficient Filesystem Partition and Mount Hardening
SEVERITY: Low
OBSERVATION:
The test team observed that filesystem partitioning and restrictive mount options were not adequately configured on the assessed endpoint.
In the current scenario, the test team observed that:
	1. /tmp was not configured as a separate partition or mount point.
	2. /dev/shm did not have the noexec option configured.
	3. /home did not have the nodev option configured.
	4. /home did not have the nosuid option configured.
	5. /var was not configured as a separate partition or mount point.
	6. /var/tmp was not configured as a separate partition or mount point.
	7. /var/log was not configured as a separate partition or mount point.
	8. /var/log/audit was not configured as a separate partition or mount point.
RISK IMPACT:
An attacker can leverage insufficient filesystem isolation and permissive mount options after obtaining access to increase the impact of a compromise. This may facilitate malicious file execution, device-file abuse, setuid-related attacks, or resource exhaustion affecting other areas of the system.
RECOMMENDATION:
It is recommended to configure separate partitions and restrictive mount options by following the below mentioned steps:
	1. Review the existing filesystem layout:
lsblk
findmnt
df -h
	2. During an approved maintenance window, create separate partitions or logical volumes for:
/tmp
/var
/var/tmp
/var/log
/var/log/audit
	3. Configure the required partitions in /etc/fstab.
	4. Configure restrictive mount options for /home, including nodev and nosuid.
	5. Configure /dev/shm with nodev, nosuid, and noexec.
Example:
tmpfs /dev/shm tmpfs defaults,nodev,nosuid,noexec 0 0
	6. Apply the configuration:
mount -o remount,nodev,nosuid,noexec /dev/shm
	7. Verify:
findmnt /dev/shm
findmnt /home
Partition changes should be performed during an approved maintenance window with a verified backup.
REFERENCE:
CIS Ubuntu Linux Benchmark
============================================================
3. ISSUE: Insecure File and Directory Permission Configuration
SEVERITY: Low
OBSERVATION:
The test team observed that insecure file and directory permission conditions were present on the assessed endpoint.
In the current scenario, the test team observed that:
	1. World-writable directories without sticky-bit protection were identified.
	2. A world-writable file was identified under /tmp.
	3. An ungrouped file or directory was identified within the ManageEngine UEMS Agent directory.
RISK IMPACT:
An attacker can abuse excessive file or directory permissions to modify, replace, or delete files accessible to other users or processes. Improper group ownership may also result in unauthorized access or manipulation of application data.
RECOMMENDATION:
It is recommended to restrict excessive file and directory permissions by following the below mentioned steps:
	1. Identify world-writable directories without sticky-bit protection:
find / -xdev -type d -perm -0002 ! -perm -1000 -print
	2. Apply the sticky bit to legitimate shared writable directories:
chmod a+t
	3. Identify world-writable files:
find / -xdev -type f -perm -0002 -print
	4. Remove unnecessary world-write permission:
chmod o-w
	5. Identify objects without a valid group:
find / -xdev -nogroup -print
	6. Assign the appropriate approved group:
chgrp <approved_group> <file_or_directory>
REFERENCE:
CIS Ubuntu Linux Benchmark
============================================================
4. ISSUE: Insufficient Mandatory Access Control Enforcement
SEVERITY: Medium
OBSERVATION:
The test team observed that AppArmor mandatory access controls were not fully enforced on the assessed endpoint.
In the current scenario, the test team observed that 126 AppArmor profiles were loaded, of which 25 were in enforce mode, 9 were in complain mode, and 92 were unconfined. Additionally, 52 running processes were identified as unconfined despite corresponding profiles being available.
RISK IMPACT:
An attacker can exploit an application operating without effective mandatory access control restrictions to access files, processes, or system resources beyond the application's intended requirements, thereby increasing the impact of a successful application compromise.
RECOMMENDATION:
It is recommended to ensure that applicable AppArmor profiles are configured in enforce mode by following the below mentioned steps:
	1. Review the current AppArmor status:
aa-status
	2. Install AppArmor utilities if required:
apt install apparmor-utils
	3. Review profiles operating in complain or unconfined mode and verify application compatibility.
	4. Configure approved profiles in enforce mode:
aa-enforce /etc/apparmor.d/<profile_name>
	5. Reload AppArmor:
systemctl reload apparmor
	6. Verify:
aa-status
REFERENCE:
Ubuntu AppArmor Documentation
CIS Ubuntu Linux Benchmark
============================================================
5. ISSUE: Inadequate Bootloader Access Protection
SEVERITY: Low
OBSERVATION:
The test team observed that adequate bootloader access protection was not configured on the assessed endpoint.
In the current scenario, the test team observed that a valid GRUB superuser and password protection configuration could not be successfully validated.
RISK IMPACT:
An attacker can use physical or console access to modify boot parameters and potentially bypass operating system security restrictions where bootloader authentication is not enforced.
RECOMMENDATION:
It is recommended to configure GRUB bootloader authentication by following the below mentioned steps:
	1. Generate a PBKDF2-protected GRUB password:
grub-mkpasswd-pbkdf2
	2. Edit:
vi /etc/grub.d/40_custom
	3. Add:
set superusers="grubadmin"
password_pbkdf2 grubadmin <generated_PBKDF2_hash>
	4. Regenerate the GRUB configuration:
update-grub
	5. Reboot the endpoint during an approved maintenance window and verify that unauthorized users cannot modify protected boot entries.
REFERENCE:
CIS Ubuntu Linux Benchmark
============================================================
6. ISSUE: Insufficient Core Dump Protection
SEVERITY: Low
OBSERVATION:
The test team observed that core dump protections were not adequately configured on the assessed endpoint, which may allow sensitive process memory to be retained.
In the current scenario, the test team observed that:
	1. fs.suid_dumpable was configured with a value of 2 instead of the required restrictive value.
	2. Core dump backtrace and storage restrictions did not meet the required baseline.
RISK IMPACT:
An attacker can access sensitive information contained within process memory dumps, potentially exposing credentials, authentication tokens, cryptographic material, application data, or other confidential information.
RECOMMENDATION:
It is recommended to restrict core dump generation and storage by following the below mentioned steps:
	1. Create or edit a sysctl configuration file:
vi /etc/sysctl.d/60-coredump-hardening.conf
	2. Configure:
fs.suid_dumpable = 0
	3. Apply the setting:
sysctl --system
	4. Create the systemd coredump configuration:
mkdir -p /etc/systemd/coredump.conf.d
vi /etc/systemd/coredump.conf.d/99-hardening.conf
	5. Add:
[Coredump]
Storage=none
ProcessSizeMax=0
	6. Reload systemd configuration:
systemctl daemon-reload
	7. Verify:
sysctl fs.suid_dumpable
systemd-analyze cat-config systemd/coredump.conf
REFERENCE:
CIS Ubuntu Linux Benchmark
systemd-coredump Documentation
============================================================
7. ISSUE: Unnecessary Services and System Components Installed
SEVERITY: Low
OBSERVATION:
The test team observed that unnecessary server services and system components were installed on the assessed endpoint, increasing the available attack surface.
In the current scenario, the test team observed that:
	1. Avahi was installed and running.
	2. CUPS was installed and running.
	3. rsync was installed.
	4. X Server components were installed and Xorg was running.
The running-process evidence confirms Avahi, CUPS, cups-browsed, and Xorg activity. Xorg was started with the "-nolisten tcp" option, and CUPS TCP port 631 was bound to loopback rather than an external interface.
RISK IMPACT:
An attacker can target unnecessary software and services for known vulnerabilities or configuration weaknesses, increasing the number of potential attack paths available on the endpoint.
RECOMMENDATION:
It is recommended to remove or disable unnecessary services and components by following the below mentioned steps:
	1. If Avahi is not required:
systemctl disable --now avahi-daemon
apt purge avahi-daemon
	2. If printing is not required:
systemctl disable --now cups
systemctl disable --now cups-browsed
apt purge cups cups-browsed
	3. If rsync is not required:
apt purge rsync
	4. Review X Server packages:
dpkg -l | grep -E 'xserver|xorg'
	5. If graphical desktop functionality is not operationally required, remove the unnecessary X Server components:
apt purge <unnecessary_X_server_packages>
Operational requirements should be verified before removing software.
REFERENCE:
CIS Ubuntu Linux Benchmark
============================================================
8. ISSUE: Legacy and Unnecessary Network Client Software Installed
SEVERITY: Low
OBSERVATION:
The test team observed that legacy and unnecessary network client software was installed on the assessed endpoint.
In the current scenario, the test team observed that FTP, Telnet, and LDAP client utilities were installed.
RISK IMPACT:
An attacker can leverage legacy network clients to facilitate insecure communications or connect users to malicious network services. FTP and Telnet may expose authentication credentials and transmitted information when used without encryption.
RECOMMENDATION:
It is recommended to remove unnecessary network client software by following the below mentioned steps:
	1. Remove the FTP client if not required:
apt purge ftp
	2. Remove the Telnet client if not required:
apt purge telnet
	3. Remove LDAP utilities if not operationally required:
apt purge ldap-utils
	4. Verify:
dpkg -l | grep -E 'ftp|telnet|ldap-utils'
Where functionality is required, secure alternatives such as SFTP/SSH and encrypted LDAP communications should be used.
REFERENCE:
CIS Ubuntu Linux Benchmark
============================================================
9. ISSUE: Inadequate Time Synchronization Configuration
SEVERITY: Low
OBSERVATION:
The test team observed that an approved system time synchronization mechanism was not active on the assessed endpoint.
In the current scenario, the test team observed that chrony, systemd-timesyncd, and ntp were not identified as active synchronization services.
RISK IMPACT:
An attacker can benefit from inaccurate system time because incorrect timestamps can interfere with security-event correlation, authentication mechanisms, certificate validation, and forensic investigation.
RECOMMENDATION:
It is recommended to configure an approved time synchronization mechanism by following the below mentioned steps:
	1. Install Chrony:
apt update
apt install chrony
	2. Edit:
vi /etc/chrony/chrony.conf
	3. Configure the organization's approved time server:
server <approved_NTP_server> iburst
	4. Enable and start Chrony:
systemctl enable --now chrony
	5. Verify synchronization:
chronyc tracking
chronyc sources -v
Only one approved time synchronization mechanism should be enabled to avoid configuration conflicts.
REFERENCE:
CIS Ubuntu Linux Benchmark
============================================================
10. ISSUE: Inadequate Cron Access and Permission Hardening
SEVERITY: Low
OBSERVATION:
The test team observed that cron configuration files and directories were configured with permissions broader than the required security baseline and cron access was not explicitly restricted.
In the current scenario, the test team observed that:
	1. /etc/crontab had permissions 644.
	2. /etc/cron.hourly had permissions 755.
	3. /etc/cron.daily had permissions 755.
	4. /etc/cron.weekly had permissions 755.
	5. /etc/cron.monthly had permissions 755.
	6. /etc/cron.d had permissions 755.
	7. /etc/cron.allow was not present.
The process evidence confirms that the cron daemon was running; therefore, the issue relates to cron permissions and access control rather than service availability.
RISK IMPACT:
An attacker can benefit from insufficient cron restrictions by gaining unnecessary visibility into scheduled jobs or potentially abusing scheduled-task functionality for persistence where other access conditions are met.
RECOMMENDATION:
It is recommended to set the ownership and permissions for cron configuration files and directories properly by following the below mentioned steps:
	1. Configure /etc/crontab:
chown root:root /etc/crontab
chmod og-rwx /etc/crontab
	2. Configure /etc/cron.hourly:
chown root:root /etc/cron.hourly/
chmod og-rwx /etc/cron.hourly/
	3. Configure /etc/cron.daily:
chown root:root /etc/cron.daily/
chmod og-rwx /etc/cron.daily/
	4. Configure /etc/cron.weekly:
chown root:root /etc/cron.weekly/
chmod og-rwx /etc/cron.weekly/
	5. Configure /etc/cron.monthly:
chown root:root /etc/cron.monthly/
chmod og-rwx /etc/cron.monthly/
	6. Configure /etc/cron.d:
chown root:root /etc/cron.d/
chmod og-rwx /etc/cron.d/
Additionally, it is recommended to restrict cron access to authorized users:
	7. Create:
touch /etc/cron.allow
	8. Configure:
chown root:root /etc/cron.allow
chmod 640 /etc/cron.allow
	9. Add only approved usernames to /etc/cron.allow.
REFERENCE:
CIS Ubuntu Linux Benchmark
============================================================
11. ISSUE: Inadequate Network Protocol Module Hardening
SEVERITY: Low
OBSERVATION:
The test team observed that unnecessary network protocol kernel modules were not explicitly disabled on the assessed endpoint.
In the current scenario, the test team observed that DCCP, TIPC, RDS, and SCTP were not appropriately disabled.
RISK IMPACT:
An attacker can leverage unnecessary network protocol functionality to increase the operating system attack surface and potentially exploit vulnerabilities in protocol implementations that are not required for normal business operations.
RECOMMENDATION:
It is recommended to disable unnecessary network protocol kernel modules by following the below mentioned steps:
	1. Create:
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
	3. After confirming that the protocols are not required:
modprobe -r dccp
modprobe -r tipc
modprobe -r rds
modprobe -r sctp
	4. Update the initial RAM filesystem:
update-initramfs -u
REFERENCE:
CIS Ubuntu Linux Benchmark
============================================================
12. ISSUE: Insecure Network Stack Configuration
SEVERITY: Medium
OBSERVATION:
The test team observed that multiple IPv4 and IPv6 kernel network parameters were not configured according to the required endpoint security baseline.
In the current scenario, the test team observed that:
	1. IPv4 secure redirects were enabled for all and default interfaces.
	2. IPv4 reverse-path filtering was configured as 2 instead of the required value.
	3. IPv6 router advertisements were accepted.
	4. IPv4 default source routing was not adequately restricted.
	5. Martian packet logging was disabled.
	6. IPv4 ICMP redirects were configured to be sent.
RISK IMPACT:
An attacker can abuse insecure network stack behaviour to facilitate spoofing, traffic redirection, or routing-related attacks. Disabled martian packet logging may also reduce visibility of suspicious or malformed traffic.
RECOMMENDATION:
It is recommended to harden the network stack by following the below mentioned steps:
	1. Create:
vi /etc/sysctl.d/60-network-hardening.conf
	2. Add:
net.ipv4.conf.all.secure_redirects = 0
net.ipv4.conf.default.secure_redirects = 0
net.ipv4.conf.all.rp_filter = 1
net.ipv4.conf.default.rp_filter = 1
net.ipv4.conf.default.accept_source_route = 0
net.ipv4.conf.all.send_redirects = 0
net.ipv4.conf.default.send_redirects = 0
net.ipv4.conf.all.log_martians = 1
net.ipv4.conf.default.log_martians = 1
net.ipv6.conf.all.accept_ra = 0
net.ipv6.conf.default.accept_ra = 0
	3. Apply:
sysctl --system
	4. Verify:
sysctl net.ipv4.conf.all.secure_redirects
sysctl net.ipv4.conf.all.rp_filter
sysctl net.ipv4.conf.all.send_redirects
sysctl net.ipv4.conf.all.log_martians
sysctl net.ipv6.conf.all.accept_ra
IPv6 router-advertisement requirements should be validated against the network architecture before disabling them.
REFERENCE:
Linux Kernel IP Sysctl Documentation
CIS Ubuntu Linux Benchmark
============================================================
13. ISSUE: Inadequate Host-Based Firewall Configuration
SEVERITY: Medium
OBSERVATION:
The test team observed that the host-based firewall was active but configured with an overly permissive inbound policy.
In the current scenario, the test team observed that UFW was active; however, the default incoming policy was configured as "allow". The IPv4 and IPv6 INPUT chains also showed an ACCEPT policy, while no restrictive rules were present in the UFW user-input chain. The required loopback protection control also did not meet the security baseline.
RISK IMPACT:
An attacker can communicate with network services listening on the endpoint from reachable network segments where inbound access is not explicitly restricted, thereby increasing the likelihood of service enumeration, exploitation, and lateral movement.
RECOMMENDATION:
It is recommended to configure the host-based firewall with a restrictive inbound policy by following the below mentioned steps:
	1. Before changing firewall policies on a remotely managed endpoint, allow the required management connection:
ufw allow from <trusted_management_subnet> to any port <management_port> proto tcp
	2. Configure the default incoming policy:
ufw default deny incoming
	3. Configure the default routed policy:
ufw default deny routed
	4. Maintain an approved outgoing policy:
ufw default allow outgoing
	5. Add explicit inbound rules only for required business services:
ufw allow from <trusted_source> to any port <required_port> proto tcp
	6. Ensure loopback traffic is permitted only through the loopback interface and spoofed loopback-source traffic from non-loopback interfaces is denied.
	7. Reload UFW:
ufw reload
	8. Verify:
ufw status verbose
iptables -S
nft list ruleset
REFERENCE:
Ubuntu Firewall Documentation
CIS Ubuntu Linux Benchmark
============================================================
14. ISSUE: Insufficient Privilege Escalation Controls
SEVERITY: Medium
OBSERVATION:
The test team observed that sudo and su privilege escalation controls were not adequately hardened on the assessed endpoint.
In the current scenario, the test team observed that:
	1. A dedicated sudo log file was not configured.
	2. A NOPASSWD sudo rule was present for /usr/bin/mintdrivers-remove-live-media.
	3. The sudo authentication timeout did not meet the required restrictive baseline.
	4. su access was not restricted through pam_wheel.
RISK IMPACT:
An attacker can abuse weak privilege escalation controls to perform administrative actions with reduced authentication requirements or benefit from cached administrative credentials. Insufficient sudo logging may also make privileged activity more difficult to trace.
RECOMMENDATION:
It is recommended to strengthen privilege escalation controls by following the below mentioned steps:
	1. Create a dedicated sudo hardening configuration:
visudo -f /etc/sudoers.d/99-hardening
	2. Add:
Defaults logfile="/var/log/sudo.log"
Defaults timestamp_timeout=15
	3. Review the identified NOPASSWD rule:
ALL ALL = NOPASSWD:/usr/bin/mintdrivers-remove-live-media
	4. Remove NOPASSWD access where passwordless execution is not operationally required.
	5. Validate sudo syntax:
visudo -c
Additionally, it is recommended to restrict su access:
	6. Create an approved administrative group if required:
groupadd sugroup
	7. Add authorized administrators:
usermod -aG sugroup <authorized_admin>
	8. Edit:
vi /etc/pam.d/su
	9. Enable:
auth required pam_wheel.so use_uid group=sugroup
	10. Test the configuration from a separate administrative session before closing the existing session.
REFERENCE:
sudo Documentation
CIS Ubuntu Linux Benchmark
============================================================
15. ISSUE: Weak Password Authentication and Account Lockout Policy
SEVERITY: Medium
OBSERVATION:
The test team observed that password authentication, password-quality, password-history, and account-lockout controls did not meet the required endpoint security baseline.
In the current scenario, the test team observed failures involving:
	1. pam_faillock enforcement.
	2. Password history enforcement.
	3. Minimum password length of 14 characters.
	4. Password complexity requirements.
	5. Maximum permitted failed authentication attempts.
	6. Account unlock duration.
	7. Password history of at least 24 previous passwords.
	8. The nullok option within pam_unix configuration.
The automated output indicated that pam_pwhistory was present; however, the associated password-history control was still marked as failed, indicating that the overall configuration did not meet the required baseline.
RISK IMPACT:
An attacker can perform password guessing, brute-force, and credential-reuse attacks more effectively where password strength, password reuse, and failed-login lockout controls are insufficient.
RECOMMENDATION:
It is recommended to configure a strong password and account lockout policy by following the below mentioned steps:
	1. Back up the current PAM configuration:
cp -a /etc/pam.d/common-auth /etc/pam.d/common-auth.bak
cp -a /etc/pam.d/common-account /etc/pam.d/common-account.bak
cp -a /etc/pam.d/common-password /etc/pam.d/common-password.bak
	2. Install password-quality support:
apt install libpam-pwquality
	3. Edit:
vi /etc/security/pwquality.conf
	4. Configure:
minlen = 14
minclass = 4
	5. Configure account lockout:
vi /etc/security/faillock.conf
	6. Configure an approved policy, for example:
deny = 5
unlock_time = 900
	7. Configure password history:
vi /etc/security/pwhistory.conf
	8. Configure:
remember = 24
	9. Ensure pam_faillock, pam_pwquality, and pam_pwhistory are correctly integrated into the PAM stack.
	10. Remove nullok from applicable pam_unix.so authentication entries.
	11. Test authentication and lockout behaviour before closing the administrative session.
REFERENCE:
CIS Ubuntu Linux Benchmark
Linux PAM Documentation
============================================================
16. ISSUE: Weak Account Defaults and Password Aging Configuration
SEVERITY: Low
OBSERVATION:
The test team observed that password aging and default account-security settings were not configured according to the required endpoint security baseline.
In the current scenario, the test team observed that:
	1. PASS_MAX_DAYS was configured as 99999.
	2. PASS_MIN_DAYS was configured as 0.
	3. Default inactive-account locking was disabled with INACTIVE=-1.
	4. The default UMASK was configured as 022.
RISK IMPACT:
An attacker can benefit from compromised credentials remaining valid for excessive periods and inactive accounts remaining available indefinitely. A permissive umask may also result in newly created files and directories receiving broader access permissions than required.
RECOMMENDATION:
It is recommended to configure secure password aging and account defaults by following the below mentioned steps:
	1. Edit:
vi /etc/login.defs
	2. Configure:
PASS_MAX_DAYS 365
PASS_MIN_DAYS 1
UMASK 027
	3. Configure new accounts to be disabled after the approved inactivity period:
useradd -D -f 30
	4. Apply the required settings to applicable existing accounts:
chage --maxdays 365 --mindays 1 --inactive 30
	5. Verify:
chage -l
REFERENCE:
CIS Ubuntu Linux Benchmark
============================================================
17. ISSUE: Insufficient System Account Login Restrictions
SEVERITY: Low
VALIDATION STATUS: Manual Validation Required
OBSERVATION:
The test team observed that the automated system-account login restriction control did not successfully meet the required endpoint security baseline.
In the current scenario, the test team observed that the automated control reported a failure while reviewing system-account login shells. However, manual review of the supplied /etc/passwd evidence shows that most service accounts are already configured with /usr/sbin/nologin or /bin/false. The account "sync" uses /bin/sync, while root and the legitimate interactive account it-hw use interactive shells. Therefore, the specific non-compliant system account should be validated before this finding is treated as confirmed.
RISK IMPACT:
An attacker can potentially misuse an unnecessarily interactive system or service account if valid credentials or another authentication mechanism for the account are obtained, providing an additional path for unauthorized access.
RECOMMENDATION:
It is recommended to validate and restrict interactive login for system and service accounts by following the below mentioned steps:
	1. Identify system accounts with interactive shells:
awk -F: '($3 < 1000 && $1!="root" && $1!="sync" && $1!="shutdown" && $1!="halt" && $7 !~ /(nologin|false)$/){print $1 ":" $7}' /etc/passwd
	2. Review each returned account and verify whether interactive login is operationally required.
	3. Where interactive login is not required:
usermod -s /usr/sbin/nologin <service_account>
	4. Lock password authentication where applicable:
passwd -l <service_account>
	5. Re-run the configuration-review control after remediation.
REFERENCE:
CIS Ubuntu Linux Benchmark
============================================================
18. ISSUE: Inadequate Security Logging Configuration
SEVERITY: Low
OBSERVATION:
The test team observed that system logging controls were not fully configured according to the required security baseline.
In the current scenario, the test team observed that:
	1. Journald persistent storage or forwarding did not meet the required baseline.
	2. Journald compression was not explicitly configured.
	3. The remote rsyslog forwarding control was marked as failed.
	4. A log file under /var/log did not meet the required restrictive permission baseline.
The automated evidence indicated that a remote rsyslog target may be present; therefore, the remote destination and actual forwarding operation should be validated before concluding that centralized logging is completely absent.
RISK IMPACT:
An attacker can benefit from insufficient logging controls because malicious activities may not be reliably retained, centrally collected, or protected. This can reduce the ability to identify, correlate, investigate, and respond to security incidents.
RECOMMENDATION:
It is recommended to configure persistent, protected, and centralized system logging by following the below mentioned steps:
	1. Create:
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
Additionally, it is recommended to validate centralized rsyslog forwarding:
	5. Review:
grep -R '@@\|@' /etc/rsyslog.conf /etc/rsyslog.d/
	6. Where no valid approved destination exists, configure:
. @@<approved_log_server>:514
	7. Restart rsyslog:
systemctl restart rsyslog
	8. Correct excessive permissions on identified log files:
chown <approved_owner>:<approved_group> <log_file>
chmod 640 <log_file>
REFERENCE:
CIS Ubuntu Linux Benchmark
============================================================
19. ISSUE: System Auditing Not Enabled
SEVERITY: Medium
OBSERVATION:
The test team observed that the Linux userspace auditing framework was not installed on the assessed endpoint.
In the current scenario, the test team observed that the auditd package was not installed. Although the kernel process list contains the kernel audit thread, this does not replace the required userspace audit daemon and audit policy configuration.
RISK IMPACT:
An attacker can perform security-sensitive operations with reduced audit visibility where comprehensive operating system auditing is unavailable, making malicious activity more difficult to detect and investigate.
RECOMMENDATION:
It is recommended to install and configure the Linux audit framework by following the below mentioned steps:
	1. Install the required packages:
apt update
apt install auditd audispd-plugins
	2. Enable and start auditd:
systemctl enable --now auditd
	3. Configure organizational audit rules under:
/etc/audit/rules.d/
	4. For example, create:
vi /etc/audit/rules.d/50-identity.rules
	5. Add:
-w /etc/passwd -p wa -k identity
-w /etc/group -p wa -k identity
-w /etc/shadow -p wa -k identity
-w /etc/sudoers -p wa -k scope
-w /etc/sudoers.d/ -p wa -k scope
	6. Load:
augenrules --load
	7. Verify:
auditctl -l
systemctl status auditd
The full organization-approved audit rule set should be implemented in addition to the example rules above.
REFERENCE:
CIS Ubuntu Linux Benchmark
Linux Audit Documentation
============================================================
20. ISSUE: File Integrity Monitoring Not Configured
SEVERITY: Low
OBSERVATION:
The test team observed that file integrity monitoring was not configured on the assessed endpoint.
In the current scenario, the test team observed that AIDE was not installed and no periodic AIDE filesystem-integrity verification was configured.
RISK IMPACT:
An attacker can modify critical system files, application files, executables, or configuration files with a reduced likelihood of those unauthorized changes being identified.
RECOMMENDATION:
It is recommended to implement file integrity monitoring by following the below mentioned steps:
	1. Install AIDE:
apt update
apt install aide aide-common
	2. Initialize the AIDE database:
aideinit
	3. Perform an integrity check:
aide --check
	4. Configure a periodic integrity check:
vi /etc/cron.d/aide-check
	5. Configure an approved schedule, for example:
0 5 * * * root /usr/bin/aide --check
	6. Secure the scheduled task:
chown root:root /etc/cron.d/aide-check
chmod 600 /etc/cron.d/aide-check
	7. Configure alerting or centralized monitoring for identified integrity changes.
REFERENCE:
AIDE Documentation
CIS Ubuntu Linux Benchmark
============================================================
21. ISSUE: Vulnerable and Outdated Software Packages Installed
SEVERITY: High
OBSERVATION:
The test team observed that multiple installed software packages were running outdated versions for which security updates had been released. These packages are associated with vulnerabilities that may result in privilege escalation, arbitrary code execution, denial of service, information disclosure, or other security impacts.
In the current scenario, the test team reviewed the installed package inventory and identified vulnerable or outdated components including:
	1. AccountsService / libaccountsservice0 - Version 23.13.9-2ubuntu6 - CVE-2026-61897, CVE-2026-61898.
	2. OpenSSL / libssl3t64 - Version 3.0.13-0ubuntu3.7 - HollowByte denial-of-service vulnerability.
	3. systemd - Version 255.4-1ubuntu8.14 - CVE-2026-16742, CVE-2026-15059.
	4. Samba libraries - Version 2:4.19.5+dfsg-4ubuntu9.4 - CVE-2026-15779, CVE-2026-6949, CVE-2026-58216, CVE-2026-58218, CVE-2026-58221, CVE-2026-58222, CVE-2026-58224.
	5. Yelp / libyelp0 - Version 42.2-1ubuntu0.24.04.1 - CVE-2026-13601.
	6. libarchive13t64 - Version 3.7.2-2ubuntu0.5 - CVE-2026-14164, CVE-2026-5745.
	7. Kerberos / libkrb5-3 - Version 1.20.1-6ubuntu2.6 - CVE-2026-11850, CVE-2026-40355, CVE-2026-40356.
	8. GIFLIB / libgif7 - Version 5.2.2-1ubuntu1 - CVE-2026-26740, CVE-2026-23868.
	9. HTML::Parser / libhtml-parser-perl - Version 3.81-1build3 - CVE-2026-8829.
	10. libgphoto2 - Version 2.5.31-2.1ubuntu1 - multiple CVE-2026-4033x/4034x vulnerabilities.
	11. GStreamer Good Plugins - Version 1.24.2-1ubuntu1.2 - CVE-2026-39043, CVE-2026-39044, CVE-2026-53705.
	12. jbig2dec / libjbig2dec0 - Version 0.20-1build3 - CVE-2026-38076.
	13. Older Linux HWE kernel packages, including versions 6.14.0-37 and 6.17.0-19, remained installed.
Canonical confirms that the installed AccountsService, OpenSSL, systemd, Samba, Yelp, Kerberos, GStreamer, libgphoto2, and jbig2dec versions precede security-fixed Ubuntu 24.04 package versions. AccountsService includes a high-priority local privilege-escalation vulnerability, while several of the other components include denial-of-service, information-disclosure, or possible code-execution issues. (Ubuntu)
RISK IMPACT:
An attacker can exploit vulnerabilities within outdated software to compromise the confidentiality, integrity, or availability of the endpoint. Depending on the affected package and attack prerequisites, successful exploitation may result in privilege escalation, arbitrary command execution, information disclosure, denial of service, or further compromise of the system.
RECOMMENDATION:
It is recommended to update all vulnerable and outdated packages to the latest vendor-supported security versions by following the below mentioned steps:
	1. Refresh the package repository:
apt update
	2. Review pending package updates:
apt list --upgradable
	3. Apply applicable security and package updates during an approved maintenance window:
apt full-upgrade
	4. Verify that the identified packages are no longer pending:
apt list --upgradable
	5. Reboot the endpoint after updating the kernel and critical system packages:
reboot
	6. Verify the active kernel:
uname -r
	7. After verifying successful operation of the updated kernel, remove obsolete packages:
apt autoremove
	8. Re-run the vulnerability and endpoint configuration review to confirm remediation.
REFERENCE:
Canonical AccountsService Security Notice - USN-8580-1
Canonical OpenSSL Security Notice - USN-8625-1
Canonical systemd Security Notice - USN-8626-1
Canonical Samba Security Notice - USN-8621-1
Canonical Kerberos Security Notice - USN-8585-1
Canonical GStreamer Security Notice - USN-8584-1
Canonical libgphoto2 Security Notice - USN-8586-1
Canonical jbig2dec Security Notice - USN-8582-1
FINAL SEVERITY SUMMARY
High: 1
Medium: 6
Low: 14
Total: 21 findings
Finding 17 should remain under manual validation until a genuinely non-compliant system/service account is confirmed from the failed control logic. The other 20 can proceed into the reporting workflow based on the evidence currently available.

From <https://chatgpt.com/g/g-p-68da8a6c742881918ea4f1aa2e62f91c/c/6a7959e4-7b5c-83ec-b68f-d90c2e049039> 
