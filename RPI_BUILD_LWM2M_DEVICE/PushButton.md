#Push Button
•	For push button repeat the same process as light control. 
ssh to your Raspberry pi using "ssh dietpi@PI_IPADDR "
Install C compiler:
1. See if the c compiler is installed or not using
	gcc -v
  
![image](https://user-images.githubusercontent.com/112636651/200152589-9daf85b2-23d9-4d32-8fa0-11b972a87f25.png)

2. If not installed then use
	sudo-software
To Build Anjay install utlis and Libraries:
1. Clone the avs_commons repo
	cd ~/projects
	git clone https://github.com/AVSystem/avs_commons
2. Build and install avs_commons library
	cd ~/projects/avs_commons
	cmake . && make && sudo make install
Buliding and installing of avs_commons are completed.

![image](https://user-images.githubusercontent.com/112636651/200152598-dedf4c62-e2a7-4c10-b559-78e56a9a98be.png)

Install & Build the Anjay Library:
1. Retrieving the Anjay code
	cd ~/projects
	git clone https://github.com/AVSystem/Anjay
2. Build Anjay code
	cd ~/projects/AnjayFor
	git submodule update --init
	cmake . -DDTLS_BACKEND="mbedtls"
	make -j

![image](https://user-images.githubusercontent.com/112636651/200152602-454da082-d553-4cbe-b1fb-8d705f126082.png)

Installing Anjay Library objects:
	cd ~/projects/Anjay
	cmake -DCMAKE_INSTALL_PREFIX=/home/dietpi/projects/Anjay-esp32-client . && make &&  make install

![image](https://user-images.githubusercontent.com/112636651/200152608-a9af653f-009f-436d-905c-4288dd2013a4.png)

If the build fails, delete the Anjay-esp32-client directory and clone a prebuilt version with:
	cd projects
	git clone --recurse-submodules --remote-submodules https://github.com/pschragger/Anjay-esp32-client

Build of Anjay Client
1. Move to anjay-esp-32 directory that was clone earlier
	cd ~/projects/Anjay-esp32-client
2. For using the esp tools setup the local environment
	cd ~/projects/Anjay-esp32-client
	. $HOME/esp/esp-idf/export.sh
	idf.py set-target esp32 

![image](https://user-images.githubusercontent.com/112636651/200152618-b04b5cf9-f53a-4b0a-9f95-a80339152986.png)

3. Setting up the device requirements
	cd ~/projects/Anjay-esp32-client
	idf.py menuconfig

Which will navigate to “component”and select config/anjay-esp-32-client Endpoint name (coap://{LESHAN_SERVER_IP}:5683) Server URI Choose socket (UDP) Choose security mode (Non-secure connection)
And setup the connection configuration WIFI SSID & WIFI PASSWORD

![image](https://user-images.githubusercontent.com/112636651/200152625-deb6e221-b2f9-444b-9d9c-0b0449a20e5f.png)

![image](https://user-images.githubusercontent.com/112636651/200152626-758733db-bc2e-4dce-a8fc-64e7cba9928c.png)

•	In setting up the requirements select the push button and change the pin to 27.
•	Next same as light control build the code and flash.

4. Using below commands build the code for device
	cd ~/projects/Anjay-esp32-client
	idf.py build

![image](https://user-images.githubusercontent.com/112636651/200152651-1956802e-68ea-4043-a4e1-6e5b92373d8d.png)

5. Then find the port and flash the device
	Finding the port number using:
		ls -l /dev/ttyUSB*

![image](https://user-images.githubusercontent.com/112636651/200152656-d23a02a9-5916-4e72-948a-7ccc4f68a24f.png)

It returns like below:

![image](https://user-images.githubusercontent.com/112636651/200152668-9e887ff1-ccf0-4a1c-8f85-5cd9ae229747.png)

To load the code, change the port number in this line. flash idf.py -p port number with port number = 0 I used
	cd ~/projects/Anjay-esp32-client
	sudo chmod 666 /dev/ttyUSB0
	idf.py -p 0 flash

Then you can see flashing:

![image](https://user-images.githubusercontent.com/112636651/200152685-2bbae894-c8b2-44df-9039-27800b00cc69.png)

To control open leshan-server:
1. Start the server using:
	cd ~/projects/leshan
	java -jar leshan-server-demo/target/leshan-server-demo-*-SNAPSHOT-jar-with-dependencies.jar &
2. My Raspberry PI is using 192.168.8.147 from the router admin client page
	http://192.168.8.147:8080
3. Run the leshan client
	java -jar leshan-client-demo/target/leshan-client-demo-*-SNAPSHOT-jar-with-dependencies.jar


![image](https://user-images.githubusercontent.com/112636651/200152699-0fa7d488-6ed4-4085-b09a-faf22b2edc2d.png)

Then when entering into leshan into the client there is anjay-esp-32-client-->Push Button

![image](https://user-images.githubusercontent.com/112636651/200152713-81a1c424-9b82-4868-8342-f4aed726ee05.png)

•	Then it navigates to leshan server as light control.
•	Here, we must select read "R"(Read) for the digital input state as well as read the digital input counter.
Now that I've clicked the button seventeen times.

![image](https://user-images.githubusercontent.com/112636651/200152730-c054311a-f307-41a2-bfbb-88f29513123f.png)

![image](https://user-images.githubusercontent.com/112636651/200152737-973848a0-981d-4336-901a-09eb2b01f50b.png)


