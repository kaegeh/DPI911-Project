#Image Indicator Blocking - T1054

#Description

Attackers can disable sensors or block traffic/events from being received by sensor to hinder detection. For example, if an attacker gets privileged access to a Splunk event forwarder, he may simply stop the Splunk process. It would prevent events from the compromised forwarder from going to the SIEM console.

#Attack

![Indicator Blocking](https://user-images.githubusercontent.com/36422282/55610402-d2f85100-5750-11e9-965c-d7894e8e43a0.PNG)

#Splunk Filter

To detect the technique we demonstrated, one should regularly check and monitor the last time a sensor has been heard from.
