
#LSASS Driver -- T1177

#Description

Local Security Authority (LSA) is the component that handles user authentication and local security policies in Windows. It includes multiple DLLs that run within a context of a single process - lsass.exe. By targeting this process, attackers can obtain user credentials. To mitigate that, lsass.exe should be run as a protected process (RunAsPPL=1).

To demonstrate this technique, we are going to use Powersploit's Install-SSP module to try to install an SSP (security support provider) DLL and add it to HKLM\SYSTEM\CurrentControlSet\Control\Lsa\Security Packages. With LSA protection enabled on the machine, it should not allow the latter and generate an event with the code 3033.

#Attack
![Path Interception](https://user-images.githubusercontent.com/36422282/55603147-40978380-5737-11e9-9bb7-5ad36999b3e6.PNG)

#Splunk Filter

To detect this technique, we should monitor Microsoft-Windows-Codeintegrity/Operational log for event code 3033 entries. Event code 3033 means that a code integrity check determined that a process (usually lsass.exe) attempted to load a driver that did not meet the Microsoft signing level requirements.

host="AGENT-2" source="WinEventLog:Microsoft-Windows-PowerShell/Operational" EventCode=4104 "Get-ServiceUnquoted"
![Path Interception Filter](https://user-images.githubusercontent.com/36422282/55603110-0928d700-5737-11e9-8f53-f5614429142a.png)

