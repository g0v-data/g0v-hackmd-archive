Below is the report for all 17 macOS findings. I have kept everything in plain text, including commands, so the font size remains uniform.
============================================================
	1. ISSUE: Inadequate Software Update and Patch Management Configuration
SEVERITY: Medium
============================================================
OBSERVATION:
The test team observed that software update and patch management settings were not fully configured in accordance with the required endpoint security baseline.
In the current scenario, the test team observed that macOS Tahoe 26.5.1 (25F80) was installed while the recommended macOS Tahoe 26.5.2 (25F84) update was available. Additionally, the automatic update-checking control was not explicitly configured and automatic App Store application updates were disabled. The supplied Software Update preferences show that automatic macOS update installation, critical updates, and configuration-data updates were otherwise enabled.
RISK IMPACT:
An attacker can exploit known vulnerabilities present in outdated operating system or application components where available security updates are not installed promptly. This may result in unauthorized access, privilege escalation, information disclosure, code execution, or denial of service depending on the vulnerability.
RECOMMENDATION:
It is recommended to install pending Apple security updates and configure automatic update mechanisms by following the below mentioned steps:
	1. Check for available software updates:
$ sudo softwareupdate --list
	2. Install all available Apple updates during an approved maintenance window:
$ sudo softwareupdate --install --all --restart
	3. Enable automatic update checking:
$ sudo defaults write /Library/Preferences/com.apple.SoftwareUpdate AutomaticCheckEnabled -bool true
	4. Ensure automatic update downloads are enabled:
$ sudo defaults write /Library/Preferences/com.apple.SoftwareUpdate AutomaticDownload -bool true
	5. Enable automatic installation of macOS updates:
$ sudo defaults write /Library/Preferences/com.apple.SoftwareUpdate AutomaticallyInstallMacOSUpdates -bool true
	6. Enable critical updates:
$ sudo defaults write /Library/Preferences/com.apple.SoftwareUpdate CriticalUpdateInstall -bool true
	7. Enable App Store application updates:
$ sudo defaults write /Library/Preferences/com.apple.commerce AutoUpdate -bool true
	8. Verify the settings:
$ defaults read /Library/Preferences/com.apple.SoftwareUpdate
$ defaults read /Library/Preferences/com.apple.commerce AutoUpdate
REFERENCE:
CIS macOS 26 Tahoe v1.1.0
Apple Software Update configuration
============================================================
2. ISSUE: Inadequate Host-Based Firewall Configuration
SEVERITY: Medium
OBSERVATION:
The test team observed that the built-in macOS host-based firewall was not enabled, reducing network-level protection for the assessed endpoint.
In the current scenario, the test team observed that the macOS Application Firewall was disabled with a reported state of 0 and firewall stealth mode was also disabled. The firewall configuration additionally contained incoming-connection allow entries for services and applications including remoted, python3, ruby, CUPS, sharingd, sshd-keygen-wrapper, and smbd.
RISK IMPACT:
An attacker can communicate more freely with network-accessible applications and services when the endpoint firewall is disabled. This increases the likelihood of service enumeration, unauthorized connection attempts, exploitation of vulnerable services, and lateral movement from reachable network segments.
RECOMMENDATION:
It is recommended to enable the macOS Application Firewall and stealth mode by following the below mentioned steps:
	1. Enable the Application Firewall:
$ sudo /usr/libexec/ApplicationFirewall/socketfilterfw --setglobalstate on
	2. Enable firewall stealth mode:
$ sudo /usr/libexec/ApplicationFirewall/socketfilterfw --setstealthmode on
	3. Review applications currently permitted to accept incoming connections:
$ sudo /usr/libexec/ApplicationFirewall/socketfilterfw --listapps
	4. Remove unnecessary application exceptions:
$ sudo /usr/libexec/ApplicationFirewall/socketfilterfw --remove <application_path>
	5. Verify the firewall status:
$ sudo /usr/libexec/ApplicationFirewall/socketfilterfw --getglobalstate
	6. Verify stealth mode:
$ sudo /usr/libexec/ApplicationFirewall/socketfilterfw --getstealthmode
	7. Review application rules again:
$ sudo /usr/libexec/ApplicationFirewall/socketfilterfw --listapps
REFERENCE:
CIS macOS 26 Tahoe v1.1.0
Apple firewall guidance. (Apple Support)
============================================================
3. ISSUE: Unrestricted Wireless Sharing Services
SEVERITY: Low
OBSERVATION:
The test team observed that wireless peer-to-peer sharing controls were not configured to restrict AirDrop and AirPlay Receiver functionality.
In the current scenario, the test team observed that the controls requiring AirDrop and AirPlay Receiver to be disabled did not meet the required baseline. The network evidence also showed that the Apple Wireless Direct Link interface, awdl0, was active.
RISK IMPACT:
An attacker can attempt to interact with wireless sharing functionality from a nearby compatible Apple device where these features remain available. This may increase the likelihood of unauthorized file-sharing requests, unintended data transfer, or exposure of device-sharing functionality.
RECOMMENDATION:
It is recommended to disable AirDrop and AirPlay Receiver when they are not required by following the below mentioned steps:
	1. For each applicable user, disable AirDrop:
$ sudo -u defaults write com.apple.NetworkBrowser DisableAirDrop -bool true
	2. Verify the AirDrop configuration:
$ sudo -u defaults read com.apple.NetworkBrowser DisableAirDrop
	3. In enterprise environments, deploy a configuration profile that sets:
allowAirDrop = false
	4. Disable AirPlay Receiver through System Settings:
System Settings > General > AirDrop & Continuity > AirPlay Receiver > Off
	5. Where configuration profiles are used, configure:
allowAirPlayIncomingRequests = false
	6. Verify that AirDrop is configured as "No One" and AirPlay Receiver is disabled for applicable users.
Apple documents AirDrop and AirPlay Receiver under the same AirDrop & Continuity settings area. (Apple Support)
REFERENCE:
CIS macOS 26 Tahoe v1.1.0
Apple AirDrop and Continuity guidance
============================================================
4. ISSUE: Unnecessary Network and Remote Sharing Services Enabled
SEVERITY: Medium
OBSERVATION:
The test team observed that multiple network and remote-sharing service-disable controls did not meet the required macOS security baseline.
In the current scenario, the test team observed failed controls associated with Screen Sharing, SMB/File Sharing, the HTTP server, and the NFS server. The supplied live network evidence did not show these services listening externally at the time of collection; therefore, the finding relates to the service-disable configuration rather than confirmed active external exposure.
RISK IMPACT:
An attacker can potentially access unnecessary sharing or server functionality if these services become active or are started without appropriate access restrictions. Maintaining unnecessary server capabilities increases the endpoint attack surface and may expose files, remote-control functionality, or vulnerable network services.
RECOMMENDATION:
It is recommended to disable network and remote-sharing services that are not operationally required by following the below mentioned steps:
	1. Disable Screen Sharing:
$ sudo launchctl disable system/com.apple.screensharing
	2. Disable SMB/File Sharing:
$ sudo launchctl disable system/com.apple.smbd
	3. Disable the Apache HTTP service if not required:
$ sudo launchctl disable system/org.apache.httpd
	4. Disable NFS if not required:
$ sudo nfsd disable
	5. Verify SMB service configuration:
$ launchctl print-disabled system | grep com.apple.smbd
	6. Verify Screen Sharing configuration:
$ launchctl print-disabled system | grep screensharing
	7. Review listening ports after remediation:
$ sudo lsof -nP -iTCP -sTCP:LISTEN
Only services required for legitimate business purposes should remain enabled.
REFERENCE:
CIS macOS 26 Tahoe v1.1.0
============================================================
5. ISSUE: Inadequate Network Discovery and Wake Service Hardening
SEVERITY: Low
OBSERVATION:
The test team observed that network discovery and Wake-on-Network controls were not configured in accordance with the required endpoint security baseline.
In the current scenario, the test team observed that Bonjour multicast advertisements were not disabled and Wake for network access was enabled when the MacBook was connected to AC power. The supplied power configuration showed womp 0 on battery power and womp 1 on AC power.
RISK IMPACT:
An attacker can obtain additional information about services advertised by the endpoint through network-discovery mechanisms and may interact with network-triggered wake functionality where reachable. These features increase network visibility and functionality beyond what may be required for normal endpoint use.
RECOMMENDATION:
It is recommended to disable unnecessary Bonjour advertisements and Wake for network access by following the below mentioned steps:
	1. Disable Bonjour multicast advertisements:
$ sudo defaults write /Library/Preferences/com.apple.mDNSResponder NoMulticastAdvertisements -bool true
	2. Verify the setting:
$ sudo defaults read /Library/Preferences/com.apple.mDNSResponder NoMulticastAdvertisements
	3. Disable Wake-on-LAN for battery power:
$ sudo pmset -b womp 0
	4. Disable Wake-on-LAN for AC power:
$ sudo pmset -c womp 0
	5. Verify:
$ sudo pmset -g custom
The Bonjour setting should be tested against business applications that depend on Bonjour discovery before enforcement.
REFERENCE:
CIS macOS 26 Tahoe v1.1.0
============================================================
6. ISSUE: Inadequate Location Services Privacy Indicator Configuration
SEVERITY: Low
OBSERVATION:
The test team observed that the configuration requiring visibility of Location Services usage for system services was not enabled.
In the current scenario, the test team observed that the ShowSystemServices preference was unset, resulting in the associated CIS privacy-indicator control being marked as failed.
RISK IMPACT:
An attacker or unauthorized application activity involving location-related functionality may be less noticeable to the user where system Location Services usage is not clearly indicated, reducing user awareness of location access.
RECOMMENDATION:
It is recommended to configure the Location Services system-services indicator by following the below mentioned steps:
	1. Enable the system-services location indicator:
$ sudo defaults write /Library/Preferences/com.apple.locationmenu.plist ShowSystemServices -bool true
	2. Verify the configured value:
$ sudo defaults read /Library/Preferences/com.apple.locationmenu.plist ShowSystemServices
	3. Confirm that the Location Services indicator is displayed when applicable.
REFERENCE:
CIS macOS 26 Tahoe v1.1.0
============================================================
7. ISSUE: Full-Disk Encryption Not Enabled
SEVERITY: High
OBSERVATION:
The test team observed that full-disk encryption was not enabled on the assessed MacBook, leaving data stored on the device without FileVault protection.
In the current scenario, the test team observed that the FileVault status explicitly reported "FileVault is Off."
RISK IMPACT:
An attacker can access sensitive information stored on the device if the MacBook is lost, stolen, or otherwise physically accessed and the storage is not adequately protected by FileVault. This may result in unauthorized disclosure of corporate files, credentials, cached information, and other locally stored data.
RECOMMENDATION:
It is recommended to enable FileVault full-disk encryption and securely manage the recovery key by following the below mentioned steps:
	1. Verify the current FileVault state:
$ fdesetup status
	2. Enable FileVault through the organization's approved device-management solution where available.
	3. Where local enablement is required, initiate FileVault using the supported FileVault configuration workflow:
$ sudo fdesetup enable
	4. Ensure the generated Personal Recovery Key is securely escrowed or stored according to organizational policy.
	5. Restart the endpoint if required to complete encryption.
	6. Verify:
$ fdesetup status
	7. Confirm that authorized users possess Secure Token/volume ownership as required for FileVault unlock.
Apple recommends managing FileVault through device management for organizational deployments and supports fdesetup for advanced configurations. (Apple Support)
REFERENCE:
CIS macOS 26 Tahoe v1.1.0
Apple FileVault Deployment Guidance
============================================================
8. ISSUE: Insufficient Authorization for System-Wide Preference Changes
SEVERITY: Medium
OBSERVATION:
The test team observed that administrative authorization requirements for system-wide preference modifications did not meet the required macOS security baseline.
In the current scenario, the test team observed that the system-wide preferences authorization control returned a shared configuration of true, rather than enforcing the expected administrator-authentication restrictions.
RISK IMPACT:
An attacker or unauthorized local user can potentially modify security-relevant system preferences with insufficient administrative authorization, depending on the affected preference pane. Such modifications may weaken networking, sharing, software-update, power, or other endpoint security configurations.
RECOMMENDATION:
It is recommended to require administrator authorization for system-wide preference modifications by following the below mentioned steps:
	1. Review the applicable authorization database rights:
$ security authorizationdb read system.preferences
$ security authorizationdb read system.preferences.network
$ security authorizationdb read system.preferences.sharing
$ security authorizationdb read system.preferences.softwareupdate
	2. Ensure that applicable system preference authorization rights are configured with user-class authentication and are not configured as shared.
	3. Apply the required settings through the organization's macOS security configuration baseline or management profile.
	4. After remediation, re-read the applicable rights:
$ security authorizationdb read system.preferences
	5. Re-run the CIS assessment to confirm that the system-wide preference authorization control passes.
Because modification of the macOS authorization database can affect access to System Settings, changes should be performed using an approved configuration workflow.
REFERENCE:
CIS macOS 26 Tahoe v1.1.0
============================================================
9. ISSUE: Inadequate Screen Lock and Login Window Security Configuration
SEVERITY: Medium
OBSERVATION:
The test team observed that multiple screen-lock and login-window security controls were not configured according to the required endpoint security baseline.
In the current scenario, the test team observed that the screen saver inactivity interval was unset, password enforcement after screen/display sleep was unset, the login-window message was not configured, the login window did not enforce name-and-password fields, and no PolicyBanner file was present.
RISK IMPACT:
An attacker can obtain unauthorized access to an unattended logged-in session where automatic locking and password enforcement are insufficient. Displaying user accounts at the login window may also facilitate username enumeration, while the absence of login banners reduces security and acceptable-use notification.
RECOMMENDATION:
It is recommended to configure automatic session locking and harden the login window by following the below mentioned steps:
	1. Configure an inactivity timeout of no more than 15 minutes for each applicable user:
$ sudo -u defaults -currentHost write com.apple.screensaver idleTime -int 900
	2. Require a password after screen saver or display sleep:
$ sudo -u defaults write com.apple.screensaver askForPassword -int 1
	3. Configure a maximum password delay of 5 seconds:
$ sudo -u defaults write com.apple.screensaver askForPasswordDelay -int 5
	4. Configure the login window to require username and password entry:
$ sudo defaults write /Library/Preferences/com.apple.loginwindow SHOWFULLNAME -bool true
	5. Configure an approved login-window message:
$ sudo defaults write /Library/Preferences/com.apple.loginwindow LoginwindowText "Authorized use only."
	6. Create a policy banner:
$ sudo mkdir -p /Library/Security
$ sudo touch /Library/Security/PolicyBanner.txt
	7. Add the organization's approved acceptable-use or security warning text to:
$ sudo nano /Library/Security/PolicyBanner.txt
	8. Configure readable permissions:
$ sudo chmod o+r /Library/Security/PolicyBanner.txt
	9. Verify the screen-lock and login-window settings after remediation.
Apple documents the use of PolicyBanner files under /Library/Security/ and supports name-and-password fields through Login Window configuration. (Apple Support)
REFERENCE:
CIS macOS 26 Tahoe v1.1.0
Apple Login Window and Policy Banner Guidance
============================================================
10. ISSUE: Insufficient Security Log Retention Configuration
SEVERITY: Low
OBSERVATION:
The test team observed that install.log retention was not configured to retain security-relevant installation records for the required period.
In the current scenario, the test team observed that the install ASL configuration specified compressed, size-based rotation with a maximum file size of 50 MB and total size of 150 MB; however, no 365-day retention value was configured.
RISK IMPACT:
An attacker can benefit from insufficient log retention because older evidence of software installation or system changes may be removed before an investigation occurs. This may reduce forensic visibility and make historical security-event reconstruction more difficult.
RECOMMENDATION:
It is recommended to configure install.log retention for at least 365 days by following the below mentioned steps:
	1. Back up the existing install log configuration:
$ sudo cp /etc/asl/com.apple.install /etc/asl/com.apple.install.bak
	2. Edit:
$ sudo nano /etc/asl/com.apple.install
	3. Ensure the install.log rule contains:
ttl=365
	4. Retain existing compression and rotation requirements as appropriate.
	5. Verify the resulting configuration:
$ grep '/var/log/install.log' /etc/asl/com.apple.install
	6. Confirm that ttl=365 is present.
REFERENCE:
CIS macOS 26 Tahoe v1.1.0
============================================================
11. ISSUE: Insecure World-Writable Directory Permissions
SEVERITY: Low
OBSERVATION:
The test team observed that world-writable directories were present under security-sensitive System and Library locations.
In the current scenario, the test team observed world-writable directories under /System/Volumes/Data/System/Library/AssetsV2/ and /System/Volumes/Data/Library/, including locations associated with GarageBand, Audio preferences, and the App Store.
RISK IMPACT:
An attacker can abuse world-writable directories to create, modify, or replace files where other permission and execution conditions permit. This may facilitate unauthorized modification, persistence, tampering, or interference with applications and system processes.
RECOMMENDATION:
It is recommended to remove unnecessary world-write permissions while preserving permissions required by macOS and installed applications by following the below mentioned steps:
	1. Identify world-writable directories under the relevant System path:
$ sudo find /System/Volumes/Data/System -type d -perm -0002 -print
	2. Identify world-writable directories under the Library path:
$ sudo find /System/Volumes/Data/Library -type d -perm -0002 -print
	3. Review each identified directory against expected vendor permissions before modification.
	4. Remove unnecessary world-write permission from confirmed non-compliant directories:
$ sudo chmod o-w ""
	5. Verify permissions:
$ stat -f "%Sp %Su:%Sg %N" ""
	6. Re-run the CIS permission controls after remediation.
REFERENCE:
CIS macOS 26 Tahoe v1.1.0
============================================================
12. ISSUE: Weak Password Authentication and Account Lockout Policy
SEVERITY: Medium
OBSERVATION:
The test team observed that password authentication, password complexity, password aging, password history, and account lockout requirements were not configured according to the required macOS security baseline.
In the current scenario, the test team observed that the account lockout threshold, minimum password length of 15 characters, alphabetic character requirement, numeric character requirement, special-character requirement, mixed-case requirement, maximum password age, and password history controls were not configured. Additionally, the supplied global password policy permits passwords containing only four or more characters and explicitly allows the password field to be left blank.
RISK IMPACT:
An attacker can perform password guessing, brute-force, and credential-reuse attacks more effectively where password complexity, length, aging, history, and account-lockout controls are insufficient. Very short or blank passwords further increase the likelihood of unauthorized account access.
RECOMMENDATION:
It is recommended to enforce an organization-approved macOS password policy by following the below mentioned steps:
	1. Review the current global account policy:
$ pwpolicy -getaccountpolicies
	2. Configure password requirements that enforce at minimum:
	• Minimum length of 15 characters
	• Alphabetic characters
	• Numeric characters
	• Special characters
	• Uppercase and lowercase characters
	• Password history of at least 15
	• Password age of no more than 365 days
	• Failed-authentication lockout threshold of no more than 5 attempts
	3. Remove any policy condition that allows blank passwords.
	4. Prefer deployment of the required password policy through an approved configuration profile or identity-management policy for enterprise endpoints.
	5. After applying the policy, verify:
$ pwpolicy -getaccountpolicies
	6. Test the policy using a non-production test account before organization-wide deployment.
REFERENCE:
CIS macOS 26 Tahoe v1.1.0
============================================================
13. ISSUE: Inadequate Sudo Authentication Timeout Configuration
SEVERITY: Low
OBSERVATION:
The test team observed that the sudo authentication timeout was not explicitly configured according to the required security baseline.
In the current scenario, the test team observed that the supplied sudoers configuration did not contain a timestamp_timeout=0 setting.
RISK IMPACT:
An attacker can potentially make use of a previously authenticated sudo session during the credential-caching window if access to the user's terminal or session is obtained, allowing commands to execute with elevated privileges without requiring immediate reauthentication.
RECOMMENDATION:
It is recommended to require sudo users to authenticate for each privileged command by following the below mentioned steps:
	1. Create a dedicated sudoers configuration:
$ sudo visudo -f /etc/sudoers.d/10_cissudoconfiguration
	2. Add:
Defaults timestamp_timeout=0
	3. Ensure the sudoers.d directory has the correct ownership:
$ sudo chown -R root:wheel /etc/sudoers.d
	4. Validate the sudoers configuration:
$ sudo visudo -c
	5. Verify the configured authentication timeout:
$ sudo sudo -V | grep "Authentication timestamp timeout"
The expected timeout should be 0.0 minutes. (Tenable®)
REFERENCE:
CIS macOS 26 Tahoe v1.1.0
============================================================
14. ISSUE: File Extensions Not Configured to be Displayed
SEVERITY: Low
OBSERVATION:
The test team observed that Finder was not configured to display all filename extensions.
In the current scenario, the test team observed that the AppleShowAllExtensions preference was unset, causing the associated CIS security control to fail.
RISK IMPACT:
An attacker can use misleading filenames or hidden extensions to make malicious files appear to be benign documents or other trusted file types, increasing the likelihood that a user may unknowingly open unsafe content.
RECOMMENDATION:
It is recommended to configure Finder to display all filename extensions by following the below mentioned steps:
	1. Enable filename extension visibility for each applicable user:
$ sudo -u defaults write NSGlobalDomain AppleShowAllExtensions -bool true
	2. Restart Finder for the setting to take effect:
$ sudo -u killall Finder
	3. Verify:
$ sudo -u defaults read NSGlobalDomain AppleShowAllExtensions
The expected value should be 1 or true.
REFERENCE:
CIS macOS 26 Tahoe v1.1.0
============================================================
15. ISSUE: Configuration Profiles Not Installed
SEVERITY: Low
OBSERVATION:
The test team observed that no macOS configuration profiles were installed on the assessed endpoint.
In the current scenario, the test team observed that the configuration-profile inventory explicitly returned "There are no configuration profiles installed."
RISK IMPACT:
An attacker can benefit from security settings that are configured only locally and can potentially be altered by users with sufficient privileges where centrally enforced configuration profiles are absent. The absence of profiles may also reduce consistency of security controls across managed endpoints.
RECOMMENDATION:
It is recommended to deploy organization-approved macOS security configuration profiles by following the below mentioned steps:
	1. Define the required endpoint configuration in the organization's device-management platform.
	2. Include security settings such as:
	• Firewall configuration
	• AirDrop/AirPlay restrictions
	• Password policy
	• Login-window controls
	• FileVault enforcement
	• Software-update policy
	• Sharing-service restrictions
	3. Enroll the Mac into the approved device-management service where applicable.
	4. Deploy the approved security configuration profile.
	5. Verify installed profiles:
$ system_profiler SPConfigurationProfileDataType
	6. Confirm that the required security payloads are installed and enforced.
Apple's deployment guidance describes configuration profiles and device management as mechanisms for managing Mac security and system settings. (Apple Support)
REFERENCE:
Apple Platform Deployment
CIS macOS 26 Tahoe v1.1.0
============================================================
16. ISSUE: Device Activation Lock Not Enabled
SEVERITY: Low
OBSERVATION:
The test team observed that Activation Lock was not enabled on the assessed MacBook.
In the current scenario, the test team observed that the system information reported "Activation Lock Status: Disabled." The endpoint is an Apple silicon MacBook Pro, which supports Activation Lock.
RISK IMPACT:
An attacker can more easily erase, reactivate, or reuse a stolen or lost Mac when Activation Lock is not enabled. This reduces the endpoint's theft-deterrence and device-recovery protections.
RECOMMENDATION:
It is recommended to enable Activation Lock through the organization's approved device-management or Find My configuration by following the below mentioned steps:
	1. For an individually managed Mac, open:
System Settings > Apple Account > iCloud > Find My Mac
	2. Enable Find My Mac.
	3. Ensure Location Services is enabled for Find My where required.
	4. Verify Activation Lock status through the organization's management platform or system inventory.
	5. For organization-owned supervised Macs, use the approved device-management service to manage Activation Lock and retain any required bypass code.
Apple states that enabling Find My on an eligible Mac enables Activation Lock. (Apple Support)
REFERENCE:
Apple Activation Lock for Mac
============================================================
17. ISSUE: Multiple Local Administrative Accounts Configured
SEVERITY: Medium
OBSERVATION:
The test team observed that multiple accounts were configured as members of the local administrative group on the assessed endpoint.
In the current scenario, the test team observed that the local admin group contained the following members:
	1. root
	2. admin
	3. e25-08884
	4. _mbsetupuser
The supplied user inventory confirms these administrative group memberships.
RISK IMPACT:
An attacker can gain extensive control over the endpoint if credentials belonging to any unnecessary administrative account are compromised. A larger number of privileged accounts increases the number of credentials and user contexts capable of modifying security settings, installing software, accessing protected resources, or disabling endpoint controls.
RECOMMENDATION:
It is recommended to restrict local administrative privileges to accounts that require them for legitimate administrative duties by following the below mentioned steps:
	1. Review current members of the admin group:
$ dscl . -read /Groups/admin GroupMembership
	2. Identify accounts that do not require administrative privileges.
	3. Remove unnecessary users from the admin group:
$ sudo dseditgroup -o edit -d -t user admin
	4. Verify the resulting group membership:
$ dscl . -read /Groups/admin GroupMembership
	5. Maintain only approved administrative accounts and use standard accounts for routine user activity.
	6. Periodically review local administrative group membership as part of endpoint-access reviews.
REFERENCE:
CIS macOS 26 Tahoe v1.1.0
============================================================
SEVERITY SUMMARY
High: 1
	1. Full-Disk Encryption Not Enabled
Medium: 7
	1. Inadequate Software Update and Patch Management Configuration
	2. Inadequate Host-Based Firewall Configuration
	3. Unnecessary Network and Remote Sharing Services Enabled
	4. Insufficient Authorization for System-Wide Preference Changes
	5. Inadequate Screen Lock and Login Window Security Configuration
	6. Weak Password Authentication and Account Lockout Policy
	7. Multiple Local Administrative Accounts Configured
Low: 9
	1. Unrestricted Wireless Sharing Services
	2. Inadequate Network Discovery and Wake Service Hardening
	3. Inadequate Location Services Privacy Indicator Configuration
	4. Insufficient Security Log Retention Configuration
	5. Insecure World-Writable Directory Permissions
	6. Inadequate Sudo Authentication Timeout Configuration
	7. File Extensions Not Configured to be Displayed
	8. Configuration Profiles Not Installed
	9. Device Activation Lock Not Enabled
TOTAL: 17 issues.

From <https://chatgpt.com/g/g-p-68da8a6c742881918ea4f1aa2e62f91c/c/6a7959e4-7b5c-83ec-b68f-d90c2e049039> 
