# Onboarding & Motivation

First-run copy, and the psychology the product is allowed to use.

---

## The reframe: the screen is not the funnel

Standard onboarding optimisation assumes a stranger alone with a signup form. **That is not how Kaláka's most important users arrive.** A 74-year-old baker is onboarded at her kitchen table by a steward who is holding the phone ([cold-start.md](cold-start.md)).

So conversion is not won by a better CTA. It is won by:

1. **Removing everything that can be removed from registration** (below), and
2. **Answering the six fears** that actually stop an elder producer from saying yes.

The copy's job is to make the *steward's* explanation easy and to make the producer feel safe. Two different onboarding paths, designed separately:

| Path | Who | Where | Target |
|---|---|---|---|
| **Assisted** | Producer, 60–80 | Kitchen table, steward-led | Profile + first listing in one sitting |
| **Self-serve** | Buyer, any age | Saw a poster at the market | Real bread visible in under 60 seconds |

## Registration: the decisions that beat any copy

- **No password. Ever.** Phone number, SMS code, done. A password is a permanent, recurring failure point for this demographic — it is the single most common reason an elderly user is locked out of an app forever.
- **No email.** Optional, later, never required.
- **Buyers browse before registering.** Nobody signs up to look at bread they haven't seen. Registration is required to *reserve*, not to look.
- **No username.** Real name, as the village knows it — "Berzsike" is a valid name here.
- **Nothing that can be deferred is asked at signup.** Photo, radius, categories, and price can all come later or from the steward.

---

## UX Copy: the six trust moments

These are where onboarding actually fails. Each needs an answer, not a reassurance.

### 1. Location permission — the highest-risk screen in the app

The unspoken fear is *"will people know where I live?"* Get this wrong and she hands the phone back.

**Recommended**
> **Nobody sees your address.**
> Neighbours see only how far away you are — "800 m". Never your house, never your address.
> **[ Show my distance ]** **[ Not now ]**

| | Copy | Tone | Best for |
|---|---|---|---|
| A | "Nobody sees your address. Neighbours see only how far away you are." | Direct, addresses the fear first | **Recommended** — leads with the answer, not the request |
| B | "Kaláka uses your location to show you what's nearby." | Standard, system-style | Buyers, self-serve — lower stakes |
| C | "Allow location access to continue." | Bare permission prompt | Never. Asks without answering. |

**Rationale:** the fear precedes the question, so the copy must too. "Not now" must be genuinely available — a producer can be added to the map by the steward and set distance later. A dead end here loses the user permanently.

### 2. Phone number
> **Your phone number.**
> We send a code, so there's no password to remember. Your number stays hidden until you choose to share it with a buyer.

**Rationale:** names the benefit of the SMS code ("no password to remember") rather than the mechanism, and pre-empts the spam fear in the same breath.

### 3. Price — the paralysis nobody plans for

Village producers frequently have no price. They have *"whatever you think is fair."* A required numeric field stops them dead.

> **What do you ask for it?**
> A price, a range, or just "as agreed" — whatever you actually say at the gate. You can change it any time.

Offer three input modes: fixed · range · **as agreed**. The third is not a fallback; for many producers it is the honest answer.

### 4. Photo
> **A photo helps, but it can wait.**
> Ask your grandchild, or the steward can take one next visit.

Never block a listing on a photo. A listing without one still sells bread.

### 5. "What if nobody comes?"
> **34 neighbours can already see you.** Most producers get their first message in the first week.

Only ever state the real number. If it is four, say four.

### 6. "What if I can't deliver?"
> **You decide what's available, and when.** If you're not baking, post nothing — you're never promising anything you haven't offered.

This is the fear of being *obligated*. The answer is the availability primitive itself ([app-logic.md](app-logic.md)): nothing exists unless she says it does today.

---

## The first-week arc

Onboarding does not end at signup. These are the psychological milestones, in order, and each needs a moment in the product:

| When | Event | Copy |
|---|---|---|
| Day 0 | Sees herself on the map | "Berzsike's bread is on the map. 34 neighbours can see it." |
| Day 1–3 | **First follower** | "Ilona is following you. She'll see when you bake." |
| Day 3–7 | **First reservation** | "Ilona reserved 2 loaves for today. She's coming at 17:00." |
| Week 2 | First confirmation and thank-you | "Ilona collected her bread and said thank you." |
| Week 4 | First recognition | "You baked for 12 families this month." |

**The first follower matters more than the first sale.** It arrives before any transaction and proves someone is watching — which is what carries a producer through the empty first days. Make sure it can happen on day one, and that it is a notification worth opening.

---

## The motivation model

You asked for psychological strength. In a village, the strongest motives are already present and none of them are engagement tricks:

1. **Being needed.** *"Someone 400 m away is looking for bread."* For a retired person, being useful again is a stronger motivator than money — this is likely the most powerful single lever in the entire product for the elder demographic. Requests ([app-logic.md](app-logic.md)) are how it gets delivered.
2. **Standing.** The original kaláka currency. Public *contribution* — "baked for 38 families" — never sales figures, never a ranking.
3. **Reciprocity.** Someone helped you; you help back. The tradition does the work.
4. **Being counted.** "One of 34 producers in this village."
5. **Curiosity about neighbours.** The feed. Entirely legitimate and very strong.
6. **Pride in craft.** Showing the work, and teaching it ([knowledge-layer.md](knowledge-layer.md)).
7. **Honest scarcity.** The bread genuinely runs out. Real urgency needs no manufacturing — and *because* it is real, it never erodes trust.

### Forbidden, even though they would work

Named explicitly, because any agent told to raise engagement will reach for them, and each one would measurably improve short-term numbers while destroying the premise:

- streaks, points, badges, levels
- variable or intermittent rewards
- artificial scarcity or countdown timers on things that aren't actually scarce
- leaderboards and social comparison between neighbours — **actively corrosive in a village**, where these people meet on Sunday
- guilt or FOMO notifications ("your neighbours miss you")
- notification volume tuned for return visits

The test: **would you be comfortable if the steward explained the mechanism out loud to the producer?** Honest scarcity passes. A streak counter does not.

---

## Localization notes

Hungarian is primary; Romanian equal in status; English structural.

**Address elders formally.** Hungarian distinguishes formal (*magázás*) from informal (*tegezés*), and most apps default to informal. For Szekler elders that reads as disrespectful. Default to formal for producers, and have a native Szekler speaker rule on whether the warmer *tetszikelés* register fits better in village context — this is a real decision, not a translation detail.

**Sample strings — draft, require native review.** Regional Szekler usage differs from Budapest Hungarian.

| EN | HU (draft) |
|---|---|
| Nobody sees your address. | A címét senki nem látja. |
| Neighbours see only how far away you are — "800 m". | A szomszédok csak azt látják, milyen messze van — „800 méter". |
| Your phone number. We'll send a code — no password to remember. | A telefonszáma. Küldünk egy kódot — nem kell jelszót megjegyeznie. |
| Not sure of a price? Write "as agreed". | Nem biztos az árban? Írja azt: „megegyezés szerint". |
| Berzsike's bread is on the map. 34 neighbours can see it. | Berzsike kenyere felkerült a térképre. 34 szomszéd látja. |
| Ilona is following you. She'll see when you bake. | Ilona követi Önt. Látni fogja, amikor süt. |
| Someone 400 m away is looking for bread. | Valaki 400 méterre kenyeret keres. |
| You baked for 12 families this month. | Ebben a hónapban 12 családnak sütött. |

Also: Hungarian runs ~10–20% longer than English — size buttons and notification lines for it. Avoid idioms entirely; these strings get read aloud by a steward.

## Accessibility is conversion here

For this demographic the two are the same problem — a control that can't be read or hit is a failed signup. Large type by default (not buried in settings), high contrast, generous touch targets, no timed interactions, no gesture-only actions, and voice as an equal path to every core action. Worth a formal WCAG 2.1 AA pass on the first-run flow specifically, before launch.
