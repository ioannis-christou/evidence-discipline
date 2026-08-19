# METHOD

Five rules. Each one exists because something went wrong first.

---

## 1. Pre-register before you look

The grader refuses to score a hypothesis that is absent from the registry, and
altering a threshold after the fact changes its fingerprint, so the change is
detectable.

This matters because the usual defence against p-hacking is good intentions,
and good intentions do not survive a long afternoon and a nearly-significant
result. Making the registry a precondition of grading turns the discipline into
a mechanism: there is no path to a score that does not pass through a
commitment made in advance.

The registry for this programme holds 72 entries. None of them passed.

## 2. Every claim needs a control that can fail

The controls used here: random entry, random pick, shuffled order, buy-and-hold,
and planted-effect detection.

The first four are negative controls — they establish what the result looks like
when there is nothing there. The last one is a **positive** control, and it
matters more than it appears.

Without a positive control, a null result cannot be distinguished from a broken
test. A pipeline that silently drops every row and a pipeline that correctly
finds nothing produce the same output: no effect. The only way to tell them
apart is to inject an effect you know is present and require the instrument to
find it. Every module here does that, and a module that fails to detect its own
planted effect is treated as broken rather than as evidence of absence.

This is the rule that turns a null result into a finding instead of a shrug.

## 3. Fail closed — absent is not zero

A record whose payload ended before the fee fields is skipped, not scored.

The incident: reading a missing fee field as zero made a correctly-priced trade
appear 9.9% mispriced. The arithmetic was right and was very nearly thrown out
on the strength of a default value that was never in the data. A missing number
and a zero are different facts, and code that conflates them will eventually
accuse itself of a bug it does not have.

## 4. Refuse rather than approximate

Where the model does not cover a case, the correct output is a refusal, not a
best guess.

The pricing routine validates its input before pricing anything and declines
any record it cannot reproduce exactly. On the sampled trades this means 24 of
30 price to the base unit at 0.0000% error and the remaining 6 — which share a
parameterisation the model does not implement, and where error reaches 17% —
return nothing at all.

A tool that answers every question is not more useful than one that answers
fewer questions correctly. It is less useful, because you can no longer tell
which answers to trust.

## 5. Do not impose horizons

Bucketing forward returns into analyst-chosen windows — 24h, 48h, "hold 6 bars"
— can only find effects at the scales the analyst happened to pick. If a signal
lives at a scale nobody chose, an imposed bucket never sees it.

This was a correction made mid-programme, not a principle held from the start.
Every test in the first phase used imposed horizons. The corrected form:

> Regress forward return on the signal as a **continuous variable**, across a
> **continuous sweep of scales**, and read where the t-statistic peaks.

The data names the scale; the analyst does not.

## 6. Say which of three things a number is

Every figure is PROVEN, MEASURED, or neither, and the label travels with it.

*Proven* means derivable from an authoritative source and re-derivable by
anyone. *Measured* means it came from observation, over a stated corpus, with
the corpus pinned. *Neither* means inference — which is allowed, but only when
it is labelled as such.

The rule that enforces it: **a number nobody can re-derive is a memory, not
evidence.** An earlier version of one document stated figures that existed
nowhere but in that document. They all turned out to be correct. That was luck,
and the review said so.

Numeric claims written in prose are now checked mechanically against the pinned
artifact — 119 of them in a single document — so a figure cannot drift out of
agreement with the data it came from without the test suite going red.

---

## The cost of this

Applied honestly, these rules make almost everything fail. That is the intended
behaviour, and it is the reason the results file is a list of things that did
not work.

The alternative is not a higher pass rate. It is the same pass rate with the
failures unlabelled.
