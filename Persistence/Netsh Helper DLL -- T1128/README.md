# Netsh Helper DLL- T1128

## Technique Description
Netsh contains functionality to add helper DLL’s for extending functionality of the utility. The registry for the paths registered to netsh.exe is at HKLM\SOFTWARE\Microsoft\Netsh. Netsh with helper DLL’s can be used to execute arbitrary code when netsh.exe is executed. 
  To demonstrate this technique we put a DLL in the system32 folder. Run netsh add helper $DLL. And when netsh is ran a calculator is also ran. 

## Assumptions
Running the netsh command should run the helper dll and pop up calculator.

## Execution
![netsh helper beacon dll](https://user-images.githubusercontent.com/36422282/55608241-0e445100-574c-11e9-9897-42679de6bb43.JPG)

## Detection

### Splunk Filter
Splunk Filter = host="DESKTOP-EHTEINI" ParentCommandLine="netsh  add helper NetshHelperBeacon.dll"

### Splunk Capture
![image](https://user-images.githubusercontent.com/36422282/55608268-18fee600-574c-11e9-8dfc-2ebc408156fd.png)

### Visibility- GRR
![image](https://user-images.githubusercontent.com/36422282/55608292-2320e480-574c-11e9-96bf-0c2b01dcf476.png)
