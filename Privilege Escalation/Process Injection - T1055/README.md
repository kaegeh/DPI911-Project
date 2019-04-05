
#Process Injection -- T1055

#Description

Process Injection occurs when arbitrary code is executed in the memory address space of a separate live process. We will cover DLL injection which uses CreateRemoteThread function to start execution in the remote process. The DLL is loaded into the process by kernel32.dll and its LoadLibrary function.

To demonstrate this technique, we are going to use the tool called RemoteDLLInjector and inject a malicious DLL into a process.

#Attack
![Process Injection 1](https://user-images.githubusercontent.com/36422282/55604356-53ad5200-573d-11e9-80c9-4425c73844df.PNG)

The Sysmon agent on the host is configured to detect DLL injection with CreateRemoteThread (Sysmon Event ID 8)
![Process Injection 2](https://user-images.githubusercontent.com/36422282/55604548-53fa1d00-573e-11e9-86b3-8ac7a3138295.PNG)

#Splunk Filter

To detect this technique, we should monitor Microsoft-Windows-PowerShell/Operational log for event code 4104 (command execution) entries. The command should contain the "Get-ServiceUnquoted" string (name of PowerSploit module, used to detect unquoted service paths, vulnerable to path interception).

Splunk Filter = host="AGENT-2" source="XmlWinEventLog:Microsoft-Windows-Sysmon/Operational" EventCode=8
![Process Injection Filter](https://user-images.githubusercontent.com/36422282/55604563-6ecc9180-573e-11e9-8e4d-41ae51168510.png)
