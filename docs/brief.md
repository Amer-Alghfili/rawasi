# Project Brief: [PROJECT NAME TBD]

## Executive Summary

A mobile application that helps Arabic-speaking Muslims pray on time and build consistent worship habits by intervening **before** the prayer rather than at it.

The product treats on-time prayer as a *pre-positioning* problem, not a reminder problem. Its users already believe, already intend, and already hear the adhan — yet Dhuhr passes in a meeting and 'Isha is prayed at 11:30pm in ninety seconds. The app addresses the actual causal chain: unreadiness (wudu, clothing), calendar collisions accepted hours earlier, the social cost of visibly leaving an event, and a corrupted permission structure that treats the wide prayer window as license to delay.

Beyond the tracker, the product's deeper purpose is **educational**: guided, bounded journeys that teach users how to make du'a in their own words and how to genuinely comprehend the Quran — replacing search, uncertain sources, and overwhelming libraries with a single trustworthy path.

**Target users:** Arabic-speaking Sunni Muslims in two segments — the *time-starved* believer who knows what to do but can't sustain it against work and family pressure, and the *barrier-blocked* believer who prays but feels locked out of intimacy with Allah, having never made a du'a in their own words or understood what they recite.

**Value proposition:** Every existing app in this category delivers *information* — prayer times, a mushaf, a du'a library — and assumes the gap is knowledge. This product treats the gap as **readiness, friction, and comprehension**. It is a launcher for worship, not a destination: it is silent when you're prepared, speaks only when action is possible, measures presence rather than compliance, and never issues verdicts on your worship. It is free permanently, carries no revenue model, and is intended to be held by a waqf so it outlives its builder.

---

## Problem Statement

**Current state.** Practising Muslims who believe fully in the obligation of salah routinely pray outside the first portion of its window, or miss it entirely. The failure is not one of belief or intention. A working professional hears the adhan, dismisses it, and prays Dhuhr ninety minutes later at his desk. He prays 'Isha at 11:30pm in ninety seconds and remembers none of it. He has several Islamic apps installed and opens none of them.

A second population prays consistently yet remains locked out of the interior dimension of worship. They have never made a du'a in their own words, reaching instead for memorised phrases or silence. They recite the Quran as sound rather than as speech, understanding perhaps half of any given ayah and gliding over the rest. When they seek guidance they encounter conflicting sources, ungraded hadith, and unattributed rulings, and withdraw feeling worse than before they searched.

**Why this happens.** The causes are behavioural and structural, not informational:

- **The intervention window is misplaced.** On-time prayer is determined by preparation in the preceding thirty minutes — wudu, appropriate clothing, calendar clearance, physical position — not by any decision made at the adhan. By the time the adhan sounds, the outcome is already set.
- **Preparation is socially punished.** The person who makes wudu early is questioned for it. The behaviour most predictive of success is the one most likely to draw comment.
- **The social cost is about leaving, not praying.** In Muslim-majority settings, being seen praying is encouraged. What is feared is being the person who exits the meeting, declines the gathering, or breaks the group's flow — anxiety about *absence from the event*, not presence at the prayer.
- **Conflicts are accepted hours in advance.** Meetings, appointments, and commitments are scheduled over prayer times without objection, and the conflict becomes unavoidable long before it is noticed.
- **A corrupted permission structure protects delay.** The wide window between prayers is misread as licence. Users believe delay is permitted, having misunderstood the wisdom behind the window — a matter on which scholars differ, with significant weight behind the position that deliberate delay without valid excuse is blameworthy.
- **For the second population, the gap is engagement, not access.** Mushaf access has been solved for over a decade. Du'a libraries are abundant. Neither addresses a person who does not know how to speak to Allah in their own words, or who cannot follow the meaning of what they recite.

**Impact.** The cost is measured in a belief-action gap that produces persistent, low-grade guilt: the sense that one's practice does not match one's conviction, and that a felt, intimate relationship with Allah is available to others but not to oneself.

**Why existing solutions fall short.** The category is built almost entirely on the assumption that the bottleneck is information. Apps deliver accurate prayer times, louder adhans, more notifications, larger libraries. Users hear the adhan and do not move. Notifications arrive at the moment when action is least possible and are muted. Libraries require the user to already know what they are looking for. No product in the category intervenes in the preparation window, addresses scheduling conflicts before they occur, or teaches comprehension as a bounded curriculum rather than offering an unbounded reference.

**Why now.** Calendar access, driving-state detection, and navigation context make pre-positioning intervention technically feasible on consumer devices for the first time. The category meanwhile remains saturated with information-delivery products, leaving the behavioural layer entirely unoccupied.

---

## Proposed Solution

**Core concept.** A mobile application that moves the point of intervention from the moment of prayer to the period preceding it, and that replaces search and reference libraries with bounded, guided curricula.

The product rests on a single reframing: on-time prayer is a **readiness state**, not a decision. A user at any moment is either positioned to pray — in wudu, appropriately dressed, calendar clear, physically able to step away — or is not. The app's function is to raise that readiness in the window before each prayer, and then to withdraw.

### Core Mechanisms

**Readiness as the primary object.** The user declares their state — in wudu, appropriately dressed. The interface displays a countdown not to the prayer but to the *preparation deadline*. The preparation deadline is user-configurable per prayer rather than fixed; a default is proposed at twenty to twenty-five minutes prior, and the user adjusts each prayer to match their own circumstances and local iqama timing. When the user is ready, the countdown is replaced by a calm confirmation and the app falls silent. Preparation is rewarded with the app's absence.

**Conditional intervention.** The app notifies only when two conditions hold simultaneously: a scheduled commitment will collide with a prayer window, *and* the user is not ready. A prepared user is never notified. A user with a clear calendar is never notified. The adhan itself never triggers a notification, on the grounds that it arrives at the moment action is least possible. Where sensing permits, reminders are timed to arrival rather than to transit, because a reminder that cannot be acted upon is noise.

**Conflict resolution before the conflict.** Calendar events are read and typed automatically. When a commitment will consume a prayer window, the app warns before the commitment begins — not before the prayer — and generates a contextually appropriate message the user can send to reschedule or excuse themselves, lowering the social cost of the exit.

**Measurement of presence, not compliance.** Prayers within the user's own target window require no logging. Prayers outside it open a structured reason-picker — a short list of recurring causes rather than free text — which accumulates into surfaced patterns the user can see for themselves. Every prayer, on time or not, asks a single low-friction question: *what did you recite?* This reveals the user's state of attention to themselves without scoring it, and quietly changes how they stand the following day.

**The app never rules.** Target windows are set by the user, per prayer, from a presentation of named scholarly positions on delay. The application measures a standard the user has chosen; it does not apply one of its own.

**Bounded journeys in place of libraries.** Rather than a searchable du'a collection or an unbounded mushaf, the product offers finite, sequenced curricula with visible length and progress: a du'a journey covering adab, the names of Allah, and how to ask in one's own words; and a Quran comprehension journey built on high-frequency vocabulary anchored to passages the user has already memorised, reinforced by spaced repetition. Journeys are silent — no recitation is required at any point. They are framed explicitly as life projects with no urgency, so that slow progress is never experienced as failure.

**Reward placement.** Gamification is confined to zones where it cannot compromise sincerity: full progress mechanics on learning journeys, streaks on adhkar where discipline necessarily precedes taste, and none whatsoever on salah, which is served by reflection rather than by scoring.

### Directional Capabilities Beyond MVP

> **Note for product planning:** the following are **not MVP scope** and should not be planned into initial delivery. They are recorded here because they indicate the product's intended trajectory and should inform architectural decisions — particularly around how device context is ingested, permissioned, and acted upon — so that early choices do not foreclose them.

The pre-positioning thesis extends naturally into device context beyond the calendar. Where the platform permits and the user explicitly grants access, the same logic applies to a broader set of signals:

- **Navigation context.** If the user is travelling to a destination they will reach after a prayer window closes, the app can propose a masjid on the route reachable in time — intervening in a conflict the user has not yet recognised as one.
- **Driving state.** Transit is a poor moment for reminders and a good one for listening. Short audio content on building worship habits can be offered when the user is driving, with any actionable reminder deferred to arrival.
- **Attentional capture.** Where platform APIs allow, detecting use of applications that habitually consume the user's attention could permit a contextual interruption carrying relevant content — a surah recently recited, a story of the Sahaba — addressing the mechanism by which the adhan is dismissed rather than unheard.

**Constraints on these capabilities.** Location is deliberately excluded as a means of inferring whether a prayer was performed; proximity to a masjid is too ambiguous to be trustworthy and false inference would undermine the product's core commitment to never issuing verdicts. Detection of other applications in use is actively constrained by both major mobile platforms and may prove infeasible; it should be treated as speculative. All context ingestion must preserve the product's governing rule: **the app speaks only where action is possible, and remains silent when the user is prepared.**

### Key Differentiators

1. Intervention occurs before the prayer, not at it — no competitor operates in this window
2. The app rewards preparation by going silent, inverting the engagement logic of the category
3. Worship is measured by presence rather than completion
4. Religious authority is deliberately withheld; scholarly difference is surfaced for the user to choose from
5. Education is delivered as a finishable curriculum rather than an unbounded reference
6. The product is free permanently, carries no revenue model, and is intended for waqf stewardship

**Why this will succeed where others have not.** Existing products compete on the accuracy and beauty of information delivery, a dimension on which the category is long since saturated and on which no further gain changes behaviour. This product competes on the causal chain that actually determines whether a prayer happens on time. Its restraint — silence when the user is prepared, no verdicts, no leaderboards, no feed — is not a limitation but the mechanism by which it remains trusted in a domain where overreach is fatal.

**High-level vision.** The tracker earns the daily habit and the trust that makes teaching possible. The journeys teach. Once the behavioural problem is solved and the curricula complete, the relationship endures through Quran study — concordance-style exploration of how a word is used across the Book — and, in later phases, through kinship and community practice. A user who no longer needs the tracker has not churned; they have graduated, and the product's enduring surfaces remain.

---

## Target Users

### Primary User Segment: The Time-Starved Believer

**Profile.** Arabic-speaking Sunni Muslim, broadly 25–45, in salaried employment with limited control over their own schedule. Often married, often with young children. Religiously literate — raised praying, knows the rulings, needs no convincing of the obligation. Frequently was more observant at an earlier point in life, commonly during university, and is aware of having drifted from that version of themselves.

**Current behaviours.** Prays, but inconsistently and often late. Fajr is frequently missed or prayed well after sunrise. Midday prayers collapse under meetings. The evening prayers collide with family routine or arrive at the end of an exhausted day and are performed rapidly and without attention. Typically has two or more Islamic applications installed, all of them muted, none of them opened. Accepts meeting invitations that overlap prayer times without objection and without noticing the conflict at the time of acceptance.

**Needs and pain points.**

- Preparation does not occur, because nothing in the environment prompts it and the workday offers no natural cue
- Scheduling conflicts are accepted hours before they become visible as conflicts
- Leaving a meeting or gathering carries a social cost they are unwilling to pay, not because prayer is stigmatised but because absence from the event is
- Early wudu, the single most protective behaviour, attracts comment from colleagues and is therefore suppressed
- Delay is rationalised through a misunderstanding of the prayer window as permission
- The prayers that are performed feel hollow; the body attends and the attention does not

**Goals.** To close the gap between what they believe and what they do. To pray in the first portion of the window as a matter of course rather than as an occasional success. To stop carrying the low-grade guilt of knowing better. To be, for their children, the person they intend to be.

**What they need from the product.** Prompting to prepare at the moment preparation is possible. Advance warning of conflicts before the conflicting commitment is accepted or begun. A means of leaving that costs less socially. Visibility of their own recurring patterns. A mechanism that returns attention to prayers performed on autopilot. Above all, an application that does not add to the guilt they already carry.

### Secondary User Segment: The Barrier-Blocked Believer

**Profile.** Arabic-speaking Sunni Muslim, broadly 20–35, frequently more consistent in prayer than the primary segment. Reads Arabic fluently in daily life but finds Quranic register substantially harder, understanding perhaps half of a given ayah and passing over the remainder. Often carries reluctance or self-consciousness about reciting aloud, which may originate in earlier experiences of correction, comparison, or perceived inadequacy, and which has left recitation an avoided activity rather than a practised one.

**Current behaviours.** Prays consistently. Recites from memory as sound rather than as comprehended speech. Has never made a du'a in their own words; reaches for memorised formulae or falls silent and hopes the intention registers. Has downloaded and deleted dhikr counters repeatedly. Follows religious accounts on social platforms, experiences frequent inspiration, and converts it into action almost never. Searches for guidance occasionally, encounters conflicting and unsourced results, and withdraws.

**Needs and pain points.**

- Does not know how to begin speaking to Allah in their own words, and imports a formal register that the relationship does not require
- Does not know the adab of du'a, the times of response, or the names of Allah by which to call — the instrument is unavailable rather than unused
- May believe du'a must be in Arabic of a certain register to be valid, and is silenced by the belief
- Asks small, never having been taught to ask large
- The relationship falls quiet in ease, so that hardship becomes a call placed to someone not spoken to in months
- May feel disqualified from asking at all by recent sin
- Cannot distinguish trustworthy sources from unsourced ones, and experiences searching as a net loss
- Recitation is untethered from meaning, so Quran engagement remains passive and unrewarding; and reluctance to recite aloud means the avenue most commonly offered by existing products is closed to them

**Goals.** To feel close to Allah rather than merely obedient. To be able to ask for what they actually want in their own words. To understand what they recite. To find the intimate, felt dimension of the religion they suspect others have access to.

**What they need from the product.** A route rather than a destination — sequenced instruction that builds capability rather than supplying more material to an unprepared user. Elimination of search, with sourcing handled on their behalf. A path with visible length and no urgency. Vocabulary instruction anchored to passages already memorised. Reinforcement that accommodates forgetting. And no requirement to recite aloud at any point.

### Notes on Segmentation

These segments overlap substantially in practice and are not mutually exclusive. The time-starved believer frequently shares every deficit of the second segment; the barrier-blocked believer benefits from the readiness tools despite already praying consistently. They are distinguished here because they enter the product through different doors and require different emphasis, not different features.

The tracker serves both, but differently: for the primary segment it functions as triage, addressing prayers being lost; for the secondary segment it functions as refinement, addressing presence and earliness where attendance is already established. The application's tone should reflect the user's actual state rather than assuming deficit, or consistent users will experience the product as speaking to someone else.

---

## Goals & Success Metrics

**A note on measurement in this product.** Conventional product metrics are actively misleading here. Session length, daily opens, and time-in-app measure consumption, and this product's stated purpose is to minimise its own consumption. A user who opens the app less because they are prepared more is a success, and any metric that reads that as decline will drive the product in the wrong direction. Metrics below are therefore selected to track **worship performed** and **capability gained**, never attention captured.

A second constraint applies. The product deliberately withholds judgment on the quality or acceptance of worship, which belongs to Allah alone. Nothing here should be read as measuring spiritual state. Presence indicators track what the user reports to themselves, and exist for the user's own reflection rather than for evaluation.

A third constraint follows from the first two. Baselines, trends, and patterns are computed silently from ordinary use. The application does not ask the user to assess their own religious performance at any point, and does not present historical comparison in a form that reads as a verdict. Where the product surfaces patterns, it does so descriptively — identifying which prayer is most frequently lost and under what recurring circumstance — and leaves interpretation and remedy to the user.

### Business Objectives

The product has no revenue model and is not intended to generate income. "Business" objectives are therefore mission objectives.

- **Deliver a working Phase 0 within a defined initial build period**, comprising readiness state, per-prayer target windows, and conditional logging, sufficient for a real user to use daily
- **Reach an initial cohort of users who sustain use beyond thirty days**, establishing that the behavioural mechanism holds outside the builder's own practice
- **Secure content contributors and a named reviewer with recognised Islamic qualification** before Phase 2 delivery, such that no religious content ships unreviewed
- **Establish waqf or foundation stewardship** before the product accumulates significant dependency, so that continuity does not rest on one individual
- **Ship and maintain at zero cost to users, permanently**, with infrastructure costs held within a level sustainable by endowment or personal contribution

### User Success Metrics

- **Proportion of prayers falling within the user's own declared target window**, trending upward over a user's tenure — the primary indicator, and the one closest to the product's purpose
- **Readiness declared before the preparation deadline**, as a proportion of prayers — the leading indicator, since the readiness state is the causal mechanism the entire product rests on
- **Reduction in scheduling conflicts accepted**, measured as prayer-overlapping commitments that are rescheduled, shortened, or exited, versus those that consume the window entirely
- **Users recognising their own patterns**, evidenced by engagement with surfaced pattern insights and subsequent change in the associated prayer
- **Journey progression sustained over months rather than abandoned in weeks**, reflecting the life-project framing rather than completion speed
- **Retention of journey material**, measured through spaced repetition performance rather than lessons completed
- **Declining reliance on the tracker among long-tenured users**, treated as graduation rather than churn, provided Quran engagement persists

### Key Performance Indicators

- **On-time rate:** prayers within user-declared target window ÷ total prayers logged. Baseline is derived implicitly from the user's first weeks of ordinary logging and is never requested from the user, never displayed as a starting score, and never referenced in comparison. Target: measurable improvement per user cohort over ninety days.
- **Readiness lead time:** median interval between readiness declaration and prayer entry. Target: stable or increasing, indicating earlier preparation
- **Notification necessity rate:** notifications sent ÷ prayers. Target: **declining over a user's tenure.** A falling rate means users are preparing unprompted. This KPI is deliberately inverted against category norms
- **Notification action rate:** proportion of sent notifications followed by readiness declaration or conflict resolution. Target: high. A low rate means the conditional doctrine is misfiring and notifications are being ignored, which is the failure state the doctrine exists to prevent
- **Conflict interception rate:** prayer-conflicting calendar events flagged before commencement ÷ total such events. Target: high coverage, contingent on calendar permission grant
- **Recitation recall completion:** proportion of logged prayers where the user answers what they recited. Target: high, as the question is designed to be near-frictionless. Decline indicates the mechanism has become burdensome
- **Thirty-day and ninety-day retention**, qualified: retention is meaningful only when paired with on-time rate. Retained users whose on-time rate is flat represent a product failure that retention alone would conceal
- **Spaced repetition retention rate** on Quran vocabulary. Target: to be established against standard SRS benchmarks once Phase 3 is defined

### Explicitly Rejected Metrics

Recorded so they are not reintroduced: session duration, daily active use as a standalone goal, screen time, content items consumed, streak length on salah, any comparative or ranked measure between users, any metric that would improve by making the application harder to leave, and any onboarding step that asks the user to self-report their current worship performance.

---

## MVP Scope

**Definition of the MVP.** The minimum viable product comprises **Phase 0 and Phase 1**: the readiness and logging spine, plus the reflection layer and calendar collision engine. The journeys are explicitly excluded, on the grounds that they are blocked on volunteer content production outside the builder's control and would indefinitely delay any release.

The sequencing is driven by **delivery constraint, not by user demand**. Demand for both halves of the product is real and largely distinct: some users arrive needing help with consistency and have little interest in structured study, while others already pray reliably and are seeking comprehension of the Quran and competence in du'a. Neither audience is secondary in importance.

What separates them is buildability. The tracker can be built by one person with no budget and no dependencies. The journeys require written curricula, scholarly review, and contributors whose availability the builder does not control. Shipping the tracker first is therefore a matter of what can be delivered now, and it has the additional benefit of establishing the daily habit and trust that the educational surfaces will later rely on.

**A consequence worth planning for:** users who arrive for the educational half will find the MVP does not yet serve them. Communication at launch should be honest about what the product currently is and where it is going, rather than implying a completeness it does not have.

### Core Features (Must Have)

- **Prayer time calculation engine.** Accurate per-location prayer times with configurable calculation method. *Rationale:* invisible infrastructure, not a user-facing feature. Required because every preparation countdown, conflict detection, and target window depends on it. The product does **not** compete on prayer time display and should not present itself as a prayer time application.
- **Readiness state.** User declaration of wudu and appropriate clothing, presented as the primary object on the home surface. *Rationale:* the causal mechanism the entire product rests on, and the cheapest feature on this list relative to its impact.
- **Preparation countdown.** A visible countdown to the user's configured preparation deadline rather than to the prayer itself, defaulting to twenty to twenty-five minutes prior and adjustable per prayer. When the user is ready, the countdown is replaced by a calm confirmation state. *Rationale:* reframes the prayer as a window to position into rather than a moment that arrives, and makes the app's silence a visible reward for preparation.
- **Per-prayer target windows with scholarly opinion presentation.** The user configures their own on-time window for each prayer, choosing from a presentation of named scholarly positions on permissible delay. *Rationale:* the application must never issue verdicts on worship. The user selects a standard; the app measures against it. Per-prayer configuration is required because iqama intervals and the relevant texts differ across the five prayers.
- **Conditional prayer logging.** Prayers within the user's target window require no log entry. Prayers outside it open a structured reason-picker offering a short list of recurring causes, with the option to add new ones. *Rationale:* friction is placed only where the data has value, and the absence of a demand on good days reinforces the launcher-not-destination principle.
- **Recitation recall.** A single low-friction question on every logged prayer: what was recited. *Rationale:* returns attention to prayers performed on autopilot without asking the user to grade their own spiritual state. Universally applied because the answer requires no deliberation.
- **Calendar ingestion and conflict detection.** Read access to the user's calendar, including recurring events, with automatic detection of commitments overlapping prayer windows and inference of event type. *Rationale:* conflicts are accepted hours before they become visible, and this is the only mechanism that can intervene at acceptance.
- **Conditional notification engine.** Notifications fire only where a detected conflict coincides with an unready user, and are timed before the conflicting commitment rather than before the prayer. No notification is triggered by the adhan. *Rationale:* the governing doctrine of the product; implemented as a rule the system enforces rather than a preference the user tunes.
- **Escape message generation.** Contextually appropriate, pre-composed messages the user can send to reschedule or excuse themselves, varying by event type. *Rationale:* addresses the social cost of leaving, which is the primary obstacle for the primary segment.
- **Pattern surfacing.** Descriptive presentation of recurring loss patterns derived silently from logged data — which prayer is most frequently lost, under which recorded circumstance. No prescriptions offered. *Rationale:* measurement is half the solution; remedy belongs to the user.
- **Adhkar tracking with streaks.** Counter-based tracking of daily adhkar with streak mechanics. *Rationale:* the one worship domain where gamification is safe, because adhkar produce no observable output and discipline must precede taste. Deliberately excluded from salah.
- **Custom user-defined activities.** Tracking of user-added worship activities beyond the prescribed set. *Rationale:* stated as a core requirement at session outset, and cheap once the tracking spine exists.

### Out of Scope for MVP

- Du'a journey and all guided curricula
- Quran comprehension journey, vocabulary instruction, and spaced repetition
- Quran concordance and word-tracing tools
- Any content feed or browsable content surface
- Short-form video or article content of any kind
- Audio content, including commute material
- Navigation intercept and masjid routing
- Driving-state detection
- Other-application usage detection
- Location-based prayer inference *(permanently excluded, not deferred)*
- Any social, community, or companionship feature
- Kinship domain
- Sadaqah tracking
- Recitation practice, correction, or audio input of any kind *(permanently excluded)*
- Non-Arabic localisation
- Family or household shared accounts
- Child-facing features, including the Maghrib–bedtime merge
- Any comparative or ranked feature between users *(permanently excluded)*

### MVP Success Criteria

The MVP succeeds if a cohort of real users, over ninety days, demonstrates a measurable increase in the proportion of prayers falling within their own declared target windows, accompanied by earlier readiness declaration and a declining notification necessity rate.

Stated more plainly: **users prepare earlier without being told to, and pray earlier as a result.** Retention alone does not constitute success. A retained user whose on-time rate has not moved represents a failure the retention figure would conceal.

---

## Post-MVP Vision

### Phase 2 Features

**The du'a journey.** A bounded, finishable curriculum covering the adab of supplication, the names of Allah and when to call by each, the times of response, how to ask in one's own words, how to ask largely, and how to speak naturally rather than in imported formal register. Structured as sequenced lessons with worked examples and recognition-based exercises rather than writing or speaking tasks. Progress is visible and the total length is stated at the outset.

The curriculum must address the full cluster of causes identified in discovery, not merely instruction in wording: feeling disqualified to ask after sin, weak certainty arising from perceived unanswered du'a, the belief that Arabic of a particular register is required, and the relationship falling quiet in ease. On the last point, the framing is strictly additive — supplication in hardship is a door, never a defect, and no content may imply that crisis du'a is inferior. The instruction is to let ease also be a time of speech.

**Gamification arrives here.** Journeys are the safe home for progress mechanics, because rewarding the completion of a lesson carries no risk to sincerity in worship. Mechanics must nonetheless avoid pressure: progress accumulates and never resets, absence costs nothing, and return is welcomed rather than penalised. The journey is framed explicitly as a life project with no schedule and no one waiting.

**Content infrastructure.** Phase 2 requires the editorial pipeline the MVP avoided: contributor recruitment, a briefing and drafting process, hadith grading, source attribution, and a named reviewer with recognised qualification accountable for accuracy. This pipeline is a deliverable in its own right and its establishment gates the phase.

### Phase 3 Features

**The Quran comprehension journey.** The product's stated ultimate purpose. High-frequency Quranic vocabulary taught in sequence, anchored wherever possible to passages the user has already memorised, so that words recited for a lifetime begin to speak. Real ayat accompany every item rather than isolated glossary entries. Spaced repetition is integral rather than supplementary, since without it early material is forgotten before later material arrives and the journey collapses. The path is entirely silent — no recitation, correction, or audio input at any stage.

**Quran concordance and word tracing.** The enduring surface of the product. Lookup of a word across every occurrence in the mushaf, allowing the user to build contextual understanding of how a term is used — following a word such as *ṣidq* through the Book to see the shape of its meaning. This is the natural continuation of the vocabulary journey: the curriculum teaches the word, the concordance lets the user pursue it.

### Later Phases

- **Contextual device capabilities.** Navigation intercept proposing a reachable masjid when the user's destination will be reached too late; driving-state audio content; and, subject to platform feasibility, attentional-capture interruption. Governed throughout by the rule that the application speaks only where action is possible, and by the permanent exclusion of location as a means of inferring whether a prayer was performed.
- **Household and family worship.** The conversion of family from obstacle to ally. Prayer conflicts with family routine are permanent and recurring, and are better dissolved than fought — a prayer performed alongside a child is not an interrupted prayer but a formative one. Includes prophetic precedent content delivered at the moment of conflict, short teachable items for children, and the structural reframing of recurring collisions as one-time restructuring rather than daily willpower.
- **Companionship.** Deliberately deferred rather than rejected. The obstacle identified in discovery is social, and the MVP's response is entirely private, which is a known mismatch. Future work may introduce companionship without competition: a single person told, a colleague who leaves the room with you, a spouse who knows the month's intention. Ranked or comparative features between users remain permanently excluded.
- **Kinship.** Silat ar-raḥim as a tracked and supported domain, with family members contributing together.
- **Additional worship domains.** Sadaqah and further areas as the tracking spine proves extensible.

### Long-term Vision

Over a two to three year horizon the product becomes a durable companion whose usage shifts as the user matures. The tracker, having done its work, recedes: users who prepare without prompting need it less, and this is treated as graduation rather than attrition. What remains is Quran study, which never finishes, and in time the communal and familial dimensions of practice.

The product is intended to be held under waqf or foundation stewardship, with intellectual property assigned to the endowment rather than to an individual, funding sufficient for perpetual hosting, a named trustee body, and a defined succession path for technical maintenance. The intent is continuity beyond its builder — a product that survives the loss of any individual, including its author.

### Expansion Opportunities

- **Localisation beyond Arabic**, opening the product to the majority of the ummah. Deferred rather than rejected; would require translation of all curricula and a second content voice
- **Regional calibration** of iqama intervals and calculation methods across Arabic-speaking regions, where practice varies materially
- **Open source contribution**, potentially aligned with waqf stewardship, as a route to maintenance continuity
- **Institutional partnership** with masjids or Islamic educational bodies for content credibility and distribution

---

## Technical Considerations

These are initial constraints and preferences captured at briefing stage, not architectural decisions. They exist to inform the Architect, not to pre-empt them.

### Platform Requirements

- **Target platforms:** Mobile only. iOS and Android. No web application, no desktop, no wearable in MVP scope.
- **Language:** Arabic only, with right-to-left layout as the primary and only text direction in MVP. No localisation framework required initially, though avoiding hard-coded strings costs little now and preserves the expansion path.
- **Connectivity:** Prayer calculation, readiness state, logging, and the countdown must function fully offline. A user in a basement office or without data must still be served by the product's core mechanism. Calendar reading and any future content delivery may reasonably require connectivity.
- **Performance:** The product's own principle is that it must open fast and close fast. Cold start to actionable home surface should be near-instantaneous. Any perceptible load defeats the launcher premise.
- **Background execution:** Reliable scheduled notification delivery is required. This is a known area of platform difficulty, particularly on Android where aggressive battery optimisation by device manufacturers routinely suppresses scheduled work, and it warrants early technical validation rather than late discovery.

### Technology Preferences

- **Frontend:** Not specified. A cross-platform framework is strongly indicated by the solo-builder constraint, since maintaining two native codebases alone is not realistic. The Architect should weigh this against the background-execution and notification-reliability requirements, which are the areas where cross-platform approaches most often struggle.
- **Backend:** Minimal by preference. The MVP's core function is local — calculation, state, logging, scheduling — and could plausibly operate with no server at all. Any backend introduces perpetual hosting cost, which conflicts directly with permanent free operation under endowment funding.
- **Data storage:** Local-first, with a required migration and backup path. User worship records must survive device replacement, including migration between iOS and Android. Records are among the most sensitive data a person could hold and should not leave the device as a matter of routine, but permanent loss at device change is not acceptable for data accumulated over years.
- **Infrastructure:** Cost must be sustainable indefinitely under waqf funding. Architectural choices that scale cost linearly with user growth are a structural risk to a product with no revenue.

### Architecture Considerations

- **Prayer time calculation:** A well-established, verifiable library should be used rather than a custom implementation. Calculation methods vary by region and school, and errors here invalidate every dependent feature. The user must be able to select calculation method.
- **Per-prayer configuration model:** Target windows, preparation lead times, and iqama assumptions are configured independently per prayer. Data structures should assume per-prayer variation from the outset rather than a global setting retrofitted later.
- **Calendar integration:** Read-only access to the platform calendar, handling recurring events correctly. Permission may be declined, and the product must remain fully functional without it, with conflict detection degrading gracefully to manual event entry.
- **Notification engine as a rule system:** The conditional doctrine — fire only on conflict plus unreadiness, never at the adhan, timed to the commitment rather than the prayer — should be implemented as enforced system logic rather than as user-adjustable preferences, since it constitutes the product's governing behaviour rather than a setting.
- **Data portability and migration.** The product must provide a mechanism by which a user's complete history — logged prayers, reasons, patterns, readiness records, adhkar streaks, custom activities, and in later phases journey progress and spaced repetition state — can be transferred to a new device, including across platforms. Because neither platform's native backup crosses to the other, this cannot be delegated to the operating system. The Architect must resolve deliberately between:
  - **User-initiated export and import** — an encrypted file the user saves and restores themselves. Preserves local-first strictly, adds no hosting cost, places no worship data on any server. Costs the user a manual step and relies on them having performed it *before* the device was lost or broken.
  - **Optional account-based synchronisation** — automatic, resilient, supports multi-device use, but introduces perpetual hosting cost against an endowment-funded product with no revenue, and places sensitive worship records on infrastructure someone must secure and maintain in perpetuity.
  - **A hybrid** — local-first by default with export always available, and optional opt-in synchronisation for users who accept the trade-off.

  The brief does not prescribe the choice. It states the constraints the choice must satisfy: **no worship data leaves the device without explicit, informed, revocable consent; the product remains fully functional for a user who declines any cloud component; and infrastructure cost must remain sustainable indefinitely under endowment funding.**
- **Content delivery for later phases:** Journeys, lessons, and spaced repetition scheduling will require content storage and update mechanisms not needed in MVP. Architectural choices should avoid foreclosing this, without building for it prematurely.
- **Device context ingestion:** Future navigation, driving-state, and attentional signals should inform how permissions and context handling are structured now, so that later addition does not require restructuring. Location is used for prayer time calculation only and is permanently excluded from prayer inference.

### Security, Privacy and Compliance

- **Data sensitivity:** Records of an individual's worship practice, including failures, constitute exceptionally sensitive personal data. Local-first storage is the strongest available protection and should be the default.
- **Permissions:** Calendar and location access must be requested with clear explanation of purpose, and refusal must leave a functional product.
- **No analytics by default:** Behavioural telemetry on worship data should be treated as prohibited absent explicit, informed, revocable consent. Aggregate product metrics, where needed, should be designed to avoid collecting individual worship records.
- **Encryption:** Any synchronisation or backup mechanism must encrypt worship records in transit and at rest, and should be designed so that the operator cannot read individual users' worship histories.
- **Content accountability:** Any religious content shipped requires attributed sourcing and review by a named qualified reviewer. This is a compliance requirement of the product's own principles, not merely an editorial preference.
- **App store considerations:** Religious applications encounter review variability across markets. Worth anticipating rather than discovering at submission.

---

## Constraints & Assumptions

### Constraints

- **Budget.** None. No development, marketing, content, or infrastructure budget beyond what the builder personally absorbs or what endowment funding later provides. The product generates no revenue by design and is free permanently. Any choice whose cost scales with user growth is a structural threat rather than an ordinary expense.
- **Resources.** One person, building alone, part-time. The single most binding constraint in the document; it governs every scope decision. Content for later phases depends on volunteer contributors whose availability the builder does not control and cannot schedule. No designer, no QA function, no operations support.
- **Timeline.** Undefined. No external deadline, no funding runway, no commitment to a launch date. This permits the life-project framing applied to users to apply equally to the build, but carries the corresponding risk that a project without deadlines may not ship.
- **Technical.** Reliable scheduled notification delivery, particularly on Android under manufacturer battery optimisation, is the product's most exposed technical dependency. Detection of other applications in use may prove infeasible on both platforms. A solo builder cannot realistically maintain two native codebases, constraining framework choice.
- **Scope.** Arabic only. Sunni only. Mobile only. No recitation input, ever. No ranked comparison between users, ever. No location-based inference of prayer performance, ever.
- **Editorial.** No religious content may ship without attributed sourcing and review by a named qualified reviewer. This gates every educational phase and cannot be relaxed under schedule pressure without compromising the product's central claim to trustworthiness.

### Key Assumptions

Recorded so they can be tested rather than inherited as fact.

- That the pre-positioning thesis holds generally. It is drawn from the builder's own successful practice and was validated in discovery through reasoning rather than through research on other users. **This is the foundational assumption of the entire product and it is currently unvalidated at scale.**
- That readiness declaration is a behaviour users will actually perform — a manual, honest, repeated self-report with no external verification and no immediate reward beyond the app's silence
- That silence functions as a reward rather than reading as absence or malfunction
- That users will grant calendar access; refusal degrades the conflict engine to manual entry, which is substantially higher friction and likely to be abandoned
- That users schedule meaningfully in a calendar at all; users whose commitments are informal, verbal, or ad hoc are poorly served by the conflict engine
- That an escape message meaningfully reduces the social cost of leaving, rather than the obstacle being emotional and unaffected by better wording
- That the recitation recall question stays low-friction across hundreds of repetitions rather than becoming an irritation that suppresses logging
- That conditional logging produces sufficient data; only late prayers generate reason data, which may under-sample the circumstances of successful prayers
- That surfaced patterns produce change, and that awareness is genuinely half the solution rather than merely half the diagnosis
- That streaks on adhkar remain safe — a judgment about the boundary of permissible gamification that has not been tested against users' actual experience
- That volunteer contributors will produce curriculum of sufficient quality and quantity, and that a qualified reviewer will accept ongoing accountability without payment
- That a bounded curriculum is genuinely finishable — that the du'a journey has a natural end rather than expanding indefinitely under editorial ambition
- That high-frequency vocabulary meaningfully improves comprehension of ordinary recitation
- That users will accept the life-project framing without the absence of pressure removing the motivation to continue
- That graduation is real and desirable, and that departing users are succeeding rather than churning
- That waqf stewardship is practically achievable for a software product, with trustees, assigned intellectual property, and perpetual funding
- That Arabic-only scope is sufficient for viability, notwithstanding that it excludes the majority of the global ummah
- That the app store review process does not materially obstruct a religious application of this kind

---

## Risks & Open Questions

### Key Risks

- **Religious harm through product error.** The highest-severity risk in the document. Incorrect rulings, ungraded or fabricated hadith, or framing that misrepresents scholarly positions could cause users to alter their worship on false information. Severity is not commercial but spiritual, and the reputational damage to a religious product that ships an error is close to unrecoverable. Mitigated by the editorial constraint, by the product's refusal to rule on contested matters, and by surfacing named scholarly positions rather than asserting a single view.
- **The product accuses rather than invites.** Tone drift across dozens of copy decisions, a pattern display that reads as an indictment, or a countdown that feels like pressure could convert a tool of support into a source of guilt. Users experiencing religious guilt do not complain; they uninstall.
- **Solo builder discontinuity.** One person, part-time, no deadline, no team. The project may stall, and if it ships and is adopted, its maintenance rests entirely on one individual's continued availability and health. Partially mitigated by waqf intent, but the waqf does not yet exist and the mitigation is currently aspirational.
- **Content pipeline failure.** Phases 2 and 3 — including the stated ultimate purpose of the product — depend on volunteers whose time is not controlled and a reviewer who must accept unpaid ongoing accountability. The beachhead risk follows directly: a tracker that works may absorb all available effort while the journeys remain permanently deferred.
- **Notification unreliability.** The conditional notification is the delivery mechanism for the product's most novel feature. If Android battery optimisation suppresses scheduled work, the conflict engine silently fails for a substantial share of users, and silent failure is worse than visible failure because neither user nor builder learns of it.
- **Readiness declaration is not sustained.** The mechanism requires an unrewarded manual self-report several times daily. If users stop declaring, the readiness state becomes stale, notifications fire wrongly or not at all, and the entire causal chain breaks.
- **The thesis does not generalise.** A user whose problem is not preparation but exhaustion, depression, or genuine loss of conviction is unserved and may feel further from help than before.
- **Insufficient perceived value at launch.** The MVP offers no content, no Quran, no du'a material — precisely what users expect from a religious application. It may be perceived as an empty habit tracker, and first impressions in a saturated category are rarely revisited.
- **Privacy exposure.** Worship records including failures, held on a device or synchronised to any server, would be materially harmful if exposed. In some contexts, records of religious practice carry risks beyond embarrassment.
- **Scope dilution through custom activities.** Arbitrary user-defined tracking may pull the product toward a general habit tracker with a religious theme, which is the category it is specifically designed not to be.

### Open Questions

- What is the product called? No name has been established, and naming affects positioning, store discovery, and tone.
- Does Phase 0 alone ship first, or is Phase 0 plus Phase 1 the minimum meaningful release? The brief assumes the latter; this remains the most contestable scope decision in the document.
- How is the initial user cohort reached with no marketing budget?
- Who is the named reviewer, and have they accepted the role?
- How many lessons constitute a du'a journey that feels complete rather than demonstrative?
- Which scholarly positions on permissible delay are presented, and who selects them?
- What is the iqama default per prayer, given material regional variation, and how is it derived for a user whose location is known but whose mosque is not?
- How does the product serve women, travellers, and anyone for whom congregational timing is not the reference point?
- Should the concordance ship ahead of the vocabulary journey, given that it is far less blocked on contributors?
- Which migration approach is adopted: manual export, optional sync, or hybrid?
- What happens the first time a user opens the app — what does onboarding do, given that asking about current practice is excluded?
- How does the product respond to a user in an extended low period, where consistency has collapsed entirely?
- Is there any circumstance in which the product should recommend professional or pastoral help beyond its own scope?

### Areas Needing Further Research

- **Validation of the pre-positioning thesis** beyond a single practitioner. The highest-value research available, and cheap: structured conversations with fifteen to twenty practising Muslims about what precedes their on-time and late prayers.
- **Competitive analysis** of the existing category, to confirm that the pre-positioning window is genuinely unoccupied rather than attempted and abandoned.
- **Android background execution feasibility**, tested early on real devices from manufacturers with aggressive optimisation.
- **Scholarly positions on delay of prayer**, compiled rigorously with attribution, as the direct input to the target-window feature.
- **Regional iqama practice** across Arabic-speaking markets.
- **Waqf establishment for digital assets**, including precedent, trustee structures, and intellectual property assignment.
- **Spaced repetition parameters** appropriate to Quranic vocabulary rather than general language learning.
- **App store policy** for religious applications across relevant markets.

---

## Appendices

### A. Research Summary

No formal market research, competitive analysis, or user interviews were conducted. The findings below derive from a structured brainstorming session using first principles analysis, persona-based role playing, assumption reversal, resource constraint forcing, and speculative scenario work. Findings are reasoned rather than empirically validated, and the highest-value next step identified is validation of the foundational thesis against real users.

**Causal fundamentals established in discovery.** These are the reasoning on which the entire product rests and should be treated as the brief's core analytical content.

1. **The intervention window is before the prayer, not at it.** Successful on-time prayer is determined by actions taken twenty to thirty minutes prior — wudu, clothing, calendar clearance, physical positioning. By the moment of the adhan, the outcome is already set.
2. **Success is a readiness state, not a decision.** A person at any moment is either positioned to pray or is not.
3. **The social fear concerns being seen leaving an event, not being seen praying.** In Muslim-majority settings prayer is socially encouraged; absence from a gathering is not.
4. **Preparation behaviour is socially punished.** Early wudu attracts comment, suppressing the single most protective behaviour.
5. **Delay is protected by a corrupted permission structure.** The wide prayer window is misread as licence. Scholars differ on where permissible delay becomes blameworthy, with significant weight behind the position that deliberate delay without excuse is sinful. The product carries the disagreement rather than resolving it.
6. **For the barrier-blocked, the gap is engagement, not access.** Mushaf and du'a availability were solved long ago; neither addresses comprehension or capability.
7. **Du'a fails for a cluster of reasons.** Feeling disqualified by sin; weak certainty from perceived unanswered supplication; ignorance of adab, times of response, and the names of Allah; belief that a particular Arabic register is required; performing formality instead of speaking naturally; asking small; the relationship falling quiet in ease so that hardship becomes a call to a stranger; unfamiliarity with speaking aloud about one's actual life; and a modern instinct that asking is not acting. **Crisis supplication is a door, not a defect — the aim is to add speech in ease, never to discourage the call already being made.**
8. **Knowledge access is itself an obstacle.** Searching produces conflicting and unsourced results and frequently leaves the user worse off. The product eliminates search rather than improving it.
9. **The product is a launcher for worship, not a destination** — with the sole exception of Quran and knowledge content, where consumption is itself the act.
10. **Motivation should track interior presence, not exterior compliance.** The common pain is not absent prayer but hollow prayer, where belief and action fail to align.
11. **The product must add, never accuse.** Any framing that makes a user feel caught or spiritually audited produces withdrawal rather than correction. Every prompt is an invitation.

**Design policies derived from the fundamentals.**

- Gamification is permitted on learning journeys and on adhkar, and excluded from salah entirely
- The application never rules on contested religious matters; it presents named scholarly positions and the user chooses
- Notifications fire only where conflict coincides with unreadiness, never at the adhan, and always where action remains possible
- Preparation is rewarded with the application's silence
- Friction is placed only where data has value; on-time prayers demand nothing
- Patterns are surfaced descriptively; remedy belongs to the user
- Baselines are derived implicitly and never requested

**Session output.** Fifty distinct product ideas were generated across five techniques, together with the phase structure adopted in MVP Scope and Post-MVP Vision. The complete idea inventory has not been separately documented and should be if a fuller record is wanted.

### B. Stakeholder Input

No external stakeholder input has been gathered. Contributors with formal Islamic education have been identified as willing in principle to assist with content, but none have been briefed, committed, or scheduled. No qualified reviewer has accepted accountability for religious accuracy. No prospective users have been consulted.

### C. References

None. No competitive analysis, market research, or scholarly compilation has yet been conducted. The research areas identified above list what is required.

---

## Next Steps

### Immediate Actions

1. **Validate the pre-positioning thesis** through structured conversations with fifteen to twenty practising Muslims regarding what precedes their on-time and late prayers. Cheapest available de-risking of the product's foundational assumption.
2. **Conduct competitive analysis** of the existing category to confirm the pre-positioning window is genuinely unoccupied.
3. **Test Android background execution and scheduled notification reliability** on real devices from manufacturers known for aggressive battery optimisation, before committing to a framework.
4. **Name the product.**
5. **Resolve the Phase 0 versus Phase 0-plus-1 scope question**, ideally informed by the thesis validation.
6. **Approach and secure a qualified reviewer** willing to accept ongoing accountability for religious accuracy, recognising this gates all educational phases.
7. **Compile scholarly positions on permissible delay**, with attribution, as direct input to the target-window feature.
8. **Investigate waqf establishment for digital assets**, including trustee structures and intellectual property assignment, before dependency accumulates.
9. **Decide the migration approach** — manual export, optional synchronisation, or hybrid — as it shapes backend architecture and perpetual cost.
10. **Design onboarding**, given the constraint that current practice must not be requested.

### PM Handoff

This Project Brief provides the full context for the product described. Please begin in **PRD Generation Mode**, reviewing the brief thoroughly and working with the stakeholder to produce the PRD section by section, requesting clarification and suggesting improvements where the brief is incomplete.

**Particular attention is requested on the following.** The product's governing principles — silence on readiness, no notification at the adhan, no gamification of salah, no religious rulings, no ranked comparison, and add-never-accuse — are load-bearing design decisions rather than preferences, and conventional product instincts will tend to erode them. Several exclusions are permanent rather than deferred and are marked as such. The measurement approach deliberately inverts category norms, treating declining notification volume as success and declining tracker use among long-tenured users as graduation rather than churn. And the resource constraint — one person, part-time, no budget — should govern every scope judgment rather than being treated as a temporary condition.