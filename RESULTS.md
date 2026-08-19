# RESULTS

Each finding states what was asked, what was measured, what the control said,
and what may not be concluded. Where no control was run, that is stated rather
than filled in.

---

## Finding 1 — price-derived signals, four asset classes, nothing

- **Asked:** whether price action across major traditional and digital assets
  contains exploitable predictive structure under pre-registered rules.
- **Measured:** 72 pre-registered hypotheses graded. 0 passed. BTC/ETH/DOGE at
  1h, AAPL/ES=F/SPY at 1d, PEPE/WIF/SHIB at 15m.
- **Control:** each hypothesis was graded against random entry, random pick,
  shuffled order and buy-and-hold. None cleared its controls.
- **May not be concluded:** that these asset classes are random in all
  dimensions — only that these 72 pre-registered specifications carried no edge.

## Finding 2 — the instructive failure

- **Asked:** whether a 24-hour breakout rule on ES=F had genuine validity.
- **Measured:** +20.28% total return, profit factor 5.68, t = 2.64. By the
  standard of most published backtests, an edge.
- **Control:** random entry matched or beat it 53% of the time.
- **May not be concluded:** that the rule has any validity. It measured a rising
  market, not a rule. Kept here permanently as the reference case for what an
  uncontrolled metric looks like.

## Finding 3 — an effect separated from its execution cost

- **Asked:** how execution frequency alters net performance in a high-turnover
  cross-section.
- **Measured:** the same memecoin basket lost 97% rebalanced hourly and 39%
  rebalanced weekly. 58 percentage points of the difference is turnover cost,
  not market direction.
- **Control:** the two rebalancing frequencies are each other's control —
  identical assets over an identical period, with only turnover differing, so
  the gap is attributable to cost rather than to direction.
- **May not be concluded:** that the weekly version is viable. It still lost 39%.

## Finding 4 — creator identity does not predict success

- **Asked:** whether creator wallet identity is a leading indicator of success.
- **Measured:** on a 197,932-account sample, 64 observed same-creator success
  pairs against 430 expected by chance, z = -5.22.
- **Control:** 3,000 permutations established the chance baseline. Outcomes are
  if anything *less* concentrated in individual wallets than chance would give.
- **May not be concluded:** anything about creator behaviour in general. This
  measures one venue at one time.

## Finding 5 — launch frequency is a strong negative signal

- **Asked:** whether a creator's historical launch frequency correlates with
  subsequent outcomes.
- **Measured:** across the full 1,427,208-account census, success rate falls
  monotonically across five buckets of creator launch count. The heaviest bucket
  is roughly 13x worse than everyone else. Population base rate 0.81%, i.e.
  99.19% of launches never complete.
- **Control:** replication on an independent sample — the same comparison on an
  earlier 200,692-account harvest returned z = -25.7.
- **May not be concluded:** that this is causal. A creator's total launch count
  includes launches made *after* the one being scored, and only the prior count
  is visible at decision time.

## Finding 6 — computed fills instead of estimated slippage

- **Asked:** whether deterministic reserve-based pricing removes slippage
  estimation error.
- **Measured:** 24 of 30 sampled real trades reproduce to the base unit, error
  0.0000%.
- **Control:** direct comparison of model output against executed chain state.
- **May not be concluded:** that the model covers all cases. The 6 misses share
  a parameterisation it does not model, where error reaches 17% — and the code
  refuses those rather than approximating them.

## Finding 7 — completeness, verified rather than claimed

- **Asked:** whether collection completeness can be verified independently of
  the walk's own self-report.
- **Measured:** an earlier 200,692-account sample gathered before the walk is
  contained in it at 99.995%, and the key range spans the full address alphabet,
  so it is not a truncated prefix.
- **Control:** independent cross-sampling and range-span validation.
- **May not be concluded:** that the base rate is a permanent probability. It is
  a snapshot, and closed accounts are absent, biasing the base rate by an amount
  not yet quantified. Use it for ranking, not as a probability.
