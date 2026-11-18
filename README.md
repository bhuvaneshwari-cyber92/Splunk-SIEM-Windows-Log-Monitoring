# Splunk SIEM – Windows Event Log Monitoring

## Project Overview

This project demonstrates the deployment of a basic Security Information and Event Management (SIEM) environment using Splunk Enterprise and Splunk Universal Forwarder in two Windows 11 virtual machines.

The objective was to collect Windows Event Logs from an endpoint, forward them to a central Splunk server, and search and analyse the collected security events.

## Lab Architecture

| Component | Configuration |
|---|---|
| SIEM Server | Windows 11 – Splunk Enterprise |
| Endpoint | Windows 11 – Splunk Universal Forwarder |
| Server IP | `192.168.215.136` |
| Forwarder IP | `192.168.215.137` |
| Forwarding Port | TCP `9997` |
| SIEM Web Interface | `http://localhost:8000` |

## Tools and Technologies

- Splunk Enterprise 10.6.1
- Splunk Universal Forwarder
- Windows 11
- VMware Workstation
- Windows PowerShell
- Windows Defender Firewall
- SPL (Search Processing Language)

## Implementation Steps

### 1. Virtual Machine Setup
- Created two Windows 11 virtual machines.
- Configured the VMs to communicate over the virtual network.
- Verified connectivity using ICMP ping tests.

### 2. Splunk Enterprise Configuration
- Installed Splunk Enterprise on the SIEM server.
- Enabled the receiving port TCP `9997`.
- Verified that Splunk was listening on the configured port.

### 3. Universal Forwarder Configuration
- Installed Splunk Universal Forwarder on the endpoint VM.
- Configured the forwarding destination as `192.168.215.136:9997`.
- Verified TCP connectivity from the endpoint to the SIEM server.

### 4. Windows Event Log Collection
Configured the Universal Forwarder to collect:

- Application logs
- System logs
- Security logs

The configuration was saved in `inputs.conf`, and the Universal Forwarder service was restarted.

### 5. Search and Verification
Used Splunk Search & Reporting to search the collected Windows Security events.

Example SPL query:

```spl
index=main sourcetype="WinEventLog:Security"
| stats count by host, source, sourcetype
```

## Verified Results

- Successful network communication between the two virtual machines.
- Successful TCP connectivity to port `9997`.
- Splunk Universal Forwarder service running.
- Windows Security events successfully received by Splunk.
- A search returned 105 Security events during one verification check.

**Note:** The event count is from a particular test window and may change over time.

## Skills Demonstrated

- SIEM deployment and configuration
- Windows Event Log monitoring
- Splunk Universal Forwarder configuration
- Basic network troubleshooting
- Windows Firewall configuration
- PowerShell administration
- SPL searches and event analysis
- Virtual machine management

## Project Evidence

Screenshots and supporting documentation will be added to this repository as the project documentation is completed.

## Future Improvements

- Create Splunk dashboards for security event monitoring.
- Investigate failed login attempts and suspicious activity.
- Build alerts for selected Windows security events.
- Expand monitoring to additional endpoints.

---

**Project Type:** Hands-on Cybersecurity / SIEM Lab  
**Environment:** Local Virtual Lab  
**Platform:** Windows 11 and Splunk
## Screenshots and Lab Evidence

### 1. Splunk Enterprise Home
![Splunk Enterprise Home](Screenshot%202026-11-17%20144405.png)

### 2. Splunk Receiving Port 9997
![Receiving Port 9997](Screenshot%202026-11-17%20144629.png)

### 3. Windows Event Collection
![Windows Event Collection](Screenshot%202026-11-17%20163040.png)

### 4. Security Event Search Results
![Security Event Search](Screenshot%202026-11-17%20163558.png)

### 5. Security Event Statistics
![Security Event Statistics](Screenshot%202026-11-17%20163627.png)
