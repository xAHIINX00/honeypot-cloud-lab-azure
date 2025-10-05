# 🖥️ 02 — Create the Honeypot VM (Windows)

> 🎯 **Goal:** Deploy a vulnerable Windows Virtual Machine (VM) in Azure to act as our Honeypot and attract attackers.

---

## ⚙️ Step 1: Create a Virtual Machine

1. Go to the [**Azure Portal**](https://portal.azure.com).  
2. In the search bar, type **Virtual machines** and click **+ Create → Azure Virtual Machine**.
3. Under **Basics**, fill in:
   - **Resource Group**: Select your lab resource group (e.g., `HoneypotLab-RG`).
   - **Virtual machine name**: `Honeypot-VM`
   - **Region**: Closest to you (e.g., *East US*).
   - **Image**: Choose **Windows 10 Pro** (or Windows Server if you prefer).
   - **Size**: Choose a small, cost-effective size such as **B1s** or **B2s**.

💡 *Tip:* Smaller VM sizes keep costs low — perfect for a lab environment.

 
 <p align="center">
  <img src="https://github.com/xAHIINX00/honeypot-cloud-lab-azure/blob/acec30ca518d538896a019e0c14cc5bd74e66d00/VM.png"/>
</p>

---

## 🌐 Step 2: Configure Networking (Make it a Honeypot)

1. In the **Networking** tab:
   - Create a new **Virtual Network** (or use an existing one).
   - Create or choose a **Network Security Group (NSG)**.
2. Add a new inbound rule that **allows all inbound traffic**:
   - Protocol: `Any`
   - Port range: `*`
   - Source: `Any`
   - Action: `Allow`

⚠️ **Important:** This configuration intentionally makes the VM vulnerable.  
It is **for lab use only** — do not use this on production environments!

🖼️ **Screenshot to Capture:**  
`docs/screenshots/03-nsg-rule-all-inbound.png`  
_Show your NSG inbound rule allowing all traffic._

---

## 🔑 Step 3: Access the VM

1. Once deployment completes, open the VM resource in Azure.
2. Click **Connect → RDP** and download the RDP file.
3. Use the credentials you created to log in.



---

## 🔒 Step 4: Disable Windows Firewall

Inside your Windows VM:

1. Press **Windows + R**, type `wf.msc`, and hit Enter.
2. In **Windows Defender Firewall with Advanced Security**, click **Windows Defender Firewall Properties**.
3. Turn **Firewall state → Off** for all profiles (Domain, Private, Public).
4. Apply changes.

🖼️ **Screenshot to Capture:**  
`docs/screenshots/04-vm-windows-firewall-off.png`

⚠️ **Note:** Disabling the firewall ensures attacker attempts reach your VM for detection by the honeypot setup.

---

## 🧠 Why We Do This

Honeypots are **intentionally exposed systems** designed to:
- Attract and record malicious activities 🕵️‍♂️  
- Observe attacker behavior in a controlled environment  
- Collect real-world data to improve detection rules  

🧩 In this lab, we’re simulating an exposed machine in Azure that logs every failed login attempt.

---

## 🧾 Quick Recap

| Step | Task | Result |
|------|------|--------|
| 1️⃣ | Create Windows VM | VM deployed in Azure |
| 2️⃣ | Allow all inbound in NSG | Honeypot exposed |
| 3️⃣ | Connect via RDP | Access to honeypot |
| 4️⃣ | Disable Windows Firewall | Ready to capture attacker traffic |

---

🚀 **Next:** Move on to [03 - Logging & KQL](03-logging-and-kql.md) to start collecting and analyzing security events!
