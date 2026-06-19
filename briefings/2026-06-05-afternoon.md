# Afternoon Briefing — Friday, June 05, 2026

*Corrective content rebuild — regenerated 2026-06-19 from live Outlook data. Scan window: 2026-06-05 07:30 → 13:30 CDT. Calendar is authoritative; no calendar writes were made.*

## 🟥 HOT ITEMS
- **CelLink (Georgetown/San Carlos) maintenance window — TOMORROW, Sat Jun 06, 9:00 AM CST.** Ted Do (CelLink IT) sent the run-of-show. **Marshall owns:** generate new SSL cert, point to GT RADIUS, switch SC FW → GT FW, and DUO → GT RADIUS. **Pre-window action required:** promote local/secondary RADIUS to primary for Georgetown SSIDs or Wi-Fi auth fails while the IPsec tunnel is down.
- **Barracuda XDR — Meraki log ingestion degraded (ARIA_Med / aria5468).** SOC ticket #126911311 awaiting response; "no events received from cisco.meraki 192.168.128.9" for ~15+ days. SOC asks to confirm syslog forwarding to collector 10.0.0.4 port 9221 (run tcpdump on the Ubuntu collector). Security-monitoring gap on a medical client.
- **Possible email security incidents:** HelpDesk ticket #10372 "possible email hack" (multiple updates) and #10371 mail-delivery failure (Covenant member Susan Zatopek) — review for compromise vs. mailflow.

## A — New Emails
| Subject | Sender | Summary | Received (CDT) |
|---|---|---|---|
| FW: IT Maintenance Window | Ted Do (CelLink) | Run-of-show for Sat 6/6 9 AM CST pre-move maintenance; Marshall owns SSL cert, GT RADIUS, FW cutover, DUO; pre-window RADIUS promotion required to avoid GT Wi-Fi auth outage. | Jun 05, 10:01 AM |
| Ticket 126911311 awaiting your response: GLB.SM.UNI Log Monitoring Degradation | SOC (Barracuda) | XDR alert: Meraki log ingestion stalled for ARIA_Med (~15+ days); SOC requests confirmation of syslog forwarding / tcpdump on collector. Security data-source gap. | Jun 05, 10:02 AM |
| [ariat] HelpDesk tickets (RMM) | support@rmmservice.com | 19 ticket update notifications. Distinct tickets: **#10372 possible email hack**, **#10371 mail not delivering (S. Zatopek/Covenant)**, **#10370 email issues**, #10368 Josh's computer, #10374 FW: RRC engagement, #10375 Abbigail Timeslips, #10356 DKIM, #10354 New Computer/VPN, #10353 Splashtop, #10351 2026 Terminations, #10361 Setting up scanner, #10360 Wi-Fi connectivity, #10358 Download App. | Jun 05, 9:28 AM–1:28 PM |
| You have tasks due today | noreply@planner.office365.com | Automated Planner reminder: "M365 Security Policy Plan Debrief" due today (M365 Security Policies plan). FYI. | Jun 05, 7:47 AM |
| Next week: Global MSP Day 2026 | respondto@barracuda.com | Marketing — Barracuda webinar invite for Jun 10. FYI only. | Jun 05, 10:28 AM |
| Test | admin@whiteheadwilson.com | Test message from Whitehead Wilson admin; no content/action. | Jun 05, 12:05 PM |

## B — Action Items Still Open
| Priority | What's needed | From | Deadline |
|---|---|---|---|
| 🔴 Critical | Pre-stage CelLink maintenance: generate new SSL cert, promote GT secondary RADIUS to primary, prep SC→GT FW + DUO cutover | Ted Do (CelLink) | Before Sat 6/6 9:00 AM CST |
| 🟠 High | Respond to Barracuda SOC #126911311 — verify Meraki syslog forwarding to collector 10.0.0.4:9221 (tcpdump on Ubuntu collector) for ARIA_Med | Barracuda SOC | ASAP (open ~15+ days) |
| 🟠 High | Investigate ticket #10372 "possible email hack" — confirm compromise vs. false alarm, secure account | RMM / client | Today |
| 🟡 Medium | Resolve #10371 — Susan Zatopek (Covenant) emails not delivering; check mailflow/quarantine | RMM / client | Today |
| 🟡 Medium | Work #10374 FW: RRC engagement, #10370 email issues, #10356 DKIM, and remaining open RMM tickets | RMM / clients | This week |
| 🔵 Low | Planner: complete "M365 Security Policy Plan Debrief" task due today | Planner | Today |

## C — EOD Plan
**MUST FINISH TODAY** (hard deadlines / Critical+High)
- Pre-stage all CelLink Saturday-window prep (SSL cert, GT RADIUS promotion, FW/DUO readiness) — Wi-Fi auth risk if RADIUS not promoted beforehand.
- Reply to Barracuda SOC #126911311 and validate Meraki log forwarding for ARIA_Med.
- Triage ticket #10372 possible email hack.

**CARRY TO TOMORROW**
- Execute the CelLink Georgetown/San Carlos maintenance window (Sat 6/6, 9 AM CST).
- Lower-priority RMM tickets (#10356 DKIM, #10361 scanner, #10358 app, #10360 Wi-Fi, #10375 Timeslips).

## D — Teams
> ⚠️ Teams partial — repeated Microsoft Graph throttling (429) prevented retrieving the full afternoon scan; oldest ~07:30–07:47 CDT slice not confirmed. Check manually.

Retrieved messages: active 1:1 with Matt Kerker (mostly casual banter — "Friday", a "John Quinlan" bit, Whitehead TV-mount complaint, a device/phone-number troubleshooting thread). **Work-relevant:** Stefan Munoz posted a morning status — "working on removing Wi-Fi interferences from production floor and working with facilities to get more Ethernet drops" (relevant to the CelLink/Georgetown site work). Marshall noted reluctance about a possible San Antonio on-site. No explicit reply requested.

## E — Time Entries
> Corrective content rebuild — NO calendar writes were performed this run. The live Outlook calendar is authoritative and was left untouched.

**Candidate billable work observed (informational only — NOT written):**
- CelLink — ~10:00 AM CDT onward — maintenance-window planning/prep (SSL, RADIUS, FW/DUO cutover) per Ted Do's email.
- ARIA_Med — Meraki/Barracuda XDR log-forwarding investigation (SOC #126911311).
- Multiple clients — HelpDesk ticket work (email hack #10372, mailflow #10371, DKIM #10356, computer/VPN/scanner/Wi-Fi tickets) across the morning.
- CelLink/Georgetown — Stefan: production-floor Wi-Fi interference remediation + Ethernet drop coordination (per Teams).

---
*Generated by Claude — 2026-06-19 (corrective rebuild)*
