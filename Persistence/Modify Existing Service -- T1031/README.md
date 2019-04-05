# Modifying Existing Service- T1031
## Technique Description
Windows service configuration information including the path to the service’s exe file is stored in the registry. The configurations can be modified using sc.exe or reg command. Modifying services can be used for the persistence of a malware. Using existing services also provides a type of masquerading which makes detection harder. Modifying existing services may interrupt their functionality or even enable services that were disabled or not commonly used.  
To demonstrate this technique we use sc.exe to change the bin path of Fax to output a sentence using PowerShell.

## Assumption
Starting this service should run PowerShell and output the given sentence.

## Execution
![modifying existing service](https://user-images.githubusercontent.com/36422282/55607849-2b2c5480-574b-11e9-9c90-d75f54407559.JPG)

## Detection

### Filter
Splunk Filter = host="DESKTOP-EHTEINI" sc config CommandLine="sc  config Fax binPath= \"C:\\windows\\system32\\WindowsPowerShell\\v1.0\\powershell.exe -noexit -c \\\"write-host 'T1031 Test'\\\"\""

### Splunk Capture
![image](https://user-images.githubusercontent.com/36422282/55607880-4008e800-574b-11e9-8d98-4d8674c008ed.png)

### Visibility- GRR
![image](https://user-images.githubusercontent.com/36422282/55607923-59119900-574b-11e9-8a78-f7ec64ba646b.png)

### Visibility- Osquery
![image](https://user-images.githubusercontent.com/36422282/55607937-5fa01080-574b-11e9-8803-966be6929152.png)
