# 02 - Create the Honeypot VM (Windows)

1. In Azure Portal → Search: Virtual machines → + Create.
2. Choose Windows 10 (or another Windows image).
3. Select a small VM size for cost control (e.g., B1ms/B2s) 
4. Create or choose a Resource Group.
5. In **Networking**: Create or choose an NSG that allows inbound traffic (for the honeypot you intentionally allow inbound).
   - Add a rule to allow all inbound (for lab only) — capture a screenshot of the NSG rules.
6. After VM creation, connect via RDP.
7. On the VM: open `wf.msc` and turn off/disable Windows Firewall (lab only).

**Why we do this**
- Honeypots are intentionally open to attract attackers so we can observe attacker behavior.
