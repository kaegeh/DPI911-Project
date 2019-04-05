#Replication Through Removable Media -- T1091

#Description

In this scenario, an adversary attempts to gain initial access onto a victim machine through removable media. Removable Media can range from a USB Flash drive, External HD/SSD etc. In This scenario, we created a Windows XP environment that was susceptible to, "Auto-Run," functionality whenever a USB drive was inserted. The USB drive contained a .bat file that executes a series of commands to be executed. This USB drive had the capabilities to steal passwords, and other malicious activity. We will display how the attack executed, along with the Splunk Filter from the Indexer to correlate the activity.

#Attack
![replication through removable media](https://user-images.githubusercontent.com/36422282/55601016-a03c6180-572c-11e9-9fff-fa683a2785a6.JPG)

*NOTE* This filter is specific and relates to the specific attack itself, as required to show correctnes within writing filters

#Splunk Filter

host="WIN-QE8T94VOGX0" source="WinEventLog:Microsoft-Windows-Sysmon/Operational" ParentCommandLine="cmd /c \"\"E:\\launch.bat\" /min\""

#Splunk Capture
![Replication through Removable Media filter](https://user-images.githubusercontent.com/36422282/55597663-b0e4db80-571c-11e9-9928-8494278e462b.PNG)


