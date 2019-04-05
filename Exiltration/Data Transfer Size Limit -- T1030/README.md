#Data Transfer Size Limits -- T1030

#Description

In this scenario, an adversary simply exfiltrates data in fixed sizes, rather than exfiltrating the file as a whole. The purposes of this is to try and evade detection, and avoid triggering alerts in NSM Tools. Red Atomic/Canary provide a proof of concept where the dd command-line utility for Linux is used for copying and converting files. The following will show the commands used to perform the attack, along with the Splunk Filter for detection


#Attack

cd /tmp/
dd if=/dev/urandom of=/tmp/victim-whole-file bs=25M count=1
split -b 5000000 /tmp/victim-whole-file
ls -l

*NOTE* This filter is specific and relates to the specific attack itself, as required to show correctnes within writing filters

#Splunk Filter

host="DESKTOP-H25LQ8L" *dd.exe*

#Splunk Capture
