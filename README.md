# Elevate Labs Cyber Security Internship

 ### Elevate Labs Cyber Security Internship-Task 4: Firewall Configuration and Traffic Filtering

## Objective
The objective of this task is to configure and test basic firewall rules to learn how to allow or block network traffic. This task provides hands-on experience in managing network security via the Windows Firewall and PowerShell environment.

## Tools Used
* **Operating System:** Windows.
* **Tool:** Windows PowerShell (Run as Administrator).


## 🛠️ Task Execution & Technical Steps

The following technical security steps were performed to configure, audit, and manage active host-based firewall rules on the system:

### 1. Check Firewall Status
Verified the current configuration status across all primary network tracking profiles to establish a baseline.
* **Command:** `Get-NetFirewallProfile | Select-Object Name, Enabled`
* **Evidence:** Documented in the top section of `firewall_profile_and_block.png`.

### 2. Block Inbound Traffic (Telnet - Port 23)
Created an explicit inbound protection rule to block traffic on port 23, mitigating risks associated with the unencrypted and insecure Telnet protocol.
* **Command:** `New-NetFirewallRule -DisplayName "Block Telnet" -Direction Inbound -LocalPort 23 -Protocol TCP -Action Block`
* **Evidence:** Successfully executed and logged at the bottom section of `firewall_profile_and_block.png`.

### 3. Allow Inbound Traffic (SSH - Port 22)
Created a standard inbound rule to permit secure encrypted traffic over port 22 specifically for automated SSH utility access.
* **Command:** `New-NetFirewallRule -DisplayName "Allow SSH" -Direction Inbound -LocalPort 22 -Protocol TCP -Action Allow`
* **Evidence:** Captured during rule object creation in `allow_ssh_rule.png`.

### 4. Verify Firewall Rules
Queried the Advanced NetSecurity database schema to verify that the specified configuration profile rules were accurately deployed and functional.
* **Command:** `Get-NetFirewallRule -DisplayName "Block Telnet"`
* **Evidence:** Active validation state shown in the top half of `rule_verification_and_removal.png`.

### 5. Cleanup (Restore Baseline State)
Flushed the custom test staging parameters to return the terminal environment safely back to its baseline infrastructure posture.
* **Command:** `Remove-NetFirewallRule -DisplayName "Block Telnet"`
* **Evidence:** Deletion verification execution trace logged at the bottom of `rule_verification_and_removal.png`.


## 📊 Verification Evidence Logs

The specific execution states and configuration profiles achieved throughout this lab assignment are validated by the following repository assets:

* **`firewall_profile_and_block.png`** — Validates active Domain, Private, and Public profile filtering statuses alongside the successful deployment parameters of the inbound `Block Telnet` rule entry.
* **`allow_ssh_rule.png`** — Documents full object creation schema traces and the functional activation parameters for the secure `Allow SSH` path entry.
* **`rule_verification_and_removal.png`** — Displays dynamic rule query verification details followed by the baseline cleanup script block execution.


## 📝 Summary & Key Takeaways
A firewall acts as a critical network security filter that continuously monitors and controls incoming or outgoing traffic paths based on predefined rules. By restricting unnecessary or unencrypted system ports (like Telnet) and approving only authenticated operational channels (like SSH), a host firewall significantly optimizes security postures and cuts down the machine's accessible threat surface.
