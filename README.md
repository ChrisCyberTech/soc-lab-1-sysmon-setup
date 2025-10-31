# SOC Lab 1 – Sysmon Setup

## 🎯 Objective
Install, configure, and validate **Sysmon** logging on two Windows endpoints (**Workstation01** and **DC01**) as the foundation for later Windows Event Forwarding (WEF) and SIEM ingestion.

This lab demonstrates:
- Proper Sysmon deployment
- Event validation (ProcessCreate, FileCreate, NetworkConnect, DNS Query, etc.)
- Export of raw `.evtx` event logs for analysis
- Evidence collection for security portfolio documentation

---

## 🖥️ Machines Used

| Hostname        | OS                  | Role                |
|-----------------|---------------------|---------------------|
| Workstation01   | Windows 11 Pro      | Client Endpoint     |
| DC01            | Windows Server      | Domain Controller   |

---

## ✅ Workstation01 Progress Checklist

| Step | Status | Description |
|------|--------|-------------|
| A1 | ✅ | Created `C:\Tools\Sysmon` and `C:\Lab\SOC1\Evidence` folders |
| A2 | ✅ | Placed Sysmon executable + config file |
| A3 | ✅ | Installed Sysmon using config |
| A4 | ✅ | Verified Sysmon service is running |
| A5 | ✅ | Enabled **Sysmon Operational** event log |
| A6 | ✅ | Captured Sysmon version + config hash |
| A7 | ✅ | Generated test events (ProcessCreate, FileCreate, NetworkConnect) |
| A8 | ✅ | Exported Sysmon-Operational.evtx log |
| A9 | ✅ | Collected artifacts into Evidence folder |

---

## 📂 Workstation01 Artifacts

| File | Purpose |
|------|---------|
| `Sysmon-Operational.evtx` | Raw exported Sysmon log |
| `SysmonVersion.txt` | Version + config hash output |
| `sysmonconfig.xml` | Config ruleset in use |
| `testfile.txt` | Generated FileCreate event |
| `LocaleMetaData` | Auto-generated metadata folder |

Artifacts stored in:

C:\Lab\SOC1\Evidence\

yaml
Copy code

---

## 🖼️ Screenshot Index (Workstation01)

SOC1-01_Workstation01_CreateFolders.png
SOC1-02_Workstation01_SysmonFiles.png
SOC1-03_Workstation01_InstallCommand.png
SOC1-04_Workstation01_ServiceRunning.png
SOC1-05_Workstation01_EventLogEnabled.png
SOC1-06_Workstation01_SysmonVersion.png
SOC1-07_Workstation01_ConfigDump.png
SOC1-08_Workstation01_TestEvents.png
SOC1-09_Workstation01_ExportedLog.png
SOC1-10_Workstation01_ArtifactsFolder.png

yaml
Copy code

---

## 🔜 Next Steps

### ✅ Continue Sysmon setup on: `DC01`

### 📌 Upcoming Labs in SOC Series

| Lab | Title | Focus |
|------|-------|-------|
| SOC Lab 2 | Windows Event Forwarding (WEF) | Forward Sysmon logs from endpoints → DC |
| SOC Lab 3 | SIEM Ingest | Send forwarded logs into SIEM (Splunk, Elastic, LimaCharlie, etc.) |
| SOC Lab 4 | Detection Lab | Write Sigma rules and alert on Sysmon events |

---

## 📎 Notes

- Sysmon version installed: **v15.15**
- Schema version validated: **4.90**
- Config used: SwiftOnSecurity-based ruleset
- DNS, Network, Process, and File events confirmed
- All screenshots and evidence stored locally and in GitHub repo

---

🔧 *Built as part of a growing security analyst portfolio showcasing endpoint telemetry, log handling, and detection engineering fundamentals.*
