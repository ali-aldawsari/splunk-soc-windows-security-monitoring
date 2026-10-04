 Splunk SOC - Windows Security Monitoring

A practical SOC lab built with Splunk to collect, monitor, detect, and investigate Windows Security Events.

 Overview

This project demonstrates a hands-on Security Operations Center (SOC) workflow using Splunk and Windows Event Logs.

The lab focuses on detecting and investigating failed Windows logon attempts, particularly Event ID 4625, and presenting the findings through Splunk searches and a SOC monitoring dashboard.

 Lab Objectives

- Collect Windows Event Logs into Splunk
- Monitor Windows Security Events
- Detect failed authentication attempts
- Investigate Event ID 4625
- Analyze affected accounts and source information
- Identify common failure reasons
- Build a basic SOC monitoring dashboard

 Lab Environment

| Component | Details |
|---|---|
| SIEM | Splunk Enterprise |
| Operating System | Windows |
| Log Source | Windows Event Logs |
| Main Event | Event ID 4625 |
| Log Index | `default` |
| Data Source | `WinEventLog:Security` |

 SOC Investigation Workflow

Log Collection → Detection → Triage → Investigation → Analysis → Dashboard

 Detection

The primary detection used in this lab is Windows Event ID 4625**, which indicates a failed logon attempt.

 ## Detection

The primary detection used in this lab is Windows **Event ID 4625**, which indicates a failed logon attempt.

### Search

```spl
source="WinEventLog:Security" EventCode=4625
```

## Analysis Queries

### Count Failed Logons

```spl
source="WinEventLog:Security" EventCode=4625
| stats count
```

### Failed Logons by Account

```spl
source="WinEventLog:Security" EventCode=4625
| stats count by Account_Name
| sort - count
```

### Failed Logons by Failure Reason

```spl
source="WinEventLog:Security" EventCode=4625
| stats count by Failure_Reason
| sort - count
```

### Failed Logons by Source Address

```spl
source="WinEventLog:Security" EventCode=4625
| stats count by Source_Network_Address
| sort - count
```
