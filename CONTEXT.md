# Elbow Recovery Tracker

A single-user tracker for a return-to-climbing rehab protocol after a posterior elbow dislocation. It exists to drive daily adherence to the protocol and to gate progression on clinical criteria rather than the calendar.

## Language

**Protocol**:
The rehab plan itself — phases, exercises, dosing, and entry criteria — authored in `elbow-dislocation-rehab-protocol.md`, which is the single source of truth.
_Avoid_: plan, program

**Phase**:
One of five stages of the Protocol (0–4). Phases 1–4 unlock by ticking all Entry Criteria, never by a date; dates are guide ranges only. Phase 0 ("In Cast") is the exception: it ends on an event — cast off, brace fitted, Block Schedule entered.
_Avoid_: stage, level, week-block

**Entry Criterion**:
A discrete, checkable clinical condition that gates a Phase (e.g. "3 × 20 s bodyweight hang pain-free"). Always ticked by a human — the app shows supporting measurements as evidence but never auto-ticks. Untickable: regression re-locks the Phase. Editable, since the clinic may add or change them; removing one is an Override, not a skip.
_Avoid_: gate, milestone (a Milestone is a celebration, not a gate)

**Item**:
A single prescribed exercise or task in the Protocol, with a cadence (how often) and a Lifespan (when it applies). Only rehab work and gate tests are Items; general training is out of scope.
_Avoid_: exercise (some Items aren't exercises, e.g. the red-flag check), task

**Block Schedule**:
The clinic-set table of date → allowed extension angle for the hinged brace. Entered at the Phase 0 → 1 transition, edited as an Override, and displayed prominently while the brace is worn.
_Avoid_: brace settings, ROM limits

**Dose**:
The current prescription for a loading Item (resistance, sets × reps, progression stage). A Dose evolves within its Item via the Progress action and is stamped onto every Tick; planned in-protocol progressions are stages of the Dose, not new Items.
_Avoid_: load, weight, level

**Hold**:
A day-state in which Progress actions are disabled and "repeat the same load" is shown, while ticking at the current Dose remains available. Entered when the morning settle prompt is answered "no" (lasts that day) or when a pain/stiffness trend is rising (persists until the trend clears). After 5 consecutive Hold days the app suggests stepping back a Phase but never does it automatically. Hold means repeat, not rest.
_Avoid_: rest day, deload

**Lifespan**:
The window during which an Item appears on the Today view: it starts when a Phase unlocks and ends when a later Phase unlocks or a named retirement condition is met. Items can span multiple Phases.
_Avoid_: duration, schedule

**Red-Flag Check**:
The weekly three-item safety screen (ROM regressing, clunking or giving way, ulnar tingling) asked on the Monday Morning Prompt, with extension-deficit history shown as evidence. Any yes raises a persistent contact-the-clinic banner that clears only via the explicit "I've contacted the clinic" action.
_Avoid_: symptom diary, health check

**Tick**:
A logged completion of a protocol item. Its shape follows the item's cadence: a tally (X times per day, done at the lower bound), a daily checkbox, or a weekly quota (X sessions per week, max one per day, week starts Monday).
_Avoid_: check-in, log entry (a log entry is a metric, not a completion)

**Milestone**:
A dated celebration moment on a fixed list. Bound Milestones fire automatically on the first Tick of something already tracked (e.g. a Phase 4 Entry Criterion); Manual Milestones (first full extension, first session at previous grade) are one-tap entries. All form a timeline. Milestones never gate anything — that is what Entry Criteria are for.
_Avoid_: achievement, badge, gate

**Morning Prompt**:
The first interaction of each day (days roll over at 4am): stiffness 0–10, pain 0–10, and — only if loading work was ticked yesterday — the settle question. Until answered, the day is unassessed: Progress is disabled, ticking is not. Metrics may be backfilled up to two days; backfill repairs data but not the streak.
_Avoid_: check-in, survey

**Override**:
A small clinic-driven edit made in the app on top of the Protocol's defaults (e.g. brace block schedule, criterion wording, phase date ranges). Structural changes are not Overrides — they go through the Protocol document.
_Avoid_: setting, customisation
