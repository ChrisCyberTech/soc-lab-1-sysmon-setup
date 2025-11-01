# SOC Lab 1 – Sysmon Setup

## 🎯 Objective  
Install, configure, and validate **Sysmon** logging on two Windows endpoints (**Workstation01** and **DC01**) as the foundation for future labs involving Windows Event Forwarding (WEF) and SIEM ingestion.

This lab demonstrates:
- Proper Sysmon deployment
- Event validation (ProcessCreate, FileCreate, NetworkConnect, DNS Query, etc.)
- Export of raw `.evtx` event logs for offline analysis
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

### 📂 Workstation01 Artifacts

| File | Purpose |
|------|---------|
| `Sysmon-Operational.evtx` | Raw exported Sysmon log |
| `SysmonVersion.txt` | Version + config hash output |
| `sysmonconfig.xml` | Config ruleset in use |
| `testfile.txt` | Generated FileCreate event |
| `LocaleMetaData` | Auto-generated metadata folder |

📁 **Path:** `C:\Lab\SOC1\Evidence\`

---

### 🖼️ Screenshot Index (Workstation01)

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

---

## 🔹 System 2: DC01 (Domain Controller)

### ✅ Sysmon Installation & Validation

| Task | Status | Evidence |
|-------|--------|----------|
| Created folders under `C:\Tools\Sysmon` and `C:\Lab\SOC1\Evidence` | ✅ | Screenshot |
| Placed Sysmon + config into folder | ✅ | Screenshot |
| Installed Sysmon using config (`-accepteula -i sysmonconfig.xml`) | ✅ | Screenshot |
| Confirmed Sysmon service running (`Get-Service sysmon64a`) | ✅ | Screenshot |
| Verified config + schema (`.\Sysmon64a.exe -c`) | ✅ | `SysmonVersion` file |

---

### ✅ Event Verification (Sysmon Operational Log)

| Event ID | Purpose | Confirmed | Notes |
|----------|----------|-----------|-------|
| **1** | Process Create | ✅ | Seen after running PowerShell + test file |
| **3** | Network Connect | ✅ | Triggered by Edge browser launch |
| **11** | File Create | ❌ *(skipped for DC01)* | Not required |

---

### 🗂️ Evidence Collected (DC01)

| File | Description |
|-------|-------------|
| `SysmonVersion` | Output of `.\Sysmon64a.exe -c` |
| `testfile.txt` | Trigger file for ProcessCreate test |
| `Sysmon-Operational.evtx` | Exported Sysmon log |

📁 **Path:** `C:\Lab\SOC1\Evidence\`

---

### 🖼️ Screenshot Index (DC01)

SOC1-01_DC01_CreateFolders.png
SOC1-02_DC01_SysmonFiles.png
SOC1-03_DC01_InstallCommand.png
SOC1-04_DC01_ServiceRunning.png
SOC1-05_DC01_EventLogEnabled.png
SOC1-06_DC01_SysmonVersion.png
SOC1-07_DC01_ConfigDump.png
SOC1-08_DC01_TestEvents.png
SOC1-09_DC01_ExportedLog.png

yaml

---

## 🔜 Next Steps (SOC Lab Series)

| Lab | Title | Focus |
|------|-------|-------|
| SOC Lab 2 | Windows Event Forwarding (WEF) | Forward Sysmon logs from endpoints → DC |
| SOC Lab 3 | SIEM Ingest | Send forwarded logs into SIEM (Splunk, Elastic, LimaCharlie, etc.) |
| SOC Lab 4 | Detection Lab | Write Sigma rules and alert on Sysmon events |

---

## 📎 Notes

- Sysmon version deployed: **v15.15**
- Schema validated: **4.90**
- Config based on SwiftOnSecurity ruleset
- Logs confirmed for Process, Network, and DNS activity
- All evidence stored locally and committed to GitHub

---

🔧 *Built as part of an ongoing security analyst portfolio demonstrating endpoint telemetry, log handling, and detection engineering fundamentals.*
