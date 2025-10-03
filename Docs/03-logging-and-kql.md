# 03 - Logging, DCR and simple KQL

1. Create a Log Analytics Workspace (LAW):
   - Portal → Log Analytics Workspaces → + Create.
2. Create Microsoft Sentinel:
   - Portal → Microsoft Sentinel → + Add → Select the LAW you created.
3. Connect the VM to the workspace:
   - Use the "Windows Security Events via AMA" connector (or install the Azure Monitor Agent and DCR to collect Security events).
   - Create a Data Collection Rule (DCR) in Sentinel if prompted; this may trigger an extension installation on the VM.

4. Generate test events:
   - On VM, attempt 3 failed logins using a non-existent user (e.g., `employee`). Check Event Viewer → Windows Logs → Security → EventID 4625.

5. Query logs (use `queries/query-4625.kql`):
   - Open Sentinel → Logs and paste the KQL.
   - Adjust time range to "Last 24 hours" or as needed.

Screenshot checklist for this doc:
- `05-eventviewer-4625.png`
- `07-law-overview.png`
- `09-windows-connector-config.png`
- `11-kql-query-4625.png`
