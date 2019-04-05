#Office Application Startup -- T1137

#Description

Macros are commands and instructions that can be grouped together as a single command to accomplish various tasks. Within Microsoft Office there lies *DDEAUTO*, which stands for *automatic dynamic data exchange*. Microsoft has pulled the plug on DDEAUTO, claiming ti to be a security risk because it can allow for obfuscation to launch commands and even scripts. We created an environment where we can just test the use of DDEAUTO to perform T1137 technique within the ATT&CK Mitre Persistence.

#Attack 

- First we enable the use of DDEAuto within the registry located at HKEY_CURRENT_USER\Software\Microsoft\Office\16.0\Word\Security
![allowdde](https://user-images.githubusercontent.com/36422282/55602401-5b67f900-5733-11e9-80fc-340ccf57b49d.PNG)

- Then we will use DDE within Microsoft Word to perform code execution
