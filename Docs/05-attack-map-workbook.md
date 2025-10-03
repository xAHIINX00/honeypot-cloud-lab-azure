# 05 - Attack Map Workbook

1. Open Sentinel → Workbooks → + Add workbook.
2. Click **Advanced Editor** and paste the contents of `resources/map.json`.
3. Save the workbook (give a name e.g., "Honeypot Attack Map").
4. Open the newly saved workbook, set time range, and click Apply.

If the map doesn't show coordinates:
- Confirm the `geoip` watchlist has latitude/longitude columns or Country/Region/City columns that the workbook uses.
- Confirm `SecurityEvent` logs contain the attacker IP and that the query in the workbook is retrieving `IpAddress`.

Screenshot checklist:
- `14-workbook-advanced-editor-json.png`
# 15-attack-map-final
- <p align="center">
  <img src="https://github.com/xAHIINX00/honeypot-cloud-lab-azure/blob/21db1a23507c21e472c7356ce3d1af046bf956b4/Attack-Map.png"/>
</p>
