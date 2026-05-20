---
name: ariat-time-entry
description: Reference for formatting Ariat Systems IT time entries into a five-field Outlook Calendar block (Subject, Location, Description, Category, Time). Provides client list, category decision rules, location values, and time format only — does not execute actions. Trigger on "log time", "time entry", "calendar entry for [client]", "I worked on", or any Ariat client name (ATXCPE, Beehive, Buda Fire, Burnett & Turner, Capital Excavation, CelLink, CPC, Covenant Presbyterian, Davey Plumbing, Decision Resources, Dickson, Dunham, EZ Heat, Fox Truck, Immanuel Lutheran, Kidd Roofing, Kyle Fire, MSM, McElroy Sullivan, MEJ, Taylor Bosworth, Texas Utility Group, Whitehead Wilson) paired with work performed. The invoking prompt decides output destination (print, file, M365 MCP).
---
# Ariat Systems Time Entry
## Usage
This skill provides formatting rules and reference data only. It does not execute actions.
The invoking prompt decides what happens with the output — print to terminal, write to a file, create the Outlook event via the Microsoft 365 MCP, etc. When invoked, follow the rules below to produce the five-field block, then hand it off per the invoking prompt's instructions.
## Output format
Always produce exactly these five fields:
Subject: <client name> Location: <Remote | On-Site; My Car | On-Site; <colleague>'s Car> Description: <summary of work performed> Category: <Project (Green) | On-Going Support (Blue) | After-Hours (Red)> Time: <YYYY-MM-DD HH:MM - HH:MM>
If a field cannot be inferred with at least 80% confidence, output the field with `<MISSING: reason>` so the user can fill it in. Do not guess.
## Clients
Use the exact display name from this list as the Subject. Common shorthands are mapped below.
| Shorthand | Full name |
|---|---|
| CPC | Covenant Presbyterian Church |
| MSM | McElroy, Sullivan, Miller & Weber, L.L.P. |
Full client list:
1. ATXCPE
2. Beehive Specialty
3. Buda Fire & EMS
4. Burnett & Turner Law
5. Capital Excavation
6. CelLink
7. Covenant Presbyterian Church
8. Davey Plumbing
9. Decision Resources, Inc
10. Dickson Productions
11. Dunham, LLP
12. EZ Heat
13. Fox Truck World
14. Immanuel Lutheran Church
15. Kidd Roofing
16. Kyle Fire & EMS
17. McElroy, Sullivan, Miller & Weber, L.L.P.
18. MEJ & Associates
19. Taylor Bosworth & Bullard
20. Texas Utility Group
21. Whitehead Wilson
If the input names a client not on this list, output `Subject: <MISSING: client "<name>" not in known list>` and proceed with the other fields where possible.
## Categories
Three categories, each with a fixed color. Pick exactly one per entry.
**Project (Green)** — Any new setup or build-out. New, non-pre-existing infrastructure work. Examples: laptop build-outs, new user setup, network build-outs, installing equipment, new client onboarding, phone system work.
**On-Going Support (Blue)** — Standard help desk work on existing infrastructure. Software and hardware troubleshooting, printer maintenance, email troubleshooting, password resets, account fixes.
**After-Hours (Red)** — Any work at any client performed after 6:00 PM or before 8:00 AM. This overrides the other two categories based on time of day.
### Category decision rules
Apply in this order:
1. **Time-of-day override** — If the work was performed outside 8:00 AM–6:00 PM, category is **After-Hours (Red)**. Stop.
2. **CPC and MSM override** — If the client is Covenant Presbyterian Church (CPC) or McElroy, Sullivan, Miller & Weber (MSM) and the work was during working hours (8:00 AM–6:00 PM), category is **Project (Green)** regardless of work type. Stop.
3. **Work type** — If the work involves new setup, build-out, install, or onboarding → **Project (Green)**. Otherwise → **On-Going Support (Blue)**.
Working hours are 8:00 AM – 6:00 PM local time.
## Location
Three values only:
- `Remote` — work performed without traveling to the client site
- `On-Site; My Car` — drove own vehicle to the client site
- `On-Site; <Name>'s Car` — rode with a colleague (use their name, e.g. `On-Site; Matt's Car`)
## Description
- Summary of the actual work performed, not the ticket or request.
- Avoid first-person pronouns where possible. Implicit subject is preferred: "Configured network and defined IP spacing for printers in the new HQ. Set up a new Xerox printer with Matt."
- Explicit first person ("I configured...") is acceptable if the implicit form is awkward.
- No third person. No passive voice padding.
- Keep it concise — one to three sentences typical.
## Time
- Format: `YYYY-MM-DD HH:MM - HH:MM` using 24-hour time.
- Drive time is rolled into the start/end block. Start = time left for the site (or began remote work). End = time returned (or finished remote work).
- If start and end times are not given but duration is, anchor to the most reasonable inferred time of day from context and note assumption in the Description field is *not* appropriate — instead use `<MISSING: start/end time>` for the Time field.
## Worked example
**Input (from calling agent or user):**
> Wed May 6 afternoon, drove to Buda Fire, configured network and set IP spacing for printers in their new HQ, then set up a new Xerox printer with Matt. Got back around 4.
**Output:**
Subject: Buda Fire & EMS Location: On-Site; My Car Description: Configured network and defined IP spacing for printers in the new HQ. Set up a new Xerox printer with Matt. Category: Project (Green) Time: 2026-05-06 14:00 - 16:00
Reasoning applied (do not include in output):
- Client "Buda Fire" → `Buda Fire & EMS` from the client list.
- "Drove" → `On-Site; My Car`.
- "Configured network... new HQ... set up new Xerox" → new infrastructure → Project. During working hours, so After-Hours rule doesn't apply.
- "Got back around 4" with "afternoon" → end at 16:00, working backward from work scope → start ~14:00.
## Confidence rule
The calling agent may pass partial information. Infer fields where confidence is ≥80%. For anything below that threshold, emit `<MISSING: reason>` rather than fabricate. The user will fill in gaps manually.
