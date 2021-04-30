## Description
Cisco ASA Firewall is a security product provided by Cisco. https://www.cisco.com/c/en/us/products/security/firewalls/index.html#~products. Example logs for Cisco ASA Firewall pix 500 can be found here: https://www.cisco.com/c/en/us/support/docs/security/pix-500-series-security-appliances/63884-config-asa-00.html#anc6 as well as here: https://www.cisco.com/c/en/us/td/docs/security/asa/syslog/b_syslog/messages-listed-by-severity-level.html#con_1009233

## Example Log
```
Jul 03 2014 14:33:09: %ASA-6-302014: Teardown TCP connection 806405 for inside:10.0.0.100/50554 to identity:172.18.124.136/51358 duration 0:00:00 bytes 442 TCP Reset-I 
```

https://www.cisco.com/c/en/us/td/docs/security/asa/syslog/b_syslog/messages-listed-by-severity-level.html


## Example Parser
https://rubular.com/r/WoI3X88OUzXnyB

```
^(?<time>[a-zA-Z0-9 ]+:[0-9]{2}:[0-9]{2}): (?<ident>%ASA-[0-9]-(?<code>[0-9]*)): (?<message>.+)
```

| Fields | Data |
| ---- | ---- |
| time | Jul 03 2014 14:33:09 |
| ident |	 %ASA-6-302014 |
| code |	302014 |
| message |	Teardown TCP connection 806405 for inside:10.0.0.100/50554 to identity:172.18.124.136/51358 duration 0:00:00 bytes 442 TCP Reset-I |

This parser extracts the code separately from the identity field - which allows you to go to the following website and search for any recommended actions. For example for our Syslog Message of 302014: https://www.cisco.com/c/en/us/td/docs/security/asa/syslog/b_syslog/syslogs3.html#con_6941209

