# Module 3 — AI Follow-up & Compliance Automation

> **Demonstrated using a public library environment.**

## Business Challenge

Organizations often rely on manual processes to monitor deadlines, send reminders, calculate penalties, and follow up on overdue requests. This results in missed deadlines, inconsistent communication, revenue leakage, and increased administrative workload.

## Solution

Designed and built an automated follow-up system that monitors active records, tracks due dates, calculates penalties, and delivers intelligent multi-stage reminders through email and WhatsApp—all without manual intervention.

## Key Capabilities

- Automated deadline monitoring
- Intelligent reminder scheduling
- Multi-stage escalation workflows
- Automatic penalty calculation
- Multi-channel notifications (Email & WhatsApp)
- Automated workflow termination once resolved

## Workflow Overview

### Daily Monitoring
1. A scheduled workflow scans all active records.
2. Due dates and overdue status are calculated automatically.
3. Penalties are generated based on configurable rules.
4. Each record is routed to the appropriate reminder stage.
5. Notifications are delivered automatically.

### Resolution Handling
1. Record status is updated once completed.
2. All pending reminders stop automatically.
3. Workflow history remains available for reporting and auditing.

## Business Impact

- Eliminated manual follow-up processes
- Improved compliance with deadlines
- Reduced missed reminders and administrative workload
- Automated penalty calculations
- Delivered timely customer communications

## Technology Stack

- n8n
- JavaScript
- Google Sheets
- Gmail
- Twilio (WhatsApp)

## Architecture

*(Workflow Screenshot Here)*

## Key Features

- Daily scheduled automation
- Intelligent reminder escalation
- Automatic penalty calculation
- Email & WhatsApp notifications
- Automatic workflow completion when resolved
