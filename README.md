# wireless-speaker-with-raspberryPi  
#To start with the project, First preapare the raspberry Pi to setup.

Download the Raspbian Stretch in the SD card of Raspberry Pi and connect the raspberry to a screen.
Open SSH of Raspian, to connect the raspberry Pi 
To connect the network to raspbbery Pi. enter 

**network={  
ssid="your_wifi_name"  
psk="your_wifi_password"  
key_mgmt=WPA-PSK  
}**  

##Some prerequisites:-

BlueZ
to install, enter
**$sudo apt-get install bluez**

PulseAudio

**$sudo apt-get install pulseaudio-* **

##Connecting RaspberryPi
Now the raspberry Pi can connect to WiFi, but you still need the IP to SSH into it. To get IP Enter

**$ sudo nmap -sN [gateway ip address]/24**

This give IP address of all devices connected including Raspberry Pi's address

Now, to connect it, Enter

**$ssh pi@Raspberrypi_ip_address**

Now open BlueZ app by,

**$bluethoothct1**  

**$agent NoInputNoOutput**
(this initializes a agent which helps connect bluetooth without user intervention.)

**$default-agent**
(Setting the agent as default, so it doesn't have to connect everytime)

**$discoverable on**
(setting the device as discoverable)

##This set's up the raspberry Pi to connect by other devices.

##try connecting a device such as phone or laptop
 Enter "no" when the raspian prompts up for authorization of the connecting device, create a connection by trusting the device by,
**$trust [MAC address of device]
$connect [MAC address of device]**

##Now check if the device is registered in PulseAudio by,
**$pactl list short**

#Now we automate all the above process by writing scripts (file available above) 

##Finalizing all the process for everytime the raspberry Pi is turned on
##to create a cron job we need to give the raspberry Pi the main file.

**$crontab -e**

**@sudo reboot python3 /home/"file_location"/Bluetooth-speaker-main.py**




