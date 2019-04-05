# Forced Authentication- T1187

## Technique Description
When a user access an untrusted resource it will attempt to authenticate to the adversaries server with information such as the user’s SMB hashed credentials.   
To demonstrate this techniques we used an .scf file which was downloaded by a user with the responder listening on another machine. When the user downloads the scf file and visits the directory the file is stored in, it tries to authenticate with the other server which is running responder which captures the hashed credentials. 

## Assumption
The hashed credentials should be captured

## Execution
### .SCF File
![fascf file](https://user-images.githubusercontent.com/36422282/55609403-96c3f100-574e-11e9-8616-deb782d30681.JPG)


### Captured Credentials
![responder](https://user-images.githubusercontent.com/36422282/55609401-96c3f100-574e-11e9-99d4-dfee06da59de.JPG)


## Detection
### Splunk Filter
Splunk Filter = host="DESKTOP-EHTEINI" source="XmlWinEventLog:Microsoft-Windows-Sysmon/Operational" EventID=11 TargetFilename="*.scf"

### Splunk Capture
![image](https://user-images.githubusercontent.com/36422282/55609437-acd1b180-574e-11e9-90c4-e1edc85fa316.png)
