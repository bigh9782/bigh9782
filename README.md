<h1>Hi, I'm Harold!  

<h2>Certificates</h2>

- <b>Google IT Support Certificate</b>
  - [Coursera Google IT Support.pdf](https://github.com/user-attachments/files/24753970/Coursera.Google.IT.Support.pdf)

- <b>Google Cybersecurity Certificate</b>
  - [Coursera Google Cybersecurity Certificate.pdf](https://github.com/user-attachments/files/24754002/Coursera.Google.Cybersecurity.Certificate.pdf)

<h2>Projects</h2>
  
- Jira Service Management Ticketing
-   <img width="1512" height="982" alt="Screenshot 2026-01-21 at 12 15 44 PM" src="https://github.com/user-attachments/assets/c52762c0-5419-4a61-b790-b210e7c45ba8" />

<img width="772" height="147" alt="Screenshot 2026-01-21 at 12 16 12 PM" src="https://github.com/user-attachments/assets/3cba13b6-bd77-452a-91c9-491cc060a9d8" />

<img width="1512" height="982" alt="Screenshot 2026-01-21 at 12 17 07 PM" src="https://github.com/user-attachments/assets/253d1dd6-1dee-4aa3-b0e9-7d3d8b569c65" />

<img width="766" height="240" alt="Screenshot 2026-01-21 at 12 17 36 PM" src="https://github.com/user-attachments/assets/349cf9f6-f231-4a3c-806e-d19618f78b1e" />

<img width="1512" height="982" alt="Screenshot 2026-01-21 at 12 18 15 PM" src="https://github.com/user-attachments/assets/05570c6f-ac29-47c2-a6b3-611f545c05f5" />

<img width="765" height="116" alt="Screenshot 2026-01-21 at 12 18 44 PM" src="https://github.com/user-attachments/assets/261ef275-7b3c-4338-af8b-b0c5dee460f0" />

<img width="1512" height="982" alt="Screenshot 2026-01-21 at 12 18 59 PM" src="https://github.com/user-attachments/assets/b57e2a6c-babe-46ed-82a3-e3e7dff5fa1b" />

<img width="770" height="262" alt="Screenshot 2026-01-21 at 12 19 19 PM" src="https://github.com/user-attachments/assets/6f7a7238-96ff-4181-af78-2d47fb05889a" />

<img width="1512" height="982" alt="Screenshot 2026-01-21 at 12 19 39 PM" src="https://github.com/user-attachments/assets/37e3d5de-6229-4401-9850-df5c3b6f3f63" />

<img width="769" height="135" alt="Screenshot 2026-01-21 at 12 19 50 PM" src="https://github.com/user-attachments/assets/979d36e9-da8f-4eea-9258-5f1cdba78fb9" />


- Creating a Live SOC / Honeynet in Azure

# Building a SOC + Honeynet in Azure (Live Traffic)
![Cloud Honeynet / SOC](https://i.imgur.com/ZWxe03e.jpg)

## Introduction

In this project, I build a mini honeynet in Azure and ingest log sources from various resources into a Log Analytics workspace, which is then used by Microsoft Sentinel to build attack maps, trigger alerts, and create incidents. I measured some security metrics in the insecure environment for 24 hours, apply some security controls to harden the environment, measure metrics for another 24 hours, then show the results below. The metrics we will show are:

- SecurityEvent (Windows Event Logs)
- Syslog (Linux Event Logs)
- SecurityAlert (Log Analytics Alerts Triggered)
- SecurityIncident (Incidents created by Sentinel)
- AzureNetworkAnalytics_CL (Malicious Flows allowed into our honeynet)

## Architecture Before Hardening / Security Controls
![Architecture Diagram](https://i.imgur.com/aBDwnKb.jpg)

## Architecture After Hardening / Security Controls
![Architecture Diagram](https://i.imgur.com/YQNa9Pp.jpg)

The architecture of the mini honeynet in Azure consists of the following components:

- Virtual Network (VNet)
- Network Security Group (NSG)
- Virtual Machines (2 windows, 1 linux)
- Log Analytics Workspace
- Azure Key Vault
- Azure Storage Account
- Microsoft Sentinel

For the "BEFORE" metrics, all resources were originally deployed, exposed to the internet. The Virtual Machines had both their Network Security Groups and built-in firewalls wide open, and all other resources are deployed with public endpoints visible to the Internet; aka, no use for Private Endpoints.

For the "AFTER" metrics, Network Security Groups were hardened by blocking ALL traffic with the exception of my admin workstation, and all other resources were protected by their built-in firewalls as well as Private Endpoint

## Attack Maps Before Hardening / Security Controls
![NSG Allowed Inbound Malicious Flows](https://i.imgur.com/1qvswSX.png)<br>
![Linux Syslog Auth Failures](https://i.imgur.com/G1YgZt6.png)<br>
![Windows RDP/SMB Auth Failures](https://i.imgur.com/ESr9Dlv.png)<br>

## Metrics Before Hardening / Security Controls

The following table shows the metrics we measured in our insecure environment for 24 hours:
Start Time 2023-03-15 17:04:29
Stop Time 2023-03-16 17:04:29

| Metric                   | Count
| ------------------------ | -----
| SecurityEvent            | 19470
| Syslog                   | 3028
| SecurityAlert            | 10
| SecurityIncident         | 348
| AzureNetworkAnalytics_CL | 843

## Attack Maps Before Hardening / Security Controls

```All map queries actually returned no results due to no instances of malicious activity for the 24 hour period after hardening.```

## Metrics After Hardening / Security Controls

The following table shows the metrics we measured in our environment for another 24 hours, but after we have applied security controls:
Start Time 2023-03-18 15:37
Stop Time	2023-03-19 15:37

| Metric                   | Count
| ------------------------ | -----
| SecurityEvent            | 8778
| Syslog                   | 25
| SecurityAlert            | 0
| SecurityIncident         | 0
| AzureNetworkAnalytics_CL | 0

## Conclusion

In this project, a mini honeynet was constructed in Microsoft Azure and log sources were integrated into a Log Analytics workspace. Microsoft Sentinel was employed to trigger alerts and create incidents based on the ingested logs. Additionally, metrics were measured in the insecure environment before security controls were applied, and then again after implementing security measures. It is noteworthy that the number of security events and incidents were drastically reduced after the security controls were applied, demonstrating their effectiveness.

It is worth noting that if the resources within the network were heavily utilized by regular users, it is likely that more security events and alerts may have been generated within the 24-hour period following the implementation of the security controls.


[twitter]: https://twitter.com/joshmadakor
[youtube]: https://www.youtube.com/c/joshmadakor
[instagram]: https://www.instagram.com/joshmadakor/
[linkedin]: https://linkedin.com/in/joshmadakor

<!--
**joshmadakor1/joshmadakor1** is a ✨ _special_ ✨ repository because its `README.md` (this file) appears on your GitHub profile.

Here are some ideas to get you started:

- 🔭 I’m currently working on ...
- 🌱 I’m currently learning ...
- 👯 I’m looking to collaborate on ...
- 🤔 I’m looking for help with ...
- 💬 Ask me about ...
- 📫 How to reach me: ...
- 😄 Pronouns: ...
- ⚡ Fun fact: ...
-->
