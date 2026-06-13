# THE CAP ROOM — Launch Pack
*Working title. Analyst: Claude · Guide: Angus · 12 June 2026*

---

## 1. The finals-timing call: agree, with a two-stage structure

Launching at finals is right, but for a sharper reason than peak eyeballs. The asset you're really selling B2B is **authority**, and authority compounds through a sequence the AFL calendar hands you for free:

| Stage | Window | What drops | Why |
|---|---|---|---|
| **Soft launch** | Late July (Rd 19–20) | Site live + free weekly brief + Money Map findings | Build the email list while stakes rise; debug in public at low risk |
| **Authority launch** | First week of finals (early Sep) | **The List Efficiency Index** — full 18-club ranking | Finals = maximum audience; every club's season is being judged anyway. The Index gives media a ready-made story every finals week |
| **Product launch** | Trade period (Oct) | **Cap Tracker** — modelled contract database | Cap space is THE October conversation; you arrive as the only data source in the room |
| **Negotiation window** | Nov–Feb | B2B outreach: media licensing, agent seats, club analytics | You negotiate from a high base: traffic numbers from finals, citations from trade period, and the off-season is when media/clubs sign deals for next year |

The one risk in finals-only timing: if you launch the contract database cold in September, finals noise drowns a "data product" story. Lead with the Index (a finals-native story), hold the database for October when it's the *only* story. That's the refinement.

---

## 2. Methodology one-pager: The List Efficiency Index (LEI)

**The claim:** one number per club — *excess wins per cap-dollar deployed* — published annually in Grand Final week.

**Output side — Wins Above Expectation (WAE).** Each game's closing exchange price defines the market's expected win probability (vig-removed). A club's expected wins for the season is the sum of those probabilities; WAE = actual wins minus expected wins. Using market expectation (not a naive model) means injuries, fixture strength and travel are already priced in — the residual isolates list management and coaching execution.

**Input side — Modelled Cap Deployment (MCD).** Player-level salary estimates built from: (a) the rookie/draft pay scale, which is formulaic; (b) ~100 media-reported contract anchors per year as Bayesian priors; (c) performance, age-curve, position-scarcity and free-agency-event regressors; (d) a hard reconciliation constraint — club estimate totals must sum to the AFL's officially published TPP aggregates. Individual estimates publish as **ranges** ($700–850K), never points.

**The ratio.** LEI = WAE / (MCD in $M), banded A+ → D− using the same grading discipline as the AR data-accuracy framework. Confidence intervals are displayed, not buried.

**Governance (the AQS playbook).** Full methodology published; annual academic review (UNSW sports-economics tie-in — Melbourne researchers already publish on AFL pay vs marginal product, so the academic lane exists); revision log public; disputes invited and answered in writing. Independence statement: no league, club, bookmaker or affiliate money. The moat is not the model — it's the *governed, published* model.

**Why it can't be easily copied:** Champion Data can't publish salary estimates of its 49%-owner's players. Hobbyists won't run the data ops, anchors pipeline, and dispute process year after year. Media can't — they're customers.

---

## 3. The launch finding (real, from today's analysis)

Analysed: every AFL match-odds market on the Betfair exchange, 2024–2026 YTD — **555 games, $199M matched** (avg $358K/game; ~$81M in 2024, $76M in 2025).

1. **The longshot tax.** Teams priced under a 20% chance won **7.4%** of games against an implied **11.6%** — the crowd pays ~4.3 points for hope. Mirror image: hot favourites (>80%) won **93.4%** vs **88.4%** priced. Boring is underpriced.
2. **The comeback premium.** Teams trading $3–$15 at half time are priced at a **20.7%** chance; they win **13.4%**. Flat-stake backing every half-time comeback lost **37.5%** over three seasons. By three-quarter time the bias narrows (19.2% priced vs 15.8% actual) but persists.
3. **The home edge is still underpriced.** Home teams win **58.4%** of games priced at **55.2%** — a 3.2-point residual the market hasn't closed in 30 years of "everyone knows about home-ground advantage."

These three are the September content engine: each is a standalone "oh wow" piece, all from one dataset, all replicable weekly in-season. (Caveats logged: in-play "back prices" can be thin at extremes — we exclude >$15 from headline claims; commission modelled at 5%.)

---

## 4. 14-week build plan (analyst: me · guide: you)

**Weeks 1–2 (mid-June): Foundation.** Name + domain locked; legal scan of source-site T&Cs (your IP counsel, ~2 hrs); data pipeline v1 — nightly pulls of results/stats/fixtures + Betfair files + odds API trial; repo of the cap/TPP corpus (started — see workbook).

**Weeks 3–5: The Index engine.** WAE calculator across 2021–2026 (exchange files cover it); MCD v0.1 — rookie-scale layer + media-anchor database (I draft, you sanity-check the whispers: your network knows agents); first full back-cast LEI for 2024 and 2025 seasons as proof.

**Weeks 6–8 (late July): Soft launch.** Site live (wireframe → build; Lovable/Supabase pattern you used for Proposal Studio is the fast path); weekly brief #1–#3 using the market-bias findings; begin LinkedIn/X distribution (parked per your instruction, but the pipes get built).

**Weeks 9–11 (Aug): Hardening.** MCD v0.2 with full regressor set; methodology paper drafted; academic reviewer engaged; Index results stress-tested — I run the devil's-advocate pass, you decide what ships.

**Weeks 12–14 (early Sep): Authority launch.** LEI 2026 published finals week one; media kit with pre-cut club graphics (licensable later); paywall on from day one for the Cap Room tier.

**Oct:** Cap Tracker ships into trade period. **Nov–Feb:** the negotiation window — media licensing, The Box seats, and (your call) a conversation with a network or masthead about exclusive Index rights for 2027.

Resourcing honesty: this plan assumes me as the analytical engine plus ~4–6 hrs/week of your guidance and network access, and one contractor-day/week for site build in weeks 6–8. It does not touch AR Group resources — important for the recap optics.

---

## 5. Name + brand notes

"The Cap Room" — the inner sanctum where list decisions get made; ownable, extends to NRL, and the tiers name themselves (The Stands / The Cap Room / The Box). Alternatives parked: *The Ledger*, *Fair Value*, *ListIQ*. Domain check pending. Design direction in the wireframe: scoreboard-ledger — old AFL scoreboard green/cream/gold numerals meets a market terminal; deliberately not another navy sports site, and visually distinct from Nightingale so the ventures never blur.

---

## 6. Open decisions for the guide

1. Name sign-off (domains move fast once content ships)
2. NRL: hold for year 2, or run exchange-data analysis in parallel since the files are free? (Recommend: hold publishing, collect data now)
3. The betting line: my recommendation stands — market *analysis*, never tips, no affiliates. Confirm.
4. Entity/IP structure: new entity outside AR Group pre-recap, or personal until validated? (One for Adrian/your tax counsel — flag the 2027 CGT transition timing.)
