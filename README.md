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
