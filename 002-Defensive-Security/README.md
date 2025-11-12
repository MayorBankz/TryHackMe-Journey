# TryHackMe - Introduction Defensive Security (Blue Team)
* Link: https://tryhackme.com/room/defensivesecurityintro
* Date: 11-11-2025
* Level: Beginner
* Skills Learned: Simulating a SIEM to detect an intrusion


## Summary
Defensive security, also known as the blue team, prepares and proactively protects an organization's infrastructure. It is concerned with two main tasks;
1. Preventing intrusions from occuring.
2. Detecting intrusions when they occur and responding properly.

Some of the tasks that are involved in defensive security include:
* Cybersecurity awareness
* Documenting and managing assets
* Preventing security - Firewall and IPS
* Logging and Monitoring - SIEM
* Frameworks, Policies & Procedures


## Security Operation Centre (SOC)
A Security Operations Centre (SOC) is a team of cybersecurity professionals that monitors the network and its systems to detect malicious cybersecurity events. Some of the main areas on interest for a SOC are:
* Trends & Vulnerabilities - Keeping up to date
* Policy Violations - Monitors for adherence to these policies
* Unauthorized & illegal activities - SOC establishes a baseline of acceptable behaviour and activity.
* Intrusion & Breach Detection - SOC team is responsible for detecting and responding to these breaches.


## Digital Forensics
Digital forensics is used to preserve and analyse digital evidence to aid in the investigation of incidents, such as breaches. This may involve looking at information from.
* File system
* System memory
* System logs
* Network logs

## Incident Response
Incident Response is how organizations manage security events such as breaches, data, leaks and cyber attacks. An incident response process is a defined set of stages to minimise damage, contain the threat, and recover quickly.
* Preparation - Creating the necessary resources and frameworks to handle an incident.
* Detection & Analysis - using tooling and process to detect incidents and assess their scope (reach) and severity.
* •	Containment, Eradication & Recovery – Limiting the impact of the incident.
* •	Post-Incident Activity – Review the overall incident, how it was handled and could’ve been prevented.


## Scenario (Simulating a SIEM system)
Inspecting the alerts in a SIEM dashboard. Find the malicious IP address from the alerts, copy it, switch to the IP scanner tab, and then use the IP address in the IP scaner.

<img width="800" height="600" alt="image" src="https://github.com/user-attachments/assets/5be68c60-3ed0-4477-bb1f-a1a84a2ae150" />

* Step 1 - Copy the suspicious IP address
  
<img width="800" height="600" alt="image" src="https://github.com/user-attachments/assets/2d900f1a-e2a0-4dd9-bd71-1fb313cb7efd" />

* Step 2 - Navigate to the IP scanner and paste the copied suspicious IP address then submit
<img width="800" height="600" alt="image" src="https://github.com/user-attachments/assets/79b7d206-af00-4aec-8b32-ce05a6886136" />

* Step 3 - Use the IP scanner to analyze the suspicious IP address identified in the SIEM alerts
<img width="800" height="600" alt="image" src="https://github.com/user-attachments/assets/93df8b74-e247-43fa-98bb-067adddc1853" />

* Step 4 - Now that we know that the IP address is malicious, we need to escalate it to a staff member

<img width="800" height="600" alt="image" src="https://github.com/user-attachments/assets/08d6366c-966d-4776-810a-65845c1f7fba" />

* Step 5 - You got the permission to block the malicious IP address, and now you can proceed and implement the block rule. Block the malicious IP address on the firewall.

<img width="800" height="600" alt="image" src="https://github.com/user-attachments/assets/674ef4fe-f017-498c-8077-e94349eedeff" />

<img width="800" height="600" alt="image" src="https://github.com/user-attachments/assets/07fe1211-882f-4e4a-a953-d0d62d1aa4bb" />







