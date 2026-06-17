# Mobile Application Security Analysis with MobSF

## Overview
Static security analysis of 12 Android education applications from the Google Play Store using **MobSF (Mobile Security Framework)** and **AndroToMistLite**. The analysis examined permissions, trackers, insecure coding practices, and OWASP Top 10 vulnerabilities.

## Tools Used
- **MobSF** (via Docker) — static analysis, permission auditing, code analysis
- **AndroToMistLite** — additional Android analysis
- **adb** — APK extraction from physical device (Nothing Phone 1)
- **Python / Matplotlib** — data visualization

## Methodology
1. Selected 12 education apps with 1M+ downloads (Duolingo, Khan Academy, Udemy, Busuu, Brilliant, etc.)
2. Extracted APKs from a physical Android device using `adb`
3. Ran each APK through MobSF for static analysis
4. Analyzed: permissions (dangerous vs. normal), trackers, code vulnerabilities, OWASP Top 10 mapping
5. Identified false positives vs. genuine security concerns

## Key Findings
- **Average security score:** ~49% across all apps
- **Trackers:** 83 total tracker instances found; Analytics and Advertising were the top categories; Busuu had the most (15), Cocomelon had zero
- **Most flagged permissions:** `RECORD_AUDIO`, `READ_EXTERNAL_STORAGE`, `POST_NOTIFICATIONS`
- **Most concerning app:** Knowunity — 12 of 36 permissions flagged as dangerous (33%), including location, contacts, and phone state access unnecessary for an academic help app
- **Unique finding:** Speak & Learn English (Learna) requested `BIND_NOTIFICATION_LISTENER_SERVICE` (signature permission) — allows reading all device notifications, not present in any other app analyzed
- **Best security posture:** Cocomelon (children's app) — minimal permissions, zero trackers
- **Code analysis:** Hardcoded secrets including Google API keys found; insecure coding practices mapped to OWASP Top 10

## Files
- `MobSF_Analysis.pdf` — Full analysis report (in Greek)

## Skills Demonstrated
- Mobile application security assessment
- Android permission analysis and risk classification
- False positive identification
- OWASP Top 10 vulnerability mapping
- Security reporting and documentation
