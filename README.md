# 🔥 Azure Cloud Honeypot Lab — Cloud Security Project

<p align="center">
  <img src="https://github.com/xAHIINX00/honeypot-cloud-lab-azure/blob/21db1a23507c21e472c7356ce3d1af046bf956b4/Attack-Map.png"/>
</p>

## 🌍 Overview
This project is a **cloud-based honeypot lab** built on **Microsoft Azure**.  
It intentionally exposes a vulnerable Windows VM to the internet, collects attacker activity logs, enriches them with **GeoIP data**, and visualizes attack sources on a **world map** inside Microsoft Sentinel.

💡 **Why this project?**  
To **learn cloud security hands-on**, understand how attackers probe exposed assets, and showcase skills in:
- Azure Cloud ☁️
- Security Operations & Monitoring 🛡️
- KQL (Kusto Query Language) 🔍
- SIEM (Microsoft Sentinel) 📊
- Log Analytics & Watchlists 🗂️

---

## ✨ Features
- ✅ **Azure Honeypot VM** (Windows) with deliberately weak security (for lab purposes only).  
- ✅ **Event Collection** → Windows Security Events (EventID `4625` failed logins).  
- ✅ **Centralized Logging** → Azure Log Analytics Workspace (LAW).  
- ✅ **SIEM Integration** → Microsoft Sentinel with data connectors & Data Collection Rules.  
- ✅ **GeoIP Enrichment** → Attackers’ IPs enriched via a `geoip` Watchlist.  
- ✅ **Attack Map Workbook** → Beautiful world map of attacker origins 🌍.  
- ✅ **Step-by-step Documentation** → Beginner-friendly guides in `docs/`.  

---

## 🏗️ Architecture

<p align="center">
  <img src="https://raw.githubusercontent.com/xAHIINX00/honeypot-cloud-lab-azure/fd18651f294ca2f70ec0025b87e6e81ac956ce5d/Architecture.png"
       alt="Architecture Diagram" width="650" />
</p>


**Data Flow:**  
`Attacker 🌐 → Honeypot VM 🖥️ → NSG (Allow All Inbound) → Data Collection Rule (DCR) → Log Analytics Workspace → Microsoft Sentinel → Attack Map Workbook`

---

## 📂 Repository Structure
