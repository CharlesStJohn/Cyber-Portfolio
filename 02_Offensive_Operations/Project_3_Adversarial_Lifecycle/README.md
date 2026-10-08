# Project 3: The Adversarial Lifecycle

## Overview
This final report completes the unified lab narrative by transitioning into an offensive simulation. The objective was to execute a structured attack path—performing reconnaissance, exploiting a critical vulnerability identified in Project 2, and establishing a remote shell—to validate the efficacy of the SIEM and endpoint telemetry configurations established in Project 1.

This project serves as a practical stress test, demonstrating the ability to "close the loop" between offensive tactics and defensive detection.

## Technical Stack & Rationale
*   **Metasploit Framework:** Utilized as the primary exploitation and workspace management tool to organize reconnaissance data and deliver targeted payloads.
*   **Nmap (`db_nmap`):** Integrated directly into the Metasploit workspace for service versioning and attack surface mapping.
*   **Meterpreter Payload:** Selected to provide an advanced, in-memory (`reverse_tcp`) command shell, simulating an adversary attempting to evade disk-based detection.

---

## Execution & Evidence

### 1. Integrated Reconnaissance
A view of the Metasploit services table populated via `db_nmap -sV`. This reconnaissance confirmed the active state of high-risk services, specifically Java RMI (Port 1099), directly within the offensive workspace.
![Adversarial Reconnaissance](images/P3_R1_Metasploit_Service_Map.png)

### 2. Full Chain Exploitation
A consolidated capture documenting the exploit execution (`exploit/multi/misc/java_rmi_server`) and the successful opening of a Meterpreter session. The terminal output confirms total system compromise with `root` access.
![Full Chain Exploitation](images/P3_R2_Adversarial_Full_Chain_Exploitation.png)

### 3. Post-Exploitation Simulation
A capture of the Windows 10 target host, showing the manual execution of a "Living off the Land" command string via PowerShell to simulate internal adversarial activity.
![Adversarial Process Trigger](images/P3_R3_Adversarial_Process_Trigger.png)

### 4. SIEM Detection Verification
The definitive validation from the defensive hub. The Splunk dashboard successfully captured the simulated adversarial command string under `EventCode=1` (Process Creation), proving the structural integrity of the logging pipeline engineered in Project 1.
![SIEM Detection Verification](images/P3_R4_SIEM_Detection_Verification.png)

---

## Findings & Detection Validation
An exploit is only half of a security assessment; the primary value of this simulation was the validation of the defensive telemetry. 

*   **Validation Troubleshooting Note:** During the final verification phase, an attempt to trigger a Sysmon network connection log (`Event ID 3`) via an Nmap scan failed to register in Splunk. Diagnostics revealed the Windows host firewall was successfully filtering the packets before a TCP connection could be established. Rather than artificially lowering the firewall, the test was pivoted to a host-based "Living off the Land" simulation via PowerShell. This successfully triggered a Process Creation log (`Event ID 1`), proving that while the perimeter defended the network layer, the host-based sensors were correctly tuned to catch internal execution.

## Hardening Roadmap
Based on this simulation, the following hardening steps are recommended to break the adversarial lifecycle:
*   **Service Minimization:** Disabling all non-essential services discovered during reconnaissance to reduce the available attack surface.
*   **Sensor Tuning:** Refining the Sysmon configuration to explicitly monitor `Event ID 3` (Network Connections) on critical ingestion ports to detect lateral movement attempts.
*   **Behavioral Alerting:** Transitioning from static keyword searches to behavioral alerting within Splunk (e.g., flagging any PowerShell execution containing "encoded" or "hidden" execution policies).

---
## Key Skills Demonstrated
* Ethical Hacking (Metasploit Framework)
* Network Reconnaissance (Nmap Integration)
* SIEM Detection Validation (Splunk)
* "Living off the Land" Simulation
