# Funding & Governance

Kaláka is a **community project, not a startup.** Profit is not the day-one goal; being genuinely useful is. That is a design constraint with teeth, not a slogan — it changes what gets built and what must never be built.

---

## The money model

Kaláka is subsidised, not sold. Four revenue lines, none of which touches ordinary participation:

| Line | What it is | When |
|---|---|---|
| **Grants & sponsorship** | EU rural development, county and commune budgets, local business sponsors | Phase 1, ongoing |
| **Merchant Pro** | Optional tools for serious merchants — ~29 RON/month (≈ €6), or per-event for occasional organisers | Phase 1 |
| **Payments** | Flat fee + card processing, **only inside Kaláka Delivery** | With Delivery |
| **Global channel** | Commission on international sales of durable goods | Phase 2 |
| **Adjacent business** | Kaláka as the top layer feeding a separate commercial operation | Ongoing — see governance below |

### The promise, drawn precisely

The earlier wording ("no subscriptions") is too broad and would forbid Merchant Pro. The line that actually matters is not free-vs-paid, it is **participation vs. tools**:

> **Participation is free forever.** Listing, selling, buying, being discovered, messaging, building reputation, and the entire knowledge layer are free for every person, permanently.
>
> **Paid tiers buy tools, never reach.** A merchant may pay to save themselves time. Nobody may pay to be seen more.

Two hard rules that make this credible:

- **A paying merchant never outranks a non-paying one.** Discovery is proximity, relevance, availability, reputation. Never money.
- **The free tier is never crippled to sell an upgrade.** No listing caps, no photo limits, no hiding contact details, no "Pro" badge that reads as trustworthiness. If a free producer feels handicapped, the promise is broken regardless of what the pricing page says.

### What Merchant Pro may contain

Legitimate — saves the merchant time or extends *their own* capability:

- **standing orders** — the Friday bread list, recurring schedules, one-tap cancellation to all subscribers
- bulk availability scheduling ("every Tuesday and Friday, 20 loaves")
- their own customer list and repeat-buyer history
- reservation management above casual volume
- receipts, and a bookkeeping export that a PFA actually needs
- a higher assistant/AI quota and advanced voice actions (this is also the honest way to cover AI cost — see [app-logic.md](app-logic.md))
- workshop and event ticketing at volume
- multiple helper accounts
- Phase 2: export listing tools, English drafting, photography scheduling

Never sellable, at any price: ranking · placement · map presence · contactability · reputation display · trust-implying badges · listing count · photos on a basic listing.

### Pricing shape

29 RON/month is trivial for a working producer — a baker selling 20 loaves a day turns that over before breakfast — and irrelevant to someone with a dozen spare eggs, who must never need it. **Self-selecting, which is correct.**

Offer a **per-event** option alongside the monthly one. Somebody running four workshops a year should not be pushed onto a subscription, and **never charge both** for the same activity. The clean rule: *we take a share only when the merchant takes money.* Free workshops stay free, permanently.

Collection via Revolut is plausible for Romania — verify what Revolut Business supports for **recurring** collection under your chosen legal entity, and have a fallback for merchants who don't use it.

## Payments — and a correction

Deferring payments until Kaláka Delivery exists is the right call, and it is consistent with Phase 1's reservation model: cash at the gate, no PSP on the critical path.

**But do not become a payment processor.** Handling other people's money in the EU means PSD2 authorisation as a payment institution — capital requirements, safeguarding, compliance staff, an ongoing regulatory relationship. It would cost more than the entire rest of the project and is not a thing a community association should attempt.

**Be a platform on top of a licensed PSP instead** — a marketplace/split-payment arrangement (Stripe Connect or a Romanian acquirer), where the licensed party holds and moves funds and Kaláka never touches them. Same product, none of the licensing. Confirm with a Romanian payments lawyer before building anything; the PSD2 commercial-agent exclusion is narrower than it looks, and holding funds even briefly can trigger authorisation.

### The fee math

0.9 RON flat plus card processing is sound **for delivery orders** and wrong for village pickup:

| Order | 0.9 RON as % |
|---|---|
| 15 RON — two loaves | **6.0%** |
| 20 RON — dozen eggs | 4.5% |
| 50 RON — honey | 1.8% |
| 80 RON — delivery basket | **1.1%** |

A flat fee is regressive: it is a rounding error on a delivery basket and a tax on a loaf of bread. Since you have scoped payments to Delivery only, this is fine as designed — **the rule to protect is that online payment never leaks back into pickup.** Cash at the gate stays, permanently, and paying online must never become a condition of reserving anything.

## Funding sources to pursue

Verify current programmes and eligibility — all of this needs local confirmation.

- **EU rural development** — LEADER via the local *Grup de Acțiune Locală*, administered in Romania through AFIR. A digital platform reviving rural micro-production and transferring traditional craft knowledge is close to a textbook fit.
- **County and commune budgets** — Hargita/Kovászna county councils; individual *primării* for their own village's rollout.
- **Hungarian cross-border cultural funding** — e.g. Bethlen Gábor Alap, for the knowledge-archive and cultural-heritage dimension.
- **Local business sponsorship** — the mill, the agricultural supplier, the local bank branch, the building merchant.
- **Cultural heritage funding** for the knowledge archive specifically, which is the most independently fundable component of the entire project.

**Fund components, not "an app."** The knowledge archive, the elder-interview programme, the workshop series and the export-photography service are all separately fundable and individually compelling. "A marketplace app" is not.

## Sponsor governance — the invariant that protects the product

A sponsor will eventually ask for preferential treatment. The answer is decided now, in writing, before anyone has taken money:

> **Ranking is never for sale.** Discovery order is proximity, relevance, availability and reputation. Money never enters it. Ever.

- Sponsors receive **named credit** — a supporters page, event branding, genuine public thanks. They do not receive placement, ranking, badges that imply endorsement, or access to user data.
- **No advertising in the feed.** The feed is neighbors; the moment it carries paid content it stops being that.
- A sponsor's own business gets a profile on exactly the same terms as everyone else, and no better.
- **This is a condition of sponsorship, stated up front.** A funder who won't accept it is the wrong funder — take less money instead, because the alternative destroys the thing they are paying for.

## Governance

### Kaláka as a pre-layer for an adjacent business

Using Kaláka as the top layer feeding another commercial operation is a legitimate and common structure — and it is the one thing here that must be handled cleanly, because it collides with how the project is being funded.

The risk is specific, not moral: you plan to raise from **municipalities and public rural-development programmes** on a community-project framing, while a private business benefits from the resulting network. Discovered late by a funder, that ends the funding and the local goodwill together. Discovered by the village, it ends the trust the whole product runs on.

The fix is structural, and cheap if done now:

- **Separate the entities.** The association (or equivalent) owns Kaláka, the community relationship and the data. The commercial operation is a distinct company that **pays the association** at arm's length for whatever it gets. Public money lands in the non-profit; the private business never receives a grant-funded benefit for free.
- **Check state-aid rules early.** EU and Romanian public funding has real constraints on private undertakings benefiting from grants. This is a question for a Romanian grants lawyer *before* the first application, not after.
- **Disclose it plainly and early** — to funders, to the commune, on the supporters page. A community project with a transparent commercial sibling is entirely normal. A community project with an undisclosed one is a scandal waiting for a slow news week.
- **The invariants still bind.** The adjacent business gets no ranking preference, no user data, and no feed access that a sponsor wouldn't get. Same rules as everyone else.

**Open:** the adjacent business has not been described here. Its nature decides how tight the separation must be — an obvious complement (logistics, milling, tourism, an existing local platform) is straightforward; anything competing with Kaláka's own producers is not.

- **Legal vehicle:** most likely a Romanian *asociație* (non-profit, OG 26/2000) or a social enterprise — required for most grant eligibility anyway. Needs a Romanian lawyer; do not guess.
- **Community representation.** Producers and the participating communes should have a real voice in direction. Not a token advisory board.
- **Financial transparency.** Publish where the money came from and where it went. For a project trading on trust, opacity about money is fatal.
- **Data is not an asset to be sold.** Ever, under any funding pressure. Write it into the founding documents so a future board cannot quietly reverse it.
- **Exit and continuity.** What happens if the grant ends or the founders leave? Open data formats, exportable profiles, no lock-in. A community project that can strand its community was never a community project.

## Legal and regulatory checklist

Unaddressed in the source session, all needing local professional advice:

- **Home food production.** Direct small-scale sale in Romania — the *certificat de producător* regime and any ANSVSA registration. Kaláka certifies nothing and labels everything clearly as home-produced; but the platform should know the rules it is operating alongside.
- **Informal work and tax.** Casual services (roof repair, gardening) arranged via a platform. Where the platform's responsibility begins and ends.
- **GDPR.** Location data, voice recordings, and elder interviews with identifiable people. A DPIA is warranted given the geolocation and voice processing.
- **Minors** in a village app.
- **Platform liability** for goods, services and food sold between users.
- **Alcohol** — pálinka is culturally central and legally awkward. Decide explicitly, in both channels.
