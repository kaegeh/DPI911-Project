#LSASS Driver -- T1177

#Description

LSASS is an abbervation that stands for, "Local Security Authority Subsystem Service." Within the context of the Local Security Authority (LSA) is the component that handles the user authenticaiton. Attacker can leverage the lsass.exe to perform malicious intent such as code execution/persistence and perform techniques such as DLL Side-Loading/DLL Search Order Hijacking. In this scenario, we leverage the use of Powershell to use the Install-SSP module to add illegitimate drivers.

#Attack
![LSASS](https://user-images.githubusercontent.com/36422282/55600805-ca415400-572b-11e9-9660-0b221b744399.PNG)

NOTE This filter is specific and relates to the specific attack itself, as required to show correctnes within writing filters

#Splunk Filter
host="AGENT-2" source="WinEventLog:Microsoft-Windows-CodeIntegrity/Operational" EventCode=3033

![lsassfilter](https://user-images.githubusercontent.com/36422282/55600839-fbba1f80-572b-11e9-80ee-65c59362b95a.png)

