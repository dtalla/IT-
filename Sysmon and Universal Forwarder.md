# Install Sysmon and Splunk Universal Forwarder.
  Installing Sysmon on an endpoint enhances security monitoring and forensic analysis by providing detailed system activity logs.

## Step 1: Install Sysmon on my Virtual Machine
   On the browser of my VM, I navigate to https://learn.microsoft.com/en-us/sysinternals/downloads/sysmon and download and start the download. 

   Then navigate to this directory to download the configuration file https://github.com/olafhartong/sysmon-modular/blob/master/sysmonconfig-excludes-only.xml

   ![Image](https://github.com/user-attachments/assets/64626635-fc65-40f8-8e78-a847a97fffbc)

  Unzip the Symon folder, then copy the configuration file to the Sysmon folder
 Open the command prompt as an administrator and run the following command:

- **Navigate to the directory and initiate the installation**
  ```bash 
    cd  $FILEPATH$
    Sysmon64.exe -accepteula -i sysmonconfig.xml
  ```


The installation is done



## Step 2: Install The Splunk Universal Forwarder


The Splunk Universal Forwarder is a lightweight agent designed to collect and forward logs and machine data to a Splunk indexer for processing and analysis.

Open the browser on your VM and navigate to your Splunk account. Navigate to resources, free trials and downloads, get free download of the universal forwarder. Download the one corresponding to your vm OS.

Please go ahead and execute the .exe file in the downloads folder. Follow the installation wizard.  

Open Services by searching "service" and run as an administrator.

Look for the Splunk Forwarder Service, open the properties, then the log on tier and make sure the log on as is set on " Local System account" 

![Image](https://github.com/user-attachments/assets/79f7a30d-2297-40d0-8df4-6d243f687a80)


Then restart the service. 

## Step 3: Set up the Splunk ES


**We need to set up our Splunk instance to receive data at port 9997**
Open your Splunk instance, under settings, look for "Forwarding and receiving" . Click " Add new " under "Receive data" and add port 9997. 

![Image](https://github.com/user-attachments/assets/d7cb4042-16de-4d92-bf16-35b12255aee8)

**Create the Index**
    Add the index assigned to receive data coming from our endpoint. Let's call it end-user
Under Settings, search for "index". Then click on "New Index" and create the "end-user" index.

![Image](https://github.com/user-attachments/assets/5b99a6d9-7d94-497d-991e-ae556e4f95a7)

## Step 3: Set up .conf file



In Splunk, .conf files are configuration files used to define settings for data inputs, indexing, searching, and app behavior. They allow you to customize Splunk’s functionality without needing a graphical interface.

Use this sample of inputs.conf on our VM to specify which type of log we want from the end-point and in which index it will be forwarded. 

### Splunk Inputs.conf File

[WinEventLog://Application]

index = end-user

disabled = false


[WinEventLog://Security]

index = end-user

disabled = false


[WinEventLog://System]

index = end-user

disabled = false


[WinEventLog://Microsoft-Windows-Sysmon/Operational]

index = end-user

disabled = false

renderXml = true

source = XmlWinEventLog:Microsoft-Windows-Sysmon/Operational






 I would suggest copying and pasting into Notepad on our VM. Then change the file extension from .txt to .conf. You can do that by using "View" on File Explorer. Then, "Show Extension", rename the file with the .conf extension 

 Copy the inputs.conf file to the directory C:\Program Files\SplunkUniversalForwarder\etc\system\local 

 ![Image](https://github.com/user-attachments/assets/4f01bfd6-f4f3-46c3-a613-936f6dbc10eb)


 Double check the outputs.conf file and make sure it has your splunk instance IP andress or hostname with the port 9997

 ### Splunk outputs.conf File

[tcpout]
defaultGroup = default-autolb-group

[tcpout:default-autolb-group]
server = [Splunk instance IP]:9997

[tcpout-server://[Splunk instance IP]:9997]



Go ahead and restart the Splunk Forwarder service. 

Back on our splunk instance, open search and reporting. Execute the following search on a 5 min time range 

``
index=="end-user"
``


![Image](https://github.com/user-attachments/assets/17d985b3-9103-4029-b527-aba19537c28c)



