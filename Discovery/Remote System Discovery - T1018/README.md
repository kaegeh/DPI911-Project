
# Remote System Discovery - T1018

## Description

Attackers will very likely attempt to conduct reconnaisance and get a listing of other systems on the network for lateral movement or pivoting.

To demonstrate this technique, we are going to use the net view command.

## Attack

![Remote System Discovery](https://user-images.githubusercontent.com/36422282/55612770-0342ee00-5757-11e9-9f07-3088c12ae069.PNG)

## Splunk Filter

NOTE: This filter is specific and relates to the specific attack technique itself.

To detect the technique we demonstrated, we should monitor Microsoft-Windows-Sysmon/Operational for net view commands.


host="AGENT-2" source="XmlWinEventLog:Microsoft-Windows-Sysmon/Operational" CommandLine="net* view*"

![Remote System Discovery](https://user-images.githubusercontent.com/36422282/55612957-78162800-5757-11e9-840c-af131d9dbf44.png)
