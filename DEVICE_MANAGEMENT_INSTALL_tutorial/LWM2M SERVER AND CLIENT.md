As we are facing the issues to connect with Wi-Fi, I connected my router to ethernet. Later I logon to Raspberry Pi Using.
	ssh dietpi@(IPADDR_OF_PI)

And started to Install development environment on RPI.
1)	In dietpi command line start dietpi software.
  		sudo dietpi-software
i)	search for git
ii)	enter spacebar to select and 
iii)	go to install on dietpi software 
iv)	check the version.
 	git –version
  
![image](https://user-images.githubusercontent.com/112636651/192080616-e6ebb2d0-2a24-4184-9ac8-00abb4d217a2.png)
![image](https://user-images.githubusercontent.com/112636651/192080624-e73103a3-fe04-4b56-835e-5b1e7d521169.png)


2)	In dietpi command line start dietpi software
sudo dietpi-software
i)	Search for java jdk
ii)	Enter spacebar to select and
iii)	Go to install on dietpi software 
iv)	Check the 
java –version

![image](https://user-images.githubusercontent.com/112636651/192080633-0b07289b-14d7-4285-a7d0-e8fad978dfa7.png)


3)	Installation of maven on Rapberry pi
i)	Created a download directory mkdir download
ii)	Changed directory into download directory - cd download
iii)	Downloaded the latest maven tarball using wget
https://dlcdn.apache.org/maven/maven-3/3.8.6/binaries/apache-maven-3.8.6-bin.tar.gz
iv)	unpacked the tarball - tar xzvf apache-maven-3.8.6-bin.tar.gz
v)	Confirming the installation using ( while installing I got an error that the command was not found. Professor Schragger said to Setup the environment variables to add maven to the paths and to continue further.)mvn -v 
vi)	I added the bin directory and tested maven installation.
 echo 'PATH="${PATH}:~/download/apache-maven-3.8.6/bin"' >>  ~/.bashrc

![image](https://user-images.githubusercontent.com/112636651/192080644-ef2bc3bd-2212-4516-bdc1-7ec6efcc081d.png)


vii)	Test maven installation using
bash
mvn -v
viii)	After the result create a JAVA_HOME environment variable.
(i)	 add the JAVA_HOME to the. bashrc 
sudo echo 'JAVA_HOME="/usr/lib/jvm/java-17-openjdk-arm64"' >> ~/.bashrc
(ii)	check the install was complete by
bash
echo $JAVA_HOME

![image](https://user-images.githubusercontent.com/112636651/192080657-a421b37a-ca19-4e2c-924d-b3d3d47319fb.png)


4) Installation of leshan git:
	Cloning the directory using 
		Cd
		mkdir projects
		cd projects
		git clone
	   https://github.com/eclipse/leshan.git	
	Build Leshan
	cd ~/projects/leshan
		mvn clean install (First I got a failure in the server demo as I                     don’t think I had an sufficient memory)
	I added the below two commands.
		set MAVEN_OPTS="-Xmx512m"
		export MAVEN_OPTS="-Xmx512m"
       	After that continue to build leshan by
		mvn clean install

![image](https://user-images.githubusercontent.com/112636651/192080668-77310010-2e26-47b5-99b1-e7e436fd6cfd.png)


Testing Leshan Server:

1) Start the server using 
	cd ~/projects/leshan
	java -jar leshan-server-demo/target/leshan-server-demo-*-SNAPSHOT-jar-with-dependencies.jar &
  
  ![image](https://user-images.githubusercontent.com/112636651/192080674-81d31fdb-d4f1-4760-a3bf-5d1042b0d388.png)

  
  
2) Connect to Leshan demo UI: http://RPI_IPADDR:8080
	My Raspberry PI is using 192.168.8.147
		http:// 192.168.8.147:8080
	This will bring to leshan register client page

![image](https://user-images.githubusercontent.com/112636651/192080682-cad18e17-9f18-4ba2-81f7-c53ccd40721c.png)


3) Run leshan client to add it to the page
	java -jar leshan-client-demo/target/leshan-client-demo-*-SNAPSHOT-jar-with-dependencies.jar


Additional Experiment of the LWM2M:

In order to use the Leshan boostrap and LWM2M standalone server, it has to be compiled from source code. The description below is for a computer running Ubuntu.

1) First install mvn and java

![image](https://user-images.githubusercontent.com/112636651/192080730-d696ec77-5cfc-4111-ac15-1105e3db0e9d.png)

![image](https://user-images.githubusercontent.com/112636651/192080791-9bf4be17-3e74-4f42-8316-be4843303e9f.png)

The libraries and example servers be compiled and ready to use. To test that the example server is working, run the Above commands in the screenshot.

Credentials must be added in order to connect to the LWM2M standalone server with a secure connection for a client application. 
Such credentials may be added using the Leshan user interface in the browser. The picture below depicts a common arrangement for the SDK examples.

![image](https://user-images.githubusercontent.com/112636651/192080922-dae266fb-8ac6-412d-a92f-f079a147e5a5.png)

After setting up the credentials.
![image](https://user-images.githubusercontent.com/112636651/192080959-2514ae12-34f9-47ba-a7e3-418a41dd7aad.png)





