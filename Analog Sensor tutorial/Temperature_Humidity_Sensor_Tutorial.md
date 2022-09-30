Hello Everyone,
I tried to Set Up DHT11 Humidity sensor on the raspberry pi.
Hardware Equipment
1) Breadboard
2) Jump Wires
3) DHT11 temperature-Humidity sensor
4) Raspberry Pi
5) 10K ohm resistor
1. Connected the DHT11 sensor pins and other above equipment as shown in the picture.

![image](https://user-images.githubusercontent.com/112636651/193221747-575789d4-df97-42bd-996d-ae1ccde3292c.png)

2. Firstly I cloned and build the wiringPi.
3. fetch an updated version then you can re-run the build script by:
		cd WiringPi
		git pull origin
		cd WiringPi
		./build
4. I compile and run the C code using the commands listed below after saving it.
gcc -o humid humid.c -lwiringPi -lwiringPiDev
sudo ./humid
4. But I got “Data not good, skip” as below.

![image](https://user-images.githubusercontent.com/112636651/193221891-4954c472-257e-4c63-8c47-a32f08221ef4.png)

so, I changed counter value to 50 then run the C code after saving.

![image](https://user-images.githubusercontent.com/112636651/193222025-c957dc8d-0695-47dd-8822-bd70c37b5852.png)

So, the result after changing was above.
