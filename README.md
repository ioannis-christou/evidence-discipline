# Evidence discipline — a measurement programme on market and on-chain data

A published research record. No strategy code, no parameters, no credentials.

The failure mode in this kind of work is never a shortage of ideas. It is an
evidence standard loose enough to let a good-looking number through. Over this
programme, 72 pre-registered hypotheses were graded and none survived — and the
useful output was not a strategy, it was a set of instruments that make a false
claim hard to state.

Every number below appears next to the control that validated it. A number
standing alone is the thing this repository exists to argue against.

## Results at a glance

| Question | Measured | Control that validated it |
|---|---|---|
| Do price-derived signals carry an edge? | 72 pre-registered hypotheses, **0 passed**, across BTC/ETH/DOGE 1h, AAPL/ES=F/SPY 1d, PEPE/WIF/SHIB 15m | random entry · random pick · shuffled order · buy-and-hold |
| Is a 24h breakout on ES=F real? | +20.28% total, profit factor 5.68, t = 2.64 | **random entry matched it 53% of the time** — rising market, not a rule |
| How much of a loss is execution cost? | Same basket: −97% hourly, −39% weekly → **58 points is turnover cost** | the two frequencies are each other's control: identical assets, identical period |
| Does creator identity predict success? | 64 observed same-creator success pairs vs 430 expected, **z = −5.22** | 3,000 permutations |
| Does launch frequency predict failure? | Monotonic across five buckets of 1,427,208 accounts; heaviest ≈ **13x worse**; base rate **0.81%** | replication on an independent 200,692-account sample, z = −25.7 |
| Can fills be computed instead of estimated? | **24 of 30** real trades reproduce to the base unit, error **0.0000%** | direct comparison against executed chain state |
| Is the census actually complete? | An earlier 200,692-account sample is contained at **99.995%**; key range spans the full address alphabet | independent cross-sampling and range-span validation |

Test harness: **1,053 automated checks across 29 modules**, all green. Every
module carries a negative control (nothing passes on pure noise) and most carry
a positive control (a planted effect *must* be detected).

## What is deliberately not here

No entry rules, no thresholds, no parameterisation, no source code, no
credentials. The method is published; the parameterisation is not. Those are
different things, and only one of them is worth reading.

## Contents

- [METHOD.md](METHOD.md) — the five working rules, and the incident behind each
- [RESULTS.md](RESULTS.md) — each finding, its control, and what may not be
  concluded from it

## Licence

MIT. Nothing here is financial advice. No capital figure or performance claim is
being made, and none should be inferred.
