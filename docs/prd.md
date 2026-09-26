# Rawasi Product Requirements Document (PRD)

## Goals and Background Context

### Scope of This PRD

This PRD covers **Epic 1 only**. The project is delivered epic by epic: each epic gets its own requirements, stories, and acceptance criteria, which are added to this document when that epic is ready to plan, not before. The brief (`docs/brief.md`) remains the context for everything outside Epic 1. Requirement IDs are namespaced per epic (`E1-FR1`, `E1-NFR1`, …) so later epics can be added without renumbering.

### Goals

- Ship an installable iOS and Android app, from one codebase, that someone can use every day from the first release
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
- **E1-FR11:** When a prayer's time arrives and the user is not ready, the home screen shows a calm, encouraging message, e.g. "حان وقت العصر، وما زال لديك وقت للاستعداد" ("Asr has arrived, you still have time to prepare"). The message stays until the user becomes ready or the next prayer's preparation window opens. There are no warning states, no failure labels, and no red or alarm styling.
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
  4. **Prayer has arrived:** the user is not ready yet. Shows an encouraging message (E1-FR11).
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
2. **Target Windows & Reflective Logging:** The user picks their own on-time window for each prayer from named scholarly positions. Only prayers outside that window are logged, and every logged prayer asks what was recited.
3. **Calendar Conflict Engine:** Find calendar events that overlap prayer times, warn before the event starts, and offer ready-made messages for excusing yourself.
4. **Pattern Surfacing:** Show recurring patterns in lost prayers plainly, without judging them.
5. **Adhkar & Custom Activities:** Track adhkar with streaks, plus activities the user defines.
6. **Backup & Device Migration:** Encrypted export and import, including between iOS and Android. _(May move to directly after Epic 2, since worship history starts accumulating there.)_

**After MVP**

7. **Du'a Journey:** Blocked until a qualified reviewer and content contributors are in place.
8. **Quran Comprehension Journey:** Vocabulary study with spaced repetition.
9. **Quran Concordance & Word Tracing**

**Later, not yet scheduled:** navigation and driving context, household and family, companionship, kinship, sadaqah, and languages other than Arabic.
