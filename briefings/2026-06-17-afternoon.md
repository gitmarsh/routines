# Afternoon Briefing — Wednesday, June 17, 2026

*Corrective content rebuild — regenerated 2026-06-19 from live Outlook data. Scan window: 2026-06-17 07:30 → 13:30 CDT. Calendar is authoritative; no calendar writes were made.*

## 🟥 HOT ITEMS
- **VPN / Duo outage (P1, multi-client)** — After last night's patching, the Meraki → Duo RADIUS auth path broke: username/password authenticates but no Duo push reaches users. Affects Cel Link / CL and others; multiple users + Nghi, Michael, Stefan all reproduce. Duo Support (ticket 01819254) changed the RADIUS secret (removed `#`) and port to 18120; Meraki Support (Case 14350238) confirms nothing listening on the RADIUS port. Root cause still open — Duo wants Authproxy debug logs + support-tool zip. Stopgap: AnyConnect VPN; Duo bypass not currently possible without standing up alternate auth.
- **Amex phishing scare — MSM (McElroy, Sullivan, Miller & Weber)** — Mike Paluso clicked a link in a Barracuda-quarantined "Amex disputed charge" email that led to a fake Amex page; he says he entered no credentials. Matt advised password change + 2FA. O365 also auto-removed a malicious URL post-delivery for MSM. Confirm no compromise.
- **Help desk volume surge** — Michael flagged the ticket count as "ridiculous" across BT, CL and Beehive; he's covering field stops (Beehive/ILC), asked Marshall + Matt to triage and reduce backlog.

## A — New Emails
| Subject | Sender | Summary | Received (CDT) |
|---|---|---|---|
| FW: ATXCPE Michelle Gilbert (RMM #10472) | Michael Statham | Forwards ATXCPE's Azure VPN Gateway P2S cert-migration notice; "we'll need to do this at MSM & ATXCPE before end of year" — action by **Jan 31, 2027**. | 8:00 AM |
| Amex email (thread, 5 msgs) | Mike Paluso (MSM) / Matt Kerker | Paluso clicked a phishing link from a quarantined Amex email; Matt confirms no creds entered, recommends Amex password change + 2FA; Paluso to comply. | 9:23–9:30 AM |
| RE: computer from Amazon / RE: Which machine to replace old | Bill Hayenga & Mike Paluso (MSM) | Bill ordered a comparable Dell (Amazon unit not viable); arriving Friday — wants a **Friday afternoon setup** scheduled. | 9:35 AM / 11:35 AM |
| FW: Cisco Meraki Case 14350238 — Clients unable to connect to VPN | Stefan Munoz | Meraki packet capture: nothing listening on RADIUS port; shared with Marshall for the VPN incident. | 10:51 AM |
| Cisco Meraki Case 14350238 (2 msgs) | support@meraki.com | Meraki support packet-capture screenshots filtered to RADIUS server 10.1.10.8 (UDP 18120 / 1812). | 12:17 / 12:27 PM |
| Regarding your Duo Support ticket 01819254 | support@duo.com | Duo call summary: no auth attempts reaching Authproxy; changed RADIUS secret + port to 18120; advises engaging Meraki, then send Authproxy debug zip. | 11:54 AM |
| Case 01819254 (Webex invite) | ketian@cisco.com | Cisco/Duo Webex meeting invite for the open VPN case. | 11:30 AM |
| Ticket 126973891 awaiting response — Barracuda XDR: O365 forwarding rule created/modified/deleted | soc@barracuda.com | Barracuda XDR follow-up on an outstanding O365 mail-forwarding-rule alert (TLP:AMBER) — needs a response. | 10:03 AM |
| Informational alert: malicious URL removed after delivery | Office365Alerts@microsoft.com | O365 auto-removed a malicious-URL email (MSM / mpaluso) — informational; ties to Amex phishing. | 9:26 AM |
| You have been authorized for Georgetown | noreply@meraki.com | Automated Meraki org-access authorization — informational. | 8:30 AM |
| Payment received: #5452 from Kyle Fire Department | communications@ramp.com | Automated Ramp notice — Kyle FD paid invoice #5452; no action. | 8:41 AM |
| SentinelOne – New Agent Package Available | noreply@mailsender.sentinelone.net | Automated: new macOS S1 agent 26.1 EA2 available. | 9:43 AM |
| Set Up Your Apple Account for work / Jamf Now invite (Buda FD) | apple.com / jamfnow.com | Automated onboarding invites for Matt Kerker (Apple business acct; Buda Fire Dept Jamf Now). | 10:58 / 11:19 AM |
| Introducing Barracuda Integrated Email Protection | amerpartners@barracuda.com | Marketing — no action. | 10:18 AM |

## B — Action Items Still Open
| Priority | What's needed | From | Deadline |
|---|---|---|---|
| 🔴 Critical | Restore Duo/Meraki RADIUS VPN auth (run Authproxy debug + support-tool zip to Duo; confirm RADIUS port/secret with Meraki) | Duo #01819254 / Meraki #14350238 | ASAP — users blocked |
| 🟠 High | Set up VPN access for critical users Charlie Biggs & Erick Ti for pending release | Nghi Nguyen (Teams) | ASAP (release pending) |
| 🟠 High | Verify MSM/Paluso Amex phishing caused no compromise; ensure password change + 2FA done | Paluso / Matt (email) | Today |
| 🟠 High | Respond to Barracuda XDR ticket 126973891 (O365 forwarding-rule alert) | Barracuda SOC | Today |
| 🟡 Medium | Schedule Bill Hayenga (MSM) new-Dell setup for Friday afternoon | BHayenga (email) | Confirm before Fri |
| 🟡 Medium | Work down help-desk backlog (8+ open RMM tickets across BT/CL/Beehive) | Michael / RMM | Today |
| 🔵 Low | Plan ATXCPE & MSM Azure VPN Gateway P2S cert-profile redistribution | RMM #10472 | Jan 31, 2027 |

## C — EOD Plan
**MUST FINISH TODAY** (hard deadlines / Critical+High)
- Restore VPN/Duo RADIUS authentication (or stand up AnyConnect stopgap for blocked users).
- Provision Charlie Biggs & Erick Ti VPN access for the pending release.
- Close the loop on the MSM Amex phishing incident (compromise check + password/2FA).
- Respond to Barracuda XDR ticket 126973891.

**CARRY TO TOMORROW**
- Help-desk backlog cleanup across BT / CL / Beehive (printing #10454, backups #10414, scanners #10470/#10467, etc.).
- Schedule Friday PM Dell setup for Bill Hayenga (MSM).
- Long-lead: ATXCPE/MSM Azure VPN Gateway cert migration (#10472).

## D — Teams
Extremely active — a live VPN/Duo incident war-room across multiple chats (Marshall, Michael, Stefan, Nghi, Matt):
- **VPN down after overnight patching** — "no duo push," "can't even bypass it," "no auth attempts reaching the proxy"; suspected the SC services restarting after reboots are conflicting; on calls with Duo + Meraki most of the morning. Marshall by ~1:27 PM: "done for now — can't troubleshoot while they're using the VPN."
- **Nghi Nguyen: "Please setup Charlie Biggs and Erick Ti ASAP. We have a release to go out soon."** — reply/needed, provisioning in progress.
- **Michael Statham:** field updates — Beehive → ILC (bad switch at ILC, David ordering a new one); flagged help-desk volume as "ridiculous," asked Marshall/Matt to reduce ticket count.
- **Matt Kerker:** holding the fort (3 device setups at BFD, new-hire MFA onboarding at CPC); notes BFD wants Ariat to take over Apple account management; Michael told him not to respond to Courtney until 2 PM.
- Note: a Teams message contained a plaintext credential (Erick's password) shared in chat — flag for a password reset / out-of-band handling.

## E — Time Entries
> Corrective content rebuild — NO calendar writes were performed this run. The live Outlook calendar is authoritative and was left untouched.

**Candidate billable work observed (informational only — NOT written):**
- **Cel Link / CL (and affected clients)** — ~8:00 AM–1:30 PM CDT — VPN/Duo RADIUS outage troubleshooting; vendor calls with Duo (#01819254) and Meraki (#14350238), RADIUS config changes, AnyConnect stopgap.
- **MSM (McElroy, Sullivan, Miller & Weber)** — late morning CDT — Amex phishing incident response (Paluso); new-Dell replacement coordination for Bill Hayenga.
- **Celerity / internal (Nghi's team)** — late morning CDT — provisioning VPN access for Charlie Biggs & Erick Ti ahead of a release.
- **Help-desk ticket work** — throughout window — multiple RMM tickets across BT/CL/Beehive (printing, failed backups, scanners, new employee, etc.).

---
*Generated by Claude — 2026-06-19 (corrective rebuild)*
