## Apache Maven Installation on Ubuntu 22.04

This guide details how to install Apache Maven on Ubuntu 22.04.

### Prerequisites
* installed Java

### Step 1: Install Java
- Check Java Version (Installed/Not-Installed)
     ```
     java -version
     ```
- Since Java is not installed on our system, we will install it using OpenJDK.
Open a terminal window and update the system package repository by running:
     ```
     sudo apt update
     ```
- To install OpenJDK 11, run:
     ```
     sudo apt install openjdk-11-jdk -y
     ```

##### Step 2: Installing Latest Maven From Source Code
* You can download Apache maven from its official website or use following command to download Apache Maven 3.9.8 on your system.
     ```
     wget https://dlcdn.apache.org/maven/maven-3/3.9.8/binaries/apache-maven-3.9.8-bin.tar.gz
     ```
* Now extract the downloaded Maven archive file using the following command.
     ```
     sudo tar xzf apache-maven-3.9.8-bin.tar.gz -C /opt
     sudo ln -s /opt/apache-maven-3.9.8 /opt/maven
     ```
    The command will:
    * Extract Maven under the /opt directory 
    * Create a symbolic link /opt/maven to that directory


* As you have downloaded pre-compiled Apache Maven files on your system. Now set the environment variables by creating a new file /etc/profile.d/maven.sh.
     ```
     sudo vi /etc/profile.d/maven.sh
     ```


* Add the below content to the file then Save your file and close it.
    ```
     export JAVA_HOME=/usr/lib/jvm/java-11-openjdk-amd64
     export M2_HOME=/opt/maven
     export MAVEN_HOME=/opt/maven
     export PATH=${M2_HOME}/bin:${PATH}
     ```




* Next load the environment variables in the current shell using the following command.
     ```
     source /etc/profile.d/maven.sh
     ```
     
     
* You have successfully installed and configured Apache Maven on your Ubuntu system. You can check the installed Maven version with the following command:
     ```
     mvn -version
     ```
     
     
* Finally, clean up the disk by removing the downloaded archive file.
     ```
     rm -f apache-maven-3.9.8-bin.tar.gz
     ```
     
     
     
    

