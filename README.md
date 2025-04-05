# Project Overview: Splunk-ES SIEM for Mimikatz Detection

This repository showcases a hands-on project focused on deploying Splunk Enterprise Security (ES) as a Security Information and Event Management (SIEM) solution. It also includes the configuration of alerts to detect Mimikatz exploit executions on network workstations.

## Project List

1. [Deploy Splunk ES & Configure Alerts for Mimikat Execution](#deploy-splunk-es--configure-alerts-for-mimikat-execution)

## Project Details

### 1. Deploy Splunk ES & Configure Alerts for Mimikat Execution

**Description:**  
This project demonstrates the deployment of Splunk Enterprise Security as a SIEM platform to monitor a network for potential threats. The key focus is on detecting Mimikatz exploit executions and triggering alerts whenever such activity is identified.

### **Steps:**
1. Install and set up Splunk Enterprise Security.
2. Configure event logs and syslog forwarding from endpoints to Splunk.
3. Create a detection rule using Splunk's query language to identify Mimikatz-related events.
4. Configure alerts to trigger whenever a Mimikatz signature is found in the logs.

---

### **Resources Used:**

- **Splunk Enterprise Security (ES):** Centralized monitoring and alerting platform.
- **Windows Event Logs:** Source for gathering workstation activity logs.
- **Sysmon:** For capturing detailed endpoint activity.
- **Mimikatz:** Used as a case study for threat detection configuration.
- **Supporting Tools:** PowerShell, regex matchers, and custom Python scripts for extended monitoring.

---

## Getting Started

To begin working with this project:

1. Access this repository:  
   

