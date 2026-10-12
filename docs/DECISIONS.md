# Decision log

Why things are the way they are. Read before reversing any of it.

## Valuation approach

**Built from the audited accounts, not management's spreadsheet.** Their file contains the
defects in `docs/FINDINGS.md`, so it is a subject of review rather than a source.

**Six methods, triangulated.** NAV as a floor, revenue and EBITDA multiples, and three DCF
cases. No single method is right; agreement between them is the evidence. The multiple-based
methods matter disproportionately because they use audited FY26 only — no forecast, no discount
rate — so they survive any attack on assumptions.

**Two of the three DCF cases use management's own student numbers.** Deliberate: it removes the
"you cut my growth story" objection. Case A is ours and is the clean pre-money case, because it
excludes the ₹2 crore.

**We were more generous than management on fee inflation** — 7% against their 3.6%. Say this out
loud; it buys credibility before the bad news. The one thing added is tax, which they omitted.

**Case A is the methodologically correct pre-money basis.** Cases B and C assume the raise is
received, so strictly they are post-money operating cases sitting in a pre-money range. This is a
known compromise. Disclose it rather than be caught on it.

## The discount rate

**Components, not a total.** An earlier version typed 23.50% as the cost of equity while its own
components summed to 25.50%. The build-up now computes. The lesson generalises: if a number
cannot be traced to a formula, it cannot be defended.

**Recommended premiums: 6% size and illiquidity, 4% company-specific** → cost of equity 23.50%,
WACC 18.67%. Six per cent sits at the top of the defensible empirical range for the smallest
companies rather than beyond it; 8% was tried and is aggressive. The 4% is backed by nameable
risks: one campus, leased land, no Board permission, first year of audited accounts,
key-person dependence.

**The conclusion is robust to this.** Even at a 17.5% cost of equity — a listed-company rate —
the most optimistic case reaches ₹4 crore, 40% of the client's ask. Only the precise number
moves. That is the line to use when challenged: *"take any rate you can defend; we still do not
get to ₹10 crore."*

**Illiquidity is in the rate, not in a discount on the output.** There are two accepted
treatments and doing both double-counts. No DLOM or minority discount has been applied. Flag
this if the work is handed to a registered valuer.

## The concluded range

Originally adviser judgement — ₹45 L to ₹200 L — bracketing where the methods clustered at a
~19% WACC. It was two typed cells, and when the premiums were set to 0% it ended up *below every
method on the page*, which was indefensible.

It is now `=MEDIAN(C17:C22)` and `=MEDIAN(D17:D22)`. This was done at the user's request for a
fully live sheet. **Know the trade-off: a judgement has become a rule, and the model now decides
the conclusion rather than the adviser.** Typing over those cells restores judgement but breaks
the live chain. Either is defensible; the inconsistency was not.

## Things declined, and why

**Reverse-engineering the valuation to ₹10 crore.** Asked for directly. Declined. The commercial
argument is the stronger one: at ₹10 Cr the implied multiples are 16.4x revenue and 79x
earnings, so the first buyer to read the audited accounts walks — costing the success fee, the
client and the adviser's name in a small city. A buyer's payback at that price is 79 years.

**Paying investors as employees.** Proposed as a way round the Section 8 dividend bar. Declined:
it needs false payroll records, TDS returns and Form 16s; the deduction fails s.37(1); it is the
textbook fact pattern for licence revocation under s.8(6); it is visible at twenty investors;
salary is taxed worse than capital gains; and the adviser who designed it is the one named
afterwards.

**A perpetual instrument paying 1% of revenue per ₹10 lakh.** Better instinct than profit-share,
because revenue-linked payments are a cost rather than a distribution. But ₹2 Cr means **20% of
gross revenue in perpetuity**, which is ~97% of current profit and exceeds all profit in the
conservative case by FY32. It is also economically worse for the client than selling equity —
~130% of profit at a 15% margin, ranking ahead of his own earnings, forever. And Rule 18 caps
secured debenture tenure at 10 years, so perpetual is likely not issuable. The fix is revenue-
based financing at **0.4–0.5% per ₹10 lakh with a 2.5–3x cap**, which is a real product.

**Taking the adviser's fee in equity.** See `docs/ENGAGEMENT.md`. Cash.

## Workbook conventions

**No pasted values where a formula belongs.** Adopted after the user caught hardcoded values in
the Reverse Test. Applying it then found two more: the cost-of-equity mismatch, and the two
"implied by the client's expectation" rows disagreeing with each other (one used the equity
target, the other the required enterprise value).

**Edit by XML surgery, preserve formatting.** The user works in Excel between sessions. Every
edit must leave `styles.xml` byte-identical and must preserve their own additions — the `$G$27`
raise cell, the "Justify value x times" column, the row deriving ₹8 Cr pre-money, their written
conclusions, and the deletion of the two Reverse Test routes.
