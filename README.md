# Kaláka

A hyperlocal social-economic network for Szeklerland / Transylvania: **make local productive capability visible again.**
Marketplace + social feed + knowledge archive + bilateral reputation + voice assistant, as one network.

**A community project, not a startup.** Funded by grants, municipalities and local sponsors. **Participation is free forever** — the commercial layers sit on top and pay for it.

> *"Everything a community needs is already within it."*

---

## The founding image

An elder, ~70, bakes bread in a wood-fired outdoor oven. Her granddaughter helps her list the loaves on the app. Orders arrive; neighbors walk over and collect them warm. No warehouse, no delivery van, no platform standing in the middle taking a cut of the relationship.

Then widen the lens: the beekeeper, the shepherd, the carpenter, the gardener — **all visible again.**

That image is the product. Every feature decision should be checkable against it.

## The name is the thesis

*Kaláka* (Hungarian; Romanian **clacă**) is the living Szekler tradition of reciprocal communal work — neighbors show up to raise your roof or bring in your harvest, nobody is paid, and you are repaid in kind and in standing. Mutual help, no money required.

| Kaláka the tradition | Kaláka the app |
|---|---|
| You know who can lay a roof | Discovery / marketplace |
| You know what's happening this week | Social feed |
| Repaid in kind, and remembered | Bilateral reputation |
| "Go to Berzsike, she bakes" | Recommendations / social graph |
| Showing up is easy and normal | Voice assistant removes friction |

If a feature doesn't serve **visibility, reciprocity or trust** between people who live near each other, it isn't Kaláka.

---

## Status of this document

Synthesized from one long ChatGPT working session ([shared chat](https://chatgpt.com/share/6a84bfb2-3848-83eb-aa40-c512dcb2af2e), 132 nodes). **The session is ore to mine, not the source of truth.**

Note on the source: the session's own final "Blueprint" and "Frontier Build Brief" are a *lossy compression* of the voice conversation that precedes them. The reasoning, the market evidence, the emotional core and the sharpest strategic argument all live in the conversation, not the summaries. This README restores them.

Tags: **[SETTLED]** · **[DEFAULT]** (starting assumption, overturnable by ADR) · **[OPEN]** (genuinely undecided).

---

## The market gap

**Romania:** OLX.ro, Facebook Marketplace, Vinted. **Hungary:** Jófogás, Facebook Marketplace, Vinted, HardverApró (long-standing, dated UI).

These are **classifieds, not neighborhood ecosystems.** Neither country has a polished hyperlocal all-in-one. Globally the category is fragmented into five models — neighborhood social network (Nextdoor), neighborhood classifieds (Karrot, Wallapop), free circular economy (Buy Nothing, OLIO), local services (TaskRabbit), local barter (Lokkna, Trocalia). Nobody has combined them.

Kaláka is aiming at a sixth category:

> **A hyperlocal economic operating system.** You register once, establish an approximate home zone, and the system continuously answers *"what economic activity is happening around me?"* — not merely *"what is for sale?"*

Sell · offer service · request · barter · give · borrow · buy · local business · skill · micro-job · group buy · community project.

---

## The core insight: a directory self-destructs on success

The sharpest argument in the session, and the reason the feed is not optional:

> I use Kaláka three times to buy eggs 2 km away. By then I know the woman who sells them. **So I stop opening the app** — I just walk over. If Kaláka is only a listing directory, every successful match removes a user.

**A pure directory is punished for working.** The feed is the structural fix: I keep opening Kaláka because I want to see what the egg lady posted, what the baker's first batch looked like, what neighbors are saying about her.

Two consequences, both settled:

1. **The feed is a retention mechanism, not a nice-to-have.** It was argued for over explicit, repeated pushback and is not up for re-litigation by any agent.
2. **The feed is the review system.** A stream of real activity — "bought honey from Anna, great quality", "looking for a roofer, any recs?" — is richer, more contextual and **harder to fake** than a star average. That is why reputation must never collapse to five stars.

---

## The three pillars

**1 · Marketplace — "what exists."** Structured, searchable, stable: profile, goods, services, price or range, inventory, approximate location, pickup radius, photos, verification, reputation.

**2 · Feed — "what is happening."** The living layer: today's availability, finished work, harvests, recommendations, requests, questions, local events, thank-yous, merchant-to-merchant tagging. **Every post is actionable** — reserve today's bread, ask a question, recommend a producer, join the workshop.

**3 · Knowledge — "how it is done."** Generational transfer: how to bake real bread in a wood oven with potatoes, captured from the people who still know. Method records, elder interviews, and bookable in-person workshops. → [knowledge-layer.md](docs/product/knowledge-layer.md)

The marketplace is the database. The feed is the heartbeat. **The knowledge layer is where new producers come from** — and it is the part with a deadline, because the people who hold this knowledge are in their seventies.

### Two mechanics that carry the product

**Availability, not listings, is the core primitive.** "Berzsike bakes bread" is true every day and tells you nothing. *Baking today · 12 loaves · until 20:00 · 6 left* is the useful object — time-boxed, self-expiring, and impossible to cache in a customer's head. Dormant listings decay out of discovery; visibility follows activity.

**The transaction is a reservation, not a payment.** *Hold two loaves, I'll come at five.* Cash changes hands at the gate. This keeps payments infrastructure off the critical path entirely, and it makes buyer reputation real — a reservation nobody collects is a genuine signal about the buyer.

→ Full mechanics: [app-logic.md](docs/product/app-logic.md)

## Product invariants [SETTLED]

1. **People, not stores.** Micro-businesses and individuals only; a profile is overseen by a named person who carries their own reputation. Not a channel for shops, chains or mass resellers.
2. **Map first, trust forward.**
3. **Local density before geographic coverage.** One town proven deeply beats a national launch. 500 genuinely active users in one village > 50,000 scattered signups.
4. **Reputation is bilateral** — customer *and* producer — and derived from behavior: verified identity, completed transactions, reviews, recommendations, consistency, account history, disputes. **Never a single star score.** The feed and social graph are part of the trust signal.
5. **Exact home coordinates are never stored as public data or exposed.** Internally geospatial; in the UI, distance bands only — "~150 m · ~800 m · ~2.1 km · nearby".
6. **Voice is a first-class interface**, especially for producers who won't tolerate a complicated app.
7. **The AI acts only through typed, authorized, validated application commands.**
   `voice → ASR → agent → validated command → application API → database` — never `voice → LLM → open database access`.
8. **Hungarian, Romanian and English from day one**, structured for more later.
9. **Don't chase engagement for its own sake.** Social features stay tied to trust or local commerce.
10. Future modules (Market · Services · Knowledge · Delivery) remain **one app, one account, one shared reputation** — never separate products.
11. **Participation is free forever.** Listing, selling, buying, being discovered, messaging, reputation and the whole knowledge layer are free for everyone, permanently. Optional Merchant Pro sells **tools, never reach** — a merchant may pay to save time; nobody may pay to be seen more.
12. **Ranking is never for sale.** Discovery order is proximity, relevance, availability and reputation. A paying merchant never outranks a free one, the free tier is never crippled to sell an upgrade, sponsors get named credit rather than placement, and there is no advertising in the feed.
13. **Producer profiles support a helper role** — the granddaughter lists the bread. Without delegation, the best producers in this market cannot use the platform at all.
14. **No dark patterns.** No hidden contact details, no forced in-app chat, no engagement gamification, no friction inserted to prevent direct dealing. Retention is earned by being useful or it is not wanted.

---

## The assistant

Branded **Kaláka**, never "ChatGPT". Target interaction, spoken by a producer with flour on their hands:

> "Kaláka, I baked 20 breads. Add them to today's stock, available until eight, and post that fresh bread awaits at Berzsike's."

→ inventory update + listing availability + feed post + follower notification + optional translation, with **one** confirmation.

Camera is part of it: point at the basket, say *"these just came out of the oven"* — the assistant recognizes the item, drafts the post, updates inventory, asks once.

Customer side: *"Find fresh eggs within three kilometres."* · *"Order two loaves from the baker I bought from last week."*

**The assistant's second job is scribe.** An elder who bakes extraordinary bread will never write a tutorial — but they will answer questions. The assistant interviews them, transcribes, and asks the follow-ups they would never think to volunteer (*how do you know the oven is ready?* → "when you can hold your hand in for as long as a Miatyánk"). That tacit layer is what a written recipe loses and what makes the knowledge archive worth having.

**Cost model [DEFAULT] — do not route every action through an LLM.** Fixed voice commands for common actions, plain speech-to-text for input, and an LLM call only where it earns it (drafting a post, translating a listing). Note the session's own finding: **media is the bigger cost driver than tokens** — optimize uploads, keep video short. Video hosting is explicitly third-party; we do not run video infrastructure.

---

## MVP: one vertical slice, end to end

> Producer creates a profile → lists bread → a customer 3 km away discovers it → follows the producer → producer posts "fresh bread available" → customer sees it → contacts them → transaction recorded → **both sides** receive a reputation event.

Then the same slice through voice. **If that slice feels magical, Kaláka has a product.**

Surface: identity (phone/email, optional verification, approximate location) · profiles with **helper delegation** · listings + **availability** + requests, with search and map · **reservations with two-sided confirmation** · feed with photos, short video, comments, reactions, follows, recommendations · buyer↔producer messaging · reviews, reporting, moderation · voice for create-listing, update-availability, post, search · **knowledge: method records, elder interviews, bookable workshops — one flagship subject (wood-oven bread) done properly.**

**Not in v1:** delivery logistics, payments infrastructure, livestreaming, dozens of categories, barter/lending/group-buying/subscriptions/analytics, and the global channel.

### Phase map

| Phase | Goal | Key move |
|---|---|---|
| **1** | Density in one commune, then its neighbours | Hand-recruited producers, seeded feed, human onboarding, knowledge capture → [cold-start.md](docs/product/cold-start.md) |
| **2** | Global reach for durable goods | Etsy-like export channel, gated on local track record → [global-channel.md](docs/product/global-channel.md) |
| **2** | Kaláka Delivery | The only place online payment ever appears — flat fee + processing, on a licensed PSP, never on village pickup |
| **Later** | Barter, lending, group buying | Extensions of the same network, never separate apps |

**Expansion is by archetype, not by map** — communities that *look like* Szeklerland, not places next to it. Hungarian-minority regions and South Tyrol before Germany, which is already well served by Direktvermarktung and farm-shop culture. → [expansion.md](docs/product/expansion.md)

**Phase 2 in one line:** perishable stays local, durable can travel. Local provenance is an authenticity proof Etsy structurally cannot produce — and the commission on international sales is what funds the free local layer.

---

## North star

Not listings, page views, downloads or time spent. **Productive local interactions per active community:** transactions completed, services exchanged, producers discovered, repeat relationships, recommendations given, people offering something *for the first time*, requests actually fulfilled, money that stays local.

> "How much useful activity happened between people who live near each other?"

Measured **per community, never in aggregate** — aggregate numbers hide five dead villages behind one live one. The number that actually tells you whether this works: **share of producers still active after six months.**

Surface **contribution, not sales** — *"Maria baked bread for 38 local families this month."* Transactions become stories of community value.

A caution kept from the session, worth keeping: Kaláka doesn't create skills, it **surfaces** them; it doesn't create community, it **reveals and activates** it. The hope that people revive abandoned trades because they can see a neighbor succeeding is a real and motivating hypothesis — treat it as a hypothesis to test, not a claim to market.

---

## Technical starting position [DEFAULT — build agents own the final call]

The source contradicts itself here: the Blueprint prescribes a stack, the Frontier Brief tells the agents to own architecture and not follow it blindly. **Informed priors, not decisions.** Prefer boring, proven technology. Don't overengineer for hypothetical scale; don't underengineer security, privacy, identity, payments, moderation or geolocation.

- **Mobile:** native — Swift/SwiftUI, Kotlin/Compose. Justified by location, camera, mic, notifications, background work, maps, media, accessibility. *See open question 5.*
- **Backend:** typed service API · PostgreSQL + **PostGIS** · Redis · S3-compatible storage · Postgres FTS until it genuinely breaks · WebSockets/managed realtime · durable job queue · structured logs, metrics, tracing.
- **Repo shape** (boundaries matter more than what fills them):

```
kalaka/
  apps/{ios,android}
  services/{api,worker,assistant}
  packages/{domain,api-contracts,design-system,localization}
  infrastructure/{terraform,environments}
  docs/{architecture,adr,product,security}
  tests/{integration,e2e,load,security}
```

---

## Competitive research queue [UNVERIFIED]

Named in the session with figures that came from search results and **must be independently verified before use in any analysis, pitch or investor material** — the session itself flagged at least one set of numbers as doubtful.

**Benchmarks at scale:** Nextdoor (community model) · Karrot (best pure neighborhood marketplace) · Wallapop (mature marketplace tech) · Buy Nothing (gifting network; exact address kept private — study their location-privacy model) · OLIO · TaskRabbit (services benchmark).

**Closest in concept, worth a teardown:** Vecinos · Jinu · Homis (group deals → coordinated local economic activity) · Coop – Local Goods (local producers, barter, follow sellers, Stripe checkout) · Lokkna (barter+buy+sell+give+services) · Trocalia · Good Neibors and Neighborly Verified (location verification and trust-first) · Chorely · lunchbox ("what can you do / what do you need", money removed from the center).

Top of queue: **Karrot, Nextdoor, Coop, Buy Nothing.**

---

## Open questions [OPEN]

1. **Which village is first?** The playbook exists ([cold-start.md](docs/product/cold-start.md)) but the commune is unnamed, and nothing else can be scheduled until it is. Still the biggest risk in the project.
2. **Reputation farming.** Reservations are confirmed by both parties with no money moving, so two colluding accounts can manufacture a track record — and Phase 2 global access is gated on exactly that record. Needs a real answer before the gate goes live.
3. **Funding secured?** The model is decided (grants and sponsorship now, global commission later) but nothing is committed. Grant timelines are long; start before the code does.
4. **Identity strength.** Phone only, or real verification? In a village a fake account is socially expensive, but a real one can still defraud.
5. **Native iOS + Android from day one doubles the cost of proving density.** Real tension with "prove the loop first." Deserves an explicit ADR, not an inherited assumption.
6. **Voice in v1.** The differentiator *and* the hardest part; Hungarian and Romanian ASR is not English ASR. Consider shipping the slice without it while designing the typed command layer so voice is purely additive.
7. **Two languages, one feed.** Does a Hungarian post reach a Romanian-speaking neighbor 400 m away? The session proposes assistant translation; whether that is sufficient — and how it feels — is a live product and cultural question in Transylvania, not a localization detail.
8. **Legal reality in Romania.** Home-produced food (raw milk, eggs, meat), informal labor, PFA/ANAF status, GDPR. A platform listing these carries exposure. Entirely unaddressed in the source.
9. **Moderation at village scale.** Two languages, a tiny team, disputes between people who see each other on Sunday. Social resolution matters more than a report button.

---

## Design documents

| Doc | Covers |
|---|---|
| [app-logic.md](docs/product/app-logic.md) | Availability primitive, reservations, requests, delegated accounts, **anti-bypass mechanics**, the Learn→Practice→Offer supply funnel, trust bootstrapping, disputes |
| [cold-start.md](docs/product/cold-start.md) | The density playbook: steward model, recruit-supply-first, anchor institutions, the expansion gate |
| [knowledge-layer.md](docs/product/knowledge-layer.md) | Generational transfer, elder capture, workshops, lineage, consent |
| [global-channel.md](docs/product/global-channel.md) | Phase 2 export marketplace, shipping classes, reputation portability, shared dispatch |
| [expansion.md](docs/product/expansion.md) | The archetype filter, candidate communities, multi-tenancy, why Germany is later and harder |
| [funding-and-governance.md](docs/product/funding-and-governance.md) | The four revenue lines, Merchant Pro boundaries, payments and the PSD2 correction, the adjacent-business separation, legal checklist |

## How the build should run

A coordinated engineering organization, not one autonomous coder. Specialized agents (architecture, backend, iOS, Android, design, AI/voice, geospatial, security, QA, DevOps, adversarial reviewer) coordinating through **specs, ADRs, API contracts and tests — not informal conversation.**

Every substantial change: `spec → implementation → automated tests → security review → architectural review → CI → human approval → deploy`.

Reversible technical decisions: agents decide autonomously. Irreversible or high-impact: written architectural justification. **No agent gets production credentials or touches production data.** Never trade architectural integrity for a green build.

Before substantial production code: product architecture · domain model · system architecture · ADR set · MVP scope · roadmap · repo structure · CI/CD · security & privacy model · agent workflow rules. Then start at the smallest complete vertical slice.

---

## Brand

**Kaláka** — umbrella name; modules become Kaláka Market, Kaláka Services, later Kaláka Delivery. The session's name moment gestures at a `.ro` domain (voice transcript garbled: *"Ro kalaka dot"*) — **confirm domain availability.**

Taglines: *"Everything a community needs is already within it."* · *"Support your neighbors, strengthen your community."*

Logo direction: a distinctive modern mark combining a subtle **K** with hands / connection / community, drawing on Szekler-Transylvanian craft without looking folkloric or dated. Clean geometry, warm human character, legible at app-icon size, premium European tech feel, works in monochrome.

---

**Kaláka = marketplace + social network + reputation graph + local discovery + AI assistant + community infrastructure.**
The marketplace tells you what exists. The feed shows you what's happening. The reputation graph tells you whom to trust. The assistant makes participation effortless. The local network makes it economically self-reinforcing.
