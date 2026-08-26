Below is the consolidated report for NSHO00SCM15, following the same Windows reporting format you specified.
The endpoint is Microsoft Windows 11 Pro, build 10.0.26200, and the evidence was collected on 20 July 2026 at 15:00 IST.

1. Insufficient Anonymous Network Access Restrictions
Observation
The test team observed that anonymous network access restrictions are not configured as per security best practices.
In the current scenario, the test team observed that anonymous enumeration of SAM accounts and network shares is not adequately restricted. Please find the affected registry path and observed value below:
	1. Network access: Do not allow anonymous enumeration of SAM accounts and shares is set to Disabled
HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\Lsa:RestrictAnonymous
Observed Value: 0
Recommended Value: 1
The related RestrictAnonymousSAM value was configured as 1; however, the broader restriction covering both SAM account and network share enumeration was not enabled.
Risk Impact
An attacker can potentially use anonymous network connections to enumerate information relating to local accounts and shared resources. This information can assist reconnaissance, targeted password attacks, SMB-based attacks, and lateral movement within the network.
Severity
Medium
Affected Asset
NSHO00SCM15
Recommendation
It is recommended to restrict anonymous enumeration of SAM accounts and network shares by following the below mentioned steps:
	1. To establish the recommended configuration via Group Policy, set the following UI path to Enabled:
Computer Configuration\Policies\Windows Settings\Security Settings\Local Policies\Security Options\Network access: Do not allow anonymous enumeration of SAM accounts and shares
	2. Verify that the following registry value is configured:
HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\Lsa:RestrictAnonymous
Recommended Value: 1
	3. Retain the existing secure configuration for:
Network access: Do not allow anonymous enumeration of SAM accounts
Reference Controls
CIS Microsoft Windows 11 Enterprise Benchmark v4.0.0
CVE
NA

2. Insecure Storage of Network Authentication Credentials
Observation
The test team observed that storage of passwords and credentials used for network authentication is not restricted as per security best practices.
In the current scenario, the test team observed that Windows is configured to permit the storage of network authentication credentials. Please find the affected registry path and observed value below:
	1. Network access: Do not allow storage of passwords and credentials for network authentication is set to Disabled
HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\Lsa:DisableDomainCreds
Observed Value: 0
Recommended Value: 1
Risk Impact
An attacker can potentially obtain stored authentication credentials after compromising the endpoint or an authorized user session. Compromised credentials may subsequently be reused to access additional systems, applications, network shares, or domain resources, increasing the likelihood of lateral movement.
Severity
Medium
Affected Asset
NSHO00SCM15
Recommendation
It is recommended to prevent storage of passwords and credentials used for network authentication by following the below mentioned steps:
	1. To establish the recommended configuration via Group Policy, set the following UI path to Enabled:
Computer Configuration\Policies\Windows Settings\Security Settings\Local Policies\Security Options\Network access: Do not allow storage of passwords and credentials for network authentication
	2. Verify the following registry value:
HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\Lsa:DisableDomainCreds
Recommended Value: 1
	3. Review Windows Credential Manager and remove unnecessary stored network credentials.
	4. Before applying the restriction, validate applications, scheduled tasks, or services that may legitimately depend on stored credentials.
Reference Controls
CIS Microsoft Windows 11 Enterprise Benchmark v4.0.0
CVE
NA

3. Weak NTLM Session Security Configuration
Observation
The test team observed that minimum NTLM session security requirements are not configured as per security best practices.
In the current scenario, the test team observed that both NTLM client and server configurations require 128-bit encryption but do not require NTLMv2 session security. Please find the affected registry paths and observed values below:
	1. Minimum session security for NTLM SSP-based clients
HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\Lsa\MSV1_0:NtlmMinClientSec
Observed Value: 536870912
Recommended Value: 537395200
	2. Minimum session security for NTLM SSP-based servers
HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\Lsa\MSV1_0:NtlmMinServerSec
Observed Value: 536870912
Recommended Value: 537395200
The current value requires 128-bit encryption, while the recommended value requires both NTLMv2 session security and 128-bit encryption.
Risk Impact
An attacker can attempt to exploit weaker NTLM authentication sessions when NTLMv2 session security is not explicitly required. This may increase exposure to credential interception, relay attacks, tampering, and man-in-the-middle attacks involving applications that use NTLM authentication.
Severity
Medium
Affected Asset
NSHO00SCM15
Recommendation
It is recommended to enforce NTLMv2 session security and 128-bit encryption by following the below mentioned steps:
	1. To establish the recommended configuration via Group Policy, configure:
Computer Configuration\Policies\Windows Settings\Security Settings\Local Policies\Security Options\Network security: Minimum session security for NTLM SSP based (including secure RPC) clients
Set the following options:
Require NTLMv2 session security
Require 128-bit encryption
	2. Configure:
Computer Configuration\Policies\Windows Settings\Security Settings\Local Policies\Security Options\Network security: Minimum session security for NTLM SSP based (including secure RPC) servers
Set the following options:
Require NTLMv2 session security
Require 128-bit encryption
	3. Verify:
NtlmMinClientSec = 537395200
NtlmMinServerSec = 537395200
Reference Controls
CIS Microsoft Windows 11 Enterprise Benchmark v4.0.0
CVE
NA

4. Inadequate Interactive Logon Security Configuration
Observation
The test team observed that interactive logon security settings are not configured as per security best practices.
In the current scenario, the test team observed multiple interactive logon security weaknesses. Please find the affected settings below:
	1. Excessive previous domain logons are cached
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\Winlogon:CachedLogonsCount
Observed Value: 10
Recommended Value: 4 or fewer
	2. Last signed-in username is displayed
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\System:DontDisplayLastUserName
Observed Value: 0
Recommended Value: 1
	3. Ctrl+Alt+Del secure attention sequence is not required
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\Winlogon:DisableCAD
Observed Value: 1
Recommended Value: 0
	4. Shutdown is permitted without authentication
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\System:ShutdownWithoutLogon
Observed Value: 1
Recommended Value: 0
Risk Impact
An attacker can obtain useful account information where the last signed-in username is displayed and may target cached domain authentication data following compromise of the endpoint. Disabling the secure attention sequence can also reduce protection against credential-capture interfaces that imitate the Windows logon screen. Permitting unauthenticated shutdown can additionally enable local denial-of-service actions.
Severity
Low
Affected Asset
NSHO00SCM15
Recommendation
It is recommended to strengthen interactive logon security by following the below mentioned steps:
	1. Configure:
Computer Configuration\Policies\Windows Settings\Security Settings\Local Policies\Security Options\Interactive logon: Number of previous logons to cache (in case domain controller is not available)
Set to:
4 or fewer logons
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

5. Weak User Account Control Elevation Configuration
Observation
The test team observed that User Account Control elevation behaviour is not configured as per security best practices.
In the current scenario, the test team observed that administrator and standard-user elevation prompts are configured with weaker values than the recommended hardened configuration. Please find the affected registry paths below:
	1. Administrator elevation prompt behaviour
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\System:ConsentPromptBehaviorAdmin
Observed Value: 5
Current Configuration:
Prompt for consent for non-Windows binaries
Recommended Value: 2
Recommended Configuration:
Prompt for consent on the secure desktop
	2. Standard-user elevation prompt behaviour
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\System:ConsentPromptBehaviorUser
Observed Value: 3
Current Configuration:
Prompt for credentials
Recommended Value: 0
Recommended Configuration:
Automatically deny elevation requests
The assessment confirmed that UAC itself remains enabled through EnableLUA=1 and secure-desktop prompting is enabled through PromptOnSecureDesktop=1.
Risk Impact
An attacker can have greater opportunity to abuse privilege-elevation workflows where elevation prompts are less restrictive. Allowing standard users to enter administrative credentials for elevation can also increase the likelihood of privileged credential exposure to malicious applications or compromised user sessions.
Severity
Medium
Affected Asset
NSHO00SCM15
Recommendation
It is recommended to strengthen User Account Control elevation behaviour by following the below mentioned steps:
	1. Configure:
Computer Configuration\Policies\Windows Settings\Security Settings\Local Policies\Security Options\User Account Control: Behavior of the elevation prompt for administrators in Admin Approval Mode
Set to:
Prompt for consent on the secure desktop
	2. Configure:
Computer Configuration\Policies\Windows Settings\Security Settings\Local Policies\Security Options\User Account Control: Behavior of the elevation prompt for standard users
Set to:
Automatically deny elevation requests
	3. Retain the existing UAC and secure-desktop protections.
Reference Controls
CIS Microsoft Windows 11 Enterprise Benchmark v4.0.0
CVE
NA

6. Insecure ICMP Redirect Processing Configuration
Observation
The test team observed that ICMP redirect processing is not configured as per security best practices.
In the current scenario, the test team observed that ICMP redirects are enabled on the Windows TCP/IP stack. Please find the affected registry path below:
	1. ICMP redirect processing is Enabled
HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\Tcpip\Parameters:EnableICMPRedirect
Observed Value: 1
Recommended Value: 0
The registry additionally contained:
HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\Tcpip\Parameters:DeadGWDetectDefault
Observed Value: 1
The primary basis for this finding is the enabled ICMP redirect processing configuration.
Risk Impact
An attacker can attempt to send malicious ICMP redirect messages from a reachable network position to influence the endpoint's routing decisions. Successful manipulation may redirect network traffic through an unintended or attacker-controlled route and increase the possibility of traffic interception or man-in-the-middle attacks.
Severity
Low
Affected Asset
NSHO00SCM15
Recommendation
It is recommended to disable ICMP redirect processing by following the below mentioned steps:
	1. To establish the recommended configuration via Group Policy, set the following UI path to Disabled:
Computer Configuration\Policies\Administrative Templates\MSS (Legacy)\MSS: (EnableICMPRedirect) Allow ICMP redirects to override OSPF generated routes
	2. Verify the following registry value:
HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\Tcpip\Parameters:EnableICMPRedirect
Recommended Value: 0
	3. Apply the policy:
gpupdate /force
	4. Verify the effective configuration after policy application.
Reference Controls
CIS Microsoft Windows 11 Enterprise Benchmark v4.0.0
CVE
NA

7. Insecure Local Account Password Configuration
Observation
The test team observed that an enabled local user account is not configured in accordance with password security best practices.
In the current scenario, the test team observed that the local account IT-HW is enabled and configured with the following account flags:
Account:
IT-HW
Account Status:
Enabled
Password Configuration:
PASSWD_NOTREQD
DONT_EXPIRE_PASSWORD
NORMAL_ACCOUNT
The PASSWD_NOTREQD flag indicates that Windows does not enforce a password requirement for this account, while DONT_EXPIRE_PASSWORD exempts the account from the configured password-expiration policy.
The effective global password policy itself was comparatively stronger, with:
Minimum Password Length: 12
Minimum Password Age: 1 day
Maximum Password Age: 30 days
Account Lockout Threshold: 5 attempts
Therefore, the issue is specific to the IT-HW account rather than the overall password policy.
Risk Impact
An attacker can gain persistent unauthorized access more easily where an enabled account is permitted to operate without requiring a password and where its credential is configured never to expire. A compromised credential may remain usable for an extended period unless manually changed or the account is disabled.
Severity
Medium
Affected Asset
NSHO00SCM15
Recommendation
It is recommended to securely configure the IT-HW local account by following the below mentioned steps:
	1. Verify whether the IT-HW account is still operationally required.
	2. If the account is not required, disable it:
Disable-LocalUser -Name "IT-HW"
	3. If the account is required, ensure that a strong password is configured.
	4. Remove the Password Never Expires configuration:
Set-LocalUser -Name "IT-HW" -PasswordNeverExpires $false
	5. Remove the password-not-required account flag using approved local account management controls.
	6. Verify:
Get-LocalUser -Name "IT-HW" | Format-List *
	7. Ensure the account follows the organization's standard password and account-expiration requirements.
Reference Controls
CIS Microsoft Windows 11 Enterprise Benchmark v4.0.0
Microsoft Local Account Security Guidance
CVE
NA

8. Missing Windows Security Updates
Observation
The test team observed that the Windows operating system is not updated with the latest cumulative security update available at the time of assessment.
In the current scenario, the test team observed that NSHO00SCM15 was running Windows 11 Pro build 26200.8037, corresponding to cumulative update KB5079473, released on 10 March 2026. Microsoft confirms that KB5079473 corresponds to Windows 11 25H2 build 26200.8037. (Microsoft Support)
The endpoint was assessed on 20 July 2026. Microsoft had already released the 14 July 2026 security update KB5101650, which updated Windows 11 version 25H2 to OS build 26200.8875 and contained the latest security fixes and improvements. (Microsoft Support)
Therefore, the endpoint remained several monthly cumulative security releases behind the supported patch level at the time of assessment.
Risk Impact
An attacker can exploit vulnerabilities that Microsoft has already addressed through security updates but which remain unpatched on the endpoint. Depending on the affected Windows component, successful exploitation may result in remote code execution, privilege escalation, information disclosure, security feature bypass, or denial of service.
Severity
Medium
Affected Asset
NSHO00SCM15
Recommendation
It is recommended to update the Windows operating system to the latest organization-approved cumulative security patch level by following the below mentioned steps:
	1. Review installed updates:
Get-HotFix | Sort-Object InstalledOn -Descending
	2. Review the current OS build:
Get-ComputerInfo | Select WindowsProductName,WindowsVersion,OsBuildNumber
	3. At the assessment date, install KB5101650 or a later approved superseding cumulative security update.
	4. Deploy updates through Windows Update for Business, WSUS, Microsoft Configuration Manager, Intune, or the organization's approved endpoint patch-management solution.
	5. Reboot the endpoint where required.
	6. Verify that the operating-system build reflects the successfully installed cumulative update.
	7. Establish a defined monthly patching process to prevent endpoints from remaining several security-release cycles behind.
Reference Controls
CIS Microsoft Windows 11 Enterprise Benchmark v4.0.0
Microsoft Windows 11 Update History
Microsoft Security Update Guide
CVE
Multiple CVEs addressed by the missing cumulative security updates

9. Trusted Platform Module (TPM) Not Available
Observation
The test team observed that Trusted Platform Module functionality is not available on the assessed Windows 11 endpoint.
In the current scenario, the test team observed the following TPM status:
TpmPresent: False
TpmReady: False
ManufacturerId: 0
AutoProvisioning: NotDefined
The assessment therefore indicates that Windows does not currently have access to an operational TPM on the endpoint.
Risk Impact
An attacker can have greater opportunity to compromise or extract sensitive cryptographic material where hardware-backed protection is unavailable. The absence of an operational TPM can prevent or weaken security capabilities that depend on hardware-backed key storage and platform integrity, including BitLocker key protection, Windows Hello, measured boot, device attestation, and other Windows credential-protection mechanisms.
Severity
Low
Affected Asset
NSHO00SCM15
Recommendation
It is recommended to enable and configure TPM 2.0 functionality where supported by the endpoint hardware by following the below mentioned steps:
	1. Verify whether a TPM 2.0 module is physically available or supported by the system firmware.
	2. Enter the BIOS/UEFI configuration and enable the applicable TPM implementation, such as:
TPM 2.0
Intel Platform Trust Technology (PTT)
AMD Firmware TPM (fTPM)
depending on the hardware platform.
	3. After enabling TPM, boot Windows and verify:
Get-Tpm
The expected secure state should include:
TpmPresent: True
TpmReady: True
	4. Initialize/provision TPM through Windows where required.
	5. After enabling TPM, review whether BitLocker, Windows Hello, Credential Guard, and other hardware-backed security controls can be enabled according to organizational policy.
	6. If the hardware genuinely does not support TPM 2.0, assess replacement or remediation according to the organization's Windows 11 hardware-security requirements.
Reference Controls
Microsoft Windows 11 Hardware Security Requirements
Microsoft Trusted Platform Module Guidance
CVE
NA

NSHO00SCM15 Finding Summary
#	Issue	Severity
1	Insufficient Anonymous Network Access Restrictions	Medium
2	Insecure Storage of Network Authentication Credentials	Medium
3	Weak NTLM Session Security Configuration	Medium
4	Inadequate Interactive Logon Security Configuration	Low
5	Weak User Account Control Elevation Configuration	Medium
6	Insecure ICMP Redirect Processing Configuration	Low
7	Insecure Local Account Password Configuration	Medium
8	Missing Windows Security Updates	Medium
9	Trusted Platform Module (TPM) Not Available	Low
High: 0
Medium: 6
Low: 3
Total: 9 findings

From <https://chatgpt.com/g/g-p-68da8a6c742881918ea4f1aa2e62f91c/c/6a7959e4-7b5c-83ec-b68f-d90c2e049039> 

