# App Logic — Core Mechanics

How Kaláka actually works, at the level a build agent can implement. Companion to the [README](../../README.md).

---

## 1. The primitive is availability, not the listing

Most marketplace schemas make the **listing** the central object. In a village food economy that is close to useless: "Berzsike bakes bread" is true every day of the year and tells you nothing. What you need to know is *baking today · 12 loaves · until 20:00 · 6 left*.

**Availability is a first-class, time-boxed, self-expiring object.** A listing is a durable template; an availability is a perishable instance of it.

```
Listing (durable)        Availability (perishable)
  what I make       →      what exists right now
  price / range            quantity, remaining
  photos, method           opens_at / closes_at
  pickup rules             auto-expires
```

Consequences that fall out of this, all of them good:

- **Search and map rank live availability above dormant listings.** A directory that shows you bread that doesn't exist is worse than no directory.
- **Stale listings decay out of discovery.** No availability signal for N weeks → the profile fades from the map and search, and the producer is nudged, not punished. *Dead listings are the single biggest killer of trust in local marketplaces.* Visibility follows activity — which is also a non-coercive reason for producers to keep posting.
- **Expiry is automatic.** Nobody has to remember to mark sold out. The 20:00 close does it.
- **Availability is the feed's native content.** One action produces the stock update *and* the post. No double entry, ever.

## 2. The transaction is a reservation, not a payment

No money moves through Kaláka in Phase 1. The primitive is:

> **Hold two loaves for me. I'll come at five.**

Producer confirms → buyer collects → **both sides tap once to confirm it happened.** That mutual confirmation is the transaction record and the reputation event. Cash changes hands at the gate, as it always has.

This is not a compromise; it is the correct primitive for this market, and it pays off three ways:

1. **Payments infrastructure leaves the critical path entirely** — no PSP, no escrow, no KYC, no chargebacks in v1.
2. **Buyer reputation becomes real.** A reservation that nobody collects is a genuine negative signal about the *buyer*. Without this, "bilateral reputation" is decoration — the buyer risks nothing and so their reputation means nothing. Reservations kept vs. abandoned is the buyer's actual track record.
3. **It matches the social reality.** Villages run on "I'll put one aside for you." The app is not inventing a behavior, it is instrumenting one.

Design notes: confirmation must be one tap for both parties, promptable by notification at the collection time. Unconfirmed reservations decay quietly rather than escalating into disputes. Never let an unconfirmed collection become a public accusation.

## 3. Requests are first-class objects

"I need X" carries equal weight to "I have X." In a thin market, requests are how latent supply gets discovered — someone who never thought of themselves as a producer sees *"anyone selling duck eggs?"* three times in a month and realizes they have a business.

Requests also give a non-producer something to do on day one, which is the first step of the supply funnel below.

## 4. Delegated accounts

From the founding image: the granddaughter lists the bread. This is a **feature**, not a workaround.

A producer profile supports a **helper** role — a family member who can post, update availability and answer messages on the producer's behalf. The profile still belongs to the named producer and the reputation accrues to them; the helper is visible in the profile, not hidden.

Without this, a meaningful share of the best producers in the target market cannot use the platform at all.

## 5. Anti-bypass — the honest version

You asked for improvement ideas here. First, a reframe that changes the whole approach:

**Kaláka takes no commission, so "bypass" costs us nothing directly.** Nobody is stealing revenue by arranging next week's bread over the fence. The real damage is different, and worth stating precisely:

- the buyer stops discovering **new** producers → the network stops compounding
- reputation events stop being recorded → the trust graph decays into a snapshot
- the producer's reach collapses back to the people who already know them

So the goal is **not to trap the transaction.** A platform that takes no fee and still forces the exchange through itself is adding friction and returning nothing — and in a village, that gets you uninstalled and gossiped about.

> **The design principle: the app must be worth opening on a day you buy nothing.**

Six mechanisms, in rough order of power:

### 5.1 Perishable information that expires (strongest)
You may know Berzsike bakes. You do **not** know whether she baked today, or whether anything is left at four in the afternoon. That information cannot be cached in a customer's head — it decays hourly. A **"Today in the village"** view — who is baking, what came in, what's left, what closes soon — is genuinely unavailable outside the app, and it is honest utility rather than a lock-in trick. This alone defeats most bypass.

### 5.2 Standing orders — let the relationship *upgrade* in-app
The moment a buyer thinks "I'll just message her directly" is the moment to offer something better than messaging:

> **Two loaves, every Friday.**

Now the app is the scheduling layer rather than the discovery layer. It is straightforwardly more convenient than a text thread: she opens Friday morning and sees *fourteen loaves committed*; she can cancel one Friday for a wedding and fourteen people are told instantly; the buyer gets a reminder. **Bypass is a downgrade.** This converts the exact moment of maximum bypass risk into the deepest form of retention.

### 5.3 Give the producer positive reasons to stay
Bypass is usually driven by the *seller*, not the buyer. Here the seller's incentives point inward, provided we build these:
- one voice post → forty followers notified, instead of forty phone calls
- "sold out" stops the phone ringing at nine at night
- accumulated reputation brings **new** customers, which the fence-conversation never does
- **access to the global channel is earned through local track record** (see [global-channel.md](global-channel.md)) — the single strongest reason a serious maker keeps their local activity on-platform

### 5.4 Record the trust even when the trade is offline
Accept that money and bread change hands at the gate, and make it trivial to log that it happened. We are not capturing payment; **we are capturing trust.** Prompt once, one tap, both sides, then get out of the way.

### 5.5 Recognition
Public contribution, not sales figures: *"Mária baked for 38 families this month."* Producers return for standing in the community — the same currency the original kaláka ran on. Related: when someone posts their **first** offering, the village feed marks it. That single event is already a north-star metric; make it a small ceremony.

### 5.6 The knowledge layer
An entire reason to open the app that has no transaction attached to it at all. See [knowledge-layer.md](knowledge-layer.md).

### Anti-patterns — explicitly forbidden
A coding agent optimizing "retention" will reach for these. Do not build them:
- hiding or gating phone numbers and contact details
- forcing chat through the app, or blocking off-platform arrangement
- friction inserted deliberately into direct dealing
- streaks, points, badges-for-logins, or any engagement gamification
- notification volume tuned for return visits rather than genuine relevance

Retention here is earned by being useful, or it is not wanted. **A community project that manipulates its community has already failed**, whatever the metrics say.

## 5.7 Daily rhythm — the habit design

The stated goal is a **daily routine app**. Kaláka has an advantage most marketplaces lack: its inventory is produced daily and perishes daily. Bread comes out of the oven at a time. Build the product around that rhythm rather than around search.

- **The app opens on today, not on a search box.** The home screen is *"Today in the village"* — who is baking, what came in, what is left, what closes soon. A marketplace grid is the wrong default for a product whose value expires by evening.
- **One morning digest. One.** *"Three things near you today: bread at 7, Anna has eggs, Saturday's workshop has two places left."* High signal or people mute it and never come back. Notification volume is a trust decision, not a growth lever.
- **An evening moment: what's left.** Surplus, end-of-day, going cheap. A second daily reason to open, and it cuts waste — which is its own argument to a funder.
- **Weekly rhythm:** market day, Friday standing orders, Sunday after church.
- **Seasonal rhythm:** plum harvest, pig season, Easter and Christmas baking. Annual recurrence, free.

Daily habit comes from *information that decays*, never from streaks or badges. The bread is genuinely different today. That is the whole mechanism.

## 6. The supply funnel: Learn → Practice → Offer

Marketplaces die of supply scarcity, not demand scarcity. Kaláka's structural answer is unusual and is the reason the knowledge layer is a pillar rather than a feature:

> **We do not only recruit producers. We manufacture them.**

```
watches "wood-oven bread" course
        ↓
prompted: who nearby sells flour, starter, firewood       ← demand created for existing producers
        ↓
bakes for the family a few times, posts a photo           ← low-stakes participation
        ↓
"you have baked five times — offer a few loaves locally?" ← the conversion moment
        ↓
first availability posted, village feed marks it          ← new supply, celebrated
```

Every stage is instrumented and every stage is a metric. This is what makes "revive their skills or learn them now" an actual mechanism instead of an aspiration.

## 7. Trust bootstrapping

In a village the strongest trust signal is not a star rating — it is **"someone I know vouches for them."**

- **Vouching**: an established member can endorse a new one; the endorsement is public, attributed, and costs the endorser something reputationally if it goes wrong.
- **Named recommendations** outrank anonymous ratings everywhere in the UI.
- Show **why** someone is trustworthy — "32 collections completed, 14 months active, recommended by István Nagy and two others" — never a bare 4.7.

## 8. Disputes are social before they are procedural

Two people who will see each other at church on Sunday should not be routed into a ticketing system. Public disputes are corrosive in a small community.

- Private resolution first, mediated by the local steward (see [cold-start.md](cold-start.md)) where needed.
- Only **aggregate** signals ever surface publicly; never a public accusation against a named neighbor.
- Reserve formal moderation for safety, fraud and abuse — not for disagreements about bread.

## 9. Operating realities to design for from day one

- **Patchy rural connectivity.** Offline-tolerant reads, queued writes, no spinner-on-a-white-screen failure modes.
- **Old and cheap phones.** Large type, few taps, high contrast, minimal animation, small install size.
- **Low app-literacy.** Voice as an equal path to every core action, not an advanced feature.
- **Seasonality.** The rural calendar is intensely cyclical — plum harvest, pig season, Easter and Christmas baking, hay, mushrooms. Seasonal prompts and content create annual recurring engagement for free.
- **Home-produced food is regulated.** Kaláka does not certify anything. Label clearly as home-produced, and check the applicable Romanian regime for direct small-scale sales (see [funding-and-governance.md](funding-and-governance.md)).
