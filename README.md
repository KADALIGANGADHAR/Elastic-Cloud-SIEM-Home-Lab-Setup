# Elastic-Cloud-SIEM-Home-Lab-Setup

**This professional guide will walk you through building a full-featured Security Information and Event Management (SIEM) lab using Elastic Cloud and Kali Linux. It includes setting up the Elastic Stack, deploying an agent, analyzing logs, creating dashboards, and configuring alerts.**

## Prerequisites

- **Elastic Cloud account.**

- **Kali Linux or Ubuntu virtual machine (VirtualBox/VMware).**
##

> ## Set Up an Elastic Cloud Account

- **Go to Elastic Cloud and sign up/log in.**

- **Start a Free Trial.**

- **Click Create Deployment.**

- **Choose:Cloud Provider: GCP / AWS / Azure**

- **Region: Closest to you (e.g., gcp us-central1 (Iowa))**

- **Template: Storage optimized (version 8.17.4 or latest)**

- **Click Create deployment.**

![image](https://github.com/user-attachments/assets/bf623fd2-e2e6-4da9-a907-568e9e2cfd63)
- **Launch Kibana & Set Up Security Environment**
- **From your Elastic Deployment dashboard, click Open Kibana.**
![image](https://github.com/user-attachments/assets/d0bed8fc-3b5d-4695-9b4c-58036c53ea0a)


- **In Kibana, Elastic for Security from the welcome screen.**

![image](https://github.com/user-attachments/assets/9644b051-0df8-4218-80d4-b1c12027d719)

- **Add Elastic Agent Using Elastic Defend Integration**

- **In Kibana, Click on Add Integration.**

- **Select Elastic Defend integration.**
![image](https://github.com/user-attachments/assets/2ec29c87-2c9c-42f0-b8e4-36c4c3af607c)

- **Click Add Elastic Defend → Create a new policy if prompted.**
![image](https://github.com/user-attachments/assets/f589fcd6-5441-468d-a06d-a7a651017fb8)
![image](https://github.com/user-attachments/assets/87cdb92b-0356-4bb9-9373-e5614cf9d976)
- **Install Elastic agent → Select the platform as Linux (Debian/Ubuntu)**
![image](https://github.com/user-attachments/assets/add96993-f643-4946-bf66-f9cd87a9d16d)

- **Copy the enrollment command provided.**
![image](https://github.com/user-attachments/assets/e81403f6-a00c-4d4f-a01c-ab8315f76271)

- **On your Kali Linux terminal, paste and run the command:**
![image](https://github.com/user-attachments/assets/6ea554e4-dc1e-4edc-9071-8089e9b91226)
![image](https://github.com/user-attachments/assets/df8797d9-5897-4df7-9873-7d420bc4407c)
![image](https://github.com/user-attachments/assets/5cf69ffd-62fd-4132-b61c-caeb371b789d)
![image](https://github.com/user-attachments/assets/ebd30ed1-9258-4b7e-ab26-5b90457003cb)

- **Verify agent status: sudo systemctl status elastic-agent**
![image](https://github.com/user-attachments/assets/b36189cb-e816-4d6e-9e4d-131593845d1e)
- **Agent Enrolled confirmed.**
![image](https://github.com/user-attachments/assets/b1d21ff1-dff0-4ea7-a005-48f4ffa57c90)
- **Click On Add the Integration  → Set up elastic defend integration**
![image](https://github.com/user-attachments/assets/8579e0ff-771a-407b-b864-7837bb37aa30)

- **In Kibana confirm that the data is being received from the agent.**

- **You should see a message: ✅ Incoming data received from 1 enrolled agent**

- **A log preview will be visible under the "Confirm Incoming Data" step.**
![image](https://github.com/user-attachments/assets/7e6f4dd5-70b3-41ce-b92a-6b5c73100c0b)
![image](https://github.com/user-attachments/assets/41b370e2-d0a6-42ce-96af-26b58dfed867)

- **In Kiban  Go to security → Discover in the left-hand navigatin** 

- **Thsi section allows you to explore indexed data(logs,alerts,etc) visually**
![image](https://github.com/user-attachments/assets/a3dda294-2c15-4be7-80f9-80cdb024a4a6)

- **At the top of the Discover panel, select your desired data view from the dropdown** 

- **Example shown: metrics- or alerts-security.alerts-**
![image](https://github.com/user-attachments/assets/e02e3292-b183-486a-8d39-8b2ee9d0e6b1)

- **Once the appropritate data view is selected you will see a histogram graph on top representing og event counts over time.**

- **Below that, the log entries(documents) listed.**

- **Use the time picker in the top-right to chabge the time range(eg: last 15 minutes).**
![image](https://github.com/user-attachments/assets/6bac1a87-4218-461f-850d-140040942d19)

## Generate Security Events with Nmap

- **On Kali VM, run:```sudo nmap -A -sV localhost```**

- **This simulates a scan and generates logs ingested by Elastic Agent.**
![image](https://github.com/user-attachments/assets/bec8e5d9-54a7-4609-b648-f5483362c74c)
 ## Query Logs in Elastic SIEM
 
-  **In Kibana, go to Discover section ,select the logs, data view to analyze raw logs**

-  **Use the search bar to enter keywords enter :nmap**

-  **This helps identify processes related to scanning activity, like Nmap usage.**
![image](https://github.com/user-attachments/assets/a397e171-6b23-421e-90f1-5a625b02dbe1)
**Analyza log details**

- **click on any log entry to view full JSON details on the right side panel**

- **Look for fields such as: process.args, process.name, agent.name etc**

- **This provides exact information about the executed command and the host.**
![image](https://github.com/user-attachments/assets/a9e065aa-d5a5-406e-a83e-8711c412ec51)
 ## Create a Dashboard to Visualize Events

 **Navigate to dashboards** 
 
- **Open Kibana** 
 
- **From the left-hand pane, go to dashboards.**
 
- **Click on "Create Dashboard"**
![image](https://github.com/user-attachments/assets/0fd3378c-32e4-4510-90e3-424135745c59)

**Add a Visulization**

- **Click "Create visulization" within the dashboard editor.**

- **select the Bar chart option.**
![image](https://github.com/user-attachments/assets/fec55376-3313-4938-adda-f8c9404118d6)
![image](https://github.com/user-attachments/assets/50cbbf74-9031-41af-aad0-afab81f0e4f0)

**Configure the Bar chart**

**Horizontal Axis (X-axis)** 

- **Select @timestamp.**

- **This will display log frequency over time**
![image](https://github.com/user-attachments/assets/d2d10c23-2c1f-433c-8dc6-f66669968625)

**Vertical Axis (Y-axis)**

- **Set the metric to count**

- **This will count the number of records per time interval**
![image](https://github.com/user-attachments/assets/e5484896-ec07-441b-a663-208c4ea306a9)
**Save the Visualization**

- **Once the visualization is ready, click "Save and return".**

- **Enter a dashboard title, for example:logs.**

- **click"Save" to store your dashboard.**

![image](https://github.com/user-attachments/assets/de7d9f55-04f7-4b6d-a19f-929e64eb3bd8)
![image](https://github.com/user-attachments/assets/c7e822ae-925a-4e61-a0d3-cad5a320ae16)
## Create Custom Detection Rule in Kibana(SIEM)

- **open kibana**
- **Go to security -> Rules.**
- **Click on Detection Rules(SIEM).**
![image](https://github.com/user-attachments/assets/6960b98d-c572-4e2e-af5d-afd023b5c1e1)
- **create new rule**
- **Select"custom query" as the rule type**
  ![image](https://github.com/user-attachments/assets/17a1aa6f-4a91-4327-b03a-6eb72578c271)
- **In the custom query field , enter the rule type**  
![image](https://github.com/user-attachments/assets/11e7ea27-9ddd-4c35-9775-fabc6eb653d9)
  **Fill in rule details**
- **Name:**
- **Description:**
- **Severity**
![image](https://github.com/user-attachments/assets/5c395269-44ff-4ce3-976f-2bdafb8e8b97)
  **Schedule the rule**
 - **set how often the rule should run(eg: every 5 minutes)**
 - **Adjust the look-backtimeif needed(eg:1 minute)**
![image](https://github.com/user-attachments/assets/bbb0f38a-8330-4fb5-9557-9846079c778d)
  **Configure Rule Actions**
 - **Choose how to respond when the rule triggers(Ex:notify,index alert, or send to an external system).**
 - **if no actions are needed, proceed to the final step**
 - **Click"Create & enable rule".**
 - **The rule will now be active and listed under Detection Rules as Nmap Detection**
![image](https://github.com/user-attachments/assets/437821a3-67d7-45e4-bd4e-75ae39ba5736)
![image](https://github.com/user-attachments/assets/b412449f-7de2-4ef8-845e-921045f5bc47)
![image](https://github.com/user-attachments/assets/84ecd2f1-b74b-4be4-878c-af1392ce7f79)
## Enable Prebuilt Detection Rules
- **In Kibana, navigate to Rules.**
- **Open the Detection Rules(SIEM)section**
- **Search and Enable the rules (Ex: SSH related rules)**
![image](https://github.com/user-attachments/assets/9afb7943-2149-4944-a261-bc4a478f095d)
![image](https://github.com/user-attachments/assets/ae4901b4-fc7a-487e-9198-b4ef053a190a)
**Launch Brute Force Attack from kali**
- **From your kali linux machine,use Hydra to simulte an SSH brute-force attack**
![image](https://github.com/user-attachments/assets/d629a86d-5cf4-49ef-b9f8-804e79da204f)
![image](https://github.com/user-attachments/assets/40ba1778-627f-4e7c-b84a-1fe3f5a2fe9d)
![image](https://github.com/user-attachments/assets/fce5f424-6ed0-459d-a8db-098299bf0518)
![image](https://github.com/user-attachments/assets/43463e31-389e-4d74-9ceb-179af990f5cc)
**Monitor Alerts in Kibana**
- **Go to kibna -> Discover.**
- **In the search bar, entered the process.name:"hydra"** 
![image](https://github.com/user-attachments/assets/3a826292-d427-496c-b6b3-632066878f95)
- **Navigate to rules**
- **Look for the SSH-related detection rules**
- **If triggered, the rule will show a "warning"status**
![image](https://github.com/user-attachments/assets/fc779042-3cc9-43ac-a827-ee6ab570b93f)
![image](https://github.com/user-attachments/assets/f749102e-60d6-46dd-8f9a-c645f1ceb142)

## Manage Elastic Agent

- **Check status:``sudo systemctl status elastic-agent``**

- **Stop agent:``sudo systemctl stop elastic-agent``**

- **Uninstall agent:``sudo elastic-agent uninstall``**
- 
## Conclusion

- **Installed and configured Elastic Cloud(SIEM)**

- **Installed Elastic Agent on Kali**

- **Queried logs and analyzed real security events**

- **Created alerts and tested rule triggering**

- **Built visual dashboards**



