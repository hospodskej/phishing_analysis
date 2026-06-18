# Phishing Email Analysis Toolkit

A Python-based framework for standardized investigation of phishing emails. Built for SOC analysts and DFIR teams to streamline triage, header analysis, authentication validation, and reporting.

## Features

- Parses `.eml` files (multipart, base64, quoted-printable, 7bit, 8bit)
- Extracts and analyzes all email headers
- Detects display name and domain spoofing (From vs Return-Path vs Reply-To)
- Validates SPF, DKIM, and DMARC records via live DNS queries
- Geo-locates sender IP address
- Extracts and defangs URLs from HTML and plain text bodies
- Reads Exchange Online Protection spam/phishing scores (SCL, PCL, BCL)
- Generates detailed Markdown reports with verdict and actionable recommendations

## Samples

+------------------------------------+------------------------------------------+------------+-----------------------------------------------------------------------+
| File                               | Type                                     | Language   | Indicators                                                            |
+------------------------------------+------------------------------------------+------------+-----------------------------------------------------------------------+
| bradesco_livelo_phish.eml          | Credential harvester (bank rewards scam) | Portuguese | Domain mismatch, SPF fail, DMARC missing, DigitalOcean VPS origin     |
| microsoft_unusual_signin.eml       | Credential harvester (Microsoft account) | English    | Domain mismatch, Reply-To Gmail, SPF none, DKIM none, tracking pixel |
| zonnepanelen_phish.eml             | Data collection scam (solar panel quotes)| Dutch      | Three-domain mismatch, SPF none, DKIM none, DMARC none, click tracker|
| legit_google_alert.eml             | Legitimate security notification         | English    | All authentication passes, no mismatch (for comparison)               |
+------------------------------------+------------------------------------------+------------+-----------------------------------------------------------------------+
