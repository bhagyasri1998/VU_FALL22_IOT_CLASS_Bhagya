## Hardware Information

1) 2022 Dell Inspiron 3000 15 Laptop, 15.6" Full HD Touchscreen Display, Intel Dual Core i3-1115G4, 12GB DDR4, 256GB PCIe SSD, Online Meeting Ready, WiFi, RJ-45, HDMI, Win 10 S
2) Mango (GL-MT300N-V2), SD card 32GB

dietpi set up on a Raspberry PI via wifi:

Before set up Installed:
1)  BreeZip http:www.breezip.com 
2) balenaEtcher https://www.balena.io/etcher/
3) dietpi images: https://dietpi.com/#download 

Step 1:
•	Open balenaEtcher and select the dietpi images that was unzipped.
•	Insert the SD card and select a target.

![image](https://user-images.githubusercontent.com/112636651/190541574-435774d0-9f78-4773-9904-71fffeb8b15c.png)

•	Then the SD card gets flashed.
•	Close balenaEtcher
Step 2:
•	Copy the dietpi.txt and dietpi-wifi.txt.
•	Edit dietpi-wifi.txt file with ssid , password credentials
	aWIFI_SSID[0]='IOT-PAS'
	aWIFI_KEY[0]='iotlogin'
•	Edit dietpi.txt 
o	AUTO_SETUP_LOCALE=en_US.UTF-8
o	AUTO_SETUP_KEYBOARD_LAYOUT=us
o	AUTO_SETUP_TIMEZONE=America/New_York
o	AUTO_SETUP_NET_ETHERNET_ENABLED=0
o	AUTO_SETUP_NET_WIFI_ENABLED=1
o	AUTO_SETUP_NET_WIFI_COUNTRY_CODE=US
o	AUTO_SETUP_DHCP_TO_STATIC=1
o	AUTO_SETUP_NET_HOSTNAME=DietPi_{YOUR_INITIALS}
o	AUTO_SETUP_HEADLESS=1
o	AUTO_SETUP_AUTOSTART_TARGET_INDEX=1
o	SURVEY_OPTED_IN=0
o	CONFIG_SERIAL_CONSOLE_ENABLE=1
•	Eject your SD card
![image](https://user-images.githubusercontent.com/112636651/190541688-61700abd-9dc0-4344-abd9-731fbd470395.png)

Step 3:

Insert SD card on to the pi. After the red led on and the green led will start to flash open admin website of the router check the clients page. 
Step 4:
Using ssh login to pi(Must change the root).
ssh root@IPADDR
password: dietpi
After logging into pi change software and password.
![image](https://user-images.githubusercontent.com/112636651/190541739-59680798-1a01-4f5a-bcfa-133847c1b6f4.png)
![image](https://user-images.githubusercontent.com/112636651/190541780-9da157e2-05b7-45c8-9b12-1593bd633901.png)
Now its ready to install platform software.


