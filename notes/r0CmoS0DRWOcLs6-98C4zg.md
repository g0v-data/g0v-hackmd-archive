Below is the complete report for the 22 consolidated findings identified from Linux_Script_Output(4).csv and the supplemental firewall, hosts, listening-port, passwd, process, and installed-package evidence.
============================================================
	1. ISSUE: Insufficient Kernel Module Hardening
SEVERITY: Low
============================================================
OBSERVATION:
The test team observed that unnecessary filesystem and removable-storage kernel modules were not disabled on the assessed endpoint, increasing the operating system attack surface.
In the current scenario, the test team observed that the cramfs, freevxfs, hfs, hfsplus, jffs2, squashfs, udf, and usb-storage kernel modules were not appropriately disabled.
RISK IMPACT:
An attacker can leverage unnecessary kernel functionality to increase the available attack surface and potentially exploit vulnerabilities associated with unsupported filesystem types or removable-storage functionality.
RECOMMENDATION:
It is recommended to disable unnecessary filesystem and removable-storage kernel modules by following the below mentioned steps:
	1. Create the hardening configuration:
vi /etc/modprobe.d/99-filesystem-hardening.conf
	2. Add:
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
	3. Unload modules that are not operationally required:
modprobe -r cramfs
modprobe -r freevxfs
modprobe -r hfs
modprobe -r hfsplus
modprobe -r jffs2
modprobe -r squashfs
modprobe -r udf
modprobe -r usb-storage
	4. Update the initramfs:
update-initramfs -u
REFERENCE:
CIS Ubuntu Linux Benchmark
============================================================
2. ISSUE: Insufficient Filesystem Partition and Mount Hardening
SEVERITY: Low
OBSERVATION:
The test team observed that filesystem partitioning and restrictive mount options were not adequately configured on the assessed endpoint.
In the current scenario, the test team observed that /tmp and /dev/shm were mounted without the noexec option. Additionally, /home, /var, /var/tmp, /var/log, and /var/log/audit were not configured as separate partitions or mount points.
RISK IMPACT:
An attacker can leverage insufficient filesystem isolation after gaining access to increase the impact of a compromise, execute malicious content from writable filesystem locations, or cause resource exhaustion affecting other areas of the operating system.
RECOMMENDATION:
It is recommended to configure separate partitions and restrictive mount options by following the below mentioned steps:
	1. Review the current filesystem:
lsblk
findmnt
df -h
	2. Configure noexec for /tmp and /dev/shm through /etc/fstab.
Example for /dev/shm:
tmpfs /dev/shm tmpfs defaults,nodev,nosuid,noexec 0 0
	3. Remount where applicable:
mount -o remount,nodev,nosuid,noexec /dev/shm
mount -o remount,noexec /tmp
	4. During an approved maintenance window, configure dedicated partitions or logical volumes for:
/home
/var
/var/tmp
/var/log
/var/log/audit
	5. Verify:
findmnt /tmp
findmnt /dev/shm
findmnt /home
findmnt /var
REFERENCE:
CIS Ubuntu Linux Benchmark
============================================================
3. ISSUE: Insecure File and Directory Permission Configuration
SEVERITY: Low
OBSERVATION:
The test team observed that insecure file, directory, ownership, and home-directory permission conditions were present on the assessed endpoint.
In the current scenario, the test team observed world-writable directories without appropriate sticky-bit protection, world-writable files, unowned and ungrouped objects within containerd snapshot data, and the ramrajit home directory configured with permissions 777 instead of a restrictive permission mode.
RISK IMPACT:
An attacker can abuse excessive filesystem permissions to modify, replace, create, or delete files accessible to other users or processes. Improper ownership and a world-accessible user home directory may further expose sensitive information or provide opportunities for tampering and persistence.
RECOMMENDATION:
It is recommended to correct excessive filesystem permissions and invalid ownership by following the below mentioned steps:
	1. Identify world-writable directories without the sticky bit:
find / -xdev -type d -perm -0002 ! -perm -1000 -print
	2. Apply the sticky bit where shared write access is required:
chmod a+t
	3. Identify world-writable files:
find / -xdev -type f -perm -0002 -print
	4. Remove unnecessary world-write access:
chmod o-w
	5. Identify unowned and ungrouped objects:
find / -xdev -nouser -print
find / -xdev -nogroup -print
	6. Assign approved ownership:
chown <approved_user>:<approved_group>
	7. Restrict the ramrajit home directory:
chown ramrajit:ramrajit /home/ramrajit
chmod 750 /home/ramrajit
REFERENCE:
CIS Ubuntu Linux Benchmark
============================================================
4. ISSUE: Inadequate Bootloader Access Protection
SEVERITY: Low
OBSERVATION:
The test team observed that adequate authentication protection was not configured for the system bootloader.
In the current scenario, the test team observed that the GRUB superuser/password configuration did not meet the required security baseline.
RISK IMPACT:
An attacker can use physical or console access to modify boot parameters and potentially bypass operating system security restrictions when bootloader authentication is not enforced.
RECOMMENDATION:
It is recommended to configure GRUB bootloader authentication by following the below mentioned steps:
	1. Generate a GRUB PBKDF2 password:
grub-mkpasswd-pbkdf2
	2. Edit:
vi /etc/grub.d/40_custom
	3. Configure:
set superusers="grubadmin"
password_pbkdf2 grubadmin <generated_PBKDF2_hash>
	4. Update GRUB:
update-grub
	5. Reboot during an approved maintenance window and confirm that protected boot entries require authentication.
REFERENCE:
CIS Ubuntu Linux Benchmark
============================================================
5. ISSUE: Insufficient Core Dump Protection
SEVERITY: Low
OBSERVATION:
The test team observed that core dump backtrace and storage protections were not configured according to the required endpoint security baseline.
In the current scenario, the test team observed that the systemd coredump storage and backtrace restriction control failed, indicating that sensitive process-memory information may be retained.
RISK IMPACT:
An attacker can access information retained in process core dumps, potentially exposing credentials, authentication tokens, cryptographic material, application data, or other sensitive memory contents.
RECOMMENDATION:
It is recommended to restrict core dump storage and processing by following the below mentioned steps:
	1. Create:
mkdir -p /etc/systemd/coredump.conf.d
vi /etc/systemd/coredump.conf.d/99-hardening.conf
	2. Add:
[Coredump]
Storage=none
ProcessSizeMax=0
	3. Reload configuration:
systemctl daemon-reload
	4. Verify:
systemd-analyze cat-config systemd/coredump.conf
REFERENCE:
CIS Ubuntu Linux Benchmark
systemd-coredump Documentation
============================================================
6. ISSUE: Insecure Graphical Login Configuration
SEVERITY: Low
OBSERVATION:
The test team observed that the graphical login interface was not configured to prevent display of the system user list.
In the current scenario, the test team observed that the GDM disable-user-list control failed. The running-process evidence further confirms that GDM and graphical desktop services are actively operating on the endpoint.
RISK IMPACT:
An attacker can obtain valid usernames directly from the graphical login interface, making subsequent password-guessing and targeted authentication attacks easier.
RECOMMENDATION:
It is recommended to disable display of the user list at the GDM login screen by following the below mentioned steps:
	1. Create the GDM dconf profile:
vi /etc/dconf/profile/gdm
	2. Add:
user-db:user
system-db:gdm
file-db:/usr/share/gdm/greeter-dconf-defaults
	3. Create:
mkdir -p /etc/dconf/db/gdm.d
vi /etc/dconf/db/gdm.d/00-login-screen
	4. Add:
[org/gnome/login-screen]
disable-user-list=true
	5. Apply:
dconf update
REFERENCE:
CIS Ubuntu Linux Benchmark
GNOME Login Screen Security Guidance
============================================================
7. ISSUE: Unnecessary Services and System Components Installed
SEVERITY: Low
OBSERVATION:
The test team observed that unnecessary server services and system components were installed on the assessed endpoint, increasing the available attack surface.
In the current scenario, the test team observed that Avahi, CUPS, rsync, and X Server components were installed. Avahi and CUPS were also confirmed as active processes, with Avahi listening on UDP 5353. CUPS was bound only to localhost and is therefore not considered externally exposed.
RISK IMPACT:
An attacker can target unnecessary software and services for known vulnerabilities or configuration weaknesses, increasing the number of potential attack paths available on the endpoint.
RECOMMENDATION:
It is recommended to remove or disable unnecessary services and system components by following the below mentioned steps:
	1. If Avahi is unnecessary:
systemctl disable --now avahi-daemon
apt purge avahi-daemon
	2. If printing is unnecessary:
systemctl disable --now cups
systemctl disable --now cups-browsed
apt purge cups cups-browsed
	3. If rsync is unnecessary:
apt purge rsync
	4. Review X Server components:
dpkg -l | grep -E 'xserver|xorg'
	5. If graphical functionality is not required:
apt purge <unnecessary_X_server_packages>
Graphical components should not be removed where GUI/XRDP operation is a legitimate business requirement.
REFERENCE:
CIS Ubuntu Linux Benchmark
============================================================
8. ISSUE: Legacy and Unnecessary Network Client Software Installed
SEVERITY: Low
OBSERVATION:
The test team observed that legacy and unnecessary network client software was installed on the assessed endpoint.
In the current scenario, the test team observed that FTP, Telnet, and LDAP client utilities were installed.
RISK IMPACT:
An attacker can leverage legacy client software to facilitate insecure network communication or social-engineering scenarios. FTP and Telnet may transmit authentication credentials and data without adequate encryption.
RECOMMENDATION:
It is recommended to remove unnecessary legacy network client software by following the below mentioned steps:
	1. Remove FTP where not required:
apt purge ftp
	2. Remove Telnet where not required:
apt purge telnet
	3. Remove LDAP utilities where not operationally required:
apt purge ldap-utils
	4. Verify:
dpkg -l | grep -E 'ftp|telnet|ldap-utils'
LDAP utilities should be retained where required for legitimate directory/SSSD administration.
REFERENCE:
CIS Ubuntu Linux Benchmark
============================================================
9. ISSUE: Inadequate Cron Access and Permission Hardening
SEVERITY: Low
OBSERVATION:
The test team observed that cron configuration files and directories were configured with permissions broader than the required security baseline and cron access was not explicitly restricted.
In the current scenario, the test team observed that /etc/crontab was configured with permissions 644, the cron.hourly, cron.daily, cron.weekly, cron.monthly, and cron.d directories were configured with permissions 755, and /etc/cron.allow was not present. The cron daemon was confirmed as actively running.
RISK IMPACT:
An attacker can benefit from insufficient cron restrictions by gaining unnecessary visibility into scheduled tasks or abusing scheduled-task functionality where other access conditions permit.
RECOMMENDATION:
It is recommended to restrict cron permissions and access by following the below mentioned steps:
	1. Configure /etc/crontab:
chown root:root /etc/crontab
chmod og-rwx /etc/crontab
	2. Configure cron directories:
chown root:root /etc/cron.hourly
chmod og-rwx /etc/cron.hourly
chown root:root /etc/cron.daily
chmod og-rwx /etc/cron.daily
chown root:root /etc/cron.weekly
chmod og-rwx /etc/cron.weekly
chown root:root /etc/cron.monthly
chmod og-rwx /etc/cron.monthly
chown root:root /etc/cron.d
chmod og-rwx /etc/cron.d
	3. Create an authorized-user file:
touch /etc/cron.allow
chown root:root /etc/cron.allow
chmod 640 /etc/cron.allow
	4. Add only approved usernames to /etc/cron.allow.
REFERENCE:
CIS Ubuntu Linux Benchmark
============================================================
10. ISSUE: Inadequate Network Protocol Module Hardening
SEVERITY: Low
OBSERVATION:
The test team observed that unnecessary network protocol kernel modules were not explicitly disabled.
In the current scenario, the test team observed that DCCP, TIPC, RDS, and SCTP were not appropriately disabled.
RISK IMPACT:
An attacker can leverage unnecessary protocol implementations to increase the network attack surface and potentially exploit vulnerabilities in protocol functionality that is not required for legitimate business operations.
RECOMMENDATION:
It is recommended to disable unnecessary network protocol modules by following the below mentioned steps:
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
	3. Where the modules are not required:
modprobe -r dccp
modprobe -r tipc
modprobe -r rds
modprobe -r sctp
	4. Update:
update-initramfs -u
REFERENCE:
CIS Ubuntu Linux Benchmark
============================================================
11. ISSUE: Insecure Network Stack Configuration
SEVERITY: Medium
OBSERVATION:
The test team observed that multiple IPv4 and IPv6 kernel network parameters were configured with values that did not meet the required endpoint security baseline.
In the current scenario, the test team observed that secure redirects were enabled, IPv4 packet forwarding was enabled, reverse-path filtering was configured as 2 instead of the required restrictive value, IPv6 router advertisements were accepted, martian packet logging was disabled, and IPv4 redirects were configured to be sent.
RISK IMPACT:
An attacker can abuse insecure network stack behaviour to facilitate IP spoofing, traffic redirection, routing manipulation, or other network-based attacks. Insufficient packet logging may also reduce visibility of suspicious traffic.
RECOMMENDATION:
It is recommended to harden the kernel network parameters by following the below mentioned steps:
	1. Create:
vi /etc/sysctl.d/60-network-hardening.conf
	2. Where IP forwarding is not required, add:
net.ipv4.ip_forward = 0
	3. Add:
net.ipv4.conf.all.secure_redirects = 0
net.ipv4.conf.default.secure_redirects = 0
net.ipv4.conf.all.rp_filter = 1
net.ipv4.conf.default.rp_filter = 1
net.ipv4.conf.all.send_redirects = 0
net.ipv4.conf.default.send_redirects = 0
net.ipv4.conf.all.log_martians = 1
net.ipv4.conf.default.log_martians = 1
net.ipv6.conf.all.accept_ra = 0
net.ipv6.conf.default.accept_ra = 0
	4. Apply:
sysctl --system
	5. Verify:
sysctl net.ipv4.ip_forward
sysctl net.ipv4.conf.all.rp_filter
sysctl net.ipv4.conf.all.send_redirects
sysctl net.ipv4.conf.all.log_martians
sysctl net.ipv6.conf.all.accept_ra
The endpoint is running Docker; therefore, net.ipv4.ip_forward=0 can affect container networking. Where forwarding is an approved Docker requirement, retain the required setting and document the security exception while enforcing segmentation through Docker/firewall policy.
REFERENCE:
CIS Ubuntu Linux Benchmark
Linux Kernel IP Sysctl Documentation
============================================================
12. ISSUE: Inadequate Host-Based Firewall Configuration
SEVERITY: Medium
OBSERVATION:
The test team observed that although UFW was active with a default deny incoming policy, the host firewall configuration contained insufficiently restrictive inbound access rules.
In the current scenario, the test team observed that inbound access was permitted from "Anywhere" for ports 1433, 22, 8020, 8027, 3389, 8080, 80, and 443, with equivalent IPv6 rules. The CIS loopback firewall control also failed.
RISK IMPACT:
An attacker can access sensitive network services from any network segment capable of routing to the endpoint because source restrictions are not applied to multiple administrative and application ports.
RECOMMENDATION:
It is recommended to restrict inbound firewall rules to approved source networks by following the below mentioned steps:
	1. Review existing rules:
ufw status numbered
	2. Before removing broad SSH/RDP rules, create trusted-source rules:
ufw allow from <trusted_management_subnet> to any port 22 proto tcp
ufw allow from <trusted_management_subnet> to any port 3389 proto tcp
	3. Restrict SQL Server:
ufw allow from <trusted_database_client_subnet> to any port 1433 proto tcp
	4. Restrict application-management ports:
ufw allow from <trusted_application_subnet> to any port 8020 proto tcp
ufw allow from <trusted_application_subnet> to any port 8027 proto tcp
ufw allow from <trusted_application_subnet> to any port 8080 proto tcp
	5. Remove the corresponding unrestricted "Anywhere" rules after trusted-source rules are confirmed:
ufw status numbered
ufw delete <rule_number>
	6. Keep ports 80/443 open broadly only where the endpoint is intentionally providing a web service.
	7. Verify:
ufw status verbose
nft list ruleset
REFERENCE:
CIS Ubuntu Linux Benchmark
Ubuntu Firewall Documentation
============================================================
13. ISSUE: Inadequate SSH Server Security Configuration
SEVERITY: Medium
OBSERVATION:
The test team observed that multiple SSH server security controls were configured with values that did not meet the required endpoint security baseline.
In the current scenario, the test team observed that sshd_config permissions were 644 instead of 0600, SSH user/group access restrictions were absent, PermitRootLogin was set to prohibit-password, X11Forwarding was enabled, MaxAuthTries was 6, ClientAliveInterval was 0, LoginGraceTime was 120 seconds, no login banner was configured, weak/insufficient MAC configuration was identified, and TCP forwarding was enabled. SSH was actively listening on IPv4 and IPv6 wildcard interfaces, and an active SSH/SFTP session was observed.
RISK IMPACT:
An attacker can exploit permissive SSH settings to increase the likelihood of brute-force access, unauthorized forwarding, root-account targeting, session abuse, or lateral movement.
RECOMMENDATION:
It is recommended to harden the SSH server configuration by following the below mentioned steps:
	1. Restrict sshd_config permissions:
chown root:root /etc/ssh/sshd_config
chmod 600 /etc/ssh/sshd_config
	2. Create:
vi /etc/ssh/sshd_config.d/99-hardening.conf
	3. Add:
PermitRootLogin no
X11Forwarding no
MaxAuthTries 4
ClientAliveInterval 15
ClientAliveCountMax 3
LoginGraceTime 60
Banner /etc/issue.net
AllowTcpForwarding no
MACs hmac-sha2-512-etm@openssh.com,hmac-sha2-256-etm@openssh.com,umac-128-etm@openssh.com
	4. Restrict SSH to approved users/groups. For example:
groupadd sshusers
usermod -aG sshusers <approved_user>
Then add:
AllowGroups sshusers
	5. Configure the banner:
vi /etc/issue.net
	6. Validate before reload:
sshd -t
	7. Reload:
systemctl reload ssh
	8. Verify effective configuration:
sshd -T | grep -Ei 'permitrootlogin|x11forwarding|maxauthtries|clientalive|logingracetime|banner|allowtcpforwarding|macs|allowgroups'
REFERENCE:
CIS Ubuntu Linux Benchmark
OpenSSH Server Documentation
============================================================
14. ISSUE: Insufficient Privilege Escalation Controls
SEVERITY: Medium
OBSERVATION:
The test team observed that sudo and su privilege escalation controls were not adequately hardened.
In the current scenario, the test team observed that a dedicated sudo log file was not configured, the sudo authentication timeout did not meet the required baseline, and the pam_wheel restriction for su access was commented out.
RISK IMPACT:
An attacker can benefit from cached sudo authentication or unrestricted su functionality after obtaining access to a user session. Insufficient sudo-specific logging may also reduce traceability of privileged commands.
RECOMMENDATION:
It is recommended to strengthen privilege escalation controls by following the below mentioned steps:
	1. Create:
visudo -f /etc/sudoers.d/99-hardening
	2. Add:
Defaults logfile="/var/log/sudo.log"
Defaults timestamp_timeout=15
	3. Set secure permissions:
chmod 440 /etc/sudoers.d/99-hardening
	4. Validate:
visudo -c
	5. Restrict su to approved administrators:
groupadd sugroup
usermod -aG sugroup <authorized_admin>
	6. Edit:
vi /etc/pam.d/su
	7. Enable:
auth required pam_wheel.so use_uid group=sugroup
	8. Test from a separate administrative session before closing the existing session.
REFERENCE:
CIS Ubuntu Linux Benchmark
sudo and Linux-PAM Documentation
============================================================
15. ISSUE: Weak Password Authentication and Account Lockout Policy
SEVERITY: Medium
OBSERVATION:
The test team observed that password authentication, complexity, password-history, and account-lockout controls did not meet the required endpoint security baseline.
In the current scenario, the test team observed failures involving pam_faillock, password-history enforcement, minimum password length of 14 characters, password complexity, failed-attempt lockout, unlock duration, password history of at least 24 passwords, and removal of the nullok option from pam_unix. The configuration explicitly contained pam_unix.so nullok.
RISK IMPACT:
An attacker can perform password guessing, brute-force, credential-reuse, and weak-password attacks more effectively when authentication and account-lockout protections are insufficient.
RECOMMENDATION:
It is recommended to configure a strong PAM password and account lockout policy by following the below mentioned steps:
	1. Back up PAM configuration:
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
	5. Edit:
vi /etc/security/faillock.conf
	6. Configure:
deny = 5
unlock_time = 900
	7. Edit:
vi /etc/security/pwhistory.conf
	8. Configure:
remember = 24
	9. Review the PAM authentication stack and ensure pam_faillock, pam_pwquality, and pam_pwhistory are correctly ordered.
	10. Remove nullok from the applicable pam_unix authentication entry.
	11. Test authentication and account lockout before terminating the administrative session.
REFERENCE:
CIS Ubuntu Linux Benchmark
Linux-PAM Documentation
============================================================
16. ISSUE: Weak Account Defaults and Password Aging Configuration
SEVERITY: Low
OBSERVATION:
The test team observed that account defaults and password-aging controls were not configured according to the required security baseline.
In the current scenario, the test team observed PASS_MAX_DAYS configured as 99999, PASS_MIN_DAYS configured as 0, inactive-account locking disabled with INACTIVE=-1, and the default umask control not meeting the required restrictive baseline.
RISK IMPACT:
An attacker can benefit from compromised credentials remaining valid for excessive periods and unused accounts remaining enabled indefinitely. Permissive default file permissions may also expose newly created data to unnecessary users.
RECOMMENDATION:
It is recommended to configure secure account and password-aging defaults by following the below mentioned steps:
	1. Edit:
vi /etc/login.defs
	2. Configure:
PASS_MAX_DAYS 365
PASS_MIN_DAYS 1
UMASK 027
	3. Configure account inactivity:
useradd -D -f 30
	4. Apply to applicable existing users:
chage --maxdays 365 --mindays 1 --inactive 30
	5. Verify:
chage -l
REFERENCE:
CIS Ubuntu Linux Benchmark
============================================================
17. ISSUE: Insufficient System Account Login Restrictions
SEVERITY: Low
OBSERVATION:
The test team observed that the automated system-account login restriction control did not meet the required endpoint security baseline.
In the current scenario, the test team observed that the system-account login control was marked as failed. The supplied /etc/passwd evidence nevertheless shows that most service accounts already use /usr/sbin/nologin or /bin/false; therefore, remediation should be applied specifically to any remaining unnecessary interactive system accounts rather than broadly changing all service accounts.
RISK IMPACT:
An attacker can potentially misuse a system or service account with an unnecessary interactive shell if authentication access to that account is obtained.
RECOMMENDATION:
It is recommended to identify and restrict unnecessary interactive system accounts by following the below mentioned steps:
	1. Identify system accounts with interactive shells:
awk -F: '($3 < 1000 && $1!="root" && $1!="sync" && $1!="shutdown" && $1!="halt" && $7 !~ /(nologin|false)$/){print $1 ":" $7}' /etc/passwd
	2. For each non-required interactive service account:
usermod -s /usr/sbin/nologin <service_account>
	3. Lock password authentication where appropriate:
passwd -l <service_account>
	4. Re-run the system-account compliance check.
REFERENCE:
CIS Ubuntu Linux Benchmark
============================================================
18. ISSUE: Inadequate Security Logging Configuration
SEVERITY: Low
OBSERVATION:
The test team observed that system logging controls were not fully configured according to the required security baseline.
In the current scenario, the test team observed that journald persistent storage/ForwardToSyslog configuration failed, journald compression was not explicitly enabled, the remote rsyslog control did not meet the baseline despite the scan detecting a remote target, and /var/log/dpkg.log did not meet the required restrictive permission baseline. The running-process evidence confirms rsyslog and systemd-journald are active.
RISK IMPACT:
An attacker can benefit from insufficient log retention, forwarding, or permission controls because malicious activities may be more difficult to identify, correlate, investigate, or preserve as forensic evidence.
RECOMMENDATION:
It is recommended to configure persistent, compressed, protected, and centrally forwarded logging by following the below mentioned steps:
	1. Create:
mkdir -p /etc/systemd/journald.conf.d
vi /etc/systemd/journald.conf.d/99-hardening.conf
	2. Add:
[Journal]
Storage=persistent
Compress=yes
	3. Create persistent journal storage:
mkdir -p /var/log/journal
	4. Restart:
systemctl restart systemd-journald
	5. Review current rsyslog remote targets:
grep -R '@@\|@' /etc/rsyslog.conf /etc/rsyslog.d/
	6. Configure the approved log destination where required:
. @@<approved_log_server>:514
	7. Validate:
rsyslogd -N1
	8. Restart:
systemctl restart rsyslog
	9. Correct dpkg.log permissions:
chown root:adm /var/log/dpkg.log
chmod 640 /var/log/dpkg.log
REFERENCE:
CIS Ubuntu Linux Benchmark
============================================================
19. ISSUE: System Auditing Not Enabled
SEVERITY: Medium
OBSERVATION:
The test team observed that the Linux userspace audit framework was not installed on the assessed endpoint.
In the current scenario, the test team observed that the auditd package was not installed. Although the kernel process list contains the kernel audit thread kauditd, this does not provide the userspace auditing and rule management required by the security baseline.
RISK IMPACT:
An attacker can conduct security-sensitive activities with reduced audit visibility, making unauthorized actions, privilege use, configuration changes, and other malicious activity more difficult to detect and investigate.
RECOMMENDATION:
It is recommended to install and configure the Linux auditing framework by following the below mentioned steps:
	1. Install:
apt update
apt install auditd audispd-plugins
	2. Enable:
systemctl enable --now auditd
	3. Create an initial audit rule file:
vi /etc/audit/rules.d/50-identity.rules
	4. Add:
-w /etc/passwd -p wa -k identity
-w /etc/group -p wa -k identity
-w /etc/shadow -p wa -k identity
-w /etc/sudoers -p wa -k scope
-w /etc/sudoers.d/ -p wa -k scope
	5. Load:
augenrules --load
	6. Verify:
auditctl -l
systemctl status auditd
The organization's complete audit rule set should be implemented in addition to these examples.
REFERENCE:
CIS Ubuntu Linux Benchmark
Linux Audit Documentation
============================================================
20. ISSUE: File Integrity Monitoring Not Configured
SEVERITY: Low
OBSERVATION:
The test team observed that file integrity monitoring was not configured on the assessed endpoint.
In the current scenario, the test team observed that AIDE was not installed and no periodic AIDE integrity-verification schedule was configured.
RISK IMPACT:
An attacker can modify critical executables, configuration files, or application files with a reduced likelihood that unauthorized changes will be detected.
RECOMMENDATION:
It is recommended to implement file integrity monitoring by following the below mentioned steps:
	1. Install:
apt update
apt install aide aide-common
	2. Initialize:
aideinit
	3. Perform a check:
aide --check
	4. Create a periodic job:
vi /etc/cron.d/aide-check
	5. Add:
0 5 * * * root /usr/bin/aide --check
	6. Secure:
chown root:root /etc/cron.d/aide-check
chmod 600 /etc/cron.d/aide-check
	7. Configure centralized alerting for integrity changes where available.
REFERENCE:
CIS Ubuntu Linux Benchmark
AIDE Documentation
============================================================
21. ISSUE: Unrestricted Exposure of Network and Container Services
SEVERITY: Medium
OBSERVATION:
The test team observed that multiple administrative, database, web, remote-access, and containerized services were bound to wildcard network interfaces, increasing the remotely reachable attack surface of the endpoint.
In the current scenario, the test team observed network listeners including Nginx on TCP 80, SSH on TCP 22, a Docker-published Microsoft SQL Server service on TCP 1433, Docker-published application services on TCP 8080, 8081, 8083, and 8084, and XRDP on TCP 3389. These services were bound to 0.0.0.0, [::], or wildcard addresses. An established XRDP session was also observed. Docker NAT rules explicitly publish the container ports, and the DOCKER-USER chain did not contain additional filtering rules.
RISK IMPACT:
An attacker can enumerate and interact with exposed administrative, database, web, and containerized services from any network segment with routing and firewall access to the endpoint. Successful exploitation of a vulnerable or weakly configured service may result in unauthorized access, lateral movement, application compromise, or data exposure.
RECOMMENDATION:
It is recommended to restrict exposed services to only the interfaces and trusted source networks required for legitimate business operations by following the below mentioned steps:
	1. Review all listening services:
ss -lntup
	2. Review Docker published ports:
docker ps --format 'table {{.Names}}\t{{.Ports}}'
	3. For container services required only locally, modify Docker Compose or Docker run configuration to bind to localhost.
For example:
127.0.0.1:1433:1433
127.0.0.1:8083:8000
127.0.0.1:8084:8001
127.0.0.1:8080:8080
127.0.0.1:8081:8081
	4. Recreate affected containers after changing published-port bindings:
docker compose down
docker compose up -d
	5. Restrict SSH and XRDP to approved management networks:
ufw allow from <trusted_management_subnet> to any port 22 proto tcp
ufw allow from <trusted_management_subnet> to any port 3389 proto tcp
	6. Remove unrestricted corresponding firewall rules using:
ufw status numbered
ufw delete <rule_number>
	7. Where Docker services must be reachable from a trusted subnet, configure restrictions in the DOCKER-USER chain or the approved host firewall policy.
	8. Verify:
ss -lntup
ufw status verbose
docker ps
CUPS does not need exposure remediation under this finding because the supplied evidence shows it bound only to loopback.
REFERENCE:
Docker Networking and Firewall Documentation
Ubuntu Firewall Documentation
============================================================
22. ISSUE: Vulnerable and Outdated Software Packages Installed
SEVERITY: High
OBSERVATION:
The test team observed that multiple installed software packages were running versions older than currently available Ubuntu security-fixed package versions.
In the current scenario, the test team reviewed the supplied installed-package inventory and identified the following confirmed examples:
	1. OpenSSL / libssl3t64
Installed version: 3.5.5-1ubuntu3.2
Security-fixed version: 3.5.5-1ubuntu3.3
The Ubuntu security update addresses the HollowByte remote memory-consumption denial-of-service vulnerability. (Ubuntu)
	2. systemd / systemd-oomd
Installed version: 259.5-0ubuntu3
Security-fixed version: 259.5-0ubuntu3.4
Relevant vulnerabilities:
CVE-2026-16742
CVE-2026-15060
CVE-2026-15059
Canonical states that these issues can result in local privilege escalation or arbitrary process termination depending on the affected component. (Ubuntu)
	3. curl / libcurl4t64
Installed version: 8.18.0-1ubuntu2.3
Security-fixed version: 8.18.0-1ubuntu2.4
Canonical reports that the issue may allow sensitive information to be exposed when connections are reused under certain conditions. (Ubuntu)
	4. nginx
Installed version: 1.28.3-2ubuntu1.6
Current Ubuntu 26.04 security package: 1.28.3-2ubuntu1.10
Canonical's current nginx security/regression package includes fixes from the nginx security update series; the associated advisory discusses vulnerabilities including CVE-2026-56434 and CVE-2026-60005. The advisory notes that the CVE-2026-42533 fix was temporarily reverted in this release because of a regression, so that CVE should not be represented as fixed by 1.28.3-2ubuntu1.10. (Ubuntu)
RISK IMPACT:
An attacker can exploit known vulnerabilities in outdated software components to compromise the confidentiality, integrity, or availability of the endpoint. Depending on the vulnerable package, successful exploitation may result in denial of service, information disclosure, privilege escalation, or further system compromise.
RECOMMENDATION:
It is recommended to update vulnerable and outdated software packages to the current vendor-supported security versions by following the below mentioned steps:
	1. Refresh package metadata:
apt update
	2. Review available upgrades:
apt list --upgradable
	3. Confirm security updates for the identified packages:
apt-cache policy openssl libssl3t64 systemd systemd-oomd curl libcurl4t64 nginx
	4. Apply approved updates:
apt full-upgrade
	5. Verify installed versions:
dpkg-query -W openssl libssl3t64 systemd systemd-oomd curl libcurl4t64 nginx
	6. Restart affected services or reboot the endpoint where required:
reboot
	7. Verify the active kernel and service state after reboot:
uname -r
systemctl --failed
	8. Remove obsolete packages only after confirming that the updated system is stable:
apt autoremove
	9. Re-run the vulnerability and endpoint configuration assessment.
REFERENCE:
Canonical OpenSSL Security Notice. (Ubuntu)
Canonical systemd Security Notice. (Ubuntu)
Canonical curl Security Notice. (Ubuntu)
Canonical nginx Security Notice. (Ubuntu)
============================================================
FINAL SEVERITY SUMMARY
High: 1
	1. Vulnerable and Outdated Software Packages Installed
Medium: 8
	1. Insecure Network Stack Configuration
	2. Inadequate Host-Based Firewall Configuration
	3. Inadequate SSH Server Security Configuration
	4. Insufficient Privilege Escalation Controls
	5. Weak Password Authentication and Account Lockout Policy
	6. System Auditing Not Enabled
	7. Unrestricted Exposure of Network and Container Services
	8. Inadequate Host-Based Firewall/remote-access exposure is incorporated into the relevant findings above; no additional duplicate finding is required.
Low: 13
	1. Insufficient Kernel Module Hardening
	2. Insufficient Filesystem Partition and Mount Hardening
	3. Insecure File and Directory Permission Configuration
	4. Inadequate Bootloader Access Protection
	5. Insufficient Core Dump Protection
	6. Insecure Graphical Login Configuration
	7. Unnecessary Services and System Components Installed
	8. Legacy and Unnecessary Network Client Software Installed
	9. Inadequate Cron Access and Permission Hardening
	10. Inadequate Network Protocol Module Hardening
	11. Weak Account Defaults and Password Aging Configuration
	12. Insufficient System Account Login Restrictions
	13. Inadequate Security Logging Configuration
	14. File Integrity Monitoring Not Configured
Correction to the numerical severity count: the actual total from the 22 findings above is High = 1, Medium = 7, Low = 14, for a total of 22 findings.

From <https://chatgpt.com/g/g-p-68da8a6c742881918ea4f1aa2e62f91c/c/6a7959e4-7b5c-83ec-b68f-d90c2e049039> 
