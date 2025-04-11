# Project Splunk-ES SIEM for Mimikatz Detection
Welcome to a hands-on project focused on deploying Splunk Enterprise Security (ES) as a Security Information and Event Management (SIEM) solution. It also includes configuring alerts to detect Mimikatz exploit executions on network workstations.
In this case, we are deploying Splunk Enterprise Security (SPLUNK ES) on Ubuntu 22.04. hosted on VMware


## Step 1: Follow best practices

### Create user, directory, and give ownership to the user.
Once the Ubuntu server is up and running. Open the terminal and run the following commands: 
- **Switch to the root with elevated privileges**
  ```bash 
    sudo su
  ```
- **Navigate to the root directory. Create a splunk user and the /opt/splunk directory**
  ```bash 
  #Navigate to the root
  cd
  #Create user
  useradd SPLUNK
  #Create directory
  mkdir /opt/splunk
  ```
- **Give ownership to the SPLUNK user**
  ```bash
  sudo chown -R SPLUNK /opt/splunk
     ```
  ![Image](https://github.com/user-attachments/assets/a3436836-6aaa-406c-af26-74616c5053b2)
  ![Image](https://github.com/user-attachments/assets/082c1a60-9cac-430b-86b8-39ce702bba92)

  ## Step 2: Download and install SPLUNK ES
  ### Access your Splunk account.

   Under Resources, access the free trial and download. Choose the free trial of SPLUNK ES. You can copy the wget command under Linux OS. Another way would be to access your account from the Linux machine and download the .tgz file.
  
     
  
  ![Image](https://github.com/user-attachments/assets/f9ed4308-5cea-4569-8d63-e93f56ab8829)

  ### Download the .tgz file to the /opt directory.

     We will first navigate to the /opt directory, then use the wget command to download the .tgz file in our directory. 
  
   ![Image](https://github.com/user-attachments/assets/237ef338-17e2-4a62-891b-dafa99f016d3)

     Extract the Tar archive to the /opt directory, copy the command, and change the file name to yours. 
  ```bash
     tar xvzf splunk-9.4.0-6b4ebe426ca6-linux-amd64.tgz -C /opt
  ```
Once complete, the /opt/splunk directory will be populated. 
 
  ### Start your Splunk instance.
       Log in as the SPLUNK user and start your Splunk instance.
       ```bash
       #change the SPLUNK user password first
       sudo passwd SPLUNK
       #log in as SPLUNK user
       su SPLUNK
       #start your splunk instance
       /opt/splunk/bin/splunk start --accept-license
       ```

       ![Screenshot 2025-04-10 223939](https://github.com/user-attachments/assets/9360e935-8589-458a-8ead-8cfaa3595540)
