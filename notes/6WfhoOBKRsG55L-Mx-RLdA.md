Below is the consolidated report for the 12 confirmed ENES-AXIS findings, using the Windows reporting format you specified. ENES-AXIS is Microsoft Windows Server 2022 Datacenter, build 10.0.20348, and the assessment evidence was collected on 18 July 2026.

1. Windows Defender Firewall Disabled for All Network Profiles
Observation
The test team observed that Windows Defender Firewall is not configured as per security best practices across the network profiles.
In the current scenario, the test team observed that Windows Defender Firewall is disabled for the Domain, Private, and Public profiles. Please find the affected registry paths and observed values below:
	1. Windows Defender Firewall for Domain Profile is set to Disabled
HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\SharedAccess\Parameters\FirewallPolicy\DomainProfile:EnableFirewall
Observed Value: 0
	2. Windows Defender Firewall for Private/Standard Profile is set to Disabled
HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\SharedAccess\Parameters\FirewallPolicy\StandardProfile:EnableFirewall
Observed Value: 0
	3. Windows Defender Firewall for Public Profile is set to Disabled
HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\SharedAccess\Parameters\FirewallPolicy\PublicProfile:EnableFirewall
Observed Value: 0
The Firewall Status output additionally confirmed that all three profiles were configured with Enabled=False.
Risk Impact
An attacker can communicate with network-accessible services without host-based firewall restrictions when Windows Defender Firewall is disabled. This increases the attack surface and can facilitate network reconnaissance, exploitation of exposed services, unauthorized connections, and lateral movement.
Severity
Medium
Affected Asset
ENES-AXIS
Recommendation
It is recommended to enable Windows Defender Firewall across all applicable profiles by following the below mentioned steps:
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
	4. Configure the default inbound action as Block and permit only explicitly required business services.
	5. Verify:
Get-NetFirewallProfile | Select Name,Enabled,DefaultInboundAction,DefaultOutboundAction
Microsoft security baselines recommend enabling Windows Firewall on all network profiles. (Microsoft Learn)
Reference Controls
CIS Microsoft Windows Server 2022 Benchmark
Microsoft Windows Defender Firewall Security Guidance
CVE
NA

2. SMB Signing Not Enforced
Observation
The test team observed that SMB signing is not configured as per security best practices.
In the current scenario, the test team observed that SMB signing is not required for SMB server and SMB client communication. Please find the affected registry paths below:
	1. SMB server signing is not required
HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\LanmanServer\Parameters:RequireSecuritySignature
Observed Value: 0
	2. SMB client signing is not required
HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\LanmanWorkstation\Parameters:RequireSecuritySignature
Observed Value: 0
The service and network evidence additionally confirmed that the SMB Server and Workstation services are active and TCP port 445 is available.
Risk Impact
An attacker can perform man-in-the-middle or SMB relay attacks where SMB signing is not required by the communicating endpoints. Unsigned SMB traffic may be intercepted, modified, or relayed, potentially resulting in unauthorized authentication or access to network resources.
Severity
Medium
Affected Asset
ENES-AXIS
Recommendation
It is recommended to enforce SMB signing for client and server communications by following the below mentioned steps:
	1. To establish the recommended configuration via Group Policy, set the following UI path to Enabled:
Computer Configuration\Policies\Windows Settings\Security Settings\Local Policies\Security Options\Microsoft network server: Digitally sign communications (always)
	2. Set the following UI path to Enabled:
Computer Configuration\Policies\Windows Settings\Security Settings\Local Policies\Security Options\Microsoft network client: Digitally sign communications (always)
	3. Verify:
Get-SmbServerConfiguration | Select RequireSecuritySignature
Get-SmbClientConfiguration | Select RequireSecuritySignature
	4. Validate compatibility with any legacy SMB-dependent devices before enforcement.
Reference Controls
CIS Microsoft Windows Server 2022 Benchmark
Microsoft SMB Signing Guidance
CVE
NA

3. Insufficient Anonymous Network Access Restrictions
Observation
The test team observed that anonymous network access restrictions are not configured as per security best practices.
In the current scenario, the test team observed that anonymous enumeration of SAM accounts and shares is not restricted. Please find the affected registry configuration below:
	1. Network access: Do not allow anonymous enumeration of SAM accounts and shares is Disabled
HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\Lsa:RestrictAnonymous
Observed Value: 0
Recommended Value: 1
The related RestrictAnonymousSAM value was set to 1; however, the broader restriction covering both account and share enumeration was not enabled.
Risk Impact
An attacker can potentially use anonymous network connections to collect information about local accounts and shared resources. The information obtained may assist targeted password attacks, SMB attacks, reconnaissance, and lateral movement.
Severity
Medium
Affected Asset
ENES-AXIS
Recommendation
It is recommended to prevent anonymous enumeration of SAM accounts and network shares by following the below mentioned steps:
	1. To establish the recommended configuration via Group Policy, set the following UI path to Enabled:
Computer Configuration\Policies\Windows Settings\Security Settings\Local Policies\Security Options\Network access: Do not allow anonymous enumeration of SAM accounts and shares
	2. Verify:
HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\Lsa:RestrictAnonymous
Recommended Value: 1
	3. Retain the existing restriction on anonymous SAM enumeration.
Microsoft's Windows Server baseline specifies RestrictAnonymous=1 for this control. (Microsoft Learn)
Reference Controls
CIS Microsoft Windows Server 2022 Benchmark
Microsoft Network Access Security Options
CVE
NA

4. Insecure Storage of Network Authentication Credentials
Observation
The test team observed that storage of passwords and credentials used for network authentication is not restricted as per security best practices.
In the current scenario, the test team observed that Windows is permitted to store network authentication credentials. Please find the affected registry configuration below:
	1. Network access: Do not allow storage of passwords and credentials for network authentication is Disabled
HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\Lsa:DisableDomainCreds
Observed Value: 0
Recommended Value: 1
Risk Impact
An attacker can potentially obtain stored network credentials after compromising the server or an authorized user context. Compromised credentials may subsequently be reused to access other hosts, network shares, applications, or domain resources, increasing the likelihood of lateral movement.
Severity
Medium
Affected Asset
ENES-AXIS
Recommendation
It is recommended to prevent storage of passwords and credentials used for network authentication by following the below mentioned steps:
	1. To establish the recommended configuration via Group Policy, set the following UI path to Enabled:
Computer Configuration\Policies\Windows Settings\Security Settings\Local Policies\Security Options\Network access: Do not allow storage of passwords and credentials for network authentication
	2. Verify:
HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\Lsa:DisableDomainCreds
Recommended Value: 1
	3. Review Windows Credential Manager for unnecessary stored credentials.
	4. Identify applications, scheduled tasks, or services that depend on stored user credentials before enforcing the setting and migrate them to an approved service-account mechanism.
Reference Controls
CIS Microsoft Windows Server 2022 Benchmark
Microsoft Network Authentication Credential Security Guidance
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
The recommended value requires both NTLMv2 session security and 128-bit encryption. Microsoft's Windows security baseline maps this configuration to value 537395200. (Microsoft Learn)
Risk Impact
An attacker can attempt to exploit weaker NTLM session negotiation where NTLMv2 session security is not explicitly required. This increases exposure to interception, tampering, credential relay, and man-in-the-middle attacks involving applications that use NTLM authentication.
Severity
Medium
Affected Asset
ENES-AXIS
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
	3. Verify that both registry values are:
537395200
Reference Controls
CIS Microsoft Windows Server 2022 Benchmark
Microsoft NTLM SSP Security Guidance
CVE
NA

6. Inadequate Interactive Logon Security Configuration
Observation
The test team observed that interactive logon security settings are not configured as per security best practices.
In the current scenario, the test team observed that excessive previous domain logons are cached locally and that the last signed-in username is displayed. Please find the affected registry paths below:
	1. Excessive previous domain logons are cached
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\Winlogon:CachedLogonsCount
Observed Value: 10
Recommended Value: 4 or fewer
	2. Last signed-in username is displayed
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\System:DontDisplayLastUserName
Observed Value: 0
Recommended Value: 1
Microsoft's Windows Server 2022 baseline recommends four or fewer cached logons. (Microsoft Learn)
Risk Impact
An attacker can obtain valid account information from the Windows sign-in interface when the previous username is displayed. Excessive cached domain logon data also increases locally stored credential-derived information that may be targeted during offline credential attacks following system compromise.
Severity
Low
Affected Asset
ENES-AXIS
Recommendation
It is recommended to strengthen interactive logon controls by following the below mentioned steps:
	1. Configure:
Computer Configuration\Policies\Windows Settings\Security Settings\Local Policies\Security Options\Interactive logon: Number of previous logons to cache (in case domain controller is not available)
Set to:
4 or fewer logons
	2. Configure:
Computer Configuration\Policies\Windows Settings\Security Settings\Local Policies\Security Options\Interactive logon: Don't display last signed-in
Set to:
Enabled
	3. Apply Group Policy and verify the effective values.
Reference Controls
CIS Microsoft Windows Server 2022 Benchmark
Microsoft Interactive Logon Security Guidance
CVE
NA

7. Weak User Account Control Elevation Configuration
Observation
The test team observed that User Account Control elevation behaviour is not configured as per security best practices.
In the current scenario, the test team observed that administrator and standard-user elevation prompts are configured with weaker values than the Windows Server security baseline. Please find the affected registry paths below:
	1. Administrator elevation prompt behaviour
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\System:ConsentPromptBehaviorAdmin
Observed Value: 5
Current Behaviour:
Prompt for consent for non-Windows binaries
Recommended Value: 2
Recommended Behaviour:
Prompt for consent on the secure desktop
	2. Standard-user elevation prompt behaviour
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\System:ConsentPromptBehaviorUser
Observed Value: 3
Recommended Value: 0
Recommended Behaviour:
Automatically deny elevation requests
Microsoft's Windows Server 2022 baseline specifies these recommended elevation behaviours. (Microsoft Learn)
Risk Impact
An attacker can have greater opportunity to abuse privilege-elevation workflows where administrator prompts are less restrictive or where standard users are allowed to provide administrative credentials for elevation. This can increase the impact of malicious or compromised applications attempting to obtain elevated privileges.
Severity
Medium
Affected Asset
ENES-AXIS
Recommendation
It is recommended to configure User Account Control elevation behaviour as per the Windows Server security baseline by following the below mentioned steps:
	1. Configure:
Computer Configuration\Policies\Windows Settings\Security Settings\Local Policies\Security Options\User Account Control: Behavior of the elevation prompt for administrators in Admin Approval Mode
Set to:
Prompt for consent on the secure desktop
	2. Configure:
Computer Configuration\Policies\Windows Settings\Security Settings\Local Policies\Security Options\User Account Control: Behavior of the elevation prompt for standard users
Set to:
Automatically deny elevation requests
	3. Retain UAC and secure-desktop protections as enabled.
Reference Controls
CIS Microsoft Windows Server 2022 Benchmark
Microsoft User Account Control Security Guidance
CVE
NA

8. Weak Local Password and Account Lockout Policy
Observation
The test team observed that local password and account lockout controls are not configured as per security best practices.
In the current scenario, the test team observed the following local account policy values:
	1. Minimum password length is not enforced
Observed Value:
MinPasswordLength = 0
	2. Minimum password age is not enforced
Observed Value:
MinPasswordAge = 0
	3. Account lockout threshold is not configured
Observed Value:
MaxBadPasswords = 0
The configured maximum password age was 42 days; therefore, that specific control was not included as a failed global password policy setting.
Risk Impact
An attacker can perform password guessing and brute-force authentication attacks more effectively where minimum password length and account lockout controls are not enforced. Weak passwords and unlimited failed authentication attempts increase the likelihood of unauthorized local account compromise.
Severity
Medium
Affected Asset
ENES-AXIS
Recommendation
It is recommended to enforce a strong password and account lockout policy by following the below mentioned steps:
	1. Configure:
Computer Configuration\Policies\Windows Settings\Security Settings\Account Policies\Password Policy\Minimum password length
Set to:
14 characters or greater, or the approved organizational standard.
	2. Configure:
Computer Configuration\Policies\Windows Settings\Security Settings\Account Policies\Password Policy\Minimum password age
Set to:
1 or more day(s)
	3. Configure:
Computer Configuration\Policies\Windows Settings\Security Settings\Account Policies\Account Lockout Policy\Account lockout threshold
Set to:
5 or fewer invalid attempts, but not 0.
	4. Configure appropriate values for:
Account lockout duration
Reset account lockout counter after
	5. Verify:
net accounts
Reference Controls
CIS Microsoft Windows Server 2022 Benchmark
Microsoft Password and Account Lockout Policy Guidance
CVE
NA

9. Insecure Local Account and Password Expiration Configuration
Observation
The test team observed that enabled local accounts are configured with non-expiring passwords and excessive password ages.
In the current scenario, the test team observed the following enabled local accounts with DONT_EXPIRE_PASSWORD configured:
	1. Built-in Administrator account
Account:
Administrator
SID:
S-1-5-21-2790943580-2768686064-1596510142-500
Password Configuration:
DONT_EXPIRE_PASSWORD
Password Age:
274 days
Last Login:
17-06-2026 09:22:57
	2. Local application/user account
Account:
snorkel
Password Configuration:
DONT_EXPIRE_PASSWORD
Password Age:
442 days
Last Login:
02-05-2025 20:05:32
The configured global maximum password age was 42 days, but both accounts were exempt from password expiration.
Risk Impact
An attacker can obtain long-lived access if credentials belonging to a non-expiring local account are compromised. Privileged accounts such as the built-in Administrator account present particularly significant risk because compromised credentials may provide extensive control over the server.
Severity
Medium
Affected Asset
ENES-AXIS
Recommendation
It is recommended to remove unnecessary non-expiring password configurations and securely manage privileged local accounts by following the below mentioned steps:
	1. Review whether both identified accounts require interactive or permanent access.
	2. Remove the non-expiring password configuration:
Set-LocalUser -Name "Administrator" -PasswordNeverExpires $false
Set-LocalUser -Name "snorkel" -PasswordNeverExpires $false
	3. Immediately rotate passwords that have exceeded the approved password age.
	4. Where the built-in Administrator account is not required for routine administration, configure:
Computer Configuration\Policies\Windows Settings\Security Settings\Local Policies\Security Options\Accounts: Administrator account status
Set to:
Disabled
	5. Where the Administrator account must remain available, manage its password using Windows LAPS or an approved privileged-access management solution.
	6. Disable the snorkel account if it is no longer operationally required.
Reference Controls
CIS Microsoft Windows Server 2022 Benchmark
Microsoft Privileged Account Security Guidance
Microsoft Windows LAPS Guidance
CVE
NA

10. Legacy and Insecure Network Services Enabled
Observation
The test team observed that legacy network services that are not recommended for modern Windows Server environments are enabled and actively exposed.
In the current scenario, the test team observed that Simple TCP/IP Services and Windows Internet Name Service (WINS) are configured for automatic startup and were actively running.
The following Simple TCP/IP Services were confirmed as exposed:
	1. Echo — TCP port 7
	2. Discard — TCP port 9
	3. Daytime — TCP port 13
	4. Quote of the Day — TCP port 17
	5. Character Generator (Chargen) — TCP port 19
The active service was identified as:
Service Name:
simptcp
Display Name:
Simple TCP/IP Services
State:
Running
Start Mode:
Automatic
The WINS service was also identified as:
Service:
WINS
State:
Running
Start Mode:
Automatic
Associated port:
TCP 42
Microsoft confirms that Simple TCP/IP Services implements Echo, Discard, Daytime, Quote of the Day, and Chargen on ports 7, 9, 13, 17, and 19 respectively. (Microsoft Learn) Microsoft also states that WINS is deprecated and should no longer be used as a name-resolution system. (Microsoft Learn)
Risk Impact
An attacker can interact with unnecessary legacy network services to increase the attack surface of the server. Services such as Echo and Chargen can also be abused in network reflection or amplification scenarios, while legacy WINS infrastructure may expose additional outdated name-resolution functionality that is no longer required in modern DNS-based environments.
Severity
Medium
Affected Asset
ENES-AXIS
Recommendation
It is recommended to remove legacy network services that are not required for business operations by following the below mentioned steps:
	1. Verify installed features:
Get-WindowsFeature Simple-TCPIP,WINS
	2. Remove Simple TCP/IP Services:
Uninstall-WindowsFeature Simple-TCPIP
	3. Remove WINS where no legacy application dependency exists:
Uninstall-WindowsFeature WINS
Microsoft identifies the feature names as Simple-TCPIP and WINS. (Microsoft Learn)
	4. Migrate any remaining WINS-dependent systems to DNS-based name resolution.
	5. Verify that TCP ports 7, 9, 13, 17, 19, and 42 are no longer listening after remediation.
	6. Where temporary retention is unavoidable, restrict access through Windows Defender Firewall to only explicitly approved management systems.
Reference Controls
Microsoft Windows Server Service Hardening Guidance
Microsoft Deprecated Windows Server Features Guidance
CIS Microsoft Windows Server 2022 Benchmark
CVE
NA

11. Missing Windows Security Updates
Observation
The test team observed that the Windows Server operating system is not updated with the latest cumulative security update available at the time of assessment.
In the current scenario, the test team observed the following installed updates:
KB5082427
KB5094128
KB5094147
KB5094128 corresponds to the June 2026 Windows Server 2022 cumulative security update, resulting in OS build 20348.5256.
The assessment was performed on 18 July 2026. At that time Microsoft had already released the 14 July 2026 KB5099540 cumulative security update, OS Build 20348.5386, which contains the latest security fixes and supersedes fixes from KB5094128. (Microsoft Support)
Risk Impact
An attacker can exploit security vulnerabilities already addressed by Microsoft but remaining unpatched on the assessed server. Depending on the affected Windows component, successful exploitation may result in remote code execution, privilege escalation, information disclosure, security-feature bypass, or denial of service.
Severity
Medium
Affected Asset
ENES-AXIS
Recommendation
It is recommended to maintain Windows Server at the latest approved cumulative security patch level by following the below mentioned steps:
	1. Review installed security updates:
Get-HotFix | Sort-Object InstalledOn -Descending
	2. Review the current OS build:
Get-ComputerInfo | Select WindowsProductName,WindowsVersion,OsBuildNumber
	3. Deploy the latest approved Windows Server 2022 cumulative security update through WSUS, Microsoft Configuration Manager, Azure Update Manager, or the organization's approved patch-management solution.
	4. At the assessment date, KB5099540 or a later superseding update should have been installed.
	5. Reboot the server where required.
	6. Verify the resulting OS build and installed KB.
	7. Establish a defined monthly security-patching process to reduce exposure to known vulnerabilities.
Reference Controls
Microsoft Windows Server 2022 Update History
Microsoft Security Update Guide
KB5099540
CVE
Multiple CVEs addressed by the missing cumulative security update

12. Unsupported and Outdated Runtime Components Installed
Observation
The test team observed that unsupported and outdated application runtime components are installed on the assessed server.
In the current scenario, the test team observed multiple Microsoft .NET 6.0.16 and ASP.NET Core 6.0.16 runtime/hosting components, including:
	• Microsoft .NET Runtime 6.0.16
	• Microsoft .NET 6.0.16 Windows Server Hosting
	• Microsoft ASP.NET Core 6.0.16 Shared Framework
	• Microsoft ASP.NET Core 6.0.16 Hosting Bundle components
	• Microsoft .NET Host/Host FX Resolver 6.0.16
The test team also observed Microsoft Visual C++ 2015-2019 runtime components from the 14.27.29016 branch.
Microsoft ended support for .NET 6 on 12 November 2024, and ASP.NET Core follows the same lifecycle. (Microsoft Learn) Microsoft lists the Visual C++ 14.27 runtime branch as having reached end of support on 12 April 2022. (Microsoft Learn)
Risk Impact
An attacker can potentially exploit known or subsequently discovered vulnerabilities affecting unsupported software components for which the installed release no longer receives normal security servicing. Unsupported runtime dependencies also increase application security, compatibility, and patch-management risk.
Severity
Low
Affected Asset
ENES-AXIS
Recommendation
It is recommended to upgrade applications to supported runtime versions and remove obsolete runtime components after dependency validation by following the below mentioned steps:
	1. Identify applications currently dependent on .NET/ASP.NET Core 6.0.16.
	2. Upgrade those applications to a currently supported .NET release compatible with the application.
	3. Validate applications against the currently supported .NET 8 LTS or another vendor-supported release before migration.
	4. Identify applications dependent on Visual C++ 14.27.
	5. Upgrade dependent applications to use a currently supported Visual C++ v14 Redistributable.
Microsoft recommends using the latest supported v14 Redistributable for applications built with Visual Studio 2015 and later. (Microsoft Learn)
	6. Remove unsupported .NET 6 and obsolete runtime components only after application compatibility testing.
	7. Reboot where required and verify all dependent applications.
Reference Controls
Microsoft .NET Lifecycle Policy
Microsoft Visual C++ Runtime Lifecycle Guidance
Unsupported Software Management Best Practices
CVE
NA

ENES-AXIS Final Finding Summary
#	Issue	Severity
1	Windows Defender Firewall Disabled for All Network Profiles	Medium
2	SMB Signing Not Enforced	Medium
3	Insufficient Anonymous Network Access Restrictions	Medium
4	Insecure Storage of Network Authentication Credentials	Medium
5	Weak NTLM Session Security Configuration	Medium
6	Inadequate Interactive Logon Security Configuration	Low
7	Weak User Account Control Elevation Configuration	Medium
8	Weak Local Password and Account Lockout Policy	Medium
9	Insecure Local Account and Password Expiration Configuration	Medium
10	Legacy and Insecure Network Services Enabled	Medium
11	Missing Windows Security Updates	Medium
12	Unsupported and Outdated Runtime Components Installed	Low
High: 0
Medium: 10
Low: 2
Total: 12 genuine findings

From <https://chatgpt.com/g/g-p-68da8a6c742881918ea4f1aa2e62f91c/c/6a7959e4-7b5c-83ec-b68f-d90c2e049039> 
