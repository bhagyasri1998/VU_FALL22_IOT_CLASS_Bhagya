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
  


2)	In dietpi command line start dietpi software
sudo dietpi-software
i)	Search for java jdk
ii)	Enter spacebar to select and
iii)	Go to install on dietpi software 
iv)	Check the 
java –version



3)	Installation of maven on Rapberry pi
i)	Created a download directory mkdir download
ii)	Changed directory into download directory - cd download
iii)	Downloaded the latest maven tarball using wget
https://dlcdn.apache.org/maven/maven-3/3.8.6/binaries/apache-maven-3.8.6-bin.tar.gz
iv)	unpacked the tarball - tar xzvf apache-maven-3.8.6-bin.tar.gz
v)	Confirming the installation using ( while installing I got an error that the command was not found. Professor Schragger said to Setup the environment variables to add maven to the paths and to continue further.)mvn -v 
vi)	I added the bin directory and tested maven installation.
 echo 'PATH="${PATH}:~/download/apache-maven-3.8.6/bin"' >>  ~/.bashrc



vii)	Test maven installation using
bash
mvn -v
viii)	After the result create a JAVA_HOME environment variable.
(i)	 add the JAVA_HOME to the. bashrc 
sudo echo 'JAVA_HOME="/usr/lib/jvm/java-17-openjdk-arm64"' >> ~/.bashrc
(ii)	check the install was complete by
bash
echo $JAVA_HOME



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



Testing Leshan Server:

1) Start the server using 
	cd ~/projects/leshan
	java -jar leshan-server-demo/target/leshan-server-demo-*-SNAPSHOT-jar-with-dependencies.jar &
  
  
  
  
2) Connect to Leshan demo UI: http://RPI_IPADDR:8080
	My Raspberry PI is using 192.168.8.147
		http:// 192.168.8.147:8080
	This will bring to leshan register client page



3) Run leshan client to add it to the page
	java -jar leshan-client-demo/target/leshan-client-demo-*-SNAPSHOT-jar-with-dependencies.jar


Additional Experiment of the LWM2M:

In order to use the Leshan boostrap and LWM2M standalone server, it has to be compiled from source code. The description below is for a computer running Ubuntu.

1) First install mvn and java






