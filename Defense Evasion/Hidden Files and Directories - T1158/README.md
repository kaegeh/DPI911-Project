
#Hidden Files and Directories - T1158

#Description

Attackers make files and directories they use hidden in order to evade accidental detection by the user of the compromised machine.

To demonstrate this technique, we are going to use the Attrib command to make a simple text file hidden.

#Attack
![Hidden Files and Directories](https://user-images.githubusercontent.com/36422282/55605827-434ca580-5744-11e9-9764-f76fb3ccf1e9.PNG)

#Splunk Filter

To detect the technique we demonstrated, we should monitor Microsoft-Windows-Sysmon/Operational for attrib commands with the +h flag set.


host="DESKTOP-H25LQ8L" source="XmlWinEventLog:Microsoft-Windows-Sysmon/Operational" CommandLine="attrib*+h*"
![Hidden Files and Directories](https://user-images.githubusercontent.com/36422282/55605835-4f386780-5744-11e9-8f06-97292b3fdcc8.png)
