
#Security Software Discovery - T1063

#Description

Attackers will very likely attempt to enumerate security software, such as firewalls, anti-viruses or IDS software, installed on the system.

To demonstrate this technique, specifically firewall enumeration, we are going to use the netsh advfirewall command.

#Attack

![Security Software Discovery](https://user-images.githubusercontent.com/36422282/55613328-7436d580-5758-11e9-90d9-a9f1a544e26c.PNG)

#Splunk Filter

To detect the technique we demonstrated, we should monitor Microsoft-Windows-Sysmon/Operational for netsh advfirewall commands.

host="AGENT-2" source="XmlWinEventLog:Microsoft-Windows-Sysmon/Operational" CommandLine="netsh* advfirewall*"

![Security Software Discovery](https://user-images.githubusercontent.com/36422282/55613422-a6483780-5758-11e9-82e0-021c6e3ce4bf.PNG)
