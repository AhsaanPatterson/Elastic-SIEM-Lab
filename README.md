<h1>Elastic SIEM Lab</h1>


<h2>Description</h2>
In this guide, I'll outline the process for establishing a home lab for Elastic Stack Security Information and Event Management (SIEM) utilizing the Elastic Web portal alongside a Kali Linux virtual machine (VM). I discovered how to create security events within the Kali VM, configure an agent to send data to the SIEM, and perform queries and analysis of the logs in the SIEM. 

<h2>Languages and Utilities Used</h2>

- <b>Kali Linux</b>

<h2>Environments Used </h2>

- <b>WVirtual Box</b> 


<p align="center">
Elastic SIEM LAB with Kali Linux Virtual Box

<p align="center"> 
Task 1: Set up an Elastic Account
</br>
1: Sign up for a free trial to use Elastic Cloud at
</br>
</br>
https://cloud.elastic.co/registration
<br />
</br>
2. Once you have an Elastic account, log in to the Elastic Cloud console at
<br />
</br>
https://cloud.elastic.co.
</br>
</br>
3. Click on “Start your free trial.”
</br>
</br>
4. Click on the “Create Deployment” button and select “Elasticsearch” as the deployment type.
</br>
</br>
5. Choose a region and deployment size that fits your needs and click on “Create Deployment.”
</br>
</br>
6. Wait for the configuration to complete.
</br>
</br>
7. Once the deployment is ready, click “continue.”
</br>
</br>
<p align="center"> 
Task 2: Setting up the Linux VM
</br>
</br>
1. Download the Kali Linux VM from the official Kali website at
 <br/>
 https://www.kali.org/get-kali/#kali-virtual-machines
 </br>
 </br>
 2. Create a new VM with the Kali VM file in your preferred virtualization platform, such as VirtualBox or VMware.
 </br>
 </br>
 3. Start the VM and follow the on-screen prompts to install Kali.
 </br>
 </br>
 4. Once the installation is complete, log in to the Kali VM using the credentials “kali” for both the username and password.
 </br>
 </br>

<p align="center"> 
Task 3: Setting up the Agent to Collect Logs
</br>
</br>
1. Log in to your Elastic SIEM instance and navigate to the Integrations page by: clicking on the Kibana main menu bar at the top left, then selecting “Integrations” at the bottom.
<br/>
</br>
<img src="https://imgur.com/5VorLIh.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
2. Search for “Elastic Defend” and click on it to open the integration page.
</br>
</br>
<img src="https://imgur.com/UGAmjKe.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</br>
</br>
3. Click on “Install Elastic Defend” and follow the instructions provided on the integration page to install the agent on your Kali VM.
</br>
</br>
<img src="https://imgur.com/FjP4QAa.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</br>
</br>
4. Paste that command into the Kali terminal (command line).
<img src="https://imgur.com/nXOx0qW.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</br>
</br>
5. Once the agent is installed, which can take a few minutes, you’ll see a message that says “Elastic Agent has been successfully installed.” It will automatically start collecting and forwarding logs to your Elastic SIEM instance, although it might take a few minutes for the logs to appear in the SIEM.
</br>
</br>
<img src="https://imgur.com/F4M3W2p.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<p align="center"> 
Task 4: Generating Security Events on the Kali VM
</br>
</br>

1. Install Nmap on the Linux VM if you’re not using Kali, Nmap already comes preinstalled in Kali. Open a new Terminal and run this command to install it: sudo apt-get install nmap.
 <br/>
 </br>
 2. Run a scan on Kali machine by running the command: sudo nmap <vm-ip>. You can also run a scan of your host machine if you place your Kali VM on a “bridged” network.
<img src="https://imgur.com/G5TBYLL.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
3. This scan generates several security events, such as the detection of open ports and the identification of services running on those ports. Run a few more Nmap scans (“nmap -sS <ip address>”, “nmap -sT <ip address>”, “nmap -p- <ip address>”etc..”
</br>
</br>
<img src="https://imgur.com/oBAyRmQ.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</br>
</br>
Task 5: Querying for Security Events in the Elastic SIEM
</br>
</br>
1. Inside your Elastic Deployment, click on the menu icon at the top-left with the three horizontal lines and then click on the “Logs” tab under “Observability” to view the logs from the Kali VM.
</br>
</br>
<img src="https://imgur.com/Y4ZPFqj.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</br>
</br>
2. In the search bar, enter a search query to filter the logs. For example, to search for all logs related to Nmap scans, enter the query: event.action:
“nmap_scan” or process.args: “sudo”.
</br>
</br>
3. Click on the “Search” button to execute the search query.
</br>
</br>
4. The results of the search query will be displayed in the table below. You can click on the three dots next to each event to view more details.
</br>
</br>
<img src="https://imgur.com/G4KDvfN.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<p align="center">
</br>
</br>
Task 6: Create a Dashboard to Visualize the Events
</br>
</br>
1.Navigate to the Elastic web portal at https://cloud.elastic.co/.
</br>
</br>
2. Click on the menu icon on the top-left, then under “Analytics,” click on “Dashboards.”
</br>
</br>
<img src="https://imgur.com/5h4bsZ3.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
</br>
3. Click on the “Create dashboard” button on the top right to create a new dashboard.
</br>
</br>
4. Click on the “Create Visualization” button to add a new visualization to the dashboard.
</br>
</br>
5. Select “Area” or “Line” as the visualization type, depending on your preference. This will create a chart that shows the count of events over time.
</br>
</br>
<img src="https://imgur.com/FsxWeoM.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<p align="center"> 
</br>
</br>
6. In the “Metrics” section of the visualization editor on the right, select “Count” as the vertical field type and “Timestamp” for the horizontal field. This will show the count of events over time.
</br>
</br>
<img src="https://imgur.com/jJkQESe.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://imgur.com/HhgM8dj.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://imgur.com/8gA7fCu.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br/>
</br>
<p align="center"> 
7. Click on the “Save” button to save the visualization and then complete the rest of the settings.
</br>
</br>
<img src="https://imgur.com/43lSLCe.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</br>
</br>
Task 7: Create an Alert
<br/>
</br>
1. Click on the menu icon on the top-left, then under “Security,” click on “Alerts.”
</br>
</br>
2. Click on “Manage rules” at the top right.
<img src="https://imgur.com/1569AYB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
3. Click on the “Create new rule” button at the top right.
</br>
</br>
4. Under the “Define rule” section, select the “Custom query” option from the dropdown menu.
</br>
</br>
5. Under “Custom query,” set the conditions for the rule. You can use the following query to detect Nmap scan events.
</br>
</br>
<img src="https://imgur.com/6OFw2yM.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</br>
</br>
This query will match all events with the action “nmap_scan.” Then click “Continue.”
</br>
</br>
6. Under the “About rule” section, give your rule a name and a description (Nmap Scan Detection).
</br>
</br>
7. Set the severity level for the alert, which can help you prioritize alerts based on their importance. Keep all the other default settings under “Schedule rule” and click “Continue.”
</br>
</br>
<img src="https://imgur.com/XV4Vgkz.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</br>
</br>
8. In the “Actions” section, select the action you want to take when the rule is triggered. You can choose to send an email notification, create a Slack message, or trigger a custom webhook.
</br>
</br>
9. Finally, click the “Create and enable rule” button to create the alert.
</br>
</br>
<img src="https://imgur.com/MVWWDD0.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<p align="center"> 
</p>

<!--
 ```diff
- text in red
+ text in green
! text in orange
# text in gray
@@ text in purple (and bold)@@
```
--!>
