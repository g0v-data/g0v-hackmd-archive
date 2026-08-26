Below is the consolidated report for TN-GOBI-ELITE-S covering all 12 confirmed findings in the same Windows reporting format you specified.
The endpoint is Microsoft Windows 10 Enterprise LTSC, build 10.0.19044, and the evidence was collected on 20 July 2026 at 16:34 IST.

1. Windows Defender Firewall Disabled for All Network Profiles
Observation
The test team observed that Windows Defender Firewall is not configured as per security best practices across the network profiles.
In the current scenario, the test team observed that Windows Defender Firewall is disabled for the Domain, Private, and Public network profiles. Please find the affected registry paths and observed values below:
	1. Windows Defender Firewall for Domain Profile is set to Disabled
HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\SharedAccess\Parameters\FirewallPolicy\DomainProfile:EnableFirewall
Observed Value: 0
	2. Windows Defender Firewall for Private/Standard Profile is set to Disabled
HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\SharedAccess\Parameters\FirewallPolicy\StandardProfile:EnableFirewall
Observed Value: 0
	3. Windows Defender Firewall for Public Profile is set to Disabled
HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\SharedAccess\Parameters\FirewallPolicy\PublicProfile:EnableFirewall
Observed Value: 0
The Firewall Status artifact additionally confirmed that Domain, Private, and Public profiles were all configured with Enabled=False.
Risk Impact
An attacker can communicate with network-accessible services without host-level firewall restrictions when Windows Defender Firewall is disabled. This increases the endpoint attack surface and can facilitate service enumeration, exploitation attempts, unauthorized connections, and lateral movement within the network.
Severity
Medium
Affected Asset
TN-GOBI-ELITE-S
Recommendation
It is recommended to enable Windows Defender Firewall across all applicable network profiles by following the below mentioned steps:
	1. To establish the recommended configuration via Group Policy, configure:
Computer Configuration\Policies\Windows Settings\Security Settings\Windows Defender Firewall with Advanced Security\Windows Defender Firewall Properties\Domain Profile\Firewall state
Set to:
On (recommended)
	2. Configure:
Computer Configuration\Policies\Windows Settings\Security Settings\Windows Defender Firewall with Advanced Security\Windows Defender Firewall Properties\Private Profile\Firewall state
Set to:
On (recommended)
	3. Configure:
Computer Configuration\Policies\Windows Settings\Security Settings\Windows Defender Firewall with Advanced Security\Windows Defender Firewall Properties\Public Profile\Firewall state
Set to:
On (recommended)
	4. Configure the default inbound action as Block and permit only approved application/service traffic.
	5. Verify using:
Get-NetFirewallProfile | Select Name,Enabled,DefaultInboundAction,DefaultOutboundAction
Reference Controls
CIS Microsoft Windows 10 Enterprise Benchmark
Microsoft Windows Defender Firewall Security Guidance
CVE
NA

2. SMB Signing Not Enforced
Observation
The test team observed that SMB signing is not configured as per security best practices.
In the current scenario, the test team observed that SMB signing is not required for both SMB server and SMB client communications. Please find the affected registry paths and observed values below:
	1. Microsoft network server: Digitally sign communications (always) is set to Disabled
HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\LanmanServer\Parameters:RequireSecuritySignature
Observed Value: 0
Recommended Value: 1
	2. Microsoft network client: Digitally sign communications (always) is set to Disabled
HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\LanmanWorkstation\Parameters:RequireSecuritySignature
Observed Value: 0
Recommended Value: 1
The service evidence confirmed that both LanmanServer and LanmanWorkstation were active, while the network assessment confirmed TCP port 445 was open.
Risk Impact
An attacker can perform man-in-the-middle or SMB relay attacks where SMB signing is not required by communicating endpoints. Unsigned SMB traffic can potentially be intercepted, modified, or relayed, resulting in unauthorized authentication or access to network resources.
Severity
Medium
Affected Asset
TN-GOBI-ELITE-S
Recommendation
It is recommended to enforce SMB signing for SMB client and server communications by following the below mentioned steps:
	1. To establish the recommended configuration via Group Policy, set the following UI path to Enabled:
Computer Configuration\Policies\Windows Settings\Security Settings\Local Policies\Security Options\Microsoft network server: Digitally sign communications (always)
	2. Set the following UI path to Enabled:
Computer Configuration\Policies\Windows Settings\Security Settings\Local Policies\Security Options\Microsoft network client: Digitally sign communications (always)
	3. Verify the server configuration:
Get-SmbServerConfiguration | Select RequireSecuritySignature
	4. Verify the client configuration:
Get-SmbClientConfiguration | Select RequireSecuritySignature
	5. Confirm compatibility with any legacy SMB-dependent devices before organization-wide enforcement.
Reference Controls
CIS Microsoft Windows 10 Enterprise Benchmark
Microsoft SMB Signing Security Guidance
CVE
NA

3. Insufficient Anonymous Network Access Restrictions
Observation
The test team observed that anonymous network access restrictions are not configured as per security best practices.
In the current scenario, the test team observed that anonymous enumeration of SAM accounts and network shares is not adequately restricted. Please find the affected registry path and observed value below:
	1. Network access: Do not allow anonymous enumeration of SAM accounts and shares is set to Disabled
HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\Lsa:RestrictAnonymous
Observed Value: 0
Recommended Value: 1
The related RestrictAnonymousSAM value was observed as 1; however, the broader restriction covering anonymous enumeration of both accounts and network shares was not enabled.
Risk Impact
An attacker can potentially use anonymous network connections to collect information about local accounts and shared resources. Such information may facilitate reconnaissance, password guessing, targeted SMB attacks, and lateral movement.
Severity
Medium
Affected Asset
TN-GOBI-ELITE-S
Recommendation
It is recommended to restrict anonymous enumeration of SAM accounts and network shares by following the below mentioned steps:
	1. To establish the recommended configuration via Group Policy, set:
Computer Configuration\Policies\Windows Settings\Security Settings\Local Policies\Security Options\Network access: Do not allow anonymous enumeration of SAM accounts and shares
Set to:
Enabled
	2. Verify:
HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\Lsa:RestrictAnonymous
Recommended Value: 1
	3. Retain the existing secure configuration for anonymous SAM-only enumeration restrictions.
	4. Review anonymous access to named pipes and network shares and allow only explicitly required resources.
Reference Controls
CIS Microsoft Windows 10 Enterprise Benchmark
CVE
NA

4. Insecure Storage of Network Authentication Credentials
Observation
The test team observed that storage of passwords and credentials used for network authentication is not restricted as per security best practices.
In the current scenario, the test team observed that Windows is configured to permit the storage of network authentication credentials. Please find the affected registry path and observed value below:
	1. Network access: Do not allow storage of passwords and credentials for network authentication is set to Disabled
HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\Lsa:DisableDomainCreds
Observed Value: 0
Recommended Value: 1
Risk Impact
An attacker can potentially obtain stored network authentication credentials after compromising the endpoint or an authenticated user context. Compromised credentials may subsequently be reused to access other endpoints, network shares, applications, or network resources and facilitate lateral movement.
Severity
Medium
Affected Asset
TN-GOBI-ELITE-S
Recommendation
It is recommended to prevent storage of passwords and credentials used for network authentication by following the below mentioned steps:
	1. To establish the recommended configuration via Group Policy, set:
Computer Configuration\Policies\Windows Settings\Security Settings\Local Policies\Security Options\Network access: Do not allow storage of passwords and credentials for network authentication
Set to:
Enabled
	2. Verify:
HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\Lsa:DisableDomainCreds
Recommended Value: 1
	3. Review Windows Credential Manager and remove unnecessary stored credentials.
	4. Validate scheduled tasks, applications, or services that legitimately depend on stored credentials before enforcing the setting.
Reference Controls
CIS Microsoft Windows 10 Enterprise Benchmark
Microsoft Network Authentication Security Guidance
CVE
NA

5. Weak NTLM Session Security Configuration
Observation
The test team observed that minimum NTLM session security requirements are not configured as per security best practices.
In the current scenario, the test team observed that both NTLM client and server configurations require 128-bit encryption but do not require NTLMv2 session security. Please find the affected registry paths below:
	1. Minimum session security for NTLM SSP-based clients
HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\Lsa\MSV1_0:NtlmMinClientSec
Observed Value: 536870912
Recommended Value: 537395200
	2. Minimum session security for NTLM SSP-based servers
HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\Lsa\MSV1_0:NtlmMinServerSec
Observed Value: 536870912
Recommended Value: 537395200
The observed value requires 128-bit encryption, whereas the recommended value additionally requires NTLMv2 session security.
Risk Impact
An attacker can attempt to exploit weaker NTLM session negotiation where NTLMv2 session security is not explicitly required. This may increase exposure to credential relay, interception, tampering, and man-in-the-middle attacks.
Severity
Medium
Affected Asset
TN-GOBI-ELITE-S
Recommendation
It is recommended to enforce NTLMv2 session security and 128-bit encryption by following the below mentioned steps:
	1. Configure:
Computer Configuration\Policies\Windows Settings\Security Settings\Local Policies\Security Options\Network security: Minimum session security for NTLM SSP based (including secure RPC) clients
Enable:
Require NTLMv2 session security
Require 128-bit encryption
	2. Configure:
Computer Configuration\Policies\Windows Settings\Security Settings\Local Policies\Security Options\Network security: Minimum session security for NTLM SSP based (including secure RPC) servers
Enable:
Require NTLMv2 session security
Require 128-bit encryption
	3. Verify:
NtlmMinClientSec = 537395200
NtlmMinServerSec = 537395200
Reference Controls
CIS Microsoft Windows 10 Enterprise Benchmark
Microsoft NTLM SSP Security Guidance
CVE
NA

6. Inadequate Interactive Logon Security Configuration
Observation
The test team observed that interactive logon security settings are not configured as per security best practices.
In the current scenario, the test team observed multiple interactive logon security weaknesses. Please find the affected settings below:
	1. Last signed-in username is displayed
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\System:DontDisplayLastUserName
Observed Value: 0
Recommended Value: 1
	2. Ctrl+Alt+Del Secure Attention Sequence is not required
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\Winlogon:DisableCAD
Observed Value: 1
Recommended Value: 0
	3. System shutdown is permitted without authentication
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\System:ShutdownWithoutLogon
Observed Value: 1
Recommended Value: 0
	4. Excessive previous domain logons are cached
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\Winlogon:CachedLogonsCount
Observed Value: 10
Risk Impact
An attacker can obtain useful account information where the previous username is displayed and may target locally cached authentication information following endpoint compromise. Disabling the secure attention sequence can reduce protection against fraudulent logon interfaces, while permitting unauthenticated shutdown can facilitate local denial-of-service activity.
Severity
Low
Affected Asset
TN-GOBI-ELITE-S
Recommendation
It is recommended to strengthen interactive logon security by following the below mentioned steps:
	1. Configure:
Computer Configuration\Policies\Windows Settings\Security Settings\Local Policies\Security Options\Interactive logon: Don't display last signed-in
Set to:
Enabled
	2. Configure:
Computer Configuration\Policies\Windows Settings\Security Settings\Local Policies\Security Options\Interactive logon: Do not require CTRL+ALT+DEL
Set to:
Disabled
	3. Configure:
Computer Configuration\Policies\Windows Settings\Security Settings\Local Policies\Security Options\Shutdown: Allow system to be shut down without having to log on
Set to:
Disabled
	4. Configure:
Computer Configuration\Policies\Windows Settings\Security Settings\Local Policies\Security Options\Interactive logon: Number of previous logons to cache (in case domain controller is not available)
Set to an organization-approved hardened value where domain authentication is applicable.
Reference Controls
CIS Microsoft Windows 10 Enterprise Benchmark
CVE
NA

7. Weak User Account Control Elevation Configuration
Observation
The test team observed that User Account Control elevation behaviour is not configured as per security best practices.
In the current scenario, the test team observed that administrator elevation occurs without prompting, secure desktop prompting is disabled, and standard users are permitted to provide credentials during elevation. Please find the affected registry paths below:
	1. Administrator elevation behaviour
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\System:ConsentPromptBehaviorAdmin
Observed Value: 0
Observed Configuration:
Elevate without prompting
	2. Secure desktop prompting
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\System:PromptOnSecureDesktop
Observed Value: 0
Observed Configuration:
Disabled
	3. Standard-user elevation behaviour
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\System:ConsentPromptBehaviorUser
Observed Value: 3
Observed Configuration:
Prompt for credentials
The EnableLUA value was observed as 1; therefore, UAC itself is enabled and the issue relates specifically to the weak elevation configuration.
Risk Impact
An attacker can more easily abuse administrative user sessions where privileged operations are allowed to elevate without prompting. Disabling secure desktop isolation further weakens the integrity of elevation prompts, while allowing standard users to enter administrator credentials can increase the possibility of privileged credential exposure.
Severity
Medium
Affected Asset
TN-GOBI-ELITE-S
Recommendation
It is recommended to strengthen User Account Control elevation behaviour by following the below mentioned steps:
	1. Configure:
Computer Configuration\Policies\Windows Settings\Security Settings\Local Policies\Security Options\User Account Control: Behavior of the elevation prompt for administrators in Admin Approval Mode
Set to:
Prompt for consent on the secure desktop
	2. Configure:
Computer Configuration\Policies\Windows Settings\Security Settings\Local Policies\Security Options\User Account Control: Switch to the secure desktop when prompting for elevation
Set to:
Enabled
	3. Configure:
Computer Configuration\Policies\Windows Settings\Security Settings\Local Policies\Security Options\User Account Control: Behavior of the elevation prompt for standard users
Set to:
Automatically deny elevation requests
	4. Retain User Account Control as enabled.
Reference Controls
CIS Microsoft Windows 10 Enterprise Benchmark
Microsoft User Account Control Security Guidance
CVE
NA

8. Insecure ICMP Redirect Processing Configuration
Observation
The test team observed that ICMP redirect processing is not configured as per security best practices.
In the current scenario, the test team observed that ICMP redirect processing is enabled on the Windows TCP/IP stack. Please find the affected registry path below:
	1. ICMP redirect processing is set to Enabled
HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\Tcpip\Parameters:EnableICMPRedirect
Observed Value: 1
Recommended Value: 0
The registry additionally contained DeadGWDetectDefault=1; however, the primary basis of this finding is the enabled ICMP redirect processing configuration.
Risk Impact
An attacker can attempt to send malicious ICMP redirect messages from a reachable network position to influence the endpoint's routing decisions. Successful manipulation can potentially redirect traffic through an unintended or attacker-controlled network path and increase the possibility of traffic interception or man-in-the-middle attacks.
Severity
Low
Affected Asset
TN-GOBI-ELITE-S
Recommendation
It is recommended to disable ICMP redirect processing by following the below mentioned steps:
	1. To establish the recommended configuration via Group Policy, configure:
Computer Configuration\Policies\Administrative Templates\MSS (Legacy)\MSS: (EnableICMPRedirect) Allow ICMP redirects to override OSPF generated routes
Set to:
Disabled
	2. Verify:
HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\Tcpip\Parameters:EnableICMPRedirect
Recommended Value: 0
	3. Apply the policy:
gpupdate /force
	4. Verify the effective value after policy application.
Reference Controls
CIS Microsoft Windows 10 Enterprise Benchmark
MSS Legacy Network Security Settings
CVE
NA

9. Unsupported and Outdated Software Components Installed
Observation
The test team observed that unsupported and outdated software components are installed and actively used on the assessed endpoint.
In the current scenario, the test team observed multiple software components that have exceeded their supported lifecycle. Please find the identified components below:
	1. Microsoft SQL Server 2012
Active SQL Instance:
GFT
Service:
MSSQL$GFT
Service State:
Running / Automatic
Executable Path:
C:\Program Files\Microsoft SQL Server\MSSQL11.GFT\MSSQL\Binn\sqlservr.exe
The SQL Server Browser service for SQL Server 2012 was also observed running automatically.
	2. Apache HTTP Server
Installed/Active Version:
Apache/2.2.17 (Win32)
Service:
NetTradeApache
Service State:
Running / Automatic
Apache HTTP Server 2.2 is an end-of-life product branch.
	3. Microsoft Visual C++ 2008 Redistributable
Installed Version:
9.0.21022
	4. Microsoft Visual C++ 2010 Redistributable
Installed Version:
10.0.40219
These runtime branches have exceeded their supported Microsoft lifecycle.
Risk Impact
An attacker can exploit known or subsequently discovered vulnerabilities affecting unsupported software components for which normal vendor security updates are no longer available. The risk is increased where unsupported components such as SQL Server and Apache remain actively running and process application or network data.
Severity
Medium
Affected Asset
TN-GOBI-ELITE-S
Recommendation
It is recommended to remove or upgrade unsupported software components by following the below mentioned steps:
	1. Upgrade the SQL Server 2012 GFT instance to a currently supported Microsoft SQL Server release after application compatibility testing.
	2. Upgrade Apache HTTP Server 2.2.17 to a currently supported web-server release compatible with the GOFRUGAL/NetTrade application.
	3. Identify applications dependent on Microsoft Visual C++ 2008 and Visual C++ 2010 runtimes.
	4. Upgrade dependent applications to versions supporting current Microsoft runtime components.
	5. Remove obsolete Visual C++ runtimes only after dependency and application testing.
	6. Establish periodic software lifecycle reviews to identify unsupported software before vendor support expires.
Reference Controls
CIS Microsoft Windows 10 Enterprise Benchmark
Microsoft SQL Server Lifecycle Guidance
Apache HTTP Server Security/Lifecycle Guidance
Microsoft Visual C++ Product Lifecycle Guidance
CVE
NA

10. Web/Application Server Services Running with Excessive Privileges
Observation
The test team observed that web and application server services are running with excessive operating system privileges.
In the current scenario, the test team observed that GOFRUGAL/NetTrade web application components are configured to run under the LocalSystem account and their processes are operating as SYSTEM. Please find the affected services below:
	1. NetTrade Apache Web Server
Service:
NetTradeApache
Service Account:
LocalSystem
Process:
D:\GOFRUGAL\GOFRUGALRetailEasy\NetTrade\apache\bin\Apache.exe
Process Owner:
SYSTEM
	2. NetTrade Tomcat Application Server
Service:
NetTradeTomcat
Service Account:
LocalSystem
Process Owner:
SYSTEM
	3. GOFRUGAL RPOS7 WebReporter
Service:
GoFrugalRPOS7WRP
Service Account:
LocalSystem
Process Owner:
SYSTEM
These web/application services therefore operate with highly privileged local system access rather than a dedicated least-privilege application account.
Risk Impact
An attacker can obtain SYSTEM-level privileges if a vulnerability in the GOFRUGAL/NetTrade web application, Apache server, Tomcat component, WebReporter, or related application code is successfully exploited. SYSTEM-level execution can allow complete endpoint compromise, sensitive data access, credential extraction, security-control modification, persistence, and further lateral movement.
Severity
High
Affected Asset
TN-GOBI-ELITE-S
Recommendation
It is recommended to configure web and application services to run using dedicated least-privilege service accounts by following the below mentioned steps:
	1. Create dedicated service accounts for the NetTrade/GOFRUGAL web application components.
	2. Do not add the service accounts to the local Administrators group.
	3. Grant only the minimum required permissions to:
	• Application directories
	• Web content
	• Log directories
	• Temporary directories
	• Required database/application resources
	4. Configure the affected Windows services to use the dedicated service accounts instead of LocalSystem.
	5. Restart the affected services after applying the new service identities.
	6. Verify the running process owners and ensure Apache, Tomcat, and WebReporter processes no longer execute as SYSTEM.
	7. Perform application functionality testing following remediation.
Reference Controls
CIS Microsoft Windows 10 Enterprise Benchmark
Principle of Least Privilege
Microsoft Windows Service Account Security Guidance
CVE
NA

11. Weak Local Password and Account Lockout Policy
Observation
The test team observed that the local password and account lockout policy is not configured as per security best practices.
In the current scenario, the test team observed the following weak local account policy configurations:
	1. Minimum password length is not enforced
Observed Value:
MinPasswordLength = 0
	2. Minimum password age is not enforced
Observed Value:
MinPasswordAge = 0
	3. Account lockout threshold is disabled
Observed Value:
MaxBadPasswords = 0
The configured maximum password age was observed as 42 days and was therefore not included as a failed configuration.
Risk Impact
An attacker can perform password guessing and brute-force authentication attacks more effectively where minimum password requirements and account lockout controls are not enforced. An account lockout threshold of zero permits repeated failed authentication attempts without automatically locking the targeted account.
Severity
Medium
Affected Asset
TN-GOBI-ELITE-S
Recommendation
It is recommended to enforce a strong password and account lockout policy by following the below mentioned steps:
	1. Configure:
Computer Configuration\Policies\Windows Settings\Security Settings\Account Policies\Password Policy\Minimum password length
Set to:
14 characters or greater, or the organization-approved standard.
	2. Configure:
Computer Configuration\Policies\Windows Settings\Security Settings\Account Policies\Password Policy\Minimum password age
Set to:
1 or more day(s)
	3. Configure:
Computer Configuration\Policies\Windows Settings\Security Settings\Account Policies\Account Lockout Policy\Account lockout threshold
Set to:
5 or fewer invalid authentication attempts, but not 0.
	4. Configure appropriate values for:
Account lockout duration
Reset account lockout counter after
	5. Verify the effective configuration using:
net accounts
Reference Controls
CIS Microsoft Windows 10 Enterprise Benchmark
Microsoft Password and Account Lockout Policy Guidance
CVE
NA

12. Insecure Local Account Configuration
Observation
The test team observed that enabled local user accounts are not configured in accordance with password and privileged account security best practices.
In the current scenario, the test team observed insecure configurations affecting the built-in Administrator account and the actively used POS account.
	1. Built-in Administrator account
Account:
Administrator
Account Status:
Enabled
SID:
Built-in account SID ending in -500
Password Configuration:
DONT_EXPIRE_PASSWORD
Password Age:
332 days
Last Login:
20-07-2026 16:21:02
The account retains the default built-in Administrator identity, has a non-expiring password, and was actively used on the assessment date.
	2. POS account
Account:
POS
Account Status:
Enabled
Password Configuration:
PASSWD_NOTREQD
DONT_EXPIRE_PASSWORD
Password Age:
332 days
Last Login:
20-07-2026 09:11:09
The PASSWD_NOTREQD flag indicates that Windows does not enforce a password requirement for the account, while DONT_EXPIRE_PASSWORD exempts the account from password-expiration requirements.
The PASSWD_NOTREQD flag does not by itself prove that the current password is blank.
Risk Impact
An attacker can obtain persistent unauthorized access more easily where enabled accounts use non-expiring credentials or are permitted to operate without an enforced password requirement. Compromise of the actively used built-in Administrator account could additionally provide extensive control over the endpoint and installed applications.
Severity
Medium
Affected Asset
TN-GOBI-ELITE-S
Recommendation
It is recommended to securely configure enabled local accounts by following the below mentioned steps:
	1. Verify whether routine use of the built-in Administrator account is required.
	2. Where operationally feasible, configure:
Computer Configuration\Policies\Windows Settings\Security Settings\Local Policies\Security Options\Accounts: Administrator account status
Set to:
Disabled
	3. Where the built-in account must remain enabled, configure:
Computer Configuration\Policies\Windows Settings\Security Settings\Local Policies\Security Options\Accounts: Rename administrator account
Set to:
An organization-approved non-default name.
	4. Remove the Password Never Expires configuration from the Administrator account.
	5. Manage the Administrator credential through Windows LAPS or an approved privileged-access-management solution.
	6. Review the POS account and configure a strong password.
	7. Remove the password-not-required configuration.
	8. Remove the DONT_EXPIRE_PASSWORD configuration where compatible with the POS application.
	9. Rotate the existing 332-day-old credentials.
	10. Restrict interactive administrative use of privileged accounts to specifically approved administrative activities.
Reference Controls
CIS Microsoft Windows 10 Enterprise Benchmark
Microsoft Local Account Security Guidance
Microsoft Windows LAPS Guidance
CVE
NA

TN-GOBI-ELITE-S Finding Summary
#	Finding	Severity
1	Windows Defender Firewall Disabled for All Network Profiles	Medium
2	SMB Signing Not Enforced	Medium
3	Insufficient Anonymous Network Access Restrictions	Medium
4	Insecure Storage of Network Authentication Credentials	Medium
5	Weak NTLM Session Security Configuration	Medium
6	Inadequate Interactive Logon Security Configuration	Low
7	Weak User Account Control Elevation Configuration	Medium
8	Insecure ICMP Redirect Processing Configuration	Low
9	Unsupported and Outdated Software Components Installed	Medium
10	Web/Application Server Services Running with Excessive Privileges	High
11	Weak Local Password and Account Lockout Policy	Medium
12	Insecure Local Account Configuration	Medium
High: 1
Medium: 9
Low: 2
Total: 12 findings

From <https://chatgpt.com/g/g-p-68da8a6c742881918ea4f1aa2e62f91c/c/6a7959e4-7b5c-83ec-b68f-d90c2e049039> 

