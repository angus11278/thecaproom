# THE CAP ROOM: PRODUCTION DATA PIPELINE v1.0
## INTERNAL. AWS-native, mirrors the Fund Flow Reporting four-stage pattern.

### Stage 0: Principles
Personal venture: separate AWS account, zero AR Group resources or credentials. Everything idempotent, everything logged, every load gated by the QA invariants that caught the dead-heat bug, the NRL name chaos and the rivalry restatement. No raw Champion Data anywhere in the pipeline.

### Stage 1: Acquire (EventBridge -> Lambda -> S3 raw/)
Nightly 02:00 AEST in season, weekly off-season.
- exchange_files: Betfair AU hub CSVs (AFL, NRL, AFLW) via the GitHub mirror; ETag-checked, only changed files pulled.
- odds_live: The Odds API snapshots at T-48h, T-24h, T-6h, T-30m per fixture (closing-line-value series the free files lack). Budget tier ~USD99/mo.
- boxscores: AFL Tables + Footywire season pages, fitzRoy-compatible parsing, 1 req/5s, identified user agent, cache-first. Legal note: same public sources the academic fitzRoy package has used openly for years; counsel review of T&Cs before launch (already in launch plan wk 1-2).
- contracts_anchors: weekly manual-assisted intake of media-reported contract values into a reviewed S3 csv (human-in-the-loop by design; anchors are priors, provenance matters).
- tpp_official: annual AFL release, manual trigger.

### Stage 2: Harmonise (Lambda, Python, shared lib `caproom_lookups`)
The ffr_lookups pattern: one versioned library owning team-name map (Footscray->Western Bulldogs etc.), venue map, player ID resolution (AFL Tables ID as master key), dead-heat settlement (draws = 0.5), women's/exhibition filters. Unit tests pin every known trap: "NZ Warriors Wowen", GWS GIANTS, Brisbane Bears.

### Stage 3: Validate (the QA gate; load fails closed)
Invariants asserted per batch before anything reaches curated/:
- Sum(WAE) per season per comp = 0 +/- 0.05
- Two runners per match market; probabilities normalise to 1
- Sum(PV) per season = league constant; Sum(MCD) per club = published TPP envelope
- Row-count deltas vs trailing average (>15 percent triggers quarantine + SNS alert)
- Name-audit diff: any NEW team/player/venue string halts the batch for review
Failures land in quarantine/ with a diff report. The public revision log is generated from this gate's history.

### Stage 4: Compute + Publish
- Athena/DuckDB over curated parquet; nightly jobs recompute EW, Luck Ledger, PV, club pages JSON, weave corpus.
- Outputs: site_data.json artefacts to S3 -> CloudFront (static site, the v5 architecture deploys as-is); weekly brief data pack; B2B export bucket (signed URLs) for The Box tier.
- Cost envelope: Lambda + S3 + Athena + CloudFront ~AUD40-80/mo at launch scale; Odds API the largest line.

### Build order (unblocks v0.2)
Week 1: Stage 1 boxscores + Stage 2 lib (the 2021-25 refresh is the critical path for everything).
Week 2: Stage 3 gate + backfill validation against this prototype's numbers (they are now the regression baseline).
Week 3: Stage 4 publish loop; site goes live off the bucket.
