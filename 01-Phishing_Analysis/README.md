# Phishing Email Investigation — BTLO (Blue Team Labs Online)

***Challenge:*** Phishing Analysis 2
***Platform:*** Blue Team Labs Online
***Difficulty:*** Easy

## Objective
Analyze a suspicious email impersonating Amazon and identify phishing indicators.

## Tools Used
- Apple Mail
- macOS Terminal
- TextEdit
- Base64 decoding
- HTML source inspection

## Investigation

### Email Header Analysis
Inspected raw email headers to identify timestamps and email metadata.

### URL Investigation
Examined Microsoft Safe Links and decoded the underlying destination URL. Identified a suspicious domain impersonating Amazon.

### Base64 Decoding
Identified Base64 encoded email content and decoded the HTML portion using Terminal.

### HTML Analysis
Examined HTML source code to identify image references and embedded hyperlinks.

## Findings
- The email impersonated Amazon.
- The message used urgency to encourage account verification.
- The destination URL contained a misspelled brand name.
- The HTML contained external image and hyperlink references.

## Lessons Learned
Learned how to inspect raw email content, decode Base64, analyze URLs, and extract phishing indicators.
