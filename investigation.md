## Authentication Attack Analysis

During the investigation, multiple failed authentication attempts
were observed on the Domain Controller.

Event ID 4625 logs indicated repeated login failures targeting
a domain user account.

The source of the activity was identified as 192.168.206.131,
which corresponds to the attacker machine in the lab environment.

The failure reason indicated incorrect passwords, suggesting a
possible brute-force or password spraying attack.

This activity demonstrates how authentication attacks can be
detected using Windows Security logs. 



## User Enumeration Attempt

An attempt was made to enumerate domain users using anonymous
authentication against the domain controller.

Command used:

rpcclient -U "" 192.168.206.145

The request failed with NT_STATUS_LOGON_FAILURE, indicating that
anonymous access is disabled on the system.

This demonstrates that the domain controller is configured with
security controls that prevent unauthenticated enumeration of
Active Directory information.

## Incident: Suspicious Authentication Activity

### Summary
Multiple failed login attempts were detected on the domain controller,
indicating a potential credential-based attack.

### Evidence
Event ID: 4625 (Failed Logon)

### Key Findings
- Target Account: john
- Source IP Address: 192.168.206.131
- Logon Type: 3 (Network Logon)
- Failure Reason: Incorrect password

### Analysis
The repeated failed login attempts originating from a remote system
suggest a brute-force or password spraying attack targeting domain accounts.

### Conclusion
The activity is consistent with an external attacker attempting to gain
unauthorized access to the domain environment.

### MITRE ATT&CK Mapping
- T1110: Brute Force
- T1046: Network Service Discovery
## Network Activity Analysis (Sysmon Event ID 3)

Following successful authentication, network activity was observed
originating from the compromised system.

### Key Findings
- Source IP: 192.168.206.149
- Destination IP: 192.168.206.145
- Process: ping.exe
- User: CORP\john

### Analysis
The use of ping indicates that the user is actively probing
internal network systems. This behavior is consistent with
post-compromise reconnaissance.

### Conclusion
The attacker is likely mapping the network to identify additional
targets for lateral movement.
- 
