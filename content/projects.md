---
title: "Projects"
description: "Open-source KQL queries for Microsoft Sentinel and Defender XDR."
showDate: false
showReadingTime: false
showTableOfContents: false
showAuthor: false
showRelatedContent: false
sharingLinks: false
---

All queries live in my [defenderxdr](https://github.com/marvin-rse/defenderxdr) repository and are free to use. If something saves you time, a ⭐ on GitHub is the best thank-you.

## Sentinel cost and sizing

**Conditional Access ingestion analysis**: Correlates daily `AADNonInteractiveUserSignInLogs` ingestion with the number and state of Conditional Access policies, to find the policy changes behind a cost spike. Background in the post [Report-only is not cost-free](/posts/conditional-access-noninteractive-signin-costs/).
[View on GitHub →](https://github.com/marvin-rse/defenderxdr/blob/main/AADNonInteractiveUserSignInLogs/ca-ingestion-analysis.md)

**Entra ID data connector sizing**: Estimates the ingestion volume of the Sentinel Microsoft Entra ID connector *before* you enable it, using Defender XDR Advanced Hunting as a proxy.
[View on GitHub →](https://github.com/marvin-rse/defenderxdr/blob/main/CalculateTableSizeEntra.md)

**Defender table sizing**: Estimates log size and average record size for Defender for Endpoint, Defender for Office 365 and Defender for Cloud Apps tables over the last 30 days, per table and in total.
[View on GitHub →](https://github.com/marvin-rse/defenderxdr/blob/main/CalculateTableSizeMDXDR.md)

## Entra ID sign-ins

**Failed non-interactive sign-ins**: Top apps and top users with failed non-interactive sign-ins, including affected users and client app types.
[View on GitHub →](https://github.com/marvin-rse/defenderxdr/blob/main/AADNonInteractiveUserSignInLogs/aad-failed-signins.md)

## Defender for Endpoint

**mshta.exe outbound hunting**: Surfaces outbound network connections from `mshta.exe` with full parent-process context, to spot LOLBin abuse for payload delivery or command and control.
[View on GitHub →](https://github.com/marvin-rse/defenderxdr/blob/main/SecureScore/mshta-outbound-hunting.md)

**Scheduled scan validation (macOS and Linux)**: Verifies that quick scans actually complete on non-Windows endpoints and visualises the trend, to catch coverage gaps and configuration drift.
[View on GitHub →](https://github.com/marvin-rse/defenderxdr/blob/main/scheduled-scan-validation.md)
