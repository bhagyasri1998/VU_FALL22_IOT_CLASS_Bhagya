Setup your software to run an IOT Platform:
Step 1:
1) SSH to the RPI using dietpi user
   Ssh dietpi@(IP ADDRESS)
   ![image](https://user-images.githubusercontent.com/112636651/190542271-d1513fbf-7985-47b6-aa6a-c430658812e1.png)

2) Install software on to the PI using dietpi-software command
3)Search for MQTT 
4) search for node-red
5) search for postgress
![image](https://user-images.githubusercontent.com/112636651/190542082-2d1640a0-ba3c-40fa-8a3d-547e3ab6f9f3.png)
![image](https://user-images.githubusercontent.com/112636651/190542095-238cfa00-dba1-4c4e-8ec5-1b7575756c9c.png)

 
 
Now dietpi is ready to install the software.
Postgres setup on pi:
1) run on your pi ssh session
sudo su postgres
2) Create
	createuser pi -P –interactive
Enter password
3) connect to Postgres and test database
psql
4) create database test
	Exit psql shell and again from the Postgres user by pressing Ctrl+D twice and login
	udo su postgres
psql test
create table people (name text, company text);
5) Add data
	insert into people values ('Ben Nuttall', 'Raspberry Pi Foundation');
insert into people values ('Rikki Endsley', 'Red Hat');
 ![image](https://user-images.githubusercontent.com/112636651/190542139-2b038ede-3c61-471e-afbd-e859f2370871.png)



