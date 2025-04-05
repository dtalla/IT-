# Project Splunk-ES SIEM for Mimikatz Detection
Welcome to a hands-on project focused on deploying Splunk Enterprise Security (ES) as a Security Information and Event Management (SIEM) solution. It also includes configuring alerts to detect Mimikatz exploit executions on network workstations.
In this case, we are deploying Splunk Enterprise Security (SPLUNK ES) on Ubuntu 22.04. hosted on VMware


## Step 1: Follow best practices

### Create user and directory.
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
