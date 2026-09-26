# Rawasi Product Requirements Document (PRD)

## Goals and Background Context

### Scope of This PRD

This PRD covers **Epic 1 only**. The project is delivered epic by epic: each epic gets its own requirements, stories, and acceptance criteria, which are added to this document when that epic is ready to plan, not before. The brief (`docs/brief.md`) remains the context for everything outside Epic 1. Requirement IDs are namespaced per epic (`E1-FR1`, `E1-NFR1`, …) so later epics can be added without renumbering.

### Goals

- Ship an installable iOS and Android app, from one codebase, that someone can use every day from the first release. Epic 1 is released as a **private beta** (TestFlight and Google Play internal testing) to the builder and a small cohort; public store release comes in a later epic
- Make **readiness**, not the prayer time, the main thing on the home screen, and have the app speak only inside each prayer's user-configured preparation window
- Calculate prayer times accurately and fully offline, using the calculation method the user chooses
- Keep all user state on the device: no server, no telemetry, no hosting cost
- Apply the product's core rules from day one: silent when the user is ready, never notify at the adhan, never judge the user's worship, Arabic RTL only
- Lay a foundation that later epics can extend without rework: project setup, CI, per-prayer data model, and user-facing text kept out of the code

### Background Context

Existing Islamic apps assume that what users lack is information: accurate times, louder adhans, bigger libraries. The brief argues that on-time prayer is really decided in the minutes *before* the adhan: whether the user is in wudu, dressed, has a clear calendar, and is able to step away. Rawasi moves the intervention into that preparation window and then goes quiet once the user is ready.

Epic 1 delivers the smallest version of that idea that is useful on its own:

- an offline prayer-time engine
- a home screen built around declaring readiness
- a preparation window for each prayer, during which an unready user sees a countdown and gets one notification

Everything else stays quiet. Readiness belongs to the user: the app never changes it. Epic 1 starts testing the product's founding assumption: that users will declare readiness and feel the app's silence as a reward.

### Change Log

| Date       | Version | Description                                                                                          | Author    |
| ---------- | ------- | ---------------------------------------------------------------------------------------------------- | --------- |
| 2026-09-27 | 0.1     | Goals, background, and requirements for Epic 1 approved. Deadline = prayer time; readiness is user-owned; window-open notification added | John (PM) |
| 2026-09-27 | 0.4     | PM checklist run. Added E1-NFR14 (no OS cloud backup), private beta release, CF-3 (pause prompts) | John (PM) |
| 2026-09-27 | 0.3     | Added Epic 1 stories and the Carry-Forward Register (CF-1: revisit Story 1.6 in Epic 2) | John (PM) |
| 2026-09-27 | 0.2     | FR11: "prayer has arrived" message limited to 30 minutes, makes no claim about time left, copy left to the UX Expert | John (PM) |

## Requirements

_Scope: Epic 1 (Foundation & Readiness Home)._

### Functional

- **E1-FR1:** On first launch, the app sets the user's location for prayer-time calculation, either from device location (with permission) or by manual city selection. Onboarding never asks about the user's current prayer habits or performance.
- **E1-FR2:** The app calculates the five daily prayer times plus sunrise on the device, offline, using an established prayer-time library.
- **E1-FR3:** The user chooses the calculation method (e.g., Umm al-Qura, Egyptian General Authority, Muslim World League) and the Asr method (standard or Hanafi). A default is suggested from their location.
- **E1-FR4:** Prayer times recalculate automatically when the date changes and when the user changes location or calculation settings.
- **E1-FR5:** The home screen centres on the upcoming prayer's readiness state, not a list of prayer times. The full day's prayer times are a secondary view.
- **E1-FR6:** The user declares two readiness items with one tap each, *in wudu* and *appropriately dressed*, and can undo either one. Readiness can be declared at any time, including before a preparation window opens.
- **E1-FR7:** Each of the five prayers has its own preparation time, set by the user (default 20 minutes). The **preparation deadline is the prayer time itself**. The **preparation window** runs from (prayer time − preparation time) until the prayer time.
- **E1-FR8:** The home screen shows a countdown to the prayer time **only when the preparation window is open and the user is not ready.** Before the window opens, the home screen shows the upcoming prayer in a quiet state with no countdown. Example: if Asr is 60 minutes away and its preparation time is 20 minutes, nothing counts down until 20 minutes before Asr.
- **E1-FR9:** When both readiness items are declared, the home screen shows a calm confirmation state. No countdown and no notification happens for that prayer.
- **E1-FR10:** Only the user changes readiness. The app never sets, clears, or expires readiness on its own, including when a prayer time passes. The home screen shows when each of these last changed:
  - overall readiness (ready ↔ not ready)
  - the *in wudu* item
  - the *appropriately dressed* item

  Example: "على وضوء منذ ١٢:٤٠" ("in wudu since 12:40").
- **E1-FR11:** When a prayer's time arrives and the user is not ready, the home screen shows a calm, inviting message for **30 minutes** after the prayer time. The message stops early if the user becomes ready or the next prayer's preparation window opens. After that, the home screen quietly moves on to the next prayer. The message invites the user to get ready but **never claims how much time remains** or whether the prayer is still valid, since that would be a ruling. There are no warning states, no failure labels, and no red or alarm styling. The exact text is left to the UX Expert. _(Epic 2 will replace the fixed 30 minutes with the user's own target window for that prayer.)_
- **E1-FR12:** A settings screen lets the user change location, calculation method, Asr method, and each prayer's preparation time.
- **E1-FR13:** When a prayer's preparation window opens and the user is not ready, the app sends one local notification for that prayer. Nothing is sent if the user is ready when the window opens. The adhan never triggers a notification.
- **E1-FR14:** Every readiness change is saved on the device with its timestamp. This history is where FR10's last-changed times come from. It is never shown back to the user as a score.
- **E1-FR15:** The app asks for notification permission with a plain explanation of why it needs it. If the user refuses, the app still works fully, and the in-app countdown and messages stay the same.
- **E1-FR16:** Scheduled notifications stay in step with readiness. If the user becomes ready before a window opens, that prayer's pending notification is cancelled. If the user clears readiness, it is rescheduled.

### Non Functional

- **E1-NFR1:** The app is built from a single cross-platform codebase that targets iOS and Android.
- **E1-NFR2:** All features in Epic 1 work fully offline after first setup.
- **E1-NFR3:** A cold start reaches a usable home screen in under 1.5 seconds on a mid-range Android device (reference device to be named by the Architect).
- **E1-NFR4:** All user data (settings and readiness history) is stored only on the device. The app makes no network calls carrying user data.
- **E1-NFR5:** The app contains no analytics, telemetry, crash reporting, or advertising SDKs that send data off the device.
- **E1-NFR6:** The interface is Arabic only and right-to-left. All user-facing text comes from resource files, not hard-coded strings.
- **E1-NFR7:** The data model stores preparation time, and later target windows and iqama settings, per prayer from the start. It never uses one global setting that would have to be split up later.
- **E1-NFR8:** Calculated prayer times are within ±1 minute of a reference source for the selected method. Automated tests check this for a fixed set of cities and dates.
- **E1-NFR9:** All text follows "add, never accuse". No text uses words of failure, lateness, or judgment about the user's worship.
- **E1-NFR10:** Running the app costs nothing: there is no backend and no paid third-party service.
- **E1-NFR11:** Text scales with the system font size, touch targets are at least 44×44 pt, and contrast meets WCAG AA.
- **E1-NFR12:** Notifications are scheduled locally on the device and work offline. There is no push server.
- **E1-NFR13:** Notifications arrive within ±1 minute of the window opening, including on Android devices with aggressive battery optimisation. This is checked on real devices during Epic 1, and the app guides the user through battery-optimisation exemptions where their phone needs it.
- **E1-NFR14:** Rawasi's data is excluded from the operating system's cloud backups (iCloud, Google backup), so no worship data leaves the device, even indirectly. Data lost with a device is accepted until Epic 6 adds encrypted export.

## User Interface Design Goals

_Scope: Epic 1._

### Overall UX Vision

The app is a launcher, not somewhere to spend time: open it, glance or tap once, close it. It stays calm, with nothing urgent, red, or alarming. When the user is ready, the app goes quiet and asks nothing more.

### Key Interaction Paradigms

- Readiness is two large one-tap toggles, *على وضوء* (in wudu) and *باللباس المناسب* (appropriately dressed). Each shows when it last changed underneath it (E1-FR10). The toggles stay visible in every state so the user can declare or undo at any time.
- The home screen has four states for the upcoming prayer:
  1. **Quiet:** the preparation window hasn't opened yet. Shows the prayer's name and time, with no countdown.
  2. **Countdown:** the window is open and the user is not ready. Counts down to the prayer time.
  3. **Ready:** a calm confirmation, with no countdown.
  4. **Prayer has arrived:** the user is not ready yet. For up to 30 minutes, shows an inviting message that makes no claim about time left (E1-FR11).
- Settings are edited in place, with no deep menus. Each prayer's preparation time is set on its own row.

### Core Screens and Views

1. Onboarding: location (automatic or pick a city), then calculation method and Asr method
2. Notification permission explainer
3. Home (readiness)
4. Today's prayer times (secondary view)
5. Settings: location, calculation method, Asr method, and preparation time for each prayer
6. Android battery-optimisation guidance, shown only on phones that need it

### Accessibility: WCAG AA

### Branding

Product name: **Rawasi**. No logo or palette is defined yet; the UX Expert should propose one. Direction: calm and restrained, an Arabic typeface chosen for readability, and no red or alarm colours anywhere.

### Target Device and Platforms: Cross-Platform

iOS and Android phones only. No tablet layout in Epic 1.

## Epic List

_Only Epic 1 is detailed in this PRD. Later epics are a roadmap and will be detailed one at a time, when each is ready to plan._

**MVP**

1. **Foundation & Readiness Home** (current): Set up the project and ship offline prayer times, readiness declaration, a preparation window for each prayer, and one notification when that window opens.
2. **Target Windows & Reflective Logging:** The user picks their own on-time window for each prayer from named scholarly positions. Only prayers outside that window are logged, and every logged prayer asks what was recited. **Must revisit Story 1.6 / E1-FR11:** replace the fixed 30-minute "prayer has arrived" period with the user's target window. See [Carry-Forward Register](#carry-forward-register).
3. **Calendar Conflict Engine:** Find calendar events that overlap prayer times, warn before the event starts, and offer ready-made messages for excusing yourself.
4. **Pattern Surfacing:** Show recurring patterns in lost prayers plainly, without judging them.
5. **Adhkar & Custom Activities:** Track adhkar with streaks, plus activities the user defines.
6. **Backup & Device Migration:** Encrypted export and import, including between iOS and Android. _(May move to directly after Epic 2, since worship history starts accumulating there.)_

**After MVP**

7. **Du'a Journey:** Blocked until a qualified reviewer and content contributors are in place.
8. **Quran Comprehension Journey:** Vocabulary study with spaced repetition.
9. **Quran Concordance & Word Tracing**

**Later, not yet scheduled:** navigation and driving context, household and family, companionship, kinship, sadaqah, and languages other than Arabic.

## Carry-Forward Register

_Decisions made in one epic that a later epic **must** revisit. When planning, drafting stories for, or implementing any epic listed in the "Revisit in" column, the PM, SM, and Dev agents must check this table and include the item. Close an item only by marking it done with the story that resolved it._

| ID    | Origin                        | Revisit in | What must change                                                                                                                                                                                                                                                                                                              | Status |
| ----- | ----------------------------- | ---------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------ |
| CF-1  | Story 1.6 (AC5–6), E1-FR11     | Epic 2     | The "prayer has arrived" message currently shows for a fixed 30 minutes. Once per-prayer target windows exist, the message must last until the end of the user's chosen target window for that prayer, still ending early on readiness or when the next prayer's preparation window opens. Update E1-FR11 and Story 1.6 ACs, and add a regression story in Epic 2. | Open   |
| CF-2  | Epic List                     | After Epic 2 | Decide whether Epic 6 (Backup & Device Migration) moves directly after Epic 2, since worship history starts accumulating there.                                                                                                                                                                                          | Open   |
| CF-3  | Checklist H1                  | Epic 2, or before any public release, whichever comes first | Users who don't need prompts for a while (menstruation, illness, travel) have no way to pause countdowns and notifications in Epic 1. Add a neutral pause (until a date, or until resumed), with no reason asked or stored. | Open   |

## Epic 1 Foundation & Readiness Home

Build Rawasi's foundation and deliver the first version someone can use every day: accurate prayer times that work offline, a home screen built around readiness, and a preparation window for each prayer, with a countdown on screen and one notification. By the end of this epic, a user can install Rawasi, set it up in under a minute, declare readiness, and have the app speak only when they are unprepared and a prayer is close.

### Story 1.1 Project Foundation and Arabic App Shell

As the builder,
I want a project that builds, tests and runs on iOS and Android and opens to a Rawasi screen in Arabic,
so that every later story builds on a working, verifiable base.

#### Acceptance Criteria

1. The app installs and launches on iOS and Android and shows a placeholder home screen with the name "رواسي".
2. The whole interface lays out right-to-left.
3. All user-facing text comes from resource files; none is hard-coded (E1-NFR6).
4. Continuous integration runs lint, tests, and builds for both platforms on every push to `main`.
5. No analytics, telemetry, crash-reporting or advertising SDKs are included (E1-NFR5).
6. The app makes no network requests.
7. App data is excluded from iCloud and Google cloud backups (E1-NFR14).
8. A build is distributed through TestFlight and Google Play internal testing for the private beta.

### Story 1.2 Offline Prayer-Time Engine and Today's Times

As a user,
I want to see today's prayer times for my city, even offline,
so that I can trust the times everything else depends on.

#### Acceptance Criteria

1. Given a location, date, calculation method and Asr method, the app calculates Fajr, sunrise, Dhuhr, Asr, Maghrib and Isha on the device (E1-FR2).
2. The user can pick a city from a list built into the app, with no network needed.
3. The "Today's prayer times" view shows all six times in Arabic.
4. Automated tests confirm the calculated times are within ±1 minute of reference times for at least 5 cities across 3 different dates each (E1-NFR8).
5. Sunrise is displayed but is never treated as a prayer anywhere in the app.

### Story 1.3 Onboarding: Location and Calculation Method

As a new user,
I want a short setup that only asks where I am and how times should be calculated,
so that I can start without being asked about my habits.

#### Acceptance Criteria

1. On first launch, the user either uses device location (with permission) or picks a city from the list (E1-FR1).
2. If location permission is refused, the city list is offered with no dead end.
3. A calculation method and Asr method are suggested based on the location, and the user can change them (E1-FR3).
4. Onboarding never asks about the user's prayer habits or performance.
5. Choices are saved on the device and survive restarts. Onboarding does not appear again.
6. Times recalculate when the date changes, the time zone changes, or the device clock is changed (E1-FR4).

### Story 1.4 Settings and Per-Prayer Preparation Time

As a user,
I want to set a preparation time for each prayer and change my location or method later,
so that the preparation window matches my real life.

#### Acceptance Criteria

1. The settings screen lets the user change location, calculation method, Asr method, and each of the five prayers' preparation times (E1-FR12).
2. Each prayer's preparation time defaults to 20 minutes and is set on its own (E1-FR7, E1-NFR7).
3. Preparation time can be set from 5 to 90 minutes, in 5-minute steps.
4. Any change applies immediately: times recalculate, and the preparation windows update.

### Story 1.5 Readiness Toggles and Last-Changed Times

As a user,
I want to declare that I'm in wudu and appropriately dressed with one tap each, and see when I last changed each,
so that my readiness is recorded exactly as I declare it.

#### Acceptance Criteria

1. The home screen shows two toggles, *على وضوء* (in wudu) and *باللباس المناسب* (appropriately dressed). Each can be switched on or off with one tap at any time (E1-FR6).
2. Overall readiness is "ready" only when both toggles are on.
3. The screen shows the time of the last change to overall readiness, to wudu, and to clothing (E1-FR10).
4. Every toggle change is saved on the device with a timestamp, and history is only ever added to (E1-FR14).
5. Readiness is never changed by the app itself: not when a prayer time passes, not at midnight, not on restart (E1-FR10).
6. Readiness history is never shown as a score, streak, or percentage.

### Story 1.6 Home States: Quiet, Countdown, Ready, and "Prayer Has Arrived"

> **⚠ Carry-forward CF-1:** AC5–6 use a fixed 30-minute period that **must be revisited in Epic 2**. It will be replaced by the user's per-prayer target window. See [Carry-Forward Register](#carry-forward-register).

As a user,
I want the home screen to say only what matters right now,
so that the app stays quiet unless I'm unprepared and a prayer is close.

#### Acceptance Criteria

1. The home screen centres on the upcoming prayer (sunrise is excluded). After Isha, the upcoming prayer is the next day's Fajr (E1-FR5).
2. **Quiet:** before the preparation window opens and while the user is not ready, the screen shows the prayer's name and time, with no countdown (E1-FR8).
3. **Countdown:** while the preparation window is open and the user is not ready, the screen shows a live countdown to the prayer time (E1-FR8).
4. **Ready:** when the user is ready, the screen shows a calm confirmation and no countdown, whatever the time (E1-FR9).
5. **Prayer has arrived:** when the prayer time arrives and the user is not ready, the screen shows an inviting message for up to 30 minutes. The message never states how much time is left and never judges (E1-FR11). _(CF-1)_
6. The message ends as soon as the user becomes ready or the next prayer's window opens. When it ends, the screen moves to the next prayer's quiet or countdown state. _(CF-1)_
7. No state uses red or alarm styling, or words of failure or lateness (E1-NFR9).
8. The screen updates on its own as time passes, without the user doing anything.

### Story 1.7 Notification When the Preparation Window Opens

As a user who isn't ready,
I want one gentle notification when a prayer's preparation window opens,
so that I start preparing while there's still time.

#### Acceptance Criteria

1. On first need, the app explains in plain Arabic why it needs notification permission, then asks for it. If the user refuses, the app keeps working, with the on-screen states unchanged (E1-FR15).
2. When a prayer's preparation window opens and the user is not ready, exactly one local notification is sent for that prayer (E1-FR13).
3. No notification is sent if the user is ready when the window opens (E1-FR9).
4. No notification is ever sent at the prayer time or the adhan (E1-FR13).
5. Becoming ready cancels pending notifications. Becoming not ready reschedules them. If readiness is cleared while a window is already open, no notification is sent for that window (E1-FR16).
6. Notifications keep arriving for at least 7 days without the user opening the app, and they survive a device restart.
7. Notifications work fully offline, with no server involved (E1-NFR12).
8. Notification text is calm, invites preparation, and is written by the UX Expert.

### Story 1.8 Notification Reliability on Android Battery Savers

As a user on a phone that blocks background work,
I want the app to help me allow its notifications,
so that the preparation notification actually arrives.

#### Acceptance Criteria

1. On phones known to block scheduled notifications, the app shows a short guidance screen explaining how to exempt Rawasi. It appears once and can be reopened from settings.
2. The guidance never appears on phones that don't need it, or on iOS.
3. A manual device checklist is written and run. It confirms notifications arrive within ±1 minute of the window opening on at least Samsung, Xiaomi and one other aggressive-battery phone brand, plus iOS (E1-NFR13).
4. Any phone where notifications still fail is recorded as a known limitation.

## Checklist Results Report

_PM checklist run on 2026-09-27 against **Epic 1 only**. Section 7 (Technical Guidance) is marked N/A because technical decisions belong to the Architect and are deliberately excluded from this PRD._

**Summary:** about 85% complete · MVP scope for Epic 1: **Just Right** · Readiness for architecture: **Ready** (H1 deferred to CF-3, H2 resolved as E1-NFR14, M2 resolved as private beta)

| Category                         | Status  | Critical Issues |
| -------------------------------- | ------- | --------------- |
| 1. Problem Definition & Context  | PASS    | Relies on `docs/brief.md`. No user research or competitive analysis exists yet (acknowledged in the brief). |
| 2. MVP Scope Definition          | PARTIAL | No explicit way to validate Epic 1 or collect feedback, given no telemetry. |
| 3. User Experience Requirements  | PARTIAL | Pausing prompts deferred to Epic 2 or before public release (CF-3); acceptable for a private beta. |
| 4. Functional Requirements       | PASS    | None |
| 5. Non-Functional Requirements   | PARTIAL | Resolved: OS cloud backup excluded (E1-NFR14). |
| 6. Epic & Story Structure        | PASS    | None |
| 7. Technical Guidance            | N/A     | Owned by the Architect. Key risk (E1-NFR13) is flagged. |
| 8. Cross-Functional Requirements | PARTIAL | Release channel resolved (private beta). City-list coverage still open (M3). |
| 9. Clarity & Communication       | PASS    | None |

### Issues by Priority

- **BLOCKERS:** none.
- **HIGH:** _(both resolved)_
  - **H1 → CF-3 (deferred):** Decide how users who are exempt from prayer (menstruation, illness), or who otherwise want quiet, can pause countdowns and notifications. Without this, the app prompts them five times a day, which breaks "add, never accuse".
  - **H2 → E1-NFR14 (resolved):** Decide whether the operating system's cloud backup (iCloud or Google) may include Rawasi data, since E1-NFR4 says data stays on the device.
- **MEDIUM:**
  - **M1 (partly resolved by the private beta, since feedback comes directly from the cohort):** Define how Epic 1 is validated: who uses it, for how long, and how feedback is gathered with no telemetry.
  - **M2 → private beta (resolved):** Define the Epic 1 release channel (TestFlight / Play internal testing vs public stores).
  - **M3:** Define which cities the bundled list covers, and how high-latitude locations are handled.
- **LOW:**
  - **L1:** Arabic-Indic vs Western digits (UX Expert).
  - **L2:** Retention policy for readiness history (it grows indefinitely).

### Final Decision

**READY FOR ARCHITECT.** M3 (city-list coverage and high latitudes) and the LOW items can be settled during UX and architecture work.

## Next Steps

### UX Expert Prompt

Using `docs/prd.md` (Epic 1 only) and `docs/brief.md`, create the front-end spec for Rawasi Epic 1. Design the four home states (quiet, countdown, ready, prayer has arrived), the readiness toggles with their last-changed times, onboarding, settings, the notification-permission explainer, and the Android battery-guidance screen. Write all Arabic copy, including the "prayer has arrived" message and the notification text, following "add, never accuse" and never claiming how much time is left. Propose a calm visual direction and settle the digits question (L1). Check the Carry-Forward Register before starting.

### Architect Prompt

Using `docs/prd.md` (Epic 1 only) and `docs/brief.md`, create the architecture for Rawasi Epic 1. All technical decisions are yours; the PRD deliberately contains none. Honour the constraints: offline-first, no backend, zero running cost, data only on the device and excluded from OS backups, and one codebase for iOS and Android. Give priority to reliable scheduled notifications under Android battery optimisation (E1-NFR13) and a per-prayer data model that Epics 2–6 can extend. Check the Carry-Forward Register before starting.
