## Setting Up dietpi on Raspberry PI ##
Before installing additional software, install DietPi over WiFi on a Raspberry PI.

Put a Linux operating system version on the PI.
## Completing the setup, you will require: ##

## Hardware Information ##

1) 2022 Dell Inspiron 3000 15 Laptop, 15.6" Full HD Touchscreen Display, Intel Dual Core i3-1115G4, 12GB DDR4, 256GB PCIe SSD, Online Meeting Ready, WiFi, RJ-45, HDMI, Win 10 S
2) Mango (GL-MT300N-V2), SD card 32GB

dietpi set up on a Raspberry PI via wifi:

## Before set up Installed: ##

1)  BreeZip http:www.breezip.com 
2) balenaEtcher https://www.balena.io/etcher/
3) dietpi images: https://dietpi.com/#download 

## Step 1: ##
•	Prepare your device with a Windows archiver extractor. I used BreeZip http:www.breezip.com and select the dietpi images that was unzipped.
•	Insert the SD card and select a target  https://www.balena.io/etcher/ 

## step 2: ##
1. Extract the DietPi disk image after downloading it.

2. Select the RaspberyPI Images at https://dietpi.com/#download.
3. Select the download for your desired Pi on the new page.
4. Check The Raspberry Pi 3 Model B, which can be found at https://en.wikipedia.org/wiki/Raspberry
5. I used: 64-bit ARMv8 image: https://dietpi.com/downloads/images/DietPi RPi-ARMv8-Bullseye.7z
6. Extract this file. - Use balenaetcher or another flashing program to write the DietPi image to your SD card.
## Step 3: ##
1. Launch Balenacher
2. Choose the dietpi picture.
3. Choose the desired card
4. Press flash. To get it to work.(I did two times then it worked).
As shown in the below figure after fash it looks like this.

![image](https://user-images.githubusercontent.com/112636651/190541574-435774d0-9f78-4773-9904-71fffeb8b15c.png)

6. Wait for the flash to end and check the copy.
7. Close Balenaetcher
## Step 4: ##
```
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
```
## Step 5: ##
1. Connect an SD card to the PI and turn it on to launch DietPI.
2. As the installation process progresses, you should see the red led turn on and the green led begin to flash.
3. Depending on the local network load, it might take ten minutes or longer for the green light to stop flashing.
4. Utilize the wireless access point to sign in to the DietPi.
5. Check the CLIENTS page for the IPADDR of the booted-up Raspberry Pi by using the router's admin website, which can be found at 192.168.8.1 if you're using the default OpenWrt configuration.
6. The following is the figure that you can see the dietpi in clients page

![image](https://user-images.githubusercontent.com/112636651/190541688-61700abd-9dc0-4344-abd9-731fbd470395.png)

7. Enter your PI's SSH login information as follows: ssh root@IPADDR password: dietpi.

The below pictures are the settings of password.  
![image](https://user-images.githubusercontent.com/112636651/190541739-59680798-1a01-4f5a-bcfa-133847c1b6f4.png)

![image](https://user-images.githubusercontent.com/112636651/190541780-9da157e2-05b7-45c8-9b12-1593bd633901.png)

8. When setting up, make sure to modify your root login. Once logged in, shut down the Pi.
9. The platform software installation can now begin.








