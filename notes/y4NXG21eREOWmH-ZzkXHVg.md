Below is the consolidated report for NSHO01CO1 in the Windows observation format you specified.
The endpoint is Microsoft Windows 11 Enterprise, build 10.0.26200, and the evidence was collected on 20 July 2026 at 15:55 IST.

1. SMB Server Signing Not Enforced
Observation
The test team observed that SMB server signing is not configured as per security best practices.
In the current scenario, the test team observed that SMB signing is not required for inbound SMB server communications. Please find the affected registry path and observed value below:
	1. Microsoft network server: Digitally sign communications (always) is set to Disabled
HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\LanmanServer\Parameters:RequireSecuritySignature
Observed Value: 0
Recommended Value: 1
The SMB client-side configuration was observed with RequireSecuritySignature=1 and is therefore correctly configured. The network assessment additionally confirmed that TCP port 445 is active on the endpoint.
Risk Impact
An attacker can perform man-in-the-middle or SMB relay attacks when SMB signing is not required by the SMB server. Unsigned SMB communications may be intercepted, modified, or relayed, potentially resulting in unauthorized authentication or access to network resources.
Severity
Medium
Affected Asset
NSHO01CO1
Recommendation
It is recommended to enforce SMB signing for SMB server communications by following the below mentioned steps:
	1. To establish the recommended configuration via Group Policy, set the following UI path to Enabled:
Computer Configuration\Policies\Windows Settings\Security Settings\Local Policies\Security Options\Microsoft network server: Digitally sign communications (always)
	2. Verify the effective SMB server configuration using:
Get-SmbServerConfiguration | Select RequireSecuritySignature
	3. Ensure the output displays:
RequireSecuritySignature : True
	4. Validate compatibility with any legacy SMB-dependent systems before organization-wide enforcement.
Reference Controls
CIS Microsoft Windows 11 Enterprise Benchmark v4.0.0
Microsoft SMB Signing Security Guidance
CVE
NA

2. Insufficient Anonymous Network Access Restrictions
Observation
The test team observed that anonymous network access restrictions are not configured as per security best practices.
In the current scenario, the test team observed that anonymous enumeration of SAM accounts and network shares is not adequately restricted. Please find the affected registry path and observed value below:
	1. Network access: Do not allow anonymous enumeration of SAM accounts and shares is set to Disabled
HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\Lsa:RestrictAnonymous
Observed Value: 0
Recommended Value: 1
The related RestrictAnonymousSAM value was configured as 1; however, the broader restriction covering both SAM accounts and network share enumeration was not enabled.
The endpoint also had active SMB/NetBIOS networking services, increasing the relevance of the configuration.
Risk Impact
An attacker can potentially use anonymous network connections to gather information about local accounts and shared network resources. The disclosed information may assist reconnaissance, password guessing, targeted SMB attacks, and lateral movement.
Severity
Medium
Affected Asset
NSHO01CO1
Recommendation
It is recommended to restrict anonymous enumeration of SAM accounts and network shares by following the below mentioned steps:
	1. To establish the recommended configuration via Group Policy, set the following UI path to Enabled:
Computer Configuration\Policies\Windows Settings\Security Settings\Local Policies\Security Options\Network access: Do not allow anonymous enumeration of SAM accounts and shares
	2. Verify the following registry path:
HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\Lsa:RestrictAnonymous
Recommended Value: 1
	3. Retain the existing secure configuration for:
Network access: Do not allow anonymous enumeration of SAM accounts
	4. Review anonymous access to named pipes and shares and restrict them to business-required resources only.
Reference Controls
CIS Microsoft Windows 11 Enterprise Benchmark v4.0.0
CVE
NA

3. Insecure Storage of Network Authentication Credentials
Observation
The test team observed that storage of passwords and credentials used for network authentication is not restricted as per security best practices.
In the current scenario, the test team observed that Windows Credential Manager is permitted to store credentials for network authentication. Please find the affected registry path and observed value below:
	1. Network access: Do not allow storage of passwords and credentials for network authentication is set to Disabled
HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\Lsa:DisableDomainCreds
Observed Value: 0
Recommended Value: 1
Risk Impact
An attacker can potentially obtain stored network credentials after compromising the endpoint or an authenticated user context. Compromised credentials may subsequently be reused to access other endpoints, network shares, applications, or domain resources, facilitating lateral movement.
Severity
Medium
Affected Asset
NSHO01CO1
Recommendation
It is recommended to prevent storage of passwords and credentials used for network authentication by following the below mentioned steps:
	1. To establish the recommended configuration via Group Policy, set the following UI path to Enabled:
Computer Configuration\Policies\Windows Settings\Security Settings\Local Policies\Security Options\Network access: Do not allow storage of passwords and credentials for network authentication
	2. Verify the registry configuration:
HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\Lsa:DisableDomainCreds
Recommended Value: 1
	3. Review Windows Credential Manager and remove unnecessary stored credentials.
	4. Verify scheduled tasks, applications, or services that may depend on stored credentials before enforcing the configuration.
Reference Controls
CIS Microsoft Windows 11 Enterprise Benchmark v4.0.0
Microsoft Network Authentication Security Guidance
CVE
NA

4. Weak NTLM Session Security Configuration
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
The observed value requires 128-bit encryption only, whereas the recommended configuration requires both NTLMv2 session security and 128-bit encryption.
The LAN Manager authentication level was separately observed with a secure configuration and is therefore not included in this finding.
Risk Impact
An attacker can attempt to exploit weaker NTLM session negotiation when NTLMv2 session security is not explicitly required. This can increase exposure to credential relay, interception, tampering, and man-in-the-middle attacks involving applications that rely on NTLM authentication.
Severity
Medium
Affected Asset
NSHO01CO1
Recommendation
It is recommended to enforce NTLMv2 session security and 128-bit encryption by following the below mentioned steps:
	1. To establish the recommended configuration via Group Policy, configure:
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
CIS Microsoft Windows 11 Enterprise Benchmark v4.0.0
Microsoft NTLM SSP Security Guidance
CVE
NA

5. Inadequate Interactive Logon Security Configuration
Observation
The test team observed that interactive logon security settings are not configured as per security best practices.
In the current scenario, the test team observed multiple interactive logon security weaknesses. Please find the affected registry paths and observed values below:
	1. Excessive previous domain logons are cached
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\Winlogon:CachedLogonsCount
Observed Value: 10
Recommended Value: 4 or fewer
	2. Last signed-in username is displayed
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\System:DontDisplayLastUserName
Observed Value: 0
Recommended Value: 1
	3. Ctrl+Alt+Del Secure Attention Sequence is not required
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\Winlogon:DisableCAD
Observed Value: 1
Recommended Value: 0
	4. System shutdown is permitted without authentication
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\System:ShutdownWithoutLogon
Observed Value: 1
Recommended Value: 0
Risk Impact
An attacker can obtain useful account information when the last signed-in username is displayed and can potentially target cached domain credential information following endpoint compromise. Disabling the Ctrl+Alt+Del secure attention sequence may reduce protection against fraudulent logon interfaces, while allowing shutdown without authentication can facilitate local denial-of-service activity.
Severity
Low
Affected Asset
NSHO01CO1
Recommendation
It is recommended to strengthen interactive logon security by following the below mentioned steps:
	1. Configure:
Computer Configuration\Policies\Windows Settings\Security Settings\Local Policies\Security Options\Interactive logon: Number of previous logons to cache (in case domain controller is not available)
Set to:
4 or fewer
	2. Configure:
Computer Configuration\Policies\Windows Settings\Security Settings\Local Policies\Security Options\Interactive logon: Don't display last signed-in
Set to:
Enabled
	3. Configure:
Computer Configuration\Policies\Windows Settings\Security Settings\Local Policies\Security Options\Interactive logon: Do not require CTRL+ALT+DEL
Set to:
Disabled
	4. Configure:
Computer Configuration\Policies\Windows Settings\Security Settings\Local Policies\Security Options\Shutdown: Allow system to be shut down without having to log on
Set to:
Disabled
Reference Controls
CIS Microsoft Windows 11 Enterprise Benchmark v4.0.0
CVE
NA

6. Weak User Account Control Elevation Configuration
Observation
The test team observed that User Account Control elevation behaviour is not configured as per security best practices.
In the current scenario, the test team observed that administrator and standard-user elevation prompts are configured with weaker values than the recommended hardened configuration. Please find the affected registry paths below:
	1. User Account Control: Behavior of the elevation prompt for administrators in Admin Approval Mode
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\System:ConsentPromptBehaviorAdmin
Observed Value: 5
Observed Configuration:
Prompt for consent for non-Windows binaries
Recommended Value: 2
Recommended Configuration:
Prompt for consent on the secure desktop
	2. User Account Control: Behavior of the elevation prompt for standard users
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\System:ConsentPromptBehaviorUser
Observed Value: 3
Observed Configuration:
Prompt for credentials
Recommended Value: 0
Recommended Configuration:
Automatically deny elevation requests
The assessment additionally observed EnableLUA=1 and PromptOnSecureDesktop=1; therefore, UAC itself is enabled and this issue is specific to elevation-prompt behaviour.
Risk Impact
An attacker can have greater opportunity to abuse privilege-elevation workflows when elevation controls are less restrictive. Allowing standard users to provide administrator credentials for elevation can also increase the risk of privileged credential exposure to malicious software or compromised user sessions.
Severity
Medium
Affected Asset
NSHO01CO1
Recommendation


Reference Controls
CIS Microsoft Windows 11 Enterprise Benchmark v4.0.0
Microsoft User Account Control Security Guidance
CVE
NA

7. Insecure ICMP Redirect Processing Configuration
Observation
The test team observed that ICMP redirect processing is not configured as per security best practices.
In the current scenario, the test team observed that ICMP redirect processing is enabled on the Windows TCP/IP stack. Please find the affected registry path below:
	1. ICMP redirect processing is set to Enabled
HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\Tcpip\Parameters:EnableICMPRedirect
Observed Value: 1
Recommended Value: 0
The registry additionally contained DeadGWDetectDefault=1; however, the primary basis of this finding is the enabled ICMP redirect processing configuration.
Risk Impact
An attacker can attempt to send malicious ICMP redirect messages from a reachable network position to influence the endpoint's routing decisions. Successful manipulation may redirect traffic through an unintended or attacker-controlled path, increasing the possibility of interception or man-in-the-middle attacks.
Severity
Low
Affected Asset
NSHO01CO1
Recommendation
It is recommended to disable ICMP redirect processing by following the below mentioned steps:
	1. To establish the recommended configuration via Group Policy, set the following UI path to Disabled:
Computer Configuration\Policies\Administrative Templates\MSS (Legacy)\MSS: (EnableICMPRedirect) Allow ICMP redirects to override OSPF generated routes
	2. Verify the registry configuration:
HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\Tcpip\Parameters:EnableICMPRedirect
Recommended Value: 0
	3. Apply the policy:
gpupdate /force
	4. Verify that the registry value remains 0 after policy application and system restart where required.
Reference Controls
CIS Microsoft Windows 11 Enterprise Benchmark v4.0.0
MSS Legacy Network Security Settings
CVE
NA

8. Insecure Built-in Administrator Account Configuration
Observation
The test team observed that the built-in Windows Administrator account is not configured as per privileged account security best practices.
In the current scenario, the test team observed that the built-in Administrator account identified by its SID ending in -500 is enabled, retains the default Administrator account name, and is configured with the DONT_EXPIRE_PASSWORD flag.
Please find the account details below:
Account Name:
Administrator
Account Status:
Enabled
Password Configuration:
DONT_EXPIRE_PASSWORD
Password Age:
9 days
Last Login:
18-03-2024 10:59:39
The effective global password policy had a maximum password age of 30 days; however, the built-in Administrator account is exempt from password expiration.
Risk Impact
An attacker can specifically target the built-in Administrator account because its SID is predictable regardless of the configured account name. Keeping the account enabled with the default name and a non-expiring password increases the likelihood and potential duration of privileged credential compromise.
Severity
Medium
Affected Asset
NSHO01CO1
Recommendation
It is recommended to securely configure the built-in Administrator account by following the below mentioned steps:
	1. Ensure an approved alternate administrative account is available and has been successfully tested.
	2. To establish the recommended configuration via Group Policy, configure:
Computer Configuration\Policies\Windows Settings\Security Settings\Local Policies\Security Options\Accounts: Administrator account status
Set to:
Disabled
where operationally feasible.
	3. If the built-in account must remain enabled, configure:
Computer Configuration\Policies\Windows Settings\Security Settings\Local Policies\Security Options\Accounts: Rename administrator account
Set to:
An organization-approved non-default account name.
	4. Remove the Password Never Expires configuration from the account.
	5. Manage the local Administrator credential using Windows LAPS or an approved privileged-access-management mechanism.
	6. Restrict use of the built-in Administrator account to emergency or specifically approved administrative activities.
Reference Controls
CIS Microsoft Windows 11 Enterprise Benchmark v4.0.0
Microsoft Windows LAPS Guidance
Microsoft Privileged Account Security Guidance
CVE
NA

9. Unsupported and Outdated Software Components Installed
Observation
The test team observed that unsupported and outdated software components are installed on the assessed endpoint.
In the current scenario, the test team observed multiple legacy software components that have exceeded their supported lifecycle. The identified software includes:
	1. Adobe Reader
Product:
Adobe Reader 9
Installed Version:
9.0.0
Adobe Reader 9 is a legacy unsupported release and no longer receives normal security updates.
	2. Microsoft Visual C++ 2005 Redistributable
Observed Versions:
8.0.56336
8.0.50727.42
The Visual C++ 2005/v80 runtime has exceeded its supported Microsoft lifecycle.
	3. Microsoft Visual C++ 2010 Redistributable
Installed Version:
10.0.40219
The Visual C++ 2010/v100 runtime has exceeded its supported Microsoft lifecycle.
	4. Legacy Adobe AIR components were also identified in the installed application inventory, including version 1.0.x packages.
Risk Impact
An attacker can exploit known or subsequently discovered vulnerabilities affecting unsupported software for which the installed release no longer receives normal security fixes. Applications such as outdated PDF readers additionally process externally supplied content, increasing the potential impact of vulnerabilities in obsolete software components.
Severity
Medium
Affected Asset
NSHO01CO1
Recommendation
It is recommended to remove unsupported software where no longer required and migrate dependent applications to supported software versions by following the below mentioned steps:
	1. Uninstall Adobe Reader 9 and replace it with a currently supported and organization-approved PDF reader.
	2. Identify applications dependent on Microsoft Visual C++ 2005 and Visual C++ 2010 runtimes.
	3. Upgrade dependent applications to versions compatible with currently supported Microsoft runtime components.
	4. Remove obsolete Visual C++ runtime packages only after application dependency and compatibility testing has been successfully completed.
	5. Identify applications relying on legacy Adobe AIR components and migrate or upgrade those applications to supported technologies.
	6. Remove unsupported Adobe AIR components after dependency validation.
	7. Establish periodic software inventory and lifecycle reviews to identify unsupported software before vendor support expires.
Reference Controls
CIS Microsoft Windows 11 Enterprise Benchmark v4.0.0
Adobe Product Lifecycle Guidance
Microsoft Visual C++ Product Lifecycle Guidance
Unsupported Software Management Best Practices
CVE
NA

NSHO01CO1 Finding Summary
#	Issue	Severity
1	SMB Server Signing Not Enforced	Medium
2	Insufficient Anonymous Network Access Restrictions	Medium
3	Insecure Storage of Network Authentication Credentials	Medium
4	Weak NTLM Session Security Configuration	Medium
5	Inadequate Interactive Logon Security Configuration	Low
6	Weak User Account Control Elevation Configuration	Medium
7	Insecure ICMP Redirect Processing Configuration	Low
8	Built-in Administrator Account Configuration	Medium
9	Unsupported and Outdated Software Components Installed	Medium
High: 0
Medium: 7
Low: 2
Total: 9 findings

From <https://chatgpt.com/g/g-p-68da8a6c742881918ea4f1aa2e62f91c/c/6a7959e4-7b5c-83ec-b68f-d90c2e049039> 

