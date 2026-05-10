# Phishing-alert-deceptive-mail-detected.md

## Project Overview

In this SOC investigation, I analyzed a phishing alert triggered by **Event ID 257** under the rule **SOC282 - Phishing Alert - Deceptive Mail Detected**. The alert involved a suspicious email sent to a user named Felix with the subject **"Free Coffee Voucher."**

The goal of this investigation was to determine whether the message was legitimate or part of a phishing attempt by reviewing the sender, recipient, message content, suspicious artifacts, and available threat intelligence.

---

## Alert Summary

The alert showed that the email was sent on **May 13, 2024 at 09:22 AM** from **free@coffeeshoop.com** to **felix@letsdefend.io** using SMTP IP **103.80.134.63**.

Additional alert details included:

- **Event ID:** 257
- **Rule Name:** SOC282 - Phishing Alert - Deceptive Mail Detected
- **SMTP Address:** 103.80.134.63
- **Source Address:** free@coffeeshoop.com
- **Destination Address:** felix@letsdefend.io
- **Email Subject:** Free Coffee Voucher
- **Device Action:** Allowed

The device action being marked as **Allowed** meant that the email security control did not block the message at delivery time.

---

## Objective

The objective of this investigation was to determine whether the email was a legitimate message or a phishing attempt by reviewing:

- sender and recipient details
- subject line and message content
- suspicious links or attachments
- threat intelligence and sandbox findings
- overall risk to the user and environment

---

## Tools and Data Reviewed

- LetsDefend alert and case data
- email security details
- suspicious URL / ZIP artifact
- VirusTotal results
- sandbox analysis documented in the report

---

## Key Indicators Observed

The following indicators supported a phishing determination:

- suspicious sender address: **free@coffeeshoop.com**
- recipient: **felix@letsdefend.io**
- suspicious SMTP IP: **103.80.134.63**
- subject line: **Free Coffee Voucher**
- urgency-based wording such as **"Hurry"** and **"This offer expires soon"**
- presence of a suspicious ZIP file / URL
- device action listed as **Allowed**

These indicators suggested that the email was designed to pressure the user into opening a malicious file or clicking a suspicious link.

---

## Investigation Process

### 1. Reviewed the alert

I began by reviewing the alert details, including the rule name, event ID, sender, recipient, SMTP address, subject line, and timestamp. This established the scope of the alert and confirmed that the message had reached the intended recipient.

### 2. Parsed the email

The email content used a reward-themed lure with urgency to pressure the recipient into acting quickly. This is a common phishing tactic designed to reduce suspicion and increase the chance of interaction.

### 3. Checked for links or attachments

The investigation confirmed that the email contained a suspicious URL / attachment in the form of a ZIP file. This significantly increased the likelihood that the message was malicious.

### 4. Analyzed the suspicious artifact

The suspicious URL was checked using VirusTotal, where multiple antivirus engines flagged it as malicious. This supported the conclusion that the email was part of a phishing attempt.

### 5. Reviewed sandbox findings

The documented analysis indicated that the URL imitated an Adobe login page and that the attachment was associated with a malicious **AsyncRAT** variant. Based on those findings, the artifact was treated as malicious.

---

## Verdict

**True Positive – Phishing Attempt**

This alert was determined to be a true positive because the email contained multiple phishing indicators, including a deceptive sender, urgency-driven content, a suspicious ZIP artifact, and supporting threat intelligence that pointed to malicious behavior.

---

## Attacker Perspective

From the attacker’s perspective, this email appears to be a social engineering attempt designed to trick the recipient into opening a malicious ZIP file or interacting with a deceptive link.

The likely attacker goals were:

- malware delivery
- credential theft
- initial access through user interaction

The use of a reward-based message such as a “Free Coffee Voucher” is a simple but effective phishing lure.

---

## Defender Perspective

From a defender’s point of view, this alert required:

- reviewing email metadata
- validating the sender and SMTP source
- identifying suspicious links or attachments
- using threat intelligence tools to assess reputation
- determining whether similar emails were sent to other users
- deciding whether containment or blocking actions were needed

Because the message was marked as **Allowed**, additional follow-up was important to determine whether the user interacted with it.

---

## SOC Relevance

This project reflects a real SOC-style workflow:

- review the alert
- gather evidence
- analyze message content and artifacts
- classify the alert as true positive or false positive
- recommend next actions

This type of investigation is directly relevant to entry-level SOC work because phishing remains one of the most common initial access methods used by attackers.

---

## MITRE ATT&CK Connection

This case aligns most closely with the following MITRE ATT&CK concepts:

- **Phishing** as an initial access technique
- **Malicious file delivery**
- **Credential harvesting** through a deceptive login page

---

## Recommended Remediation Actions

The following actions would be appropriate after confirming the alert as malicious:

- quarantine or remove the email from affected mailboxes
- block the sender address and related domain if confirmed malicious
- block associated URL and file indicators
- notify the recipient and determine whether they interacted with the email
- search for similar phishing messages across the environment
- update detections or user awareness guidance if needed

---

## Lessons Learned

This investigation reinforced several important security lessons:

- phishing emails often rely on urgency and rewards to influence users
- suspicious ZIP files should be treated as high risk
- email security tools may allow malicious messages through
- threat intelligence and sandbox analysis are valuable during alert triage
- documenting findings clearly is an important part of SOC work

---

## Skills Demonstrated

- phishing investigation
- email analysis
- alert triage
- threat detection
- incident analysis
- security monitoring
- defender mindset
- security operations workflow

---

## Summary

This investigation involved analyzing a phishing alert tied to a deceptive email campaign delivering a suspicious ZIP artifact. By reviewing the alert details, parsing the email content, assessing the artifact, and considering supporting threat intelligence, I determined that the alert was a **true positive phishing attempt**.

This project demonstrates my ability to think through an alert from both the attacker and defender perspective and apply a structured SOC investigation process.
