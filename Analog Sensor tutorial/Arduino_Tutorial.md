Hardware Equipment:
1. Breadboard with ESP32 Wrover
2. Jump Wires
3. DHT11 sensor
4. 10k ohm resistor
1) Need to be installed – Arduino IDE
	https://www.arduino.cc/en/software
2) Connect all the hardware Equipment as shown in below Figure:

![image](https://user-images.githubusercontent.com/112636651/193222411-da018370-38ce-43bb-bb4e-da407828564d.png)

3) Don’t forget to connect the ESP-32 to your laptop with the USB cable.
4) Install the downloaded Arduino IDE.
5) Select Preferences from the file.
6) Then add URL to the Additional board manager.
	https://dl.espressif.com/dl/package_esp32_index.json
7) Next install “ESP32 by Espressif Systems” by selecting toolsBoardBoards Manager.

8) Later select “ESP32 Wrover Module” in the tools->Board->ESP32 as shown below.

![image](https://user-images.githubusercontent.com/112636651/193222496-a21c2ee1-a886-46df-b3a2-a7d4e36a4a11.png)

After selecting the "ESP32 Wrover Module" was shown below

![image](https://user-images.githubusercontent.com/112636651/193222663-51682f8c-3fe0-41f8-b246-21a326266fcc.png)

9) Connect the ESP32 board to the computer using USB cable.
10) select the COM4 port in the tools.
11) Download the below library zip file and go to sketch ->Include library ->Add Zip library and select that zip file. It was shown in the below figure.

![image](https://user-images.githubusercontent.com/112636651/193222739-7616400e-e1df-4c4d-a002-5c9f3e10e222.png)

12) Copy the code of the C tutorial and paste into a file.
13) Upload and compile the code.
14) Then the uploading was done.
15) Check the serial monitor tab and set the baud rate 115200
16) Finally, you can see the temperature and humidity readings.
