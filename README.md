# SOC Detection Lab

This is a personal project for me to get more insight into how a security
detection pipeline can be setup using open source software, and  to give me a
start to finish view of how events and logs propagate through the detection
pipeline.

## Architecture

![Project Physical Network Map](https://github.com/astraliksye/soc-homelab/blob/main/assets/soc_detection_network_map.png "Network Map")

### SIEM/HIDS: Wazuh

Wazuh was selected for its ease of setup and configuration as well as my
complete unfamiliarity with it.

In the theme of simplicity, I setup Wazuh using Docker on an always-on machine
on my network running Ubuntu Server. There are three components to the Wazuh
server: the indexer, the manager, and the dashboard. I opted to setup all three
on a single node, following [these instructions from Wazuh](https://documentation.wazuh.com/current/deployment-options/docker/wazuh-container.html).

### Monitored hosts

#### Windows 11

This is a well-used Windows machine running on physical hardware. Being
my primary rig, it has plenty of apps and services running. It also hosts
VirtualBox, on which the other monitored host (Debian 13) will run.

#### Debian 13

This is a virtual machine running inside VirtualBox on the primary
Windows 11 machine. To give some variety to the traffic and possible
detections, I installed DVWA (Damn Vulnerable Web Application) as an
intentionally insecure web application I can attack. This gives more variety
to possible detections and keeps the project inline with my interest in web
technologies.

### Attacker machine

A laptop running Gentoo. Originally, I wanted to use a Kali WSL 2 instance
running on the Windows 11 machine, but I want the network traffic to hit
physical NICs curing attacks in case I want to implement a NIDS in the future.

## Detections

These are the attack categories the project focuses on.

[TODO: link to telemetry document]

[TODO: link to each detection document]

### Web

- Brute force login
- SQL injection attempt
- XSS payload
- Command injection
- File inclusion
- Web shell

### Windows

- Encoded Powershell commands
- LSASS exploitation
- Excessive use of LOLBins
- Suspicious outbound connections
- Persistence attempts

### Debian

- SSH brute force login
- Privilege escalation
- Suspicious outbound connections
- Persistence attempts

## Incident Response Playbooks

Documentation for responding to incidents on this particular setup.
More theoretical than the case studies.

[TODO: link to each playbook]

### Web Application Compromise

### Suspected Credential Theft

### Lateral Movement Attempt

## Case Studies

Exercises in attacking and responding to incidents. More practical than the
IR playbooks.

[TODO: link to case studies]

### SQL Injection

### Brute Force Login
