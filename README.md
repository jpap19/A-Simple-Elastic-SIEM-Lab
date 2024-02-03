<h1>A Simple Elastic SIEM Lab</h1>

<h2>Description</h2>
In this activity, we are going to set up a home lab for Elastic Stack Security Information and Event Management (SIEM) using the Elastic Web portal and a Kali Linux VM. 
We will generate security events on the Kali VM, set up an agent to forward data to the SIEM, query and analyze the logs in the SIEM.
<br />

<h2>Resources And Links To Download Required Softwares:</h2>

- <b>Oracle VirtualBox</b> https://www.virtualbox.org/wiki/Downloads
- <b>cloud.elastic</b>     https://cloud.elastic.co/registration
- <b>kali</b>              https://www.kali.org/get-kali/#kali-virtual-machines.
- <b>Basic Linux Knowledge is needed</b>

<h2>Program walk-through:</h2>

<p align="center">
 
 The links provided here above can be used to download required softwares. The implementation will be in done in 6 Steps:

STEP 1: Set up a free Elastic account and Install the Kali VM.

STEP 2: Configure the Elastic Agent on the Linux VM to collect the logs and forward it to the SIEM.

STEP 3: Generate security events on the Kali VM.

STEP 4: Query to find the security events in the Elastic SIEM.

STEP 5: Create a Dashboard to visualize security events.

STEP 6: Create alerts for security events.

<h2>Program walk-through Implementation:</h2>

STEP 1 Set up a free Elastic account and Install the Kali VM:

 
1.1 Set up a free Elastic account: <br/>

Use Elastic Cloud registration link here above to Sign up for a free trial account. Then log in to the Elastic Cloud console, Click on “Start your free trial.”
Click on the “Create Deployment” button and select “Elasticsearch” as the deployment type. Choose a region and deployment size that fits your needs and click on “Create Deployment.”
Wait for the configuration to complete. Once the deployment is ready, click “continue.”

1.1.1 Free Elastic account set up  and Deployment created: <br/>

<img src="https://github.com/jpap19/A-Simple-Elastic-SIEM-Lab/blob/main/Images/FreeAccountCreated.png" height="150%" width="100%" alt="Nessus Essential Home Lab"/>
<br />
<br />
1.2 Installation and setting up of Kali VM: <br/>

Go to the links provided here above, download and install Oracle Virtual Box, then download Kali Linux VM and save in a folder on the computer. virtual box  will be used to setup and run a virtual machine, Kali Linux VM  will be installed on the virtual machine.

Once the installation is complete, log in to the Kali VM using the credentials “kali” for both the username and password.

<img src="https://github.com/jpap19/A-Simple-Elastic-SIEM-Lab/blob/main/Images/KaliSettingUp.png" height="150%" width="150%" alt="Nessus Essential Home Lab"/>
<br />
<br />

STEP 2: Configure the Elastic Agent on the Linux VM to collect the logs and forward it to the SIEM.

An agent is a software program that is installed on a device, such as a server or endpoint, to collect and send data to a centralized system for analysis and monitoring.
In the context of Elastic SIEM, an agent is used to collect and forward security-related events from your endpoints to your Elastic SIEM instance.

To set up the agent to collect logs from your Kali VM and forward them to your Elastic SIEM instance, we will follow these steps:

2.1 Log in to the Elastic SIEM instance and navigate to the Integrations page by: clicking on the 3 horizontal lines from the main menu bar at the top left, then selecting “add Integrations” at the bottom: <br/>

<img src="https://github.com/jpap19/A-Simple-Elastic-SIEM-Lab/blob/main/Images/AddingIntegrations.png" height="150%" width="100%" alt="Nessus Essential Home Lab"/>
<br />
<br />

2.2 Search for “Elastic Defend” and click on it to open the integration page: <br/>

<img src="https://github.com/jpap19/A-Simple-Elastic-SIEM-Lab/blob/main/Images/ElasticDefend.png" height="150%" width="150%" alt="Nessus Essential Home Lab"/>
<br />
<br />

2.3 Click on “Add Elastic Defend” and follow the instructions provided on the integration page to install the agent on your Kali VM.: <br/>

<img src="https://github.com/jpap19/A-Simple-Elastic-SIEM-Lab/blob/main/Images/ElasticAgentInstallation.png" height="150%" width="100%" alt="Nessus Essential Home Lab"/>
<br />
<br />

<img src="https://github.com/jpap19/A-Simple-Elastic-SIEM-Lab/blob/main/Images/ElasticAgentInstallation2.png" height="150%" width="100%" alt="Nessus Essential Home Lab"/>
<br />
<br />

2.4 Copy the command highlighted here above and Paste into the Kali terminal (command line).: <br/>

<img src="https://github.com/jpap19/A-Simple-Elastic-SIEM-Lab/blob/main/Images/CommandPastedInKali.png" height="150%" width="150%" alt="Nessus Essential Home Lab"/>
<br />
<br />

2.5 Once the agent is installed, which can take a few minutes, you’ll see a message that says “Elastic Agent has been successfully installed.” 
It will automatically start collecting and forwarding logs to the Elastic SIEM instance, although it might take a few minutes for the logs to appear in the SIEM.: <br/>

<img src="https://github.com/jpap19/A-Simple-Elastic-SIEM-Lab/blob/main/Images/ElasticAgentSuccessfullInstalled.png" height="150%" width="150%" alt="Nessus Essential Home Lab"/>
<br />
<br />

2.6 We can verify that the agent has been installed correctly by running this command: sudo systemctl status elastic-agent.service: <br/>

<img src="https://github.com/jpap19/A-Simple-Elastic-SIEM-Lab/blob/main/Images/ElasticAgentInstallationVerification.png" height="150%" width="100%" alt="Nessus Essential Home Lab"/>
<br />
<br />

STEP 3: Generating Security Events on the Kali VM: <br/>

To verify that the agent is working correctly, we can generate some security-related events on Kali VM. To do this, we can use a tool like Nmap. Nmap (Network Mapper) is a free and open-source utility used for network exploration, management, and security auditing. It is designed to discover hosts and services on a computer network, thus creating a “map” of the network. Nmap can be used to scan hosts for open ports, determine the operating system and software running on the target system, and gather other information about the network. Nmap already comes preinstalled in Kali. Open a new Terminal and run this command to install it using the command: sudo apt-get install nmap. Then Run a scan on Kali machine by running the command: sudo nmap <vm-ip>. we can also run a scan of your host machine if Kali VM is placed on a “bridged” network.

3.1 An Nmap scan of my host machine.: <br/>

<img src="https://github.com/jpap19/A-Simple-Elastic-SIEM-Lab/blob/main/Images/MoreNmapScans2.png" height="150%" width="100%" alt="Nessus Essential Home Lab"/>
<br />
<br />

This scan generates several security events, such as the detection of open ports and the identification of services running on those ports.”

3.2 Run a few more Nmap scans (“nmap -sS <ip address>”, “nmap -sT <ip address>”, “nmap -p- <ip address>”etc.. : <br/>

<img src="https://github.com/jpap19/A-Simple-Elastic-SIEM-Lab/blob/main/Images/PingingGoogle.png" height="150%" width="150%" alt="Nessus Essential Home Lab"/>
<br />
<br />

<img src="https://github.com/jpap19/A-Simple-Elastic-SIEM-Lab/blob/main/Images/nmap%20scan4.png" height="150%" width="150%" alt="Nessus Essential Home Lab"/>
<br />
<br />

3.3 Confirming the agent is sending data to the SIEM : <br/>

<img src="https://github.com/jpap19/A-Simple-Elastic-SIEM-Lab/blob/main/Images/ConfirmIncomingData.png" height="150%" width="150%" alt="Nessus Essential Home Lab"/>
<br />
<br />

STEP 4: Query to find the security events in the Elastic SIEM.

Now that we have forwarded data from the Kali VM to the SIEM, we can start querying and analyzing the logs in the SIEM. To do this, we will follow these steps:
Inside the Elastic Deployment, click on the menu icon at the top-left with the three horizontal lines and then click on the “Logs” tab under “Observability” to view the logs from the Kali VM.: <br/>

4.1 The “Logs” tab under “Observability”: <br/>
<img src="https://github.com/jpap19/A-Simple-Elastic-SIEM-Lab/blob/main/Images/Logs.png" height="70%" width="100%" alt="Nessus Essential Home Lab"/>
<br />
<br />

In the search bar, enter a search query to filter the logs. For example, to search for all logs related to Nmap scans, enter the query: event.action:
“nmap_scan” or process.args: “sudo”. Click on the “Search” button to execute the search query. it can sometimes take a while for the events to populate and show up on the SIEM, so this query might not work right away.
The results of the search query will be displayed in the table below. We can click on the three dots next to each event to view more details.

4.2 Results of the Query to find the security events in the Elastic SIEM : <br/>

<img src="https://github.com/jpap19/A-Simple-Elastic-SIEM-Lab/blob/main/Images/QuerryResults.png height="150%" width="150%" alt="Nessus Essential Home Lab"/>
<br />
<br />

<img src="https://github.com/jpap19/A-Simple-Elastic-SIEM-Lab/blob/main/Images/QuerryResults2.png" height="150%" width="150%" alt="Nessus Essential Home Lab"/>
<br />
<br />

STEP 5: Create a Dashboard to visualize security events.

We can also use the visualizations and dashboards in the SIEM app to analyze the logs and identify patterns or anomalies in the data. For example, we can create a simple dashboard that shows a count of security events over time.
Here’s how you can do that: Navigate to the Elastic web portal, Click on the menu icon on the top-left, then under “Analytics,” click on “Dashboards.”: <br/>

5.1 Elastic web portal Dashboards view under “Analytics: <br/>
<img src="https://github.com/jpap19/A-Simple-Elastic-SIEM-Lab/blob/main/Images/AnalyticsDashboardView.png" height="80%" width="100%" alt="Nessus Essential Home Lab"/>
<br />
<br />

We can then Click on the “Create dashboard” button on the top right to create a new dashboard. Click on the “Create Visualization” button to add a new visualization to the dashboard.
Select “Area” or “Line” as the visualization type, depending on our preference. This will create a chart that shows the count of events over time.

5.2 Elastic web portal visualization type interface : <br/>

In the “Metrics” section of the visualization editor on the right, select “Count” as the vertical field type and “Timestamp” for the horizontal field. This will show the count of events over time.

5.3 Elastic web portal “Metrics” section of the visualization type interface : <br/>

<img src="https://github.com/jpap19/A-Simple-Elastic-SIEM-Lab/blob/main/Images/VisualizationType.png" height="150%" width="150%" alt="Nessus Essential Home Lab"/>
<br />
<br />

5.4 HORIZONTAL AXIS - Elastic web portal “Metrics” section of the visualization type interface : <br/>

<img src="https://github.com/jpap19/A-Simple-Elastic-SIEM-Lab/blob/main/Images/ElasticVisualizationAreaHozontalVerticasAxis.png" height="150%" width="150%" alt="Nessus Essential Home Lab"/>
<br />
<br />

5.5 VERTICAL AXIX - Elastic web portal “Metrics” section of the visualization type interface : <br/>

<img src="https://github.com/jpap19/A-Simple-Elastic-SIEM-Lab/blob/main/Images/ElasticVisualizationAreaHozontalVerticasAxis2.png" height="150%" width="150%" alt="Nessus Essential Home Lab"/>
<br />
<br />

5.6 Click on the “Save” button to save the visualization and then complete the rest of the settings : <br/>

<img src="https://github.com/jpap19/A-Simple-Elastic-SIEM-Lab/blob/main/Images/VisualizationEvents.png" height="150%" width="150%" alt="Nessus Essential Home Lab"/>
<br />
<br />

STEP 6: Create alerts for security events.

In a SIEM, alerts are a crucial feature for detecting security incidents and responding to them in a timely manner. Alerts are created based on predefined rules or custom queries, and can be configured to trigger specific actions when certain conditions are met. In this task, we will be creating an alert in the Elastic SIEM instance to detect Nmap scans. The purpose is to monitor logs for Nmap scan events and then notify us when they are detected.
Here is how we can do that: Click on the menu icon on the top-left, then under “Security,” click on “Alerts. ”Click on “Manage rules” at the top right.

6.1 Security Alerts rules Creation: <br/>
<img src="https://github.com/jpap19/A-Simple-Elastic-SIEM-Lab/blob/main/Images/CustomsQuerry.png" height="150%" width="100%" alt="Nessus Essential Home Lab"/>
<br />
<br />

 Click on the “Create new rule” button at the top right. Under the “Define rule” section, select the “Custom query” option from the dropdown menu. 
 Under “Custom query,” set the conditions for the rule. we are going to  use the following query (event.action: "nmap scan") to detect Nmap scan events.

This query will match all events with the action “nmap_scan.” Then click “Continue.” Under the “About rule” section, give your rule a name and a description (Nmap Scan Detection).
Set the severity level for the alert, which can help you prioritize alerts based on their importance. Keep all the other default settings under “Schedule rule” and click “Continue.”

6.3 Creating rules to detect Nmap scan events - Beguining step : <br/>

<img src="https://github.com/jpap19/A-Simple-Elastic-SIEM-Lab/blob/main/Images/CreatingRule2.png" height="150%" width="150%" alt="Nessus Essential Home Lab"/>
<br />
<br />
 
In the “Actions” section, select the action to take when the rule is triggered. Choose to send an email notification, create a Slack message, or trigger a custom webhook.
Finally, click the “Create and enable rule” button to create the alert.

6.4 Creating rules to detect Nmap scan events - Final step : <br/>

<img src="https://github.com/jpap19/A-Simple-Elastic-SIEM-Lab/blob/main/Images/CreatingRule3.png" height="150%" width="150%" alt="Nessus Essential Home Lab"/>
<br />
<br />

CONCLUSION: <br/>

In this activity, we have set up a home lab using Elastic SIEM and a Kali VM. We forwarded data from the Kali VM to the SIEM using the Elastic Beats agent, generated security events on the Kali VM using Nmap, and queried and analyzed the logs in the SIEM using the Elastic web interface. We also created a dashboard to visualize security events and then created an alert to detect security events.


<!--
 ```diff
- text in red
+ text in green
! text in orange
# text in gray
@@ text in purple (and bold)@@
```
--!>
