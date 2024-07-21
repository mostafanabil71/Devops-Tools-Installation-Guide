## Docker & Docker-Compose Installation on Ubuntu 22.04

This guide details how to install Docker and Docker-Compose on Ubuntu 22.04.


### Step 1: Installing Docker
 * To ensure we get the latest version, we’ll install Docker from the official Docker repository.
 * First, update your existing list of packages
    ```
    sudo apt update
    ```
    
    
* Next, install a few prerequisite packages which let apt use packages over HTTPS:
    ```
    sudo apt install apt-transport-https ca-certificates curl software-properties-common
    ```
    
    
* Then add the GPG key for the official Docker repository to your system:
    ```
    curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg
    ```


* Add the Docker repository to APT sources:
    ```
    echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
    ```


* Update your existing list of packages again for the addition to be recognized:
    ```
    sudo apt update
    ```


* Make sure you are about to install from the Docker repo instead of the default Ubuntu repo:
    ```
    apt-cache policy docker-ce
    ```
    
    
* Notice that docker-ce is not installed, but the candidate for installation is from the Docker repository for Ubuntu 22.04 (jammy).


* Finally, install Docker:
    ```
    sudo apt install docker-ce
    ```


* Docker should now be installed, the daemon started, and the process enabled to start on boot. Check that it’s running:
    ```
    sudo systemctl status docker
    ```
    
### Step2: Executing the Docker Command Without Sudo (Optional)
By default, the docker command can only be run the root user or by a user in the docker group, which is automatically created during Docker’s installation process

* To avoid typing sudo whenever you run the docker command, add your username to the docker group:
    ```
    sudo usermod -aG docker ${USER}
    ```
    
    
* To apply the new group membership, log out of the server and back in, or type the following:
    ```
    su - ${USER}
    ```
* Confirm that your user is now added to the docker group by typing:
    ```
    groups
    ```
    
### Step 3: Download Docker Compose
* Run the following command to download Docker Compose and make this software globally accessible on your system as docker-compose
    ```
    sudo curl -L "https://github.com/docker/compose/releases/download/1.26.0/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
    ```
### Step 4: Set Up Executable Permissions
* Next, set the correct permissions to make sure the docker-compose command is executable:
    ```
    sudo chmod +x /usr/local/bin/docker-compose
    ```


* To verify that the installation was successful, run:
    ```
    docker-compose --version
    ```