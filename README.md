# SOC Detection Pipeline (Wazuh-Based)

## Overview

This project implements a **Security Operations Center (SOC) detection pipeline** using open-source tooling, with **Wazuh** as the core SIEM/HIDS platform. The goal is to design, operate, and document a realistic detection environment that demonstrates how security telemetry is generated, ingested, detected, and investigated across multiple operating systems and attack types.

The focus of this project is **detection engineering and incident response**, not simply tool deployment. It emphasizes understanding how events propagate through the pipeline and how detections can be validated through controlled attack scenarios.

---

## Project Goals

- Build and operate a functional SOC-style detection pipeline
- Ingest and correlate logs from Windows and Linux systems
- Implement and validate detections across multiple attack categories
- Document incident response playbooks and case studies
- Maintain realistic scope and signal-to-noise ratios

---

## Architecture

![Project Physical Network Map](https://media.githubusercontent.com/media/astraliskye/soc-homelab/main/assets/soc_detection_network_map.png "Network Map")

### SIEM / HIDS: Wazuh

Wazuh was selected as the core detection platform due to its combination of host-based intrusion detection, log analysis, and extensibility through custom rules and decoders.

The Wazuh stack (Indexer, Manager, and Dashboard) is deployed using Docker on an always-on Ubuntu Server host. All components run on a single node for simplicity while preserving the logical separation present in larger deployments.

Deployment follows official Wazuh containerization guidance:

- Indexer
- Manager
- Dashboard

---

## Monitored Hosts

### Windows 11 Endpoint

A physical Windows 11 system representing a high-noise, real-world endpoint. This host runs a variety of applications and services and provides telemetry related to:

- Process creation
- Authentication events
- PowerShell activity
- System behavior typical of end-user machines

It also hosts VirtualBox for running the Linux-based monitored environment.

---

### Debian 13 Server

A Debian 13 virtual machine running inside VirtualBox. This system hosts **DVWA (Damn Vulnerable Web Application)** to provide a controlled target for web-based attacks.

This host generates telemetry related to:

- Web application exploitation
- Authentication activity
- Privilege escalation attempts
- Persistence mechanisms

---

## Attacker Host

A separate laptop running Gentoo Linux is used to perform attacks against the monitored environment. Using a physically separate attacker system ensures that network traffic traverses real interfaces, allowing for future expansion into network-based detection (NIDS).

---

## Detection Scope

To keep the project focused and analyzable, detections are intentionally limited to **three attacks per category** across web, Windows, and Linux environments.

This scoped approach allows for deeper analysis of each detection rather than superficial coverage of many attack types.

Detailed telemetry, detection logic, and validation steps are documented separately.

[TODO: Telemetry documentation]  
[TODO: Detection documentation]

---

## Implemented Detection Categories

### Web Application Attacks

- Brute force login attempts
- SQL injection attempts
- Web shell activity

### Windows Attacks

- Encoded PowerShell execution
- LSASS access or exploitation indicators
- Excessive or suspicious use of LOLBins

### Linux Attacks

- SSH brute force authentication attempts
- Privilege escalation attempts
- Persistence mechanisms

---

## Incident Response Playbooks

This project includes **incident response playbooks** tailored to the specific architecture and detections implemented. These playbooks describe expected investigation steps, containment strategies, and validation procedures.

[TODO: Link to IR playbooks]

### Planned Playbooks

- Web Application Compromise
- Suspected Credential Theft
- Lateral Movement Attempt

---

## Case Studies

Case studies provide **end-to-end exercises** that combine attack execution, detection validation, alert analysis, and response actions. These are more practical than the playbooks and reflect realistic analyst workflows.

[TODO: Link to case studies]

### Planned Case Studies

- SQL Injection Attack Lifecycle
- Brute Force Authentication Attack

---

## Roadmap

### Detection Engineering

- [ ] Implement custom Wazuh detection rules
- [ ] Develop custom decoders where needed
- [ ] Map detections to MITRE ATT&CK techniques

### SOC Operations

- [ ] Create dashboards for detection visibility
- [ ] Document alert triage workflows
- [ ] Reduce false positives through tuning

### Automation & Response

- [ ] Add basic alert enrichment
- [ ] Implement active response actions
- [ ] Track alert lifecycle and outcomes

### Documentation & Polish

- [ ] Architecture deep-dive
- [ ] Detection validation write-ups
- [ ] End-to-end walkthroughs

---

## Disclaimer

This project is intended for educational and demonstration purposes only. No production systems or real user data are involved.
