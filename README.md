# Elastic Defend EDR Lab

## About

I'm building this home lab to get hands-on experience with EDR and learn how a SOC analyst investigates endpoint alerts.

I'm using Elastic Defend on Lubuntu to investigate suspicious activity, examine process and parent-process details, and trace file paths through security events.

## Lab Architecture

The lab uses a Lubuntu endpoint for testing and an Elastic Cloud Serverless project to review security alerts and endpoint events.

```
┌──────────────────────────────┐
│       Lubuntu Endpoint       │
│                              │
│  Suspicious File / Activity  │
└──────────────┬───────────────┘
               │
               ▼
┌──────────────────────────────┐
│        Elastic Agent         │
│                              │
│    Endpoint Telemetry        │
└──────────────┬───────────────┘
               │
               ▼
┌──────────────────────────────┐
│     Elastic Cloud Project    │
│                              │
│       Elastic Defend         │
│       Elastic Security       │
└──────────────┬───────────────┘
               │
               ▼
┌──────────────────────────────┐
│      Alert Investigation     │
│                              │
│  Process and Parent Process   │
│  File Path and Event Details │
└──────────────┬───────────────┘
               │
               ▼
┌──────────────────────────────┐
│     Findings and Evidence    │
│                              │
│    Screenshots and Reports   │
└──────────────────────────────┘
```

## What I've Done

- Set up Elastic Defend in my Elastic Cloud project.
- Investigated a security alert.
- Examined process and parent-process details.
- Followed the file path shown in the event.
- Checked the Lubuntu `/tmp` directory for the suspected file.
- Documented the investigation findings.

## Investigation Finding

An alert was generated, but the suspected file was not found in the Lubuntu `/tmp` directory during my subsequent check.

## Tools Used

- Elastic Defend
- Elastic Security
- Elastic Agent
- Lubuntu Linux
- Elastic Cloud Serverless

## Repository Structure

- `architecture/` — Lab architecture and workflow
- `screenshots/` — Evidence collected during investigations
- `reports/` — Investigation reports and findings

## Project Status

This is an ongoing home lab. I'll continue adding investigation scenarios and documenting what I learn about endpoint detection and response.
