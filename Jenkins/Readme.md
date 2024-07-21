## Jenkins Installation on Ubuntu 22.04
This guide details how to install and configure Jenkins, a CI/CD automation tool, on Ubuntu 22.04.

### Prerequisites
* Ubuntu 22.04 system
* Administrator privileges
* Terminal window/command line
* Java 8 or 11 installed


### Step 1: Install Java
Jenkins requires the Java Runtime Environment (JRE). This guide uses OpenJDK for the Java environment. OpenJDK is a Development Kit and includes the Java Runtime Environment.

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

##### Step 2: Add Jenkins Repository
* It is recommended to install Jenkins using the project-maintained repository, rather than from the default Ubuntu repository.
* The reason for that is that the Jenkins version in the default Ubuntu repository might not be the latest available version, which means it could lack the latest features and bug fixes.
* To add the Jenkins repository to your Ubuntu system import the GPG key.
* The GPG key verifies package integrity but there is no output. Run:

1. Import GPG key:
     ```
     curl -fsSL https://pkg.jenkins.io/debian-stable/jenkins.io-2023.key | sudo tee \
     /usr/share/keyrings/jenkins-keyring.asc > /dev/null
     ```
2. Add Jenkins repository:
     ```
     echo deb [signed-by=/usr/share/keyrings/jenkins-keyring.asc] \
     https://pkg.jenkins.io/debian-stable binary/ | sudo tee \
     /etc/apt/sources.list.d/jenkins.list > /dev/null
     ```

##### Step 3: Install Jenkins

1. Update the system repository one more time.
     ```
     sudo apt update
     ```
2. Install Jenkins by running:
     ```
     sudo apt install jenkins -y
     ```
3.  Check if Jenkins is installed and running, by running the following command
    and after verifying Jenkins status, now exit the status screen by pressing Ctrl+Z.
     ```
     sudo systemctl status jenkins
     ```

    

##### Step 4: Modify Firewall (UFW)
* Allow Jenkins to communicate by setting up the default UFW firewall to allow traffic on port 8080 (Jenkins default):

1. If you haven't configured the UFW firewall yet, Please enable it first
     ```
     sudo ufw enable
     ```


2. Open port 8080 on UFW by running the following commands:
     ```
     sudo ufw allow 8080
     sudo ufw status
     ```

##### Step 5: Set up Jenkins
1. Access Jenkins web interface: Open a web browser, and navigate to your server's IP address.
     ```
    http://<server_ip_address_or_domain>:8080
    ```


2. Replace <server_ip_address_or_domain> with your server's actual IP or domain name.
3. A page opens prompting you to Unlock Jenkins.
4. Obtain the required administrator password by using the following command
    ```
    sudo cat /var/lib/jenkins/secrets/initialAdminPassword
    ```

 
5. Copy the displayed alphanumeric code and paste it into into the "Administrator password" field and click "Continue".
6. The setup prompts to either Install suggested plugins or Select plugins to install. lets choose for simplicity install the suggested plugins .
7. The next step is to the Create First Admin User. Enter the credentials you want to use for your Jenkins administrator, then click Save and Continue
8. The next step is to configure instance (optional): Confirm the preferred network address for your Jenkins installation. Click "Save and Finish".
9. Start using Jenkins: You should see a "Jenkins is ready!" message. Click "Start using Jenkins" to access the dashboard.

Congratulations! You now have a functional Jenkins installation on Ubuntu 22.04.



