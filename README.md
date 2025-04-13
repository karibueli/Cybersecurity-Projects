# Deploying a SIEM (Microsoft Sentinel)
## Objective
Setup a simple SIEM using Microsoft Sentinel platform. Utilise Content hub, Data Connectors, Log management, Threat Intel, Workbooks and other features available.

# Microsoft Sentinel Architecture

![MS Sentinel Architecture](https://github.com/user-attachments/assets/374542f7-e72c-4a05-870c-2c781bb8acf7)
***Source:Microsoft.com***

### Tasks:
1. Create/Signup Sentinel subscription
2. Create resource group
3. Create Log Analytics Workspace.
4. Create/Signup for an account on ***pulsedive.com***
5. Data connectors - ingest data from ***pulsedive.com*** API

## **Typical Data Sources for a SIEM**

**APPS**:  SAP, Service-NOW, Workday.

**Network** : Azure Firewall, NSG, WAF

**OS**: Windows, Linux, MAC OS

**Platform**: EntraID, Azure Activity, S3 Bucket(AWS)

**Security**: Defender (for Cloud, Endpoint,) Purview

***NOTE*** In this Demo Project we will ingest Threat Intel data from *pulsedive.com* (free) via our Data connector into our MS Sentinel Workspace.
