# Expansion — By Archetype, Not By Map

The instinct to jump from Szeklerland to Germanic communities in Germany is strategically right, and it replaces the earlier plan (village → county → Transylvania → Romania/Hungary → Europe) with something better.

> **Expand to communities that look like Szeklerland, not to places next to Szeklerland.**

Geographic contiguity is the wrong axis. A Hungarian village 40 km away and a South Tyrolean village 1,200 km away can be the same market; a Bucharest suburb 300 km away is a different product entirely.

---

## The archetype filter

A candidate community needs most of these. Score honestly before committing a steward.

1. **Coherent identity with internal trust** — usually a linguistic or cultural minority, or a tight traditional region. People already believe "we look after our own."
2. **Surviving production** — bread, dairy, honey, meat, wool, wood, craft. **There must already be supply.** Kaláka reveals production; it cannot conjure it.
3. **Village-scale density** — walkable or a short drive. Hyperlocal fails at metropolitan scale and at true dispersion.
4. **Underserved by existing platforms** — the Szeklerland condition: only OLX, Jófogás and Facebook. *This is the criterion most likely to disqualify a wealthy candidate.*
5. **An anchor institution that can host a steward** — commune, church, cultural association, cooperative.
6. **Bonus: a diaspora or premium export market** — makes Phase 2 immediate rather than theoretical.

## Candidates, roughly ordered

**Tier 1 — same culture, adjacent, underserved.** Székely communes beyond the first (home ground) · Csángó communities · Hungarian communities in Felvidék (Slovakia) and Vojvodina (Serbia). Same language, same product, near-zero adaptation cost. This is where community #2 through #10 should come from.

**Tier 2 — best archetype match outside the Hungarian world.** **South Tyrol / Alto Adige** is the strongest single candidate anywhere: German-speaking minority in Italy, fiercely intact identity, an intense small-producer food economy, and wealthy nearby buyers. If the model transfers there, it transfers anywhere. Also: Sorbs in Lusatia, Frisians, Alpine Austria and Bavaria, Basque and Breton communities, Galicia and Asturias.

**Tier 3 — Romania's own German communities.** Siebenbürger Sachsen and Banat Swabians: culturally ideal, but the populations largely emigrated after 1990. Verify who is actually still there before planning around it.

## A caution on Germany

Germany is not an empty market the way Szeklerland is. *Direktvermarktung*, farm shops, *Hofläden*, SoLaWi/CSA box schemes and several regional platforms already occupy this space, and rural Germany is comparatively well served.

That fails criterion 4 — the very condition that makes Kaláka obvious at home. Germany is a **later and harder** market, entered with a differentiated product (the knowledge layer and the export channel are the plausible wedges), not the easy second step it appears to be. **Take South Tyrol or Felvidék first.**

## What actually replicates

**Not the code — the playbook.** A new community needs a steward, an anchor institution, 15–25 hand-recruited producers and a seeded feed ([cold-start.md](cold-start.md)). Software is the cheap part; the steward is the unit of expansion. Budget and hire accordingly.

## Architectural consequence — decide now

Each community is a **dense, largely self-contained network.** A baker in Csíkszereda and a weaver in South Tyrol have no reason to appear in each other's feed.

So the product is **multi-tenant by community from day one**:

- feed, discovery, moderation and language defaults scoped per community
- each with its own steward, its own onboarding state, its own launch date
- communities connect through exactly two channels: the **global export marketplace** ([global-channel.md](global-channel.md)) and, optionally, a **shared knowledge archive** — a Szekler bread method is worth reading in Tyrol
- per-community metrics, never aggregate ([cold-start.md](cold-start.md))

Retrofitting multi-tenancy onto a single global feed is expensive and touches everything. Build it in now, while it costs almost nothing.

## Localization is not translation

Each archetype brings its own categories, seasons and vocabulary. Szekler pig season is not a Tyrolean harvest calendar. Content taxonomy, seasonal prompts and the knowledge archive must be **per-community configurable**, not a hardcoded Romanian list with translated labels.
