#LSASS Driver -- T1177

#Description

LSASS is an abbervation that stands for, "Local Security Authority Subsystem Service." Within the context of the Local Security Authority (LSA) is the component that handles the user authenticaiton. Attacker can leverage the lsass.exe to perform malicious intent such as code execution/persistence and perform techniques such as DLL Side-Loading/DLL Search Order Hijacking. In this scenario, we leverage the use of Powershell to use the Install-SSP module to add illegitimate drivers.

#Attack

NOTE This filter is specific and relates to the specific attack itself, as required to show correctnes within writing filters

#Splunk Filter
