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

***Step 1***. Go to your MS Sentinel ==DEMOLA==  click ==Data connectors== option and ==filter Data Type to Threat Intelligence== then Select ==Threat Intelligence - TAXII== as Screen shot below.

![image](https://github.com/user-attachments/assets/30b07acd-f150-471d-9c18-2e6983d54ae8)

***Step 2***. Then Open Connector Page and configure details acquired from ***pulsedive.com*** as next two screenshot shows.

![Pulsedive Account](https://github.com/user-attachments/assets/ae2f36b9-805a-4fdc-9e07-77dce79feafd)

***Step 3***. Fill details as below from pulsedive.com account details & API and click ADD.

![Threat Intel - Taxii Sentinel Setup](https://github.com/user-attachments/assets/01321b06-3189-4e2d-b4ce-22c607f75fcb)

***Step 4***. Go to MS Sentinel Logs > Tables (microsoft Sentinel>ThreatIntelIndicators table) and click RUN

***Step 5***. You will now witness that, Log Analytics showing Malicious-Activity ThreatIntel ingested into sentinel by pulsedive.com from domain name com.hugfu.top

![image](https://github.com/user-attachments/assets/d917e07a-6ba6-4031-92c2-e8b77bd20dd2)

***Step 6***. Ingesting Entra ID ***AuditLogs*** into Sentinel

1. Go to MS Sentinel > Content Hub, Search for Azure Active Directory (newly named Microsoft Entra ID)

![image](https://github.com/user-attachments/assets/cca0f61a-22aa-42c4-801f-fedb9d79e924)

2. Then go to Data Connector > select MS Entra ID, click Open Connector Page and select just AuditLogs

Once ***Auditlogs*** ingested into Sentinel, click ***Logs*** then Table, Under ***LogManagement*** select ***Auditlogs*** and click RUN as screenshot below showing timestamps and logs that have been generated.

![image](https://github.com/user-attachments/assets/f29037ca-e6ea-46ae-878d-3bb90b607730)

## **Azure Monitor Agent (AMA) and Data Collection Rules (DCR)**
***Observability Monitory Logs*** > Ingest into Azure Monitor + Log Analytics
***Data Collection Security Event Logs*** > Ingest into Sentinel Workspace.

## **Analytic Rules**

* Analytic rules are your SIEM Use-case defined via *KQL*
* Sentinel comes with over 500 rules templates.
* Limit of 512 rules per workspace
* **7 Types of analytic rules:**
 1. ***Scheduled*** > Continuously run in defined timeframe, alert is fired if a condition is met. Below screenshot showing how to create a ***Scheduled Rule*** in Sentinel

![image](https://github.com/user-attachments/assets/03b1b742-f9e0-42bd-ac41-614d0abc6b86)

Below is final configuration of ***Scheduled rule*** created and enabled to search simple ***KQL*** Query for Add user operation in ***AuditLogs***

![Schedulled Rule Details](https://github.com/user-attachments/assets/4595c8b2-dff3-4362-a02c-7b4f0b8c086c)

Below is another ***Scheduled Rule*** to pull ***SecurityEvent*** for new process initiated with ***EventID 4688** This rule pulls All events thats hows a new process has been initiated.

![image](https://github.com/user-attachments/assets/ccbfa434-bffd-4224-a599-e7c19fae98d7)

2. ***Near-Real-Time (NRT)*** > run continuously and shall provide "up-to-the-minute" threat detection, there is a limit of 50 NRT rules per workspace.

![image](https://github.com/user-attachments/assets/9505386d-c096-491b-bb5d-ee25aa9a1724)
