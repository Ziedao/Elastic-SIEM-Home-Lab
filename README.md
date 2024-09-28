# Personal Project Documentation: Elastic SIEM Home Lab

## Project Overview

This project involves setting up a home lab for Elastic Stack Security Information and Event Management (SIEM) using an Elastic Cloud instance and a Kali Linux VM. The objective is to generate security events, analyze them, and enhance my skills in security monitoring.

## Prerequisites

- VirtualBox or VMware
- Basic knowledge of Linux and virtualization

## Tasks Completed

### 1. Elastic Account Setup
- **Steps**:
  - Created a free account on Elastic Cloud at [Elastic Cloud](https://cloud.elastic.co/registration).
  - Set up a deployment of Elasticsearch.
<div style="display: flex; justify-content: space-around;">
  <img src="screenshots/siem-acc.png" alt="Image 1" style="width: 45%;"/>
  <img src="screenshots/elastic-home-page.png" alt="Image 2" style="width: 45%;"/>
</div>

### 2. Kali VM Installation
- **Steps**:
  - Downloaded and installed Kali Linux using VirtualBox from [Kali Linux](https://www.kali.org/get-kali/#kali-virtual-machines).
  - Created a new VM and configured it in VirtualBox.
  - Logged in using the credentials `kali` for both username and password.
<div style="display: flex; justify-content: space-around;">
  <img src="screenshots/kali.png" alt="Image 1" style="width: 45%;"/>
</div>

### 3. Elastic Agent Configuration
- **Steps**:
  - Log in to your Elastic SIEM instance.
  - Navigate to the Integrations page.
  - Search for "Elastic Defend" and click on it to open the integration page.

  <div style="display: flex; justify-content: space-around;">
  <img src="screenshots/addintegration.png" alt="Image 1" style="width: 45%;"/>
  <img src="screenshots/elasticDefend.png" alt="Image 2" style="width: 45%;"/>
  </div>

  - Click on “Install Elastic Defend” and follow the installation instructions.

  <div style="display: flex; justify-content: space-around;">
  <img src="screenshots/addelastic.png" alt="Image 1" style="width: 45%;"/>
  <img src="screenshots/install.png" alt="Image 2" style="width: 45%;"/>
  </div>

  - Install Elastic Agent on the kali host

  <div style="display: flex; justify-content: space-around;">
  <img src="screenshots/copy.png" alt="Image 1" style="width: 45%;"/>
  <img src="screenshots/executekali.png" alt="Image 2" style="width: 45%;"/>
  </div>

  - verify that the agent has been installed correctly by running this command

  - **Command**: 
    ```bash
    sudo systemctl status elastic-agent.service
    ```
  <div style="display: flex; justify-content: space-around;">
  <img src="screenshots/test.png" alt="Image 1" style="width: 45%;"/>
  </div>

### 4. Security Event Generation
- **Steps**:
  - Ensure Nmap is installed. If not, install it using:
    ```bash
    sudo apt-get install nmap
    ```
  - Run an Nmap scan:
    ```bash
    sudo nmap <vm-ip>
    ```
  - Perform multiple scans for different types of security events.

  <div style="display: flex; justify-content: space-around;">
  <img src="screenshots/nmap.png" alt="Image 1" style="width: 45%;"/>
  </div>

### 5. Log Querying
- **Steps**:
  - In Elastic SIEM, click on the “Logs” tab under “Observability”.
  - Enter a search query, for example:
    ```plaintext
    process.args : nmap OR process.args: sudo
    ```
  <div style="display: flex; justify-content: space-around;">
  <img src="screenshots/logs.png" alt="Image 1" style="width: 45%;"/>
  <img src="screenshots/logs1.png" alt="Image 2" style="width: 45%;"/>
  </div>

  - By clicking on the three dots next to each event, you can view more details.

  <div style="display: flex; justify-content: space-around;">
  <img src="screenshots/3dots.png" alt="Image 1" style="width: 45%;"/>
  <img src="screenshots/details.png" alt="Image 2" style="width: 45%;"/>
  </div>
### 6. Dashboard Creation
- **Steps**:
  - Navigate to the Elastic web portal.
  - Click on the menu icon, then under “Analytics,” select “Dashboards”.
  - Click on the “Create dashboard” button.
  <div style="display: flex; justify-content: space-around;">
  <img src="screenshots/dashboard.png" alt="Image 1" style="width: 45%;"/>
  <img src="screenshots/dashboard1.png" alt="Image 2" style="width: 45%;"/>
  </div>

  - Click on “Create Visualization” and choose visualization type (Area or Line).

  - Set the metrics as:

    - **Vertical**: Count
    - **Horizontal**: Timestamp

  <div style="display: flex; justify-content: space-around;">
  <img src="screenshots/visualisation.png" alt="Image 1" style="width: 45%;"/>
  <img src="screenshots/dash.png" alt="Image 2" style="width: 45%;"/>
  </div>
### 7. Alert Setup
- **Steps**:
  - Navigate to the “Alerts” section under “Security”.
  - Click on “Manage rules” and then “Create new rule”.

  <div style="display: flex; justify-content: space-around;">
  <img src="screenshots/alerts.png" alt="Image 1" style="width: 45%;"/>
  <img src="screenshots/rule.png" alt="Image 2" style="width: 45%;"/>
  </div>

  - Under “Define rule”, select “Custom query” and input:
    ```plaintext
    process.args : nmap
    ```
  - Set rule details, severity, and action.
  
  <div style="display: flex; justify-content: space-around;">
  <img src="screenshots/scan.png" alt="Image 1" style="width: 45%;"/>
  </div>

  - Following the execution of Nmap scan, the rule we configured in the Elastic SIEM promptly triggered an alert, effectively detecting the activity. This confirmed the accuracy of the setup, highlighting the efficiency of our rule in identifying potential network reconnaissance. The alert provided detailed logs, allowing us to analyze the nature of the scan and its impact on our monitored systems.

  <div style="display: flex; justify-content: space-around;">
  <img src="screenshots/nmapalert.png" alt="Image 1" style="width: 45%;"/>
  </div>

## Conclusion

This project provided valuable hands-on experience with Elastic SIEM and security monitoring. The skills gained will be beneficial for future roles in cybersecurity.

## My Next Steps Are

- Continue generating different types of security events.
- Explore additional features and integrations in Elastic SIEM.
- Document further findings and experiences to enhance learning.
