# 04 - Watchlist: GeoIP enrichment

1. Download the geoip CSV used in the lab:
   - https://raw.githubusercontent.com/joshmadakor1/lognpacific-public/refs/heads/main/misc/geoip-summarized.csv
2. In Sentinel → Configuration → Watchlists → + Add watchlist:
   - Name/Alias: `geoip`
   - Source type: Local File (upload the CSV)
   - Number of header rows before data: 0
   - Search Key: `network` (the CSV must have a `network` column that represents IP ranges)
3. Wait for the watchlist to fully import (approx ~54,000 rows in the sample).
4. Test enrichment:
   - Use `queries/query-geoip-lookup.kql` and replace `<ATTACKER_IP>` with an IP from your logs.
   - Run and confirm Country/Region/City columns are present.

Screenshot checklist:
- `12-watchlist-import-count.png`
- `13-ipv4_lookup-result.png`
