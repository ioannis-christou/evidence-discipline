# PARKED — good ideas kept, dead claims nailed down

Two things go in this register and nothing else: ideas worth building but not
now, and claims that have been checked and disproven so they do not come back a
third time. Every entry says which it is, and shows the evidence rather than
asserting it.

The second category is the one that pays. An idea that has been disproven once
and not written down will be proposed again in three weeks, by someone
well-intentioned, with the same reasoning — and it will cost the same time to
kill twice.

---

## Kept: enumerate from a chokepoint rather than listening at the firehose

Anything that every instance of an event must touch is a complete index of that
event. Where a protocol routes a fixed fee to one account on every creation, the
history of that one account enumerates every creation that ever happened — no
socket, no waiting, no long-running listener that returns nothing.

The class of trick is worth more than the instance. It converts an unbounded
streaming problem into a bounded, resumable, cheap one.

**What must not be claimed from it:** enumeration is not detection. It gives
history, not speed. Anything about being *first* to an event is a latency
question this technique does not touch, and that distinction is easy to lose
once the enumeration starts working well.

**Before use:** find the chokepoint empirically, not from a blog post. Take a
known instance, walk its participants, find the one that receives the constant
transfer every time, and confirm it on at least three separate instances before
trusting it.

## Disproven: a reported bug that had been fixed four days earlier

An external note reported that a component only inspected top-level records and
would therefore miss nested ones. Checked against the current code: false. The
component had been scanning nested records for four days by the time the claim
was made.

The claim came from reading a comment that began *"this used to..."* as a
description of the present.

**Rule that came out of it:** when a review cites a code comment as evidence,
check whether the comment describes the present or the past. It is now rule 5 in
[METHOD.md](METHOD.md), and it earned its place.

---

## Why a register instead of a memory

The same idea arriving twice is not a problem. The same *dead* idea arriving
twice, with nobody able to remember why it died, is how a project spends a month
re-learning something it already knew.

A disproven claim without its evidence attached is just an opinion with
seniority.
