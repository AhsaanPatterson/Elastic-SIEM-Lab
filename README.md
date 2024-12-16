<h1>Elastic SIEM Lab</h1>


<h2>Description</h2>
In this guide, I'll outline the process for establishing a home lab for Elastic Stack Security Information and Event Management (SIEM) utilizing the Elastic Web portal alongside a Kali Linux virtual machine (VM). I discovered how to create security events within the Kali VM, configure an agent to send data to the SIEM, and perform queries and analysis of the logs in the SIEM. 

<h2>Languages and Utilities Used</h2>

- <b>Virtual Box</b> 
- <b>Kali Linux</b>

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
Step 4: Define Constants and Hook Variables
</br>
Inside the Program class, declare necessary constants and variable that will be used for setting the keyboard hook:
 <br/>
<img src="https://imgur.com/cfxennm.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<p align="center"> 
Step 5: Implement the Main Method
</br>
Create the Main method where you'll set the hook and run the application:
<img src="https://imgur.com/rjtUNV8.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<p align="center"> 
Step 6: Create Delegate for Keyboard Callbacks
</br>
Define a delegate for the keyboard hook procedure
<br/>
<img src="https://imgur.com/L0JMZGd.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<p align="center"> 
Step 7. Implement the Hook Callback Method
</br>
Create the HookCallback method to handle the key events:
<br/>
<img src="https://imgur.com/9UrKzC6.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<p align="center"> 
Step 8: Write Logic to Handle Different Keys
</br>
Inside the HookCallback, implement the logic to log specific keys (like OemPeriod, Oemcomma, Space, etc.) to a text file:
<br/>
<img src="https://imgur.com/nkYFdLX.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br/>
<p align="center"> 
Step 9: Set the Low-Level Keyboard Hook
</br>
Implement the SetHook method to set up the keyboard hook
<br/>
<img src="https://imgur.com/R0iJVMQ.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>

<p align="center"> 
Step 10: Import Windows API Functions
</br>
Below your class definition, use [DllImport] to import required functions from the Windows API
<br/>
 <img src="https://imgur.com/gVoveGi.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>

<p align="center"> 
Step 11: Compile and Run the Program
</br>
Save your code and compile the project.
Run the program, and it should start logging keystrokes to C:\ProgramData\mylog.txt.
Do not run the program on your home pc, please use a virtual lab when running
</br>
</br>
Important Notes:
 <br/>
 <b>Ethical Considerations</b>: Keyloggers can be misused for unethical purposes. Ensure you have permission to log keystrokes and comply with applicable laws.
 <br/>
 <b>Administrative Privileges</b>: You may need to run the application with administrative privileges, depending on the system settings.
 <br/>
</br>
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
