
#Remote File Copy - T1105

#Description

Attackers will very likely attempt to enumerate security software, such as firewalls, anti-viruses or IDS software, installed on the system.

To demonstrate this technique, specifically using the certutil command, we are going to use this command to pull a file from the web (Atomic Test #7).

#Attack

![Remote File Copy](https://user-images.githubusercontent.com/36422282/55614179-7437d500-575a-11e9-92e6-325f7c800ae7.PNG)

#Splunk Filter

To detect the technique we demonstrated, we should monitor Microsoft-Windows-Sysmon/Operational for certutil commands that have a URL as an argument.

host="AGENT-2" source="XmlWinEventLog:Microsoft-Windows-Sysmon/Operational" CommandLine="certutil* http*"

![Remote File Copy](https://user-images.githubusercontent.com/36422282/55614168-70a44e00-575a-11e9-9c9e-d3c81743b74f.png)
