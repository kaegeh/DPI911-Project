
#Path Interception -- T1034

#Description

Path Interception happens when a malicious executable is placed in a specific path so that it is executed by an application instead of the intended legitimate executable. We will cover the Unquoted Paths vulnerability.

To demonstrate this technique, we are going to use Powersploit's Get-ServiceUnquoted module. This module detects unquoted service paths, vulnerable to path interception.

#Attack
![Path Interception](https://user-images.githubusercontent.com/36422282/55603147-40978380-5737-11e9-9bb7-5ad36999b3e6.PNG)

#Splunk Filter

To detect this technique, we should monitor Microsoft-Windows-PowerShell/Operational log for event code 4104 (command execution) entries. The command should contain the "Get-ServiceUnquoted" string (name of PowerSploit module, used to detect unquoted service paths, vulnerable to path interception).

host="AGENT-2" source="WinEventLog:Microsoft-Windows-PowerShell/Operational" EventCode=4104 "Get-ServiceUnquoted"
![Path Interception Filter](https://user-images.githubusercontent.com/36422282/55603110-0928d700-5737-11e9-8f53-f5614429142a.png)

