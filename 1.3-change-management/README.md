# 1.3 – Change Management

**CompTIA Security+ SY0-701 – Exam Objective 1.3**

**Source videos:** Professor Messer – Change Management; Technical Change Management

| Topic | What's in this module |
|---|---|
| Change management (the process) | Notes + Exercise 1 |
| Technical change management | Notes (covered by Exercise 1) |

## What This Covers

### Change management (the process)

In a company, one change can hit hundreds or thousands of systems, so changes go through a formal process. Updates never stop — operating systems and applications are patched all the time, and a system that isn't kept up to date is usually less secure. The process isn't there to block change. It's there to make change safe.

**Why have one**
- Keeps systems up and available
- Makes sure everyone is informed, so there's no confusion
- Stops mistakes
- Without it, anyone could change anything at any time, and applications start to clash or behave inconsistently

The process can set how often changes may happen, which types are allowed, and what the rollback procedure is. Where a process already exists, changes are easy to control. Where it doesn't, it's hard to introduce.

**A typical process** (yours may differ a little)

1. **Request** – fill in a standard change form, so the decision-makers get the same information every time
2. **Reason** – why the change is needed
3. **Scope** – one system or many; the people deciding need to know
4. **Schedule** – the date and time, which systems are affected, and the impact
5. **Risk analysis** – the change control board weighs the risk of making the change against the risk of not making it (a big change in the busiest time of year is riskier, for example)
6. **Decision** – the board allows or refuses the change
7. **After the change** – users try their systems and confirm nothing broke

**Who's involved**

| Role | What they do |
|---|---|
| Owner | Owns the application or data. Starts the request and is kept informed. Doesn't usually control the process or make the change. Tests afterwards and confirms everything works |
| Change control board | Reviews the risk and decides whether the change goes ahead |
| IT/technician | Makes the actual change |
| Stakeholders | Anyone affected by the change. They'll want input, especially on timing. It could be one person or a big part of the company |

Example: shipping and receiving own the label-printing software and IT upgrades it. But accounting uses it for shipping reports, customer deliveries depend on it, that affects when revenue counts, and the CEO would notice. A "simple" printing change can reach the bottom line.

**Impact analysis and risk**

Risk is often rated high, medium or low, and weighed both ways:
- **Risk of making the change:** the fix doesn't fix anything; the fix breaks something else; the OS fails because of the update; data is corrupted (so you need backups)
- **Risk of not making it:** a known vulnerability stays open to attackers; an application becomes unavailable; a related service stops working because a second service wasn't updated

**Test results (sandbox).** When the risk is high, test first in a **sandbox**, which is a copy of production where mistakes affect nobody. Apply the change there, check it worked, and keep testing. It's also the time to test your backout plan.

**Backout plan.** A documented, step-by-step way back to the original (or something very close) if the change goes wrong. Plenty of "minor" changes have brought down whole networks because nobody planned a way back. Uninstall the patch and check that the original files are back. Some changes are hard to reverse and need other methods. Always take a full backup first, in case the backout plan fails too.

**Maintenance window.** Getting approval is often the easy part; finding the time is harder. Avoid the working day; use nights, weekends, holidays or early mornings. That's tough for 24/7 environments. The time of year matters too: a retail company may freeze its systems over its busiest weeks (a **change freeze**) and only restart changes afterwards.

**Documentation and SOPs.** Change management is part of your security policies and procedures. It's documented (usually on the intranet), it's part of the standard operating procedures (SOPs), and nobody changes the network without approval. The process itself gets updated over time to work better.

**Quick recall**
- Purpose: keep systems available, keep everyone informed, avoid mistakes
- Flow: request form (reason, scope, schedule, impact) → risk analysis → board decision → change → users test
- The owner starts it and checks it afterwards; the board decides; IT does the work; stakeholders are anyone affected (often more people than you'd think)
- Weigh the risk of changing against the risk of not changing
- Test in a sandbox, always have a backout plan, always have a backup
- Do changes in a maintenance window; freeze changes in busy periods
- Exam terms: approval process, ownership, stakeholders, impact analysis, test results, backout plan, maintenance window, standard operating procedure (SOP)

### Technical change management

The change management process decides *what* changes. The technician makes the change. With one or two devices at home that's easy; with hundreds or thousands, a simple update gets complicated.

**Allow lists and deny lists.** A technician may be asked to change one of these. Some applications are dangerous, and they have known vulnerabilities or are known to carry malware.

| | Allow list | Deny list |
|---|---|---|
| Rule | Only the named applications can run | Anything can run except the named applications |
| Feel | Strict — everything else is blocked | More flexible |
| Example | Only approved apps run on workstations | Anti-malware works like a huge deny list: everything runs except code it identifies as bad |

In your lab: Windows Firewall treats inbound traffic like an allow list (blocked unless a rule allows it) and outbound traffic like a deny list (allowed unless a rule blocks it).

**Restricted activities (scope).** A change request has a documented scope, and you can only change what it lists. A two-hour window to upgrade printer drivers doesn't let you change other applications just because time is free. But scope can sometimes grow when it's needed to finish the main job — for example, the driver upgrade also needs a config file edited on every machine. If it's a small change, policy may let the technician make the call. That's why the process should say what to do when scope has to change.

**Downtime.** A change doesn't always mean downtime, but time is set aside in case. That's why changes happen out of hours. In 24/7 environments there's often no window to spare, so use a **secondary system**: switch users to it, update the primary, then switch back (often automated). You can watch for problems, and if something's wrong, fall back to the secondary system, which hasn't been touched. Always tell people about possible outages — by email, or on a central change calendar.

**Restarts.** The last step before going live is often a restart — a new configuration may only apply after one.
- **Service restart** – restart one service (Windows Services or Task Manager; on Linux, restart the daemon). Usually quick
- **Application restart** – users log out, fully close the app and reopen the updated one
- **System reboot** – restart the OS, or power the device off and on. It also shows the system comes back properly after a power cut

**Legacy applications.** Old systems that have run for years, aren't planned for replacement, and often have no developer support (the developer may not exist any more). Often "don't touch"; nobody understands them. Documenting how they work brings them into normal support. They may still have quirks from an older OS.

**Dependencies.** One update may need another to happen first, or a service won't work until a second one is installed. One change becomes several. Dependencies can sit on other systems too; for example, new firewall management software may need all the firewalls on newer code first, so you update the firewalls, then the software.

**Documentation.** Constant change means documentation goes out of date quickly, so updating it is part of the change process: update network diagrams, IP addresses and configurations, and write new procedures for upgraded applications.

**Version control.** Keeps track of the versions of code, software and configurations that have been installed — router configs, Windows patches, registry changes, anything between point A and point B — and lets you revert to an earlier version. Many applications and operating systems have it built in. If yours doesn't, use a third-party version control system.

**Quick recall**
- Allow list = only named items run; deny list = everything runs except named items; anti-malware ≈ a big deny list
- Stay inside the scope on the change request but have a documented way to widen it
- Downtime goes in a maintenance window; 24/7 systems switch to a secondary system, update the primary, and can fall back
- Restarts: service (quick), application (users close and reopen), system reboot (also tests power-cycle recovery)
- Legacy applications: old, unsupported, poorly understood, document them
- Dependencies: A may need B first, sometimes on a different system
- Update diagrams, policies and procedures after every change
- Version control tracks versions and lets you revert
- Exam terms: allow lists/deny lists, restricted activities, downtime, service restart, application restart, legacy applications, dependencies, updating diagrams, updating policies/procedures, version control
