# Windows Security Event Searches – Splunk SPL

These searches help investigate Windows Security events collected by Splunk Universal Forwarder.

## 1. View Windows Security Events

```spl
index=main sourcetype="WinEventLog:Security"
```

**Purpose:** Displays collected Windows Security events.

## 2. Count Security Events by Event Code

```spl
index=main sourcetype="WinEventLog:Security"
| stats count by EventCode
| sort -count
```

**Purpose:** Identifies which Windows Security event codes appear most frequently.

## 3. Search for Failed Logon Attempts

```spl
index=main sourcetype="WinEventLog:Security" EventCode=4625
```

**Purpose:** Searches for failed Windows logon attempts.

## 4. Search for Successful Logons

```spl
index=main sourcetype="WinEventLog:Security" EventCode=4624
```

**Purpose:** Searches for successful Windows logon events.

## 5. Count Events by Host and Source

```spl
index=main sourcetype="WinEventLog:Security"
| stats count by host, source, sourcetype
```

**Purpose:** Summarizes collected Security events by host and log source.

---

**Note:** These are reusable investigation queries. Event results depend on the available Windows logs and selected time range. The searches are documented for future testing; not every query has necessarily been executed in this lab.
