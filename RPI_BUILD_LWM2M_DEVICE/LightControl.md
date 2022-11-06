ssh to your Raspberry pi using "ssh dietpi@PI_IPADDR "
Install C compiler:
1. See if the c compiler is installed or not using
	  gcc -v
  
![image](https://user-images.githubusercontent.com/112636651/200152220-c1196dcd-fa51-4fa8-a998-f93410fc4a4b.png)

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

![image](https://user-images.githubusercontent.com/112636651/200152235-d7af4c32-a537-4fe3-a729-119ae452a779.png)

Install & Build the Anjay Library:
1. Retrieving the Anjay code
	  cd ~/projects
   	  git clone https://github.com/AVSystem/Anjay
2. Build Anjay code
	  cd ~/projects/AnjayFor
	  git submodule update --init
	  cmake . -DDTLS_BACKEND="mbedtls"
	  make -j
	  
![image](https://user-images.githubusercontent.com/112636651/200152241-214c4259-0602-4acb-a3b5-193dd7bda2c9.png)


Installing Anjay Library objects:
	  cd ~/projects/Anjay
	  cmake -DCMAKE_INSTALL_PREFIX=/home/dietpi/projects/Anjay-esp32-client . && make &&  make install
	  
![image](https://user-images.githubusercontent.com/112636651/200152261-bd9f05d2-6a9a-492b-a178-2003a0729e5a.png)

![image](https://user-images.githubusercontent.com/112636651/200152244-5c5925c9-a755-4db9-8d6b-3e65c9e967c9.png)

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
  
![image](https://user-images.githubusercontent.com/112636651/200152250-9d048984-919c-486d-b0c1-db898de6af73.png)

3. Setting up the device requirements
  	cd ~/projects/Anjay-esp32-client
  	idf.py menuconfig
Which will navigate to “component”and select config/anjay-esp-32-client Endpoint name (coap://{LESHAN_SERVER_IP}:5683) Server URI Choose socket (UDP) Choose security mode (Non-secure connection)
And setup the connection configuration WIFI SSID & WIFI PASSWORD

![image](https://user-images.githubusercontent.com/112636651/200152271-dde81e70-3663-4050-9717-916c9e272b18.png)

![image](https://user-images.githubusercontent.com/112636651/200152272-ac6eb93f-0c1c-456c-a5a4-56a8073c5df0.png)

In board options we should enable light control and enter the pin number to 5 in selected light colour.

4. Using below commands build the code for device
  	cd ~/projects/Anjay-esp32-client
  	idf.py build
  
![image](https://user-images.githubusercontent.com/112636651/200152282-33967cfc-bf60-40ec-9c2e-0143db593a1d.png)

5. Then find the port and flash the device
	Finding the port number using:
		ls -l /dev/ttyUSB*


![image](https://user-images.githubusercontent.com/112636651/200152291-a7366395-b05f-41f3-ba29-268c2017bf57.png)

It returns like below:

![image](https://user-images.githubusercontent.com/112636651/200152298-71c4c6dd-6a12-4f1a-8325-a071298c40a8.png)

To load the code, change the port number in this line. flash idf.py -p port number with port number = 0 I used
	  cd ~/projects/Anjay-esp32-client
  	sudo chmod 666 /dev/ttyUSB0
  	idf.py -p 0 flash

Then you can see flashing:

![image](https://user-images.githubusercontent.com/112636651/200152306-ae3a860e-89f2-4a2d-bc8c-a50057f38458.png)

To control open leshan-server:
1. Start the server using:
	  cd ~/projects/leshan
	  java -jar leshan-server-demo/target/leshan-server-demo-*-SNAPSHOT-jar-with-dependencies.jar &
2. My Raspberry PI is using 192.168.8.147 from the router admin client page
	http://192.168.8.147:8080
3. Run the leshan client
	  java -jar leshan-client-demo/target/leshan-client-demo-*-SNAPSHOT-jar-with-dependencies.jar

![image](https://user-images.githubusercontent.com/112636651/200152309-9141268f-5a33-4be4-92f1-7b7a018dc825.png)

Then when entering into leshan into the client there is anjay-esp-32-clientLight control.

![image](https://user-images.githubusercontent.com/112636651/200152317-05928b48-1289-408b-a279-c233a3d63910.png)

And we must select on/off by clicking on it. and the same as the dimmer by selecting the value between 0 and 100.

![image](https://user-images.githubusercontent.com/112636651/200152322-645ba55e-f375-462e-996e-2ba589886951.png)

![image](https://user-images.githubusercontent.com/112636651/200152344-e5456460-d3e0-4888-b4c1-0f95ff320723.png)

![image](https://user-images.githubusercontent.com/112636651/200153010-bd6542c3-15fc-4cd4-87b9-74354cea06fe.png)


