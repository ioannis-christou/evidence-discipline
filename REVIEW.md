# REVIEW — what an adversarial review of my own work found

A module in this programme was submitted for adversarial review twice. The first
review returned 16 findings and rejected it. The rework raised the selftest from
60 checks to 115 and was submitted again. The second review returned 9 more and
rejected it again.

The verdict from the first review is the reason this file is public:

> The research is largely correct. **The evidence standard is what failed** —
> the strongest-sounding controls are the ones that cannot fail.

That sentence is worth more than a passing grade would have been.

---

## Controls that could not fail

These are the findings that matter, because each one is a safeguard that looked
rigorous and tested nothing.

**A positive test built from the specification, then validated against the
specification.** The expected values were generated from the same source they
were checked against. No input could make it fail. It had been reported as
"cross-checked against a real mainnet case" — that check had happened once, by
hand, in a shell session, and never in the code that claimed it.

**The headline safety mechanism was never tested.** The module pinned an
external file by content hash. The only test covered a *missing* file. Nothing
ever checked that a **modified** file was rejected — that is, the one thing the
pin exists to do.

**A security scan that was theatre.** It banned camelCase JavaScript function
names inside a Python module. Passing untouched: the Python equivalents, the
signing calls, and three HTTP libraries. It also stopped scanning before the
CLI entry point, so the only code that actually runs when the module is executed
was outside the audited region. The reviewer demonstrated this by inserting a
credential-exfiltration function into that region; every audit stayed green.

**Two guards that were mathematically incapable of failing.** One asserted that
a derived address was off-curve — guaranteed by the derivation function itself.
One asserted that two different inputs produced two different outputs.

**A comparison against a hardcoded literal with no provenance.** If the literal
had been produced with the same procedure it was checking, the check was
circular. Nobody could tell, because the provenance was not recorded.

## Claims that outran their evidence

**"VERIFIED" printed for data nobody fetched.** The report checked that a file
parsed, that it named the right owner, and that its length was right — but never
that it described the address it claimed to. The reviewer hand-wrote the file in
four lines, with the address field set to `TOTALLY_MADE_UP`, and the tool printed
`VERIFIED` along with a slot number of `999999999`. The document had specified
that particular output as the gate for re-admitting previously deleted claims.
**The gate was satisfied by typing.**

Nobody was going to forge it deliberately. That is not the point. The point is
that the word carried no provenance, so the criterion was not a criterion.

**A claim on disk with no artifact behind it.** A verification result was
recorded in prose. There were no raw bytes, no response, no fixture — the string
existed only in the document. The same defect had been raised in an earlier
review and was committed again twelve hours later by the same author.

**"Strictly stronger" was wrong, and the correction is instructive.** A content
hash proves **immutability, not provenance**: it shows bytes have not changed
since they were pinned, and says nothing about where they came from. It is
stronger for offline verification and weaker as an anchor to upstream history.
Both halves are load-bearing, and the original claim collapsed them into one.

**An inference inside the function that swore it never inferred.** A marker
documented as belonging to one data structure was accepted as a valid value in a
different one, with no example anywhere in the codebase to support it.

## A control that broke on success

One selftest asserted that a particular output file did not exist. That file is
what a successful run of the same script produces. So the full regression suite
was green only for as long as the outstanding verification went unrun, and would
turn red the moment it was completed.

The control was trying to say *a green selftest is not a completed
verification*, which is correct. It was implemented as *no verification has ever
been completed*, which is a different statement and becomes false on success.

## What the reviewer independently confirmed

The review is not a demolition. Re-measured from scratch, with an independent
implementation that imported none of the code under review: the checksum, the
program identifier, every structure offset, the computed sizes, all account
counts, a 1,011-transaction table reproduced byte-for-byte, and six address
derivations correct on **300 of 300** real cases.

The research reproduced exactly. Every number. What failed was the apparatus
around it.

## Why this is published

Two reviews, 25 findings, and the module was still not accepted at the end of
them. That is the honest state, and publishing it costs nothing that is worth
keeping.

An engineer who shows you only accepted work has told you what their ceiling
looks like on a good day. This file tells you what happens on a bad one — and
what the correction looked like.
