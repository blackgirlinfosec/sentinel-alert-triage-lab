# 🛡️ Microsoft Sentinel Alert Triage – Beginner SOC Analyst Lab

## 🎯 Objective
This lab simulates real-world SOC analyst work using Microsoft Sentinel. I investigated a high-severity PowerShell alert, analyzed its context, mapped it to MITRE ATT&CK tactics, and documented my triage decision just like I would on the job.

---

## 📌 Incident Overview

- **Alert Name:** Detect PowerShell Download Activity (Invoke-WebRequest)
- **Severity:** High
- **Status:** New
- **Entities Involved:**
  - User: [Redacted]
  - Host: [Redacted]
  - Process: `powershell.exe -ExecutionPolicy Bypass`

---

## 🧠 MITRE ATT&CK Mapping

- **Execution (T1059.001 – PowerShell)**  
  Indicates that code was executed via PowerShell using bypass techniques.

- **Command and Control (T1071.001 – Web Protocols)**  
  Suggests outbound communication to a remote server, possibly to receive commands or download additional tools.

---

## 🔍 Entity Behavior Findings

Using Sentinel’s **Entity Behavior**, I found:
- 29 previous security alerts tied to this user
- A "Potential Impossible Travel" incident
- A password reset initiated by an admin shortly after the alert

This activity strengthens the case that the alert is serious and not isolated.

---

## 🧭 Investigation Graph

The **Investigation Graph** helped visualize connections between:
- The user account
- The host machine
- The suspicious PowerShell command

This confirmed the alert’s scope and risk.

---

## ⚖️ Triage Decision

- **Classification:** True Positive  
- **Why:** The PowerShell command used a bypass flag, suggesting evasion. Combined with behavioral context and MITRE mapping, this indicates real risk—not just noise.

**Recommended Action:**
- Escalate to Tier 2 or Incident Response
- Investigate for persistence, lateral movement, or exfiltration
- Review sign-in and host activity logs
- Consider isolating the affected host

---

## 🧠 Understanding Alert Classifications

- **True Positive (TP):** A real threat occurred, and the alert caught it
- **False Positive (FP):** Alert looks bad, but the activity is legitimate
- **False Negative (FN):** Real threat happened, but no alert was triggered
- **True Negative (TN):** No threat occurred, no alert — normal behavior

In this case, the alert was a **True Positive**.

---

## 📸 Screenshots Included

- [Sentinel Dashboard Overview](./01-sentinel-dashboard-overview.png)
- [Enabled Data Connector](./02-enabled-data-connector.png)
- [Incident List View](./03-incident-list-view.png)
- [Incident Detail View](./04-incident-detail-view.png)
- [Investigation Graph View](./05-investigation-graph-view.png)
- [Entity Behavior Overview](./06-entity-behavior-overview.png)


---

## 🧾 Analyst Notes

For a full workplace-style triage summary, see [`workplace-summary.txt`](./workplace-summary.txt)

---

## 💡 Reflections

This lab taught me how to:
- Analyze alerts based on behavior, not just tools
- Use MITRE ATT&CK to tell the story of an attack
- Think like a real SOC analyst

PowerShell is a legitimate tool, but when used with flags like `-ExecutionPolicy Bypass`, it can become a weapon. The key is knowing the context — and this lab helped me practice that skill.

