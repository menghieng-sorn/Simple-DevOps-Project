#  Install & configure Maven build tool on Jenkins
Maven is a code build tool which used to convert your code to an artifact. this is a widely used plugin to build in continuous integration


#### Prerequisites
1. Jenkins server

#### Install Maven on Jenkins
1. Download maven packages https://maven.apache.org/download.cgi onto Jenkins server. In this case, I am using /opt/maven as my installation directory
 - Link : https://maven.apache.org/download.cgi
    ```sh
     # Creating maven directory under /opt
     mkdir /opt/maven
     cd /opt/maven
     # downloading maven version 3.10.0
     wget https://dlcdn.apache.org/maven/maven-3/3.10.0/binaries/apache-maven-3.10.0-bin.tar.gzv
     tar -xvzf apache-maven-3.10.0-bin.tar.gz
     ```
	
1. Setup M2_HOME and M2 paths in .bash_profile of the user and add these to the path variable
   ```
   cd ~
   vi ~/.bash_profile
   M2_HOME=/opt/maven
   M2=$M2_HOME/bin
   JAVA_HOME=/usr/lib/jvm/java-21-openjdk-21.0.12.1.1-1.2.el9.x86_64
   PATH=$PATH:$HOME/bin:$JAVA_HOME:$M2_HOME:$M2
   export PATH
   ```
#### Checkpoint 
1. logoff and login to check maven version
  
    ```sh
    mvn --version
    ```
So far we have completed the installation of maven software to support maven plugin on the jenkins console. Let's jump onto Jenkins to complete the remaining steps. 

### Setup maven on Jenkins console
1. Install maven plugin without restart  
  - `Manage Jenkins` > `Jenkins Plugins` > `available` > `Maven Invoker`
  - `Manage Jenkins` > `Jenkins Plugins` > `available` > `Maven Integration`

2. Configure maven path
  - `Manage Jenkins` > `Global Tool Configuration` > `Maven`

