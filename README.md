# SOC Home Lab

Windows domain home lab to test ideas and practice detecting and responding to threats.

## Stack

Subnet 172.16.0.0/12:
  Kali Attack Box (attack-box)
  Windows Domain
    Windows 2025 DC (dc01)
      - GPOs applied to each  host
        - Disable Windows Defender (simulate a compromised machine)
        - Enabled Powershell script block logging
        - Enabled command line auditing
    Windows host (management01)
      - Windows 11 Pro
      - Sysmon
      - Splunk UF
    finance01
      - Windows 11 Pro
      - Sysmon
      - Splunk UF

Subnet 192.168.1.0/24:
  splunk
    - Debian 13
    - Splunk Enterprise

## Detections

![T1059.001 -> T1003.001](/detections/T1059.001.md) - Powershell downlaods Mimikatz followed by credential dumping via accessing LSASS.exe.

## Setup

1. Windows AD domain with two hosts joined to domain
2. Sysmon with SwiftOnSecurity's configuration on both hosts
3. Powershell script block logging and command-line auditing enabled via Group Policy
4. Windows Defender disabled via Group Policy
5. Splunk enterprise on Linux
6. Splunk UF installed on each machine
7. Atomic Red Team installed on each host

## About

Hey my name is Skye. I have experience with software development and IT operations, trying to move into SOC analyst work. My hobbies include building projects, playing video games, reading, and disc golfing.
