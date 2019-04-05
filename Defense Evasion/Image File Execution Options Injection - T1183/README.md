# Image File Execution Options Injection - T1183

## Description

IFEO are used by attackers to hide execution of a process. For example, IEFOs can enable an arbitrary program to launch when another arbitrary program exits.

To demonstrate this technique, we are going to start evil.exe when notepad.exe exits.

## Attack

![Image File Execution Options 1](https://user-images.githubusercontent.com/36422282/55606414-ab03f000-5746-11e9-926e-69d32608c835.PNG)

## Splunk Filter

To detect the technique we demonstrated, we should monitor Microsoft-Windows-Sysmon/Operational Event IDs 12 and 13 (Registry object create/delete and registry value set respectively), looking for events from HKLM\SOFTWARE\Microsoft\Windows NT\CurrentVersion\Image File Execution Options\


host="AGENT-2" source="XmlWinEventLog:Microsoft-Windows-Sysmon/Operational" EventCode="12" OR EventCode="13" "Image File Execution Options"
![Image File Execution Options](https://user-images.githubusercontent.com/36422282/55606585-56ad4000-5747-11e9-8c92-61a0a4f90c4b.png)
