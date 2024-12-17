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
 2. Set up a new virtual machine using the Kali VM file on your chosen virtualization software, like VirtualBox or VMware.
 </br>
 </br>
 <img src="https://imgur.com/8JTfmyQ.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
 </br>
 </br>
 3. Start the VM and follow the on-screen prompts to install Kali.
 </br>
 </br>
 4. After the installation finishes, access the Kali VM by entering “kali” for both the username and password..
 </br>
 </br>

<p align="center"> 
Task 3: Setting up the Agent to Collect Logs
</br>
</br>
1. Sign in to your Elastic SIEM instance and go to the Integrations page by clicking on the main menu bar in Kibana at the top left and choosing “Integrations” from the list at the bottom.
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
3. Select “Install Elastic Defend” and follow the guidance provided on the integration page to set up the agent on your Kali VM.
</br>
</br>
<img src="https://imgur.com/FjP4QAa.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</br>
</br>
4. Paste that command into the Kali terminal (command line).
<img src="https://imgur.com/nXOx0qW.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</br>
</br>
5. After the agent installation is complete, which may take several minutes, you will receive a notification stating, “Elastic Agent has been successfully installed.” The agent will begin collecting and sending logs to your Elastic SIEM instance, but please allow some time for the logs to show up in the SIEM.
</br>
</br>
<img src="https://imgur.com/F4M3W2p.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<p align="center"> 
Task 4: Generating Security Events on the Kali VM
</br>
</br>
If you are not using Kali, install Nmap on your Linux VM. Open a new Terminal and execute the following command to install it: `sudo apt-get install nmap`. If you are using Kali, Nmap is already included by default.
<br/>
 </br>
2. Perform a scan on the Kali machine by executing the command: `sudo nmap <vm-ip>`. Additionally, if your Kali VM is configured on a “bridged” network, you can also scan your host machine.
 <img src="https://imgur.com/G5TBYLL.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
3.This scan produces various security events, including the detection of open ports and the identification of services associated with those ports. Execute additional Nmap scans using commands like `nmap -sS <ip address>`, `nmap -sT <ip address>`, and `nmap -p- <ip address>`, among others.
</br>
</br>
<img src="https://imgur.com/oBAyRmQ.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</br>
</br>
Task 5: Querying for Security Events in the Elastic SIEM
</br>
</br>
1.Within your Elastic Deployment, click on the menu icon at the top left, which features three horizontal lines, and then select the “Logs” tab found under “Observability” to access the logs from the Kali VM.
</br>
</br>
<img src="https://imgur.com/Y4ZPFqj.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</br>
</br>
2. In the search bar, input a query to filter the logs. For instance, to find all logs associated with Nmap scans, you can use the query: `event.action: "nmap_scan"` or `process.args: "sudo"`.
</br>
</br>
3. Click on the “Search” button to execute the search query.
</br>
</br>
4. The results of your search query will appear in the table below. You can click on the three dots next to each event to access additional details.
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
2. Click on the menu icon at the top left, then under “Analytics,” select “Dashboards.”
</br>
</br>
<img src="https://imgur.com/5h4bsZ3.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
</br>
3. Click the “Create dashboard” button located at the top right to initiate the creation of a new dashboard.
</br>
</br>
4. Select the “Create Visualization” button to add a new visualization to your dashboard.
</br>
</br>
5. Select “Area” or “Line” as the visualization type, depending on your preference. This will create a chart that shows the count of events over time.
</br>
</br>
<img src="https://imgur.com/FsxWeoM.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<p align="center"> 
</br>
</br>
6. In the “Metrics” section of the visualization editor on the right, choose “Count” as the vertical field type and select “Timestamp” for the horizontal field. This setup will display the number of events over time.
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
5. In the “Custom query” section, specify the conditions for the rule. You can utilize the following query to identify Nmap scan events.
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
7. Assign a severity level to the alert to help prioritize alerts according to their significance. Leave all other default settings under “Schedule rule” unchanged and click “Continue.”
</br>
</br>
<img src="https://imgur.com/XV4Vgkz.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</br>
</br>
8. In the “Actions” section, choose the action you wish to execute when the rule is triggered. Options include sending an email notification, creating a Slack message, or initiating a custom webhook.
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
