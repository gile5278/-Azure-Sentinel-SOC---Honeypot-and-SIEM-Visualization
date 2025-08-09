# Azure Sentinel SOC — Honeypot and SIEM Visualization

## Overview
This project demonstrates the setup of a **cloud-based Security Operations Center (SOC)** in Microsoft Azure, featuring a **Honeypot Virtual Machine** to attract real-world attacks, integrated with **Azure Sentinel (SIEM)** for log analysis and geolocation-based visualization.

The goal of this lab is to simulate a real-world security monitoring environment, collect failed RDP login attempts, enrich them with **GeoIP data** from an imported Watchlist, and visualize attack sources on a world map dashboard. This setup strengthens skills in SIEM configuration, log analysis, incident monitoring, and security visualization.

---

## Key Features
- **Honeypot Deployment**: Intentionally exposed Azure VM to simulate malicious login attempts.
- **SIEM Integration**: Collected and analyzed Windows Security Event Logs via Azure Sentinel and Log Analytics Workspace.
- **Geolocation Enrichment**: Correlated attacker IP addresses with an imported GeoIP Watchlist to determine physical locations.
- **Attack Visualization**: Created an interactive Azure Sentinel Workbook map displaying attacker origins.
- **Incident Analysis**: Applied Kusto Query Language (KQL) to filter and visualize failed login activity.

---

## Technology Stack
- **Platform**: Microsoft Azure (VM, Resource Groups, Virtual Network, Network Security Groups, Log Analytics Workspace, Azure Sentinel)
- **Languages**: PowerShell, Kusto Query Language (KQL)
- **Data Source**: GeoIP Watchlist (imported into Sentinel)
- **Security Tools**: Azure Sentinel (SIEM), Microsoft Defender for Cloud
- **OS**: Windows Server 2022 (Honeypot VM)

---

## Setup Guide
1. Clone this repository:
   ```bash git clone
   https://github.com/gile5278/-Azure-Sentinel-SOC---Honeypot-and-SIEM-Visualization.git 
2. Follow the step-by-step deployment instructions in SETUP.md.
3. Upload the provided GeoIP dataset into Azure Sentinel Watchlists.
4. Import the provided Workbook template from the **workbook/** folder into Azure Sentinel.
5. View the real-time attack map in the Azure Sentinel dashboard.

## Repository Structure
- `SETUP.md` –            Detailed setup and configuration steps
- `workbook/` –           Sentinel Workbook template (.workbook) for attack visualization
- `README.md` –           Project overview and usage guide

## Visualization Example

![Resource Group Screenshot](Document_Images/image20.png) 

## Lessons Learned
- Setting up and configuring a cloud-hosted SIEM.
- Writing and optimizing KQL queries for security log analysis.
- Enriching logs with external datasets (GeoIP Watchlist) for better context.
- Designing meaningful visualizations to enhance incident response.

## Disclaimer
This project is for educational and demonstration purposes only.
The Honeypot VM in this lab is intentionally exposed to attract malicious traffic and should never be deployed in a production environment.
