# The Cap Room

**The hidden economy of Australian football.** Independent football economics: every contract dollar, every closing price, every club's luck, measured and published with a methodology you can attack.

No league, club, bookmaker or affiliate funding. No tips. Gambling help 1800 858 858.

## What is in this repository

| Path | Contents |
|---|---|
| `site/index.html` | The full prototype: single-file tabbed app. Home (MCG hero + fair value ticker), the Index, Luck Ledger, Players, Money, 18 club pages, live rivalry weaver (14,915 games, 1897-2026), Almanac plates, Findings, Method. |
| `data/` | All published datasets: wins above expectation (AFL + NRL, 2021-2026), Player Value v0.1 (1998-2023), the paid-v-deserved ledger, club expected wins, head-to-head corpus. |
| `analysis/` | Paid v Deserved workbook (live formulas, stress-tested v1.1) and the foundation workbook. |
| `docs/` | Launch pack, finals media kit, the Collingwood Luck Ledger article, hero plate SVGs. |
| `pipeline/` | AWS production pipeline specification (four-stage, fail-closed QA gate). |

## The QA covenant

Every figure passes independent re-derivation, out-of-sample splits, reliability testing and invariant checks before publication. Findings that fail are published as kills in the revision log. Current kill log: the AFL longshot tax (died out of sample), the six-point margin myth (never existed), a draw-settlement bug (fixed, restated), the Wayne Milera salary error (fixed with a career floor, documented in the workbook).

## Key numbers

- 14,915 games, 1897-2026, all 18 current clubs
- $429M of exchange volume priced, 2021-2026
- Player Value validated +0.67 to +0.71 against held-out Brownlow votes, every season tested
- Zero persistence of luck: beating the market is a coin flip (r = -0.04 across 72 club-season pairs)

## Important notes

- **Keep this repository PRIVATE.** Confidential methodology specifications (index econometrics, PV v0.2 allocation weights, salary model internals) are deliberately NOT in this repo and live offline until entity and IP structure are settled.
- No individual AFL salary is public; all per-player pay figures are modelled estimates in bands. See the workbook READ ME before quoting anything.
- The hero photograph and any club marks require licensing review before public deployment.
- Raw Champion Data appears nowhere in this project, by design.

## Running the site

Open `site/index.html` in a browser. Everything is embedded: no server, no build step, no external requests (Google Maps satellite buttons activate only when a referrer-restricted key is added to `CAPROOM_CONFIG`).

Built with the Nightingale design system. Sydney.
