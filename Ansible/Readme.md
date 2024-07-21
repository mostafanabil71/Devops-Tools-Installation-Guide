## Ansible Installation on Ubuntu 22.04
This guide details how to install Ansible and configure it on Ubuntu 22.04.

### Step 1: Installing Ansible
* From your control node, run the following command to include the official project’s PPA (personal package archive) in your system’s list of sources:
    ```
    sudo apt-add-repository ppa:ansible/ansible
    ```
* Press ENTER when prompted to accept the PPA addition.
* Next, refresh your system’s package index so that it is aware of the packages available in the newly included PPA:
    ```
    sudo apt update
    ```
* Following this update, you can install the Ansible software with:
    ```
    sudo apt install ansible
    ```


* Your Ansible control node now has all of the software required to administer your hosts. Next, we will go over how to add your hosts to the control node’s inventory file so that it can control them.


### Step 2: Setting Up the Inventory File
* The inventory file contains information about the hosts you’ll manage with Ansible.
* Upon installation, Ansible creates a default inventory file known as the hosts file that is typically located at /etc/ansible/hosts.
* Ansible also gives you the flexibility to create a custom inventory file at your preferred location on your control node to suit your preferences.
* In this case, you’ll need to provide the path to your custom inventory file with the -i parameter when running Ansible commands and playbooks.
* Using per-project inventory files is a good practice to minimize the risk of running a playbook on the wrong group of servers.


* To edit the contents of your default Ansible inventory, open the /etc/ansible/hosts file using your text editor of choice, on your Ansible control node:
    ```
    sudo nano /etc/ansible/hosts
    ```


* Whenever you want to check your inventory, you can run:
    ```
    ansible-inventory --list -y
    ```

    
    
    
    
    




