Below is the consolidated report for RRFPRODM26 using the same Windows reporting format you specified.
The endpoint is Microsoft Windows 11 IoT Enterprise LTSC, build 10.0.26100, and the evidence was collected on 20 July 2026 at 16:59 IST.

1. Insufficient Anonymous Network Access Restrictions
Observation
The test team observed that anonymous network access restrictions are not configured as per security best practices.
In the current scenario, the test team observed that anonymous enumeration of SAM accounts and network shares is not adequately restricted. Please find the affected registry path and observed value below:
	1. Network access: Do not allow anonymous enumeration of SAM accounts and shares is set to Disabled
HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\Lsa:RestrictAnonymous
Observed Value: 0
Recommended Value: 1
The related RestrictAnonymousSAM value was configured as 1; however, the broader restriction covering both SAM account and network share enumeration was not enabled.
The network evidence additionally confirmed that SMB services are active on the endpoint, including TCP port 445.
Risk Impact
An attacker can potentially use anonymous network connections to enumerate information about local accounts and network shares. This information can assist reconnaissance, password guessing, SMB-based attacks, and lateral movement within the network.
Severity
Medium
Affected Asset
RRFPRODM26
Recommendation
It is recommended to restrict anonymous enumeration of SAM accounts and network shares by following the below mentioned steps:
	1. To establish the recommended configuration via Group Policy, set the following UI path to Enabled:
Computer Configuration\Policies\Windows Settings\Security Settings\Local Policies\Security Options\Network access: Do not allow anonymous enumeration of SAM accounts and shares
	2. Verify the following registry path:
HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\Lsa:RestrictAnonymous
Recommended Value: 1
	3. Retain the existing secure configuration for:
Network access: Do not allow anonymous enumeration of SAM accounts
	4. Review anonymous access to named pipes and shares and permit only explicitly required resources.
Reference Controls
CIS Microsoft Windows 11 Enterprise Benchmark v4.0.0
CVE
NA

2. Insecure Storage of Network Authentication Credentials
Observation
The test team observed that storage of passwords and credentials used for network authentication is not restricted as per security best practices.
In the current scenario, the test team observed that Windows is configured to permit the storage of credentials used for network authentication. Please find the affected registry path and observed value below:
	1. Network access: Do not allow storage of passwords and credentials for network authentication is set to Disabled
HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\Lsa:DisableDomainCreds
Observed Value: 0
Recommended Value: 1
Risk Impact
An attacker can potentially obtain stored authentication credentials after compromising the endpoint or an authenticated user session. Compromised credentials may subsequently be reused to access other endpoints, network shares, applications, or network resources, increasing the likelihood of lateral movement.
Severity
Medium
Affected Asset
RRFPRODM26
Recommendation
It is recommended to prevent storage of passwords and credentials used for network authentication by following the below mentioned steps:
	1. To establish the recommended configuration via Group Policy, set the following UI path to Enabled:
Computer Configuration\Policies\Windows Settings\Security Settings\Local Policies\Security Options\Network access: Do not allow storage of passwords and credentials for network authentication
	2. Verify the registry configuration:
HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\Lsa:DisableDomainCreds
Recommended Value: 1
	3. Review Windows Credential Manager and remove unnecessary stored network credentials.
	4. Validate applications, scheduled tasks, or services that may legitimately depend on stored credentials before enforcing the setting.
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
The current value requires 128-bit encryption only, whereas the recommended configuration requires both NTLMv2 session security and 128-bit encryption.
Risk Impact
An attacker can attempt to exploit weaker NTLM session negotiation where NTLMv2 session security is not explicitly required. This can increase exposure to credential relay, interception, tampering, and man-in-the-middle attacks involving applications that rely on NTLM authentication.
Severity
Medium
Affected Asset
RRFPRODM26
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
CVE
NA

4. Inadequate Interactive Logon Security Configuration
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
The registry additionally contained CachedLogonsCount=10; however, this value was not used as a primary basis of the finding because the available registry evidence did not conclusively establish domain-join status.
Risk Impact
An attacker can obtain useful account information where the previous username is displayed at the sign-in interface. Disabling the Ctrl+Alt+Del secure attention sequence may reduce protection against fraudulent logon interfaces, while allowing shutdown without authentication can facilitate local denial-of-service activity.
Severity
Low
Affected Asset
RRFPRODM26
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
	4. Review the number of cached previous logons and reduce it where domain authentication is applicable and operationally feasible.
Reference Controls
CIS Microsoft Windows 11 Enterprise Benchmark v4.0.0
CVE
NA

5. Weak User Account Control Elevation Configuration
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
The test team additionally observed that EnableLUA=1 and PromptOnSecureDesktop=1; therefore, UAC itself is enabled and the issue is limited to the configured elevation-prompt behaviour.
Risk Impact
An attacker can have greater opportunity to abuse privilege-elevation workflows where elevation controls are less restrictive. Allowing standard users to enter administrative credentials for elevation can also increase the likelihood of privileged credential exposure to malicious applications or compromised user sessions.
Severity
Medium
Affected Asset
RRFPRODM26
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
	3. Retain User Account Control and secure-desktop prompting as enabled.
Reference Controls
CIS Microsoft Windows 11 Enterprise Benchmark v4.0.0
CVE
NA

6. Weak Local Password and Account Lockout Policy
Observation
The test team observed that the local password and account lockout policy is not configured as per security best practices.
In the current scenario, the test team observed the following weak local account policy configurations:
	1. Minimum password length is not enforced
Observed Value:
MinPasswordLength = 0
	2. Minimum password age is not enforced
Observed Value:
MinPasswordAge = 0
	3. Account lockout threshold is configured to permit excessive failed authentication attempts
Observed Value:
MaxBadPasswords = 10
The configured maximum password age was observed as 42 days and was therefore not included as a failed configuration.
Risk Impact
An attacker can perform password guessing and brute-force attacks more effectively when a minimum password length is not enforced and multiple failed authentication attempts are permitted before account lockout. A minimum password age of zero can also allow users to repeatedly change passwords in order to bypass password-history controls.
Severity
Medium
Affected Asset
RRFPRODM26
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
5 or fewer invalid logon attempts, but not 0.
	4. Configure appropriate values for:
Account lockout duration
Reset account lockout counter after
	5. Verify the effective configuration using:
net accounts
Reference Controls
CIS Microsoft Windows 11 Enterprise Benchmark v4.0.0
CVE
NA

7. Insecure Local Account Configuration
Observation
The test team observed that enabled local user accounts are not configured in accordance with password and privileged account security best practices.
In the current scenario, the test team observed insecure configurations affecting the built-in Administrator account and the actively used POS account.
	1. Built-in Administrator account
Account:
Administrator
SID:
S-1-5-21-2331301223-3305749386-3850997422-500
Account Status:
Enabled
Password Configuration:
DONT_EXPIRE_PASSWORD
Password Age:
58 days
The account retains the predictable built-in Administrator SID and default account name and is configured with a non-expiring password.
	2. POS account
Account:
POS
Account Status:
Enabled
Last Login:
20-07-2026 14:05:04
Password Configuration:
PASSWD_NOTREQD
DONT_EXPIRE_PASSWORD
NORMAL_ACCOUNT
The PASSWD_NOTREQD flag indicates that Windows does not enforce a password requirement for the account, while DONT_EXPIRE_PASSWORD exempts the credential from password-expiration requirements.
The presence of PASSWD_NOTREQD does not by itself prove that the account currently has a blank password.
Risk Impact
An attacker can obtain persistent unauthorized access more easily where enabled accounts are configured with non-expiring credentials or are permitted to operate without an enforced password requirement. Compromise of the built-in Administrator account could additionally provide extensive control over the endpoint.
Severity
Medium
Affected Asset
RRFPRODM26
Recommendation
It is recommended to securely configure enabled local accounts by following the below mentioned steps:
	1. Verify whether the built-in Administrator account is operationally required.
	2. Where not required, configure:
Computer Configuration\Policies\Windows Settings\Security Settings\Local Policies\Security Options\Accounts: Administrator account status
Set to:
Disabled
	3. Where the Administrator account must remain enabled, configure:
Computer Configuration\Policies\Windows Settings\Security Settings\Local Policies\Security Options\Accounts: Rename administrator account
Set to:
An organization-approved non-default account name.
	4. Remove the Password Never Expires configuration from the Administrator account.
	5. Manage the local Administrator credential through Windows LAPS or an approved privileged-access-management solution.
	6. Review the POS account and enforce a strong password.
	7. Remove the password-not-required configuration from the POS account.
	8. Remove the Password Never Expires configuration where application compatibility permits.
	9. Where the POS application requires a non-interactive service identity, migrate to an appropriately restricted service account rather than a general interactive user account.
Reference Controls
CIS Microsoft Windows 11 Enterprise Benchmark v4.0.0
Microsoft Local Account Security Guidance
Microsoft Windows LAPS Guidance
CVE
NA

8. Unsupported and Outdated Runtime Component Installed
Observation
The test team observed that an unsupported Microsoft runtime component is installed on the assessed endpoint.
In the current scenario, the test team observed the following unsupported runtime:
	1. Microsoft Visual C++ 2008 Redistributable - x86
Installed Version:
9.0.30729
Microsoft Visual C++ 2008 / v90 has exceeded its supported product lifecycle and no longer receives normal security servicing.
Risk Impact
An attacker can potentially exploit known or subsequently identified vulnerabilities affecting unsupported runtime components for which the installed release no longer receives normal security updates. Unsupported software also increases application dependency, compatibility, and long-term patch-management risk.
Severity
Low
Affected Asset
RRFPRODM26
Recommendation
It is recommended to remove unsupported runtime components where they are no longer required and migrate dependent applications to supported runtime versions by following the below mentioned steps:
	1. Identify applications currently dependent on Microsoft Visual C++ 2008 Redistributable.
	2. Upgrade dependent POS or business applications to versions compatible with currently supported Microsoft Visual C++ runtime components.
	3. Test all dependent applications in a controlled environment before removing the legacy runtime.
	4. Remove Microsoft Visual C++ 2008 only after confirming that no production application dependency remains.
	5. Establish periodic installed-software and lifecycle reviews to identify unsupported runtime components before vendor support expires.
Reference Controls
CIS Microsoft Windows 11 Enterprise Benchmark v4.0.0
Microsoft Visual C++ Product Lifecycle Guidance
Unsupported Software Management Best Practices
CVE
NA

RRFPRODM26 Finding Summary
#	Issue	Severity
1	Insufficient Anonymous Network Access Restrictions	Medium
2	Insecure Storage of Network Authentication Credentials	Medium
3	Weak NTLM Session Security Configuration	Medium
4	Inadequate Interactive Logon Security Configuration	Low
5	Weak User Account Control Elevation Configuration	Medium
6	Weak Local Password and Account Lockout Policy	Medium
7	Insecure Local Account Configuration	Medium
8	Unsupported and Outdated Runtime Component Installed	Low
High: 0
Medium: 6
Low: 2
Total: 8 findings

From <https://chatgpt.com/g/g-p-68da8a6c742881918ea4f1aa2e62f91c/c/6a7959e4-7b5c-83ec-b68f-d90c2e049039> 

