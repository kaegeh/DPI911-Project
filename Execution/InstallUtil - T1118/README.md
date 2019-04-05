#InstallUtil -- T1091

#Description

InstallUtil allows for an adversary to be able to perform code execution via the use of a legitimate and trusted Windows utility. Therefore, attackers can bypass process whitelisting through the use of Installutil. RedAtomic/Canary provides a proof-of-concept for this ATT&CK Mitre Execution technique, and will be followed in this file listing. Please refer to the following screenshots for the attack process and Splunk Filter detection.

NOTE This filter is specific and relates to the specific attack itself, as required to show correctnes within writing filters

#Attack

#Splunk Filter host="WIN-QE8T94VOGX0" source="WinEventLog:Microsoft-Windows-Sysmon/Operational" ParentCommandLine="cmd /c ""E:\launch.bat" /min""

#Splunk Capture 
