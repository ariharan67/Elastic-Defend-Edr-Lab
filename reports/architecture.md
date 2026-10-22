# Elastic Defend EDR Lab — Architecture

## 1. Project Overview

This project demonstrates endpoint detection and response (EDR) using Elastic Defend on a Lubuntu endpoint. The lab focuses on process investigation, file activity monitoring, security alert analysis, and evidence-based incident reporting.

## 2. Lab Architecture

Lubuntu Endpoint
       |
       v
Elastic Agent
       |
       v
Elastic Cloud Serverless
       |
       v
Elastic Defend Integration
       |
       v
Security Alerts and Event Logs
       |
       v
Investigation and Documentation


## 3. Lab Components
_________________________________________________________________________________________________
| Component                | Purpose                                                            |
|__________________________|____________________________________________________________________|
|                          |                                                                    |
| Lubuntu                  | Endpoint used for security testing and investigation               |
| Elastic Agent            | Collects endpoint telemetry and sends it to Elastic                |
| Elastic Defend           | Provides endpoint security monitoring and protection               |
| Elastic Cloud Serverless | Central platform for reviewing security events                     |
| Elastic Security         | Used to inspect alerts, process activity, and event details        |
|_______________________________________________________________________________________________|

## 4. Investigation Workflow

1. Generate or observe a security alert.
2. Review the alert details and timestamp.
3. Examine the process and parent-process information.
4. Identify the file path associated with the activity.
5. Search for related events in Elastic.
6. Check the relevant file location on the Lubuntu endpoint.
7. Correlate endpoint observations with Elastic event evidence.
8. Document the findings and investigation outcome.

## 5. Investigation Finding

A security alert was generated, and the suspected file was not found in the Lubuntu '/tmp' directory during subsequent inspection.

The absence of the file was recorded as an endpoint observation. Any conclusion about successful prevention or quarantine must be supported by the corresponding Elastic event evidence.

## 6. Evidence Collection

The investigation evidence may include:

- Security alert details and timestamp
- Process and parent-process information
- Suspected file path
- Related endpoint events
- Terminal output showing the file-location check
- Investigation notes and screenshots

## 7. Project Objective

The objective is to develop practical EDR investigation skills by correlating security alerts, endpoint observations, and process activity to produce clear, evidence-based incident reports.