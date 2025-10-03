# honeypot-cloud-lab-azure

This project demonstrates how to build a cloud honeypot in Microsoft Azure, collect logs to a central Log Analytics Workspace (LAW), enrich logs with GeoIP data using a Sentinel Watchlist, and visualize attacker origins with an Attack Map workbook.

**What you'll get in this repo**
- Step-by-step docs to reproduce the lab (beginner friendly).
- KQL queries to find failed logins (EventID 4625) and enrich them with geoip.
- `resources/map.json` — a workbook template you can import into Microsoft Sentinel.
- Example screenshots list and filenames to include in `docs/screenshots/`.
