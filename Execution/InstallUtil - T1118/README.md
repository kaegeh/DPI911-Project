#InstallUtil -- T1091

#Description

InstallUtil allows for an adversary to be able to perform code execution via the use of a legitimate and trusted Windows utility. Therefore, attackers can bypass process whitelisting through the use of Installutil. RedAtomic/Canary provides a proof-of-concept for this ATT&CK Mitre Execution technique, and will be followed in this file listing. Please refer to the following screenshots for the attack process and Splunk Filter detection.

#Attack
![InstallUtil_Splunkforwarder](https://user-images.githubusercontent.com/36422282/55598133-349fc780-571f-11e9-8da0-1c097610335e.PNG)
![InstallUtil_SplunkforwarderExample](https://user-images.githubusercontent.com/36422282/55598133-349fc780-571f-11e9-8da0-1c097610335e.PNG)

NOTE This filter is specific and relates to the specific attack itself, as required to show correctness within writing filters

#Splunk Filter

host="DESKTOP-EHTEINI" CommandLine="csc.exe  /target:library T1118.cs" OR CommandLine="InstallUtil.exe  /logfile= /LogToConsole=false /U T1118.dll"

#Splunk Capture 
![installutil](https://user-images.githubusercontent.com/36422282/55598210-a710a780-571f-11e9-8d02-439c57c49f9e.png)
