# 🌍 05 — Attack Map Workbook

> 🎯 **Goal:** Import and configure an Attack Map workbook in Microsoft Sentinel to visualize global attacker origins based on enriched GeoIP data.

---

## 🧭 Step 1 — Open the Workbooks Section

1. In **Microsoft Sentinel**, go to your connected workspace.  
2. Click **Workbooks** → **+ Add workbook**.

🖼️ **Screenshot to Capture:**  
`docs/screenshots/14-workbook-advanced-editor-json.png`  
_Showing the empty workbook in the Advanced Editor._

---

## 🧱 Step 2 — Import the Workbook JSON

1. In the workbook window, click **Advanced Editor** (top-right corner).  
2. Delete any existing content inside the editor.  
3. Open your repo file:  
4. Copy its contents and paste them into the **Advanced Editor** in Sentinel.  
5. Click **Apply** → then **Done Editing**.  
6. Save the workbook with a name like **“Honeypot Attack Map”**.

<p align="center">
  <img src="https://github.com/xAHIINX00/honeypot-cloud-lab-azure/blob/21db1a23507c21e472c7356ce3d1af046bf956b4/Attack-Map.png"/>
</p>

---

## 🕵️‍♂️ Step 3 — Apply Time Range and Refresh

- Set the workbook **Time Range** (e.g., *Last 24 hours*).  
- Click **Apply** to visualize real-time attacker data on the map.  
- The map points represent the **geographic origins** of failed logins (`EventID 4625`) detected from your honeypot VM.

---

## ⚙️ Step 4 — Troubleshooting the Map

If the map doesn’t display as expected:

- ✅ Confirm the **`geoip` watchlist** is imported correctly and includes `Country`, `Region`, and `City` columns.  
- ✅ Ensure your `SecurityEvent` logs contain valid `IpAddress` values.  
- ✅ Verify your `map.json` query uses `_GetWatchlist("geoip")` and `ipv4_lookup` correctly.  
- ✅ Adjust workbook query time range to include recent attack logs.

> 💡 *Tip:* Use the summary query from [04 - Watchlist: GeoIP Enrichment](04-watchlist-geoip.md) to confirm data before visualizing.

---

## 🧾 Quick Recap

| Step | Action | Outcome |
|------|--------|----------|
| 1️⃣ | Open Sentinel → Add Workbook | Create new visualization workspace |
| 2️⃣ | Paste `resources/map.json` | Attack Map JSON imported |
| 3️⃣ | Apply Time Range | Live map of attacker locations displayed |
| 4️⃣ | Troubleshoot if needed | Map refined for accuracy |

---

🎉 **Congratulations!**
You’ve completed the full **Azure Cloud Honeypot Lab Project** 🎯  
You now have a working setup that:
- Collects failed login data from a live honeypot VM 🖥️  
- Enriches it with GeoIP details 🌎  
- Visualizes real attack sources in an interactive Attack Map 📊  

---

🛡️ **Next Steps (Optional Enhancements)**
- Add automation with Sentinel **Playbooks** (SOAR).  
- Create alerts for specific attack patterns.  
- Connect with **TheHive** or **Shuffle** for incident response.

---

✨ *Project Completed — Excellent work, Analyst!* ✨


