# Screen Capture - T1113

## Description

Attackers can capture the screen of a compromised host. 
To demonstrate this technique, we ran PowerSploit's Get-TimedScreenshot module. This module can take screenshots at regular intervals and save them to a specified directory.

## Attack

![Screen Capture](https://user-images.githubusercontent.com/36422282/55612076-6df32a00-5755-11e9-9e8c-e55eeecfdf11.PNG)

## Splunk Filter

NOTE: This filter is specific and relates to the specific attack technique itself.

To detect the technique we demonstrated, we should monitor Microsoft-Windows-PowerShell/Operational Event ID 4104 (command executed) events that contain the "Get-TimedScreenshot" string, which would indicate execution of the PowerSploit module with the same name.

host="AGENT-2" source="WinEventLog:Microsoft-Windows-PowerShell/Operational" EventCode="4104" "Get-TimedScreenshot" 
![Screen Capture](https://user-images.githubusercontent.com/36422282/55611908-ee655b00-5754-11e9-9446-c512346426c5.png)
