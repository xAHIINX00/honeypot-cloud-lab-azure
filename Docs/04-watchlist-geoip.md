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

## ⏳ Step 3 — Wait for Import to Complete

The watchlist can take several minutes to process and become queryable.  
Once ready, it will appear in your Sentinel workspace under **Watchlists**.

✅ **Verify:** You should see a status **“Succeeded”** and your alias **`geoip`** listed.

---

## 🔎 Step 4 — Test GeoIP Enrichment (Single IP)

We’ll enrich failed login (EventID 4625) logs with GeoIP data to show where attackers are coming from.

1. Go to **Microsoft Sentinel → Logs**.
2. Paste this KQL query (or open `queries/query-geoip-lookup.kql`):
3. Replace `<ATTACKER_IP>` with an IP observed from `query-4625.kql`.

<p align="center">
  <img src="https://github.com/xAHIINX00/honeypot-cloud-lab-azure/blob/00b33601ca2adc582cb89f23cfa73452a80c5464/GeoIp-Lookup.png"/>
</p>

## Step 5️⃣  Enrich & Summarize All Recent Events (KQL)
// Purpose: Summarize all failed login attempts by country/region for visualization

<p align="center">
  <img src="https://github.com/xAHIINX00/honeypot-cloud-lab-azure/blob/24db7615bae86e85f13570f282fb554564e752d3/Chart%20Logs.png"/>
</p>
