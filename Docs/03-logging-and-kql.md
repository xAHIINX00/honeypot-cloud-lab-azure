# 🧾 03 — Logging, DCR, and Simple KQL Queries

> 🎯 **Goal:** Connect your honeypot VM to Azure Log Analytics and Microsoft Sentinel, then collect and query failed login logs (EventID 4625).

---

## 🧩 Step 1: Create a Log Analytics Workspace (LAW)

1. In the [**Azure Portal**](https://portal.azure.com), search for **Log Analytics Workspaces**.
2. Click **+ Create**.
3. Fill in the details:
   - **Resource Group:** `HoneypotLab-RG`
   - **Name:** `Honeypot-LAW`
   - **Region:** Same region as your VM (e.g., *East US*)
4. Click **Review + Create → Create**.

🖼️ **Screenshot to Capture:**  
`docs/screenshots/07-law-overview.png`  
_Show your workspace name and region._

---

## 🛰️ Step 2: Create Microsoft Sentinel Workspace

1. In Azure Portal, search for **Microsoft Sentinel**.
2. Click **+ Add**.
3. Select the Log Analytics Workspace you just created (`Honeypot-LAW`).
4. Click **Add** — this activates Sentinel for that workspace.

🖼️ **Screenshot to Capture:**  
`docs/screenshots/08-sentinel-overview.png`  
_Show Sentinel connected to your workspace._

---

## 🔗 Step 3: Connect the Honeypot VM to Sentinel

1. Go to **Microsoft Sentinel → Configuration → Data Connectors**.
2. Search for **Windows Security Events via AMA**.
3. Click on it and then click **Open Connector Page**.
4. Click **Connect**, then create a **Data Collection Rule (DCR)**:
   - **Name:** `Honeypot-DCR`
   - **Data Source:** Security Events
   - **Destination:** `Honeypot-LAW`
   - **Target Resource:** your VM (`Honeypot-VM`)

> ⚡ *This may automatically install the Azure Monitor Agent (AMA) on your VM.*

🖼️ **Screenshot to Capture:**  
`docs/screenshots/09-windows-connector-config.png`  
`docs/screenshots/10-dcr-creation.png`  

_Show your DCR setup and connector configuration._

---

## 🧠 Step 4: Generate Test Events (Simulate Attacks)

Let’s create some failed login events to test the setup.

1. Connect to your honeypot VM via RDP.
2. Lock the screen (press **Ctrl + Alt + Del → Lock**).
3. Attempt **3–5 failed logins** using a fake username (e.g., `employee`, `admin1`, etc.).
4. Open **Event Viewer → Windows Logs → Security**.
5. Look for **Event ID 4625 (An account failed to log on)**.

🖼️ **Screenshot to Capture:**  
`docs/screenshots/05-eventviewer-4625.png`

💡 *Each failed login generates a security event that’s sent to your Log Analytics Workspace.*

---

## 🧮 Step 5: Query Logs Using KQL

Now, let’s confirm that your logs are reaching Sentinel.

1. Go to **Microsoft Sentinel → Logs**.
2. Paste this simple query (from `queries/query-4625.kql`):

   ```kql
   SecurityEvent
   | where EventID == 4625

