#LSASS Driver -- T1177

#Description

Local Security Authority (LSA) is the component that handles user authentication and local security policies in Windows. It includes multiple DLLs that run within a context of a single process - lsass.exe. By targeting this process, attackers can obtain user credentials. To mitigate that, lsass.exe should be run as a protected process (RunAsPPL=1).

To demonstrate this technique, we are going to use Powersploit's Install-SSP module to try to install an SSP (security support provider) DLL and add it to HKLM\SYSTEM\CurrentControlSet\Control\Lsa\Security Packages. With LSA protection enabled on the machine, it should not allow the latter and generate an event with the code 3033.

#Attack
![LSASS](https://user-images.githubusercontent.com/36422282/55600805-ca415400-572b-11e9-9660-0b221b744399.PNG)

#Splunk Filter

To detect this technique, we should monitor Microsoft-Windows-Codeintegrity/Operational log for event code 3033 entries. Event code 3033 means that a code integrity check determined that a process (usually lsass.exe) attempted to load a driver that did not meet the Microsoft signing level requirements.

host="AGENT-2" source="WinEventLog:Microsoft-Windows-CodeIntegrity/Operational" EventCode="3033"

![lsassfilter](https://user-images.githubusercontent.com/36422282/55600839-fbba1f80-572b-11e9-80ee-65c59362b95a.png)

