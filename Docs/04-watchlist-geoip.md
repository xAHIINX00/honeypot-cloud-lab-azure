# 🗺️ 04 — Watchlist: GeoIP Enrichment

> 🎯 **Goal:** Import a GeoIP watchlist into Microsoft Sentinel and enrich attacker IPs to identify their geographic origin.

---

## 🔽 Step 1 — Download the GeoIP CSV

Use this sample GeoIP CSV file for the lab:  
`https://raw.githubusercontent.com/joshmadakor1/lognpacific-public/refs/heads/main/misc/geoip-summarized.csv`

> ⚠️ Before uploading, verify the CSV license. If unsure, link to it instead of pushing the file to your repo.

---

## ➕ Step 2 — Add a Watchlist in Sentinel

1. Azure Portal → **Microsoft Sentinel → Configuration → Watchlists**
2. Click **+ Add watchlist**
3. Configure:  
   - **Name:** `GeoIP`  
   - **Alias:** `geoip` (_used in KQL as `_GetWatchlist("geoip")`_)  
   - **Source type:** Local file → Upload the CSV  
   - **Header rows before data:** `0`  
   - **Search key:** `network` (the CSV must include a `network` column in CIDR format such as `8.8.8.0/24`)
4. Click **Create** and wait a few minutes for the import to finish.

<p align="center">
  <img src="https://github.com/xAHIINX00/honeypot-cloud-lab-azure/blob/e15c64bdd5afcf0850b63144a18afae7b462933e/watchlist.png"/>
</p>
---

## 🔎 Step 3 — Test GeoIP Enrichment (KQL)

Run this in Sentinel → **Logs**.  
Replace `<ATTACKER_IP>` with an IP found from `query-4625.kql`.
