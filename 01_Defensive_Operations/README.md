# Pillar 1: Defensive Operations

This section documents my practical application of Security Operations Center (SOC) fundamentals. It focuses on establishing network visibility, configuring log ingestion, and executing structured vulnerability assessments. 

These proof-of-concept labs serve as the practical application of the theoretical frameworks validated by my CompTIA CySA+ and Security+ certifications.

## Methodology
In building these defensive labs, I prioritize a structured, methodical approach:
*   **Visibility:** Ensuring comprehensive log coverage and clear data ingestion across endpoints.
*   **Accuracy:** Refining alerting rules to reduce false positives and isolate genuine anomalous behavior.
*   **Structured Analysis:** Following established industry frameworks (e.g., NIST, SANS) to document and triage potential threats.

---

## Lab Documentation & Configurations

| Project Title | Focus | Status | Key Tooling |
| :--- | :--- | :--- | :--- |
| **[Windows Endpoint Monitoring & SIEM Ingestion](Project_1_Endpoint_Monitoring/README.md)** | Deploying Sysmon on a Windows 10 host and configuring log ingestion into a central SIEM. | **Documented** | Splunk, VirtualBox, Sysmon, Win10 |
| **[Vulnerability Management & Risk Assessment](Project_2_Vulnerability_Management/README.md)** | Performing credentialed baseline audits of Windows and Linux environments. | **Documented** | Nessus Essentials, CVSS Scoring | 

---

## Planned Development
The following labs are slated for future deployment to further expand my defensive capabilities:
*   **Network Traffic Analysis:** Deep-dive inspection of network traces using Wireshark to identify cleartext credential exposure and data exfiltration.
*   **Linux Host Hardening:** Applying secure configuration baselines (UFW, SSH hardening) to an Ubuntu host.
*   **Automated IOC Verification:** Utilizing Python scripts to automate the checking of hashes and IPs against public threat intelligence feeds.
