****LAB STILL IN PROGRESS****

This write-up continues my learning of the Splunk Platform.I will be setting up my own SOC lab and learning about the Splunk installation process and installing it on a Virtual Machine (Linux Ubuntu and Windows). 

Objectives:

In this lab, I will use two VMS, both Linux and Windows to install Splunk on the machines and integrate vital log sources through listening ports and installing forwarders.
Note: From my previous labs, a forwarder in splunk forwards the data it recieves from network traffic to the indexer so that this information can get ingested and turned into information we can use. A listening port is a port that waits to recieve network request from a UDP or TCP port. 


Linux Lab

Install Splunk on Ubuntu Server.
Install and integrate Universal Forwarder.
Collecting Logs from important logs sources/files like syslog, auth.log, audited, etc.


Windows Lab

Install Splunk on Windows Machine.
Install and Integrate the Universal Forwarder.
Integrating and monitoring Coffely.THM's weblogs.
Integrating Windows Event Logs.

Splunk Installation 

Splunk is pretty straight forward to install, I will have to go to the official Splunk website and install the application on the desired machine, which will be using the Linux OS. Splunk is already installed for the sake of this lab, but I need to unzip it. It is located in the downloads folder path /Downloads/Splunk. I run Sudo Su to make myself the Root User (Admin) and I use the "ls"(List) command to navigate to the folder where Splunk is located. I now have to move it to the /opt directory, which is where additional software is stored that isn't originally part of the linux OS download. I do this by utilizing the "mv"(Move) command. 

Now I need to run the Splunk license. To do this, I used the "cd"(change directory) command to make my way to the splunk folder and ran ./splunk start --accept-license. After this, it prompted me to create an admin account user name and password, which for learning purposes will be 1234 and 12345678. I now have splunk fully installed and ready to start using!

Note: To reverse the "Sudo Su" command in Linux, put in the "Exit command".

IMPORTANT NOTE: Originally the instructions where a little confusing since it only showed the application installing after the command tar xvzf splunk_installer.tgz. After a little research and going back to previous labs, I had to utilize the "cd" command to go to Downloads>Splunk and then utilize the "ls" command to show me the splunk installer file. Then, after I ran the xvzf splunk_installer.tgz command it installed as intended.  

Commands

IMPORTANT COMMANDS:
Splunk Start-This command is used to start the Splunk server. This command starts all the necessary Splunk processes and enables the server to accept incoming data. If the server is already running, this command will have no effect.
Splunk Stop-This command is used to stop the Splunk server. This command stops all the running Splunk processes and disables the server from accepting incoming data. If the server is not running, this command will have no effect.
Splunk Restart-This command is used to restart the Splunk server. This command stops all the running Splunk processes and then starts them again. This is useful when changes have been made to the Splunk configuration files or when the server needs to be restarted for any other reason.
Splunk Add Oneshot-This command is used to add a single event to the Splunk index. This is useful for testing purposes or for adding individual events that may not be part of a larger data stream.
Splunk Search- This command is used to search for data in the Splunk index. This command can be used to search for specific events, as well as to perform more complex searches using Splunk's search language.
***Splunk Help- This is the most important, as it lists all of the help options. 

Splunk Data Ingestion

IMPORTANT: There are two primary types of forwarders in Splunk, and each one has a different use case. These are Heavy Forwarders and Universal Forwarders.

Heavy Forwarders

Heavy forwarders are used when we need to apply a filter, analyze or make changes to the logs at the source before forwarding it to the destination. I will be using the universal forwarder instead, however.

Universal Forwarders

It is a lightweight agent that gets installed on the target host, and its main purpose is to get the logs and send them to the Splunk instance or another forwarder without applying any filters or indexing. 

Note: The universal forwarder has to be downloaded separately and has to be enabled before use. I will be using a universal forwarder to ingest logs.     

After installing the forwarder with the command  tar xvzf splunkforwarder.tgz, then I move it to the opt location by using the command mv splunkforwarder /opt/ . Now im going to run the Splunk forwarder instance and give it credentials.Now that the forwarder is installed we have tell it what data to send and where to send it to.

Note: Splunk forwarder runs on port 8089 by default. 

Configuring the Forwarder on Linux







