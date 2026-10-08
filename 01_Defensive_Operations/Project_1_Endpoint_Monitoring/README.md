# Project 1: Windows Endpoint Monitoring & SIEM Ingestion

## Overview
This project establishes the defensive foundation for a segmented laboratory environment. The primary objective is to engineer a data pipeline capable of capturing high-fidelity endpoint telemetry, moving beyond basic Windows event logging to ensure total visibility over a target host. 

This environment serves as the baseline for subsequent vulnerability assessments (Project 2) and adversarial simulations (Project 3).

## Technical Stack & Rationale
*   **Splunk Enterprise:** Deployed as the central SIEM to aggregate, parse, and index diverse data types across the lab ecosystem.
*   **Sysmon (System Monitor):** Installed on the Windows endpoint to capture kernel-level telemetry, specifically process command lines (Event ID 1) and network connections (Event ID 3), which are critical for forensic analysis.
*   **Splunk Universal Forwarder (UF):** Configured on the target machine to securely ship logs to the SIEM over port `9997`.

## Laboratory Architecture
The environment was built utilizing a segmented virtual network to isolate the host machine while simulating a standard attack surface.

| Asset Name (VirtualBox) | Hostname | IP Address | Role |
| :--- | :--- | :--- | :--- |
| **Kali Linux** | `kali` | `192.168.56.102` | SIEM Host / Attacker Vantage Point |
| **Windows 10** | `Win10-Defensive` | `192.168.56.106` | Primary Target Endpoint |
| **Metasploitable 2** | `metasploitable` | `192.168.56.104` | Legacy Linux Target |

---

## Execution & Evidence

### 1. Network Architecture
A view of the segmented lab architecture within the VirtualBox hypervisor, detailing the isolated subnet.
![The Cyber Range](images/P1_R1_CyberRange_Architecture.png)

### 2. Telemetry Ingestion Verification
A Splunk search result confirming the Windows 10 host is successfully shipping real-time telemetry via the Universal Forwarder.
![Connectivity Proof](images/P1_R2_Splunk_Connectivity_Proof.png)

### 3. Sysmon Data Validation
A high-fidelity search proving Sysmon is successfully capturing kernel-level activity, verifying that the logging agent is correctly configured.
![Granular Ingestion](images/P1_R3_Sysmon_Ingestion_Confirmation.png)

### 4. Process Creation Tracking (Event ID 1)
Validation of EventCode=1 (Process Creation), demonstrating the system's ability to track and log specific command-line execution for future adversarial detection.
![The Whoami Capture](images/P1_R4_Telemetry_Whoami_Test.png)

### 5. Event Visualization
A basic aggregation chart generated via Splunk SPL (`stats count by EventCode`) to transform raw Sysmon telemetry into readable analytical trends.
![Tactical Visualization](images/P1_R5_Splunk_EventID_Visualization.png)

---

## Findings & Value
By configuring Sysmon to capture specific Event IDs and routing them into Splunk, this project successfully demonstrates the shift from reactive logging to proactive monitoring. Without this granular telemetry (specifically process tracking and network connections), an analyst remains blind to "Living off the Land" techniques and lateral movement. 

## Hardening Roadmap
To mature this environment toward a production-grade standard, the following steps are planned:
*   **Configuration Tuning:** Deploying a curated XML configuration (e.g., SwiftOnSecurity) to filter out background noise and focus ingestion strictly on high-risk directories.
*   **Real-Time Alerting:** Utilizing Splunk Search Processing Language (SPL) to build automated triggers for `EventCode=1` when system tools like `vssadmin` or `powershell` are invoked unexpectedly.
*   **Tactical Dashboards:** Leveraging Splunk Dashboard Studio to aggregate raw telemetry into visual trends for continuous posture monitoring.

---
## Key Skills Demonstrated
* SIEM Engineering (Splunk)
* Endpoint Detection & Response (Sysmon)
* Network Segmentation & Virtualization
