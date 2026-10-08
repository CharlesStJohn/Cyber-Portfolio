# Utility Scripts

This directory contains standalone Python and Bash scripts developed to perform specific data manipulation, text parsing, and basic administrative tasks. 

These utilities demonstrate the practical application of core programming competencies—specifically data extraction, file manipulation, and automation—relevant to security operations.

## Development Standards
Every project within this directory is developed with a strict focus on:
*   **Error Handling:** Ensuring scripts fail gracefully and provide useful traceback output.
*   **Documentation:** Providing clear instructions for execution and expected behavior.
*   **Code Readability:** Prioritizing sound logical structure and clear variable naming over unnecessary complexity.

---

## Applied Utilities

| Project Title | Goal | Key Skills Demonstrated | Status |
| :--- | :--- | :--- | :--- |
| **Log Ingestion & Parsing Tool** | Extracting IPs and timestamps from raw logs to output structured data. | Python, File I/O, Regex, Error Handling. | **Planned Q1 2027** |

---

## Planned Development
As foundational syntax knowledge solidifies, the following utilities are slated for development:
*   **System Health Check:** A Bash utility to audit baseline security configurations (firewall rules, active services) on a Linux host.
*   **Hash Analyzer:** A Python script utilizing the `hashlib` library to generate and verify SHA256 hashes for cryptographic file integrity.
*   **Threat Intelligence IP Checker:** Integrating public threat feeds to automate IP reputation checks via API interaction.
*   **Automated Log Scheduler:** Implementing cron and task scheduling for recurring security audits.

---
**Current Status:** Actively transitioning core syntax knowledge into functional scripts. The immediate focus is finalizing the Log Ingestion & Parsing Tool utilizing native file operations and Regular Expressions.
