Below is the final consolidated BIXAPP Windows Server 2022 report in the Windows format you specified. BIXAPP is confirmed as Microsoft Windows Server 2022 Standard, build 10.0.20348, with the evidence collected on 18 July 2026.

1. Windows Defender Firewall Disabled for Domain and Private Profiles
Observation
The test team observed that Windows Defender Firewall is not configured as per security best practices across all network profiles.
In the current scenario, the test team observed that Windows Defender Firewall is disabled for the Domain and Private profiles. Please find the affected registry paths and observed values below:
	1. Windows Defender Firewall for Domain Profile is set to Disabled
HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\SharedAccess\Parameters\FirewallPolicy\DomainProfile:EnableFirewall
Observed Value: 0
	2. Windows Defender Firewall for Private/Standard Profile is set to Disabled
HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\SharedAccess\Parameters\FirewallPolicy\StandardProfile:EnableFirewall
Observed Value: 0
The firewall-status output additionally confirmed that the Domain and Private profiles were disabled, while the Public profile was enabled.
Risk Impact
An attacker can communicate with network-accessible services without the intended host-based firewall restrictions when the server is operating under a Domain or Private network profile. This can increase the attack surface and facilitate service enumeration, exploitation attempts, unauthorized connections, and lateral movement.
Severity
Medium
Affected Asset
BIXAPP
Recommendation
It is recommended to enable Windows Defender Firewall for all applicable network profiles by following the below mentioned steps:
	1. To establish the recommended configuration via Group Policy, configure the following UI path:
Computer Configuration\Policies\Windows Settings\Security Settings\Windows Firewall with Advanced Security\Windows Firewall with Advanced Security\Windows Firewall Properties\Domain Profile\Firewall state
Set to:
On (recommended)
	2. Configure the following UI path:
Computer Configuration\Policies\Windows Settings\Security Settings\Windows Firewall with Advanced Security\Windows Firewall with Advanced Security\Windows Firewall Properties\Private Profile\Firewall state
Set to:
On (recommended)
	3. Configure the default inbound action as Block unless an approved inbound firewall rule explicitly permits the required traffic.
	4. Verify the effective configuration using:
Get-NetFirewallProfile | Select Name,Enabled,DefaultInboundAction,DefaultOutboundAction
Reference Controls
CIS Microsoft Windows Server 2022 Benchmark
Microsoft Windows Defender Firewall Security Guidance
CVE
NA

2. SMB Signing Not Enforced
Observation
The test team observed that SMB signing is not configured as per security best practices.
In the current scenario, the test team observed that SMB signing is not required for either SMB server or SMB client communication. Please find the affected registry paths and observed values below:
	1. Microsoft network server: Digitally sign communications (always) is not enforced
HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\LanmanServer\Parameters:RequireSecuritySignature
Observed Value: 0
	2. Microsoft network client: Digitally sign communications (always) is not enforced
HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\LanmanWorkstation\Parameters:RequireSecuritySignature
Observed Value: 0
The assessment additionally confirmed that SMB services were active and TCP port 445 was available on the assessed server. Microsoft confirms that a RequireSecuritySignature value of 0 means SMB signing is not required. (Microsoft Learn)
Risk Impact
An attacker can perform man-in-the-middle or SMB relay attacks when SMB signing is not required by both communicating systems. Unsigned SMB communications may potentially be intercepted, modified, or relayed, resulting in unauthorized authentication or access to network resources.
Severity
Medium
Affected Asset
BIXAPP
Recommendation
It is recommended to enforce SMB signing for both client and server communications by following the below mentioned steps:
	1. To establish the recommended configuration via Group Policy, set the following UI path to Enabled:
Computer Configuration\Policies\Windows Settings\Security Settings\Local Policies\Security Options\Microsoft network server: Digitally sign communications (always)
	2. Set the following UI path to Enabled:
Computer Configuration\Policies\Windows Settings\Security Settings\Local Policies\Security Options\Microsoft network client: Digitally sign communications (always)
	3. Verify the SMB server configuration:
Get-SmbServerConfiguration | Select RequireSecuritySignature
	4. Verify the SMB client configuration:
Get-SmbClientConfiguration | Select RequireSecuritySignature
	5. Confirm compatibility with any legacy SMB devices before organization-wide enforcement.
Microsoft documents these exact Group Policy controls for SMB signing. (Microsoft Learn)
Reference Controls
CIS Microsoft Windows Server 2022 Benchmark
Microsoft SMB Signing Guidance
CVE
NA

3. Weak Local Password and Account Lockout Policy
Observation
The test team observed that the local password and account lockout policy is not configured as per security best practices.
In the current scenario, the test team observed the following insecure local account policy configurations:
	1. Minimum password length is not configured
Observed Value:
MinPasswordLength = 0
	2. Minimum password age is not configured
Observed Value:
MinPasswordAge = 0
	3. Account lockout threshold is not configured
Observed Value:
MaxBadPasswords = 0
A minimum password length of 0 allows local accounts to be configured without an enforced minimum length, while an account lockout threshold of 0 allows repeated failed authentication attempts without automatically locking the targeted account.
Risk Impact
An attacker can perform password guessing and brute-force authentication attempts more effectively when minimum password length and account lockout restrictions are not properly configured. This increases the likelihood of unauthorized local account compromise.
Severity
Medium
Affected Asset
BIXAPP
Recommendation
It is recommended to configure a strong password and account lockout policy by following the below mentioned steps:
	1. To establish the recommended configuration via Group Policy, configure:
Computer Configuration\Policies\Windows Settings\Security Settings\Account Policies\Password Policy\Minimum password length
Set to:
14 or more characters, or the organization-approved stronger value.
	2. Configure:
Computer Configuration\Policies\Windows Settings\Security Settings\Account Policies\Password Policy\Minimum password age
Set to:
1 or more day(s)
	3. Configure:
Computer Configuration\Policies\Windows Settings\Security Settings\Account Policies\Account Lockout Policy\Account lockout threshold
Set to:
5 or fewer invalid logon attempts, but not 0.
	4. Configure an appropriate value for:
Computer Configuration\Policies\Windows Settings\Security Settings\Account Policies\Account Lockout Policy\Account lockout duration
	5. Configure an appropriate value for:
Computer Configuration\Policies\Windows Settings\Security Settings\Account Policies\Account Lockout Policy\Reset account lockout counter after
	6. Verify the effective configuration using:
net accounts
Microsoft's Windows Server configuration baseline defines password and account lockout controls for server systems. (Microsoft Learn)
Reference Controls
CIS Microsoft Windows Server 2022 Benchmark
Microsoft Password Policy and Account Lockout Guidance
CVE
NA

4. Insecure Built-in Administrator Account Configuration
Observation
The test team observed that the built-in Windows Administrator account is not configured in accordance with privileged account security best practices.
In the current scenario, the test team observed that the built-in account identified by SID ending in -500 was enabled and retained the default account name Administrator. The account was also configured with DONT_EXPIRE_PASSWORD, had a password age of 276 days, and had recently been used for interactive logon. The process evidence additionally showed multiple processes running within an active Administrator session.
Risk Impact
An attacker can specifically target the built-in Administrator account because the account's SID is predictable regardless of its display name. Keeping the account enabled, retaining its default name, configuring its password to never expire, and routinely using it interactively increase the likelihood and impact of privileged credential compromise.
Severity
Medium
Affected Asset
BIXAPP
Recommendation
    It is recommended to secure the built-in Administrator account and discontinue routine use of the account by following the below mentioned steps:
        1. Ensure that an approved alternative administrative account exists and has been successfully tested.
        2. To disable the built-in Administrator account through Group Policy, configure:
    Computer Configuration\Policies\Windows Settings\Security Settings\Local Policies\Security Options\Accounts: Administrator account status
    Set to:
    Disabled
        3. Where the account must remain enabled, rename the built-in Administrator account through:
    Computer Configuration\Policies\Windows Settings\Security Settings\Local Policies\Security Options\Accounts: Rename administrator account
    Set the account to an organization-approved non-default name.
    The Windows Server baseline recommends changing the default Administrator account name. (Microsoft Learn)
        4. Remove the Password Never Expires configuration.
        5. Where available, manage the local Administrator credential using Windows LAPS or an approved privileged-access management solution.
        6. Avoid routine web browsing, application execution, or daily administrative activities using the built-in Administrator account.
Reference Controls
CIS Microsoft Windows Server 2022 Benchmark
Microsoft Privileged Account Security Guidance
Microsoft Windows LAPS Guidance
CVE
NA

5. Web Server Running with Excessive Privileges
Observation
The test team observed that the web server process is running with excessive operating system privileges.
In the current scenario, the test team observed that Apache/XAMPP web server processes were running under the built-in Administrator account. Please find the identified processes below:
	1. Apache HTTP Server
Process:
d:\xamppnew\apache\bin\httpd.exe
Process Owner:
Administrator
	2. Apache HTTP Server
Process:
D:\xamppnew\apache\bin\httpd.exe -d D:/XamppNew/apache
Process Owner:
Administrator
The endpoint was also providing web services over TCP ports 80 and 443.
Risk Impact
An attacker can inherit the security privileges of the Administrator account if the Apache web server, hosted application, web framework, module, or other application component is successfully compromised. This may allow an attacker to execute privileged commands, modify system configuration, access sensitive data, establish persistence, or potentially compromise the server completely.
Severity
High
Affected Asset
BIXAPP
Recommendation
It is recommended to configure the Apache/XAMPP web server to operate under a dedicated least-privilege service account by following the below mentioned steps:
	1. Create a dedicated Windows service account specifically for Apache, for example:
svc_apache
	2. Do not add the service account to the local Administrators group.
	3. Grant only the minimum required filesystem permissions to:
	• Apache installation files.
	• Web application files.
	• Log directories.
	• Temporary directories.
	• Required upload or application data directories.
	4. Where Apache is installed as a Windows service, configure the Apache service Log On identity to use the dedicated service account.
	5. Where Apache is currently being started interactively through XAMPP, configure it as a controlled Windows service running under the dedicated account.
	6. Restart Apache after applying the configuration.
	7. Verify that httpd.exe no longer operates under the Administrator account.
Reference Controls
CIS Microsoft Windows Server 2022 Benchmark
Principle of Least Privilege
Microsoft Windows Service Account Security Guidance
CVE
NA

6. Missing Windows Security Updates
Observation
The test team observed that the Windows Server operating system was not updated with the latest cumulative security update available at the time of assessment.
In the current scenario, the test team observed that the installed Windows Server 2022 patch inventory contained KB5094128 as the latest cumulative security update. KB5094128 was installed on 17 June 2026. The assessment evidence was collected on 18 July 2026.
At the time of assessment, Microsoft had already released the 14 July 2026 cumulative update KB5099540, OS Build 20348.5386, for Windows Server 2022. KB5099540 includes the latest security fixes and incorporates fixes from the June KB5094128 release. (Microsoft Support)
Risk Impact
An attacker can exploit security vulnerabilities that have already been addressed by Microsoft but remain unpatched on the assessed server. Depending on the affected component, successful exploitation may result in remote code execution, privilege escalation, information disclosure, security feature bypass, or denial of service.
Severity
Medium
Affected Asset
BIXAPP
Recommendation
It is recommended to maintain the Windows Server operating system at the current approved cumulative security patch level by following the below mentioned steps:
	1. Review installed Windows security updates using:
Get-HotFix | Sort-Object InstalledOn -Descending
	2. Review the current OS build:
Get-ComputerInfo | Select WindowsProductName,WindowsVersion,OsBuildNumber
	3. Deploy the latest approved Windows Server 2022 cumulative security update through the organization's approved patch-management mechanism such as WSUS, Microsoft Configuration Manager, Azure Update Manager, or equivalent.
	4. At the time of assessment, KB5099540 or a later superseding cumulative update should have been installed.
	5. Reboot the server where required.
	6. Verify the installed cumulative update and operating system build following remediation.
	7. Establish a defined monthly security patching cycle to minimize the period during which known vulnerabilities remain unpatched.
Reference Controls
Microsoft Windows Server 2022 Update History
Microsoft Security Update Guide
KB5099540
CVE
Multiple CVEs addressed by the missing cumulative security update

7. Unsupported and Outdated Microsoft Visual C++ Runtime Components Installed
Observation
The test team observed that unsupported and outdated Microsoft Visual C++ runtime components are installed on the assessed server.
In the current scenario, the test team observed the following Microsoft Visual C++ runtime versions:
	1. Microsoft Visual C++ 2008 Redistributable - x86
Installed Version:
9.0.21022
	2. Microsoft Visual C++ 2015-2019 Redistributable / Visual C++ 2019 x86 runtime
Installed Version:
14.27.29016
	3. Microsoft Visual C++ 2015-2019 Redistributable x64
Installed Version:
14.28.29325
Microsoft identifies Visual C++ 2008 as out of support since April 2018. Microsoft also identifies the 14.27 and 14.28 runtime branches as older out-of-support runtime branches and recommends supported applications built with Visual Studio 2015 and later use the latest supported v14 Redistributable. (Microsoft Learn)
Risk Impact
An attacker can potentially exploit vulnerabilities affecting obsolete or unsupported runtime components where security fixes are no longer provided for the installed runtime branch. Unsupported components also increase long-term application dependency and patch-management risk.
Severity
Low
Affected Asset
BIXAPP
Recommendation
It is recommended to remove unsupported runtime components where they are no longer required and upgrade dependent applications to supported runtime versions by following the below mentioned steps:
	1. Identify applications dependent on Microsoft Visual C++ 2008 before removal.
	2. Identify applications currently dependent on Visual C++ 14.27 and 14.28 runtime components.
	3. Upgrade affected applications to versions compatible with a currently supported Microsoft Visual C++ runtime.
	4. Install the latest supported v14 Visual C++ Redistributable for applications built with Visual Studio 2015 or later.
	5. Remove obsolete runtime packages only after dependency and application compatibility testing is successfully completed.
	6. Verify all dependent applications following remediation.
Reference Controls
Microsoft Visual C++ Redistributable Lifecycle Guidance
Unsupported Software Management Best Practices
CVE
NA

8. Insecure ICMP Redirect Processing Configuration
Observation
The test team observed that ICMP redirect processing is not configured as per security best practices.
In the current scenario, the test team observed that ICMP redirects are enabled on the Windows TCP/IP stack. Please find the affected registry path and observed value below:
	1. ICMP redirects are allowed to influence host routing
HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\Tcpip\Parameters:EnableICMPRedirect
Observed Value: 1
Recommended Value: 0
The Windows Server 2022 baseline recommends that this configuration be disabled. (Microsoft Learn)
Risk Impact
An attacker can send malicious ICMP redirect messages from a reachable network position in an attempt to influence the server's routing decisions. Successful manipulation could redirect network traffic through an attacker-controlled path and increase the likelihood of traffic interception or man-in-the-middle attacks.
Severity
Low
Affected Asset
BIXAPP
Recommendation
It is recommended to disable ICMP redirect processing by following the below mentioned steps:
	1. To establish the recommended configuration via Group Policy, set the following UI path to Disabled:
Computer Configuration\Policies\Administrative Templates\MSS (Legacy)\MSS: (EnableICMPRedirect) Allow ICMP redirects to override OSPF generated routes
	2. Verify that the following registry value is configured as 0:
HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\Tcpip\Parameters:EnableICMPRedirect
Recommended Value:
0
	3. Apply the Group Policy configuration:
gpupdate /force
	4. Verify the registry value following policy application.
The Windows Server baseline maps this setting directly to EnableICMPRedirect=0. (Microsoft Learn)
Reference Controls
CIS Microsoft Windows Server 2022 Benchmark
MSS Legacy Network Security Settings
CVE
NA

9. Insufficient Anonymous Network Access Restrictions
Observation
The test team observed that anonymous network access is not restricted as per security best practices.
In the current scenario, the test team observed that anonymous enumeration of SAM accounts and network shares is not restricted. Please find the affected registry path and observed value below:
	1. Network access: Do not allow anonymous enumeration of SAM accounts and shares is not enabled
HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\Lsa:RestrictAnonymous
Observed Value: 0
Recommended Value: 1
The separate RestrictAnonymousSAM configuration was set to 1; however, the broader control covering both account and share enumeration remained disabled. Microsoft's Windows Server baseline recommends RestrictAnonymous=1 for applicable member/workgroup servers. (Microsoft Learn)
Risk Impact
An attacker can potentially use anonymous network connections to enumerate information about local accounts and network shares. This information can assist reconnaissance and facilitate targeted password attacks, SMB attacks, privilege escalation attempts, and lateral movement.
Severity
Medium
Affected Asset
BIXAPP
Recommendation
It is recommended to restrict anonymous enumeration of SAM accounts and network shares by following the below mentioned steps:
	1. To establish the recommended configuration via Group Policy, set the following UI path to Enabled:
Computer Configuration\Policies\Windows Settings\Security Settings\Local Policies\Security Options\Network access: Do not allow anonymous enumeration of SAM accounts and shares
	2. Verify that the following registry value is set to 1:
HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\Lsa:RestrictAnonymous
Recommended Value:
1
	3. Retain the existing secure configuration for:
Network access: Do not allow anonymous enumeration of SAM accounts
	4. Review other anonymous access controls and ensure anonymous permissions are not unnecessarily granted to named pipes or shares.
Microsoft identifies the recommended state for this policy as Enabled. (Microsoft Learn)
Reference Controls
CIS Microsoft Windows Server 2022 Benchmark
Microsoft Network Access Security Options
CVE
NA

10. Insecure Storage of Network Authentication Credentials
Observation
The test team observed that storage of passwords and credentials used for network authentication is not restricted as per security best practices.
In the current scenario, the test team observed that Windows Credential Manager is permitted to store network authentication credentials. Please find the affected registry path and observed value below:
	1. Network access: Do not allow storage of passwords and credentials for network authentication is set to Disabled
HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\Lsa:DisableDomainCreds
Observed Value: 0
Recommended Value: 1
A value of 0 allows Credential Manager to retain credentials for later domain/network authentication. Microsoft documents that enabling the corresponding security policy prevents Credential Manager from storing those credentials. (Microsoft Learn)
Risk Impact
An attacker can potentially obtain stored network authentication credentials after compromising the server or a privileged user context. Compromised credentials may subsequently be reused to access other systems, network shares, applications, or domain resources, increasing the risk of lateral movement.
Severity
Medium
Affected Asset
BIXAPP
Recommendation
It is recommended to prevent the storage of passwords and credentials used for network authentication by following the below mentioned steps:
	1. To establish the recommended configuration via Group Policy, set the following UI path to Enabled:
Computer Configuration\Policies\Windows Settings\Security Settings\Local Policies\Security Options\Network access: Do not allow storage of passwords and credentials for network authentication
	2. Verify the registry configuration:
HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\Lsa:DisableDomainCreds
Recommended Value:
1
	3. Review stored Windows credentials and remove unnecessary entries where operationally appropriate.
	4. Before enforcing the policy, identify scheduled tasks, backup jobs, applications, or services that legitimately depend on stored network credentials and migrate them to approved managed service identities or other secure authentication mechanisms.
Reference Controls
CIS Microsoft Windows Server 2022 Benchmark
Microsoft Network Authentication Credential Storage Guidance
CVE
NA

11. Weak NTLM Session Security Configuration
Observation
The test team observed that minimum NTLM session security requirements are not configured as per security best practices.
In the current scenario, the test team observed that both NTLM client and server configurations require 128-bit encryption but do not require NTLMv2 session security. Please find the affected registry paths and observed values below:
	1. Minimum session security for NTLM SSP based clients
HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\Lsa\MSV1_0:NTLMMinClientSec
Observed Value:
536870912
Recommended Value:
537395200
	2. Minimum session security for NTLM SSP based servers
HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\Lsa\MSV1_0:NTLMMinServerSec
Observed Value:
536870912
Recommended Value:
537395200
The current decimal value 536870912 represents Require 128-bit encryption only. The recommended value 537395200 combines Require NTLMv2 session security with Require 128-bit encryption. Microsoft's Windows Server baseline specifies this combined configuration for both client and server NTLM SSP security. (Microsoft Learn)
Risk Impact
An attacker can attempt to exploit weaker NTLM session negotiation when NTLMv2 session security is not explicitly required. Requiring both NTLMv2 session security and 128-bit encryption provides stronger protection against interception, tampering, and man-in-the-middle attacks involving applications that use the NTLM Security Support Provider.
Severity
Medium
Affected Asset
BIXAPP
Recommendation
It is recommended to enforce NTLMv2 session security and 128-bit encryption for both NTLM SSP client and server communications by following the below mentioned steps:
	1. To establish the recommended configuration via Group Policy, configure:
Computer Configuration\Policies\Windows Settings\Security Settings\Local Policies\Security Options\Network security: Minimum session security for NTLM SSP based (including secure RPC) clients
Set both options:
Require NTLMv2 session security
Require 128-bit encryption
	2. Configure:
Computer Configuration\Policies\Windows Settings\Security Settings\Local Policies\Security Options\Network security: Minimum session security for NTLM SSP based (including secure RPC) servers
Set both options:
Require NTLMv2 session security
Require 128-bit encryption
	3. Verify:
HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\Lsa\MSV1_0:NTLMMinClientSec
Recommended Value:
537395200
	4. Verify:
HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\Lsa\MSV1_0:NTLMMinServerSec
Recommended Value:
537395200
Microsoft's Windows Server baseline specifies these exact recommended values. (Microsoft Learn)
Reference Controls
CIS Microsoft Windows Server 2022 Benchmark
Microsoft NTLM SSP Session Security Guidance
CVE
NA

12. Inadequate Interactive Logon Security Configuration
Observation
The test team observed that interactive logon security settings are not configured as per security best practices.
In the current scenario, the test team observed that excessive domain logon credentials are cached locally and that the last signed-in username is displayed on the Windows logon screen. Please find the affected registry paths below:
	1. Excessive previous domain logons are cached
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\Winlogon:CachedLogonsCount
Observed Value:
10
Recommended Value:
4 or fewer logons
	2. Last signed-in username is displayed
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\System:DontDisplayLastUserName
Observed Value:
0
Recommended Value:
1
Microsoft's Windows Server baseline recommends caching no more than four previous logons and enabling the control that prevents display of the last signed-in username. (Microsoft Learn)
Risk Impact
An attacker can obtain useful account information from the Windows sign-in interface when the previous user's account name is displayed, making targeted password guessing easier. Additionally, excessive cached domain logon information increases the amount of credential-derived information stored locally and potentially available for offline credential attacks if the server is compromised.
Severity
Low
Affected Asset
BIXAPP
Recommendation
It is recommended to strengthen interactive logon security by following the below mentioned steps:
	1. To limit cached domain logons through Group Policy, configure:
Computer Configuration\Policies\Windows Settings\Security Settings\Local Policies\Security Options\Interactive logon: Number of previous logons to cache (in case domain controller is not available)
Set to:
4 or fewer logons
	2. To prevent disclosure of the previous user's account name, configure:
Computer Configuration\Policies\Windows Settings\Security Settings\Local Policies\Security Options\Interactive logon: Don't display last signed-in
Set to:
Enabled
	3. Verify the cached logon registry configuration:
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\Winlogon:CachedLogonsCount
Recommended Value:
4 or fewer
	4. Verify the last-user display configuration:
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\System:DontDisplayLastUserName
Recommended Value:
1
Microsoft identifies these exact settings and Group Policy locations for Windows Server 2022. (Microsoft Learn)
Reference Controls
CIS Microsoft Windows Server 2022 Benchmark
Microsoft Interactive Logon Security Guidance
CVE
NA

Final BIXAPP Finding Summary
#	Issue	Severity
1	Windows Defender Firewall Disabled for Domain and Private Profiles	Medium
2	SMB Signing Not Enforced	Medium
3	Weak Local Password and Account Lockout Policy	Medium
4	Insecure Built-in Administrator Account Configuration	Medium
5	Web Server Running with Excessive Privileges	High
6	Missing Windows Security Updates	Medium
7	Unsupported and Outdated Microsoft Visual C++ Runtime Components Installed	Low
8	Insecure ICMP Redirect Processing Configuration	Low
9	Insufficient Anonymous Network Access Restrictions	Medium
10	Insecure Storage of Network Authentication Credentials	Medium
11	Weak NTLM Session Security Configuration	Medium
12	Inadequate Interactive Logon Security Configuration	Low
High: 1
Medium: 8
Low: 3
Total: 12 findings

From <https://chatgpt.com/g/g-p-68da8a6c742881918ea4f1aa2e62f91c/c/6a7959e4-7b5c-83ec-b68f-d90c2e049039> 
