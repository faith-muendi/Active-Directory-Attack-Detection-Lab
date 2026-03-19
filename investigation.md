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
