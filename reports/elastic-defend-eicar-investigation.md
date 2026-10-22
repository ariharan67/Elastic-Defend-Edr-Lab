# Elastic Defend EDR Lab — Malware Prevention Alert Investigation

## 1. Project Overview

 Project: Endpoint Detection and Response (EDR) Investigation  
 Platform: Elastic Security Serverless  
 Endpoint: Lubuntu Linux  
 Detection technology: Elastic Defend  
 Test artifact: EICAR antivirus test file  
 Alert severity: High  
 Investigation date: October 22, 2026  
Alert timestamp: 23:06:10.276 -

## 2. Executive Summary

This investigation evaluated Elastic Defend's detection capabilities using the EICAR antivirus test file, a harmless test artifact designed to exercise antivirus detection.

During the test, Elastic Security generated a High-severity alert titled "Malware Prevention Alert." The alert associated the file `EICAR.com.txt` with the `curl` process, whose parent process was `bash`.

After reviewing the alert, I checked the `/tmp` directory on the Lubuntu endpoint. The test file was not present when I performed the subsequent check.

The investigation confirmed that Elastic Security generated a malware-related alert. However, the available evidence does not conclusively establish whether Elastic Defend blocked, quarantined, or removed the file.

## 3. Lab Architecture

The lab consists of the following components:

- Endpoint: Dell laptop running Lubuntu.
- Endpoint protection: Elastic Agent with Elastic Defend.
- Security monitoring: Elastic Security Serverless.
- Analyst workstation: Browser used to access Elastic Security and investigate alerts.

The endpoint sends security telemetry to Elastic Security, where the analyst reviews alerts and investigates process and file activity.

## 4. Test Scenario

 Objective: Generate a controlled antivirus test event and investigate the resulting alert.

The EICAR test file was requested using `curl` from a Bash shell.

The process relationship observed in the alert was:


bash
 └── curl
      └── EICAR test-file download attempt


This process relationship identifies the shell and download utility involved in the test. It does not, by itself, indicate malicious intent.

## 5. Alert Evidence

The following values were observed during the investigation.
________________________________________________________
| Field               | Observed value                 |
|_____________________|________________________________|
|                     |                                |
| Alert name          | Malware Prevention Alert       |
| Severity            | High                           |
| Alert status        | Active                         |
| File name           | "EICAR.com.txt"                |
| Process name        | curl                           |
| Parent process name | bash                           |
| Parent executable   | /usr/bin/bash                  |
| Event category      | file                           |
| Event action        | modification                   |
| Event outcome       | success                        |
| Event type          | change, denied, info           |
| User                | steve07                        |
| Timestamp           | October 22, 2026, 23:06:10.276 |
|_____________________|________________________________|

 Evidence interpretation: These values describe the observed event. In particular, "event.outcome: success" does not establish that malware prevention succeeded. The exact operation represented by that field must be verified against the relevant event.

## 6. Investigation Timeline

 Step 1 — Generate the test event

       The EICAR test file was requested using `curl` on the Lubuntu endpoint.

 Step 2 — Review the security alert

       Elastic Security displayed a High-severity alert named `Malware Prevention Alert`.

 Step 3 — Examine process telemetry

       I reviewed the process name, parent process, file name, and other event fields to understand the activity associated with the alert.

 Step 4 — Verify file presence

       I checked the "/tmp" directory after the alert appeared. The file "EICAR.com.txt" was not present during that check.

 Step 5 — Assess the evidence

       I compared the alert details with the filesystem observation. Although the file was missing, the available evidence did not identify exactly why it was absent.

## 7. SOC Analyst Assessment

 1) Confirmed findings

- Elastic Security generated a High-severity malware-related alert.
- The alert associated the EICAR test file with "curl".
- The recorded parent process was "bash".
- The alert status was Active at the time of review.
- The file was not found in "/tmp" during a subsequent check.

 2) Unconfirmed findings

- Whether Elastic Defend blocked the initial download.
- Whether the file was quarantined or removed by endpoint protection.
- Why the file was absent during the later filesystem check.
- Whether the event outcome describes a successful download or another operation.

 3) Investigation verdict

**Detection observed; prevention outcome unverified.**

  A missing file is not sufficient evidence to attribute its disappearance to Elastic Defend. A conclusive prevention finding requires an explicit prevention action or equivalent supporting telemetry.

## 8. MITRE ATT&CK Mapping

  No adversary technique is assigned in this report.

  The activity was a controlled EICAR test, and the collected evidence does not demonstrate a real intrusion, malicious code execution, or persistence. Mapping the test directly to an adversary technique without additional evidence could misrepresent the findings.

## 9. Lessons Learned

This investigation provided practical experience with:

- Reviewing High-severity alerts in Elastic Security.
- Examining process and parent-process relationships.
- Investigating file-related event telemetry.
- Checking endpoint filesystem state.
- Distinguishing an alert from a confirmed prevention action.
- Writing an evidence-based SOC investigation report.

 **Key takeaway: Detection and prevention are separate security outcomes. An alert shows that a detection occurred; explicit prevention evidence is needed to confirm that the endpoint blocked or removed a threat.

## 10. Recommended Evidence Attachments
 

1. /screenshots/maleware-alert.png — the High-severity Malware Prevention Alert.
2. /screenshots/alert-investigations.png — the event fields showing the file and process details.
3. /screenshots/filesystem-check.jpeg — the terminal output from the "/tmp" directory check.


## 11. Project Conclusion

This project demonstrates a basic EDR alert-investigation workflow using Elastic Security and Elastic Defend on a Lubuntu endpoint.

The test generated a malware-related alert and provided an opportunity to examine process telemetry and verify the file's later presence on disk. The investigation also highlighted an important SOC principle: conclusions must be based on verified evidence rather than assumptions.

---

  Project classification: Defensive security lab  
  Test type: Controlled antivirus test  
  Outcome: Alert generated; suspect file not found on the endpoint when checked; no confirmed prevention
