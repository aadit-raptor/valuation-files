# Astral School valuation — complete project context

Independent valuation and fundraising advisory for **Astral School**, Nagre Nagar, Nashik,
run under **Excelerate Learning Foundation**, CIN `U88900MH2025NPL445351`.
The client wants to raise **₹2 crore** by selling a stake. The adviser (the user) is retained
to produce an independent valuation and then place the stake with investors.

**This is the complete project context. Everything needed to continue is in this one file.**

---

## The one sentence the whole model rests on

> The school business is worth X. It owes ₹1.39 crore. What is left for the owners is X minus that.

Enterprise value minus net debt equals equity value. The client's own report never performs
that subtraction, which is the single largest reason his number and ours differ.

---

## Facts (audited FY 2025-26, first reporting period)

| | ₹ |
|---|---|
| Revenue from operations | 60,90,900 |
| Adjusted EBITDA (normalised) | 22,74,220 |
| Profit after tax | 12,58,940 |
| Book equity | 13,18,945 |
| Shares outstanding | **6,000** @ ₹10 par (authorised also 6,000 — no headroom) |
| Book value per share | 219.82 |
| Borrowings (unsecured) | 1,62,28,190 |
| Less cash | (23,46,984) |
| **Net debt** | **1,38,81,206** |
| **Net debt ÷ EBITDA** | **6.10x** |

Auditor: Ulhas Borse & Co, FRN 0127883W, UDIN 26161661CUAYAX4200.
Land is **leased, not owned**. Building under construction ₹1,46,24,820.
Maharashtra Board permission **not yet obtained**. Students at Nagre Nagar: 155 in FY26.
Govind Nagar is a separate preschool and is **not** part of what is being sold.

## Conclusions

- Pre-money equity, at a defensible discount rate: **roughly ₹0.45 Cr to ₹2.0 Cr**.
- Client expects ₹10 lakh per 1%. That is ₹10 Cr **post**-money, so **₹8 Cr pre-money** for a
  ₹2 Cr raise — his real ask is ₹2 Cr lower than he states.
- At any defensible valuation, **₹2 crore cannot be raised as equity without the promoter
  losing control**. This is the central finding and it points to debt, not equity.
- Rate-independent cross-checks: 3–5x revenue gives ₹43.9–165.7 L; 10–15x EBITDA gives
  ₹88.6–202.3 L; NAV floor ₹13.19 L. These contain no forecast and no discount rate, so they
  survive any attack on assumptions.

---

## Hard rules for this engagement

1. **Never reverse-engineer the valuation to the client's ₹10 crore.** It was asked for and
   declined, with reasons. Advocate for the top of a defensible range; do not manufacture one.
2. **Never help disguise a distribution.** Paying investors as fake employees was proposed and
   declined. So was a 20%-of-revenue perpetual instrument (unaffordable and likely not issuable).
3. **No pasted values where a formula belongs.** Every number in the workbook must trace to a
   formula or to audited source data. This has already caught three real errors.
4. **Preserve the user's edits and formatting.** They work in Excel between sessions and upload
   revised copies. Edit workbooks by **direct XML rewrite**, never an openpyxl round-trip, and
   verify `styles.xml` is byte-identical afterwards.
5. **LibreOffice cannot recalculate in this container.** Compute expected values in Python,
   inject them as cached `<v>` values, and set `fullCalcOnLoad`. See Part 3.
6. **Flag, don't fix silently.** When a number moves, say which direction and who it favours.

---

## File map

```
00-source/          client documents, untouched
03-valuation/       CURRENT-astral-valuation.xlsx  <- the live model
04-deliverables/    Astral_Valuation_Briefing.pdf  <- presenter's briefing (pre-fix)
05-engagement/      Fee_Proposal_Astral_School.xlsx
HANDOFF.md          this file
```

Repo: `github.com/aadit-raptor/valuation-files`, branch `claude/friendly-lamport-fmzemh`.
Commit as work completes; push only when asked.

## What this file contains

| Part | |
|---|---|
| Part 1 | The engagement — client, deal, our fee, the Section 8 problem |
| Part 2 | Findings against management's report, and open questions |
| Part 3 | The workbook — cell map and editing conventions |
| Part 4 | Decision log — why things are as they are, and what was declined |
| Part 5 | Open work, with a ready prompt for each task |

## State as of the last session


The live workbook has both risk premiums set to **0%**, giving a 13.50% cost of equity and an
11.67% WACC. That is a listed-company rate for an unlisted single school, and at it the central
finding reverses — the promoter appears to keep a majority. **Four fixes are outstanding and are
listed at the top of Part 5.** Do not present the model until they are done.


---

# PART 1 — THE ENGAGEMENT
## The parties

**Client** — the owner of Astral School, Nagre Nagar, Nashik. The school operates under
Excelerate Learning Foundation, CIN `U88900MH2025NPL445351`, incorporated during FY 2025-26.
Directors per the audited accounts: Suchita Mangesh Rajguru (DIN 11049371) and
Ruby Mufaddal Merchant (DIN 11049372).

**Adviser** — the user. Engaged to produce an independent valuation and then place the stake.
Not an IBBI-registered valuer, so the work is **commercial and transaction advisory**, not a
statutory valuation under Section 247 of the Companies Act.

## The school

- Grades PG to 2 currently; the plan runs to Grade 6.
- 8,500 sq ft of classrooms, plus a planned 2,500 sq ft hall. A 10,000+ sq ft ground is
  earmarked for a sports complex.
- Student roll at Nagre Nagar: 60, 104, 45, 55, 90, 120, 145, 155 across FY19 to FY26
  (the dip is COVID). Management projects 200 for FY27.
- **Govind Nagar is a second, separate preschool.** Management's own notes state the investor
  acquires an interest in Nagre Nagar only, and that Govind Nagar and any future preschool
  remain standalone. Check which entity any projection actually covers.
- Maharashtra Board permission has **not** been obtained. ₹20 lakh is budgeted for it.

## The raise

₹2 crore. Management's stated use of proceeds:

| Purpose | ₹ |
|---|---|
| Board permissions | 20,00,000 |
| Loan repayment | 80,00,000 |
| Computer lab, library, soft play | 25,00,000 |
| Sports turf and multipurpose court | 25,00,000 |
| Working capital reserve | 25,00,000 |

Note that only the turf is plainly growth capital. Most of this is refinancing and buffer,
which is an argument for debt rather than equity.

**Promoter borrowings** (from the management workbook, not the audited accounts):
home loan ₹40 L, gold loan 1 ₹26 L, gold loan 2 ₹10 L, personal loan ₹20 L — ₹96 lakh in total,
₹94,000 a month in EMI, all around 10%. The audited balance sheet separately shows
₹1,62,28,190 of unsecured borrowings in the company. Who lent that is an open question; the
working hypothesis is that promoters borrowed personally and on-lent to fund the building,
which would make the loan-repayment use of proceeds far more defensible than it first appears.

## The client's price expectation

₹10 lakh per 1% of equity. Two things follow that he probably has not noticed:

1. That fixes **post**-money at ₹10 crore. Raising ₹2 crore means selling 20%, so the
   **pre**-money is ₹8 crore. His real ask is ₹2 crore lower than he says.
2. At a fixed price per 1%, raising more money does not raise the valuation — it just sells
   more of the school, and the implied pre-money *falls*.

## Our fee

| | |
|---|---|
| Stage 1, engagement fee | **₹75,000** flat, 50% on signing and 50% on delivery of the valuation report. Not contingent on the valuation concluded. |
| Stage 2, placement fee | **0.08% of equity per ₹10,00,000 placed**, or its cash equivalent at the valuation adopted — client elects. On a ₹2 Cr raise that is 1.6% of the company, which is **8% of funds raised**. |
| Scope | Payable only on investors **introduced by the adviser**. Nil on client-introduced investors. |
| Third-party costs | Registered valuer, company secretary, legal, filings — **billed directly to the client**, not deducted from the fee. |

Terms carried in the proposal: 9-month exclusivity, 6-month tail, an introduction register
countersigned by both parties, GST extra, TDS under s.194J may be withheld.

**Advice given on the fee, and worth repeating if it comes up:** taking the success fee in
equity is a bad idea here. Section 8 shares cannot pay a dividend, so the fee would never pay
out, and receiving shares for services is taxable at fair value on receipt — roughly ₹5 lakh of
tax in cash on an asset that yields nothing. Take cash. If upside is wanted, take a warrant over
the for-profit SportsCo struck at the round price, which also reverses the incentive so that a
higher certified valuation makes the adviser *worse* off.

## The structural problem — unresolved and blocking

The CIN ends `NPL`, the ownership code for a **not-for-profit licensed (Section 8) company**.
Such a company is licensed on an undertaking that it will apply profits to its objects and
**will not pay any dividend to its members** (s.8(1)(b)), and on winding up surplus assets go to
another Section 8 company rather than to members (s.8(9)).

If that is right, then **nothing in the client's pitch can lawfully be delivered**: it promises
investors a 15% share of annual net income and an exit at a revenue multiple. Neither is
available. Nor, safely, is a premium buyback. The only route left is selling the shares to
somebody else facing the identical problem.

Two pieces of evidence point the other way and should be weighed honestly:

- The auditor's Note 1 states that dividends are payable and that shareholders receive surplus
  assets on liquidation. That is standard Schedule III boilerplate and almost certainly a
  template not adjusted for Section 8 — but a qualified professional signed it.
- The company paid tax at about 29% with no exemption claimed, which suggests no 12AB
  registration. That is consistent with a Section 8 company nobody has optimised, and it means
  it carries all the restrictions while receiving none of the tax benefit.

**Resolve this before any further structuring work.** Go to mca.gov.in, MCA Services,
View Company/LLP Master Data, enter the CIN; the Company Sub-Category field settles it. Then ask
the client for the certificate of incorporation, the Section 8 licence if one exists, and the
Memorandum of Association.

Also outstanding and material: the **land lease** — lessor, tenure, whether assignment or a
change of control is permitted, and whether a charge can be created over the building. If a
charge cannot be granted, secured debt may not be available either.

## Structures considered

| Option | Verdict |
|---|---|
| Equity in the Section 8 company | **Cannot pay.** No dividend, nothing on liquidation, no safe buyback. |
| Convert to a private limited company | Would lose the school's recognition — a for-profit cannot hold it. |
| Infrastructure company owning the building | Obstructed: the building is already on the Section 8 company's books, funded by its borrowings. Moving it out is a related-party transfer of exactly the kind Section 8 exists to prevent. |
| Management services company | Mainstream in Indian K-12, but draws scrutiny from fee regulators and under s.40A(2), and the compliance cost is disproportionate at this scale. |
| **Secured NCDs, right-sized** | **Recommended.** Interest is a cost, not a distribution, so Section 8 does not bite. |
| **Separate for-profit SportsCo** | **Recommended.** After-hours court rental, coaching and tournaments are ordinary commercial activity and need not sit inside the school. |
| Milestone ratchet | Recommended alongside. Tranche 2 prices at ₹7–10 Cr if enrolment and profit targets are met, so the client can earn his number. |

On the debt: capacity is well under ₹1 crore on current earnings. Simple interest on ₹2 crore at
11% is ₹22 lakh a year, against adjusted EBITDA of ₹22.74 lakh — interest coverage below 1 from
day one. A deferred-payment structure compounds rather than solves that: ₹2 Cr at 12% with a
four-year moratorium becomes ₹3.15 Cr, needing about ₹76 lakh a year to service.

Note also that lending by twenty people to a **public** company risks being treated as accepting
deposits under ss.73–76, which this company cannot do at ₹13 lakh of net worth. Secured
debentures on private placement under ss.42 and 71 are the route; Rule 18 caps secured debenture
tenure at 10 years, so a perpetual instrument is likely not issuable.


---

# PART 2 — FINDINGS AGAINST MANAGEMENT'S REPORT
Source: `00-source/Management_Projections_Sept2026.xlsx`, 14 tabs, prepared for the client.
Everything below is traceable to a named cell or note. Cite the reference, not the conclusion.

## Material defects

**1. Net debt is never deducted.** The report values the company and sells equity at that price.
Enterprise value minus net debt equals equity value, and ₹1,38,81,206 never comes off. This is
the single largest reason their number and ours differ.

**2. No tax line anywhere.** The projections run revenue, expenses, net income — with no tax at
any point. On the moderate case that is roughly ₹25 lakh a year of cash assumed away by Year 6.

**3. Book value per share is out by about 7x.** The `Share-Valuation` tab states 60,000 shares
and ₹31 per share. The audited accounts say **6,000 shares** — stated five times — and the
auditor's own EPS of ₹209.82 only works with 6,000. Their net assets figure of ₹19,05,022 also
omits ₹5,86,080 of short-term provisions; the correct figure is ₹13,18,945. Their arithmetic
reconciles exactly: 19,05,022 ÷ 60,000 = ₹31.75. Correct book value is **₹219.82**.
*Note this error runs in the client's favour — a good one to open with.*

**4. An arithmetic error in the expense total.** On `Financial-Summary` the Year-1 expense lines
sum to ₹67,48,000 against a stated total of ₹87,48,000. The gap is exactly the ₹20 lakh
one-time board-permission item, which the row displays as zero. The Moderate and Bullish tabs
simply drop that ₹20 lakh, which is the entire reason Year 1 flips from a ₹12.48 lakh loss to a
₹7.52 lakh profit. **Their stated "₹20 lakh of upside" in Year 1 is that expense vanishing, not
growth.**

**5. The report values the company on post-money projections and then sells equity at that
price.** The growth in Cases B and C depends on the ₹2 crore being received. An investor cannot
be asked to pay today for growth their own money will create.

**6. Their own deck shows the investment losing money.** `Investor-Returns`: the conservative
case at a 3x revenue exit gives MOIC **0.72** — 72 paise back on the rupee after six years.
Moderate at 3x is 1.05. In `Investor-Pitch-2` (₹15 L per 1%), moderate at 3x is **0.82**.

**7. Three different valuations in one file.** ₹10 Cr post-money (`Investor-Pitch`), ₹15 Cr
(`Investor-Pitch-2`), ₹11.67 Cr implied (₹1.75 Cr for 15% on `Investor-Returns`), plus a "CA
reference" of ₹31/share. The raise amount varies too: ₹1 Cr, ₹1.5 Cr, ₹1.75 Cr — and the client
now says ₹2 Cr.

**8. The audited year and the projections do not reconcile.** Audited FY26 revenue is ₹60.91
lakh and the company was **profitable** at ₹12.59 lakh; the projection's current year shows
₹75 lakh of revenue and a loss. Audited staff cost ₹10.08 lakh against ₹28.08 lakh projected.
Audited lease rent ₹8.04 lakh against ₹20.40 lakh projected.

**9. The loan figures do not match the balance sheet.** The pitch cites ₹96 lakh of loans; the
audited balance sheet shows ₹1,62,28,190 of unsecured borrowings. A ₹66 lakh gap, unexplained.

**10. The structural promise cannot be delivered.** Every sheet is built on an investor's share
of annual net income plus an exit. See `Part 1` — if the Section 8 reading is right,
neither is lawfully available.

## Open questions for management, in order of impact

1. **Is FY 2025-26 a full twelve months?** The company was incorporated during that year and all
   prior-year comparatives are nil. Revenue per student of ₹39,297 is close to the ₹37,500 they
   use, which suggests a full academic year — but if it is a part year the run-rate is higher
   and **the entire valuation range shifts up**. Highest-impact unknown; ask first.
2. Why does projected rent jump from ₹8.04 lakh audited to ₹20.40 lakh? Worth ₹12 lakh a year
   of EBITDA.
3. Why is projected staff cost 2.8x the audited figure for a similar roll? Adding Grades 1–6
   needs qualified teachers, so a rise is expected — but 2.8x needs explaining, and it is the
   largest cost line in the model.
4. Who lent the ₹1.62 crore shown as unsecured borrowings? If promoters on-lent personally
   borrowed money, the loan-repayment use of proceeds becomes far more defensible and should be
   presented that way.
5. Do the projections cover Nagre Nagar alone or both campuses? The investor acquires Nagre
   Nagar only.
6. What are the land lease terms — lessor, tenure, assignment, change of control, right to
   create a charge? Decides whether the building can secure debt and whether there is any
   residual asset value.
7. What is the physical capacity of 8,500 sq ft? Management projects 540 to 920 students.
8. Confirm the Section 8 status and what instrument can lawfully be offered.
9. Is any 12AB registration or exemption claimed? Tax was paid at about 29% with none claimed,
   which may be an oversight worth several lakh a year — and would lift the value.

## Our own weak points — disclose these before anyone finds them

- Terminal value carries most of the enterprise value. Normal for a growing business, but it
  means the answer leans on long-run assumptions.
- The discount rate is a judgement. Defensible, not objective. That is why the sensitivity grid
  exists, and why the multiple-based methods matter — they contain no discount rate at all.
- The staff cost ramp from 26% to 39% of revenue is an assumption. If staff costs stay at the
  audited 16.5%, value rises materially.
- Case A's student numbers are ours, not management's. Arguable.
- The concluded range is adviser judgement bracketing where the methods cluster, not a
  calculation. (It is currently a MEDIAN formula — see `Part 4`.)


---

# PART 3 — THE WORKBOOK
Live file: `03-valuation/CURRENT-astral-valuation.xlsx`. Seven tabs, in this sheet order:
`Summary`, `Audited Base`, `Assumptions`, `Projections`, `DCF`, `Multiples & NAV`, `Reverse Test`.
(An `Open Questions` tab existed in early versions; the user deleted it. Do not re-add it.)

## How the data flows

```
Audited Base ─┬─> Assumptions ─> Projections ─> DCF ─┬─> Summary
              └─> Multiples & NAV ───────────────────┘
                  Reverse Test (tests the client's ask against Audited Base)
```

One direction only. Nothing downstream is allowed to restate a number from upstream.

## Key cell references

**Audited Base** — the only tab holding source data as typed numbers.

| Cell | |
|---|---|
| `C7` | Revenue 6,090,900 |
| `C13` | Profit before tax (=SUM(C7:C12)) |
| `C15` | Profit after tax |
| `C25` | Adjusted EBITDA (=SUM(C19:C24)) |
| `C32` | Net assets / book equity |
| `C33` | Shares outstanding, 6,000 |
| `C34` | Book value per share |
| `C37` | **Net debt** — referenced by every equity bridge in the workbook |

**Assumptions**

| Cell | |
|---|---|
| `C6` | Fee per student FY26 actual |
| `C7` | Fee inflation |
| `C8` | Tax rate |
| `C9` | **WACC** — reads `='DCF'!$C$15`; every discount in the model points here |
| `C10` | Terminal growth |
| `C11` | Maintenance capex % of revenue |
| `C12`,`C13` | Rent base and growth |
| row 17 | Fee per student by year |
| rows 21,22,23 | Student numbers, Case A / B / C |
| rows 29,30 | Staff cost % and other operating cost % of revenue |
| rows 31,32 | Rent, depreciation |

**Projections** — three stacked case blocks. Free cash flow rows, which everything else pulls:

| Case | FCF row |
|---|---|
| A — organic | **row 22** |
| B — mgmt conservative | **row 41** |
| C — mgmt moderate | **row 60** |

**DCF**

| Cell | |
|---|---|
| `C6`–`C10` | Risk-free, ERP, beta, size/illiquidity premium, company-specific premium |
| `C11` | Cost of equity `=C6+C8*C7+C9+C10` |
| `C12`,`C13` | Pre-tax and after-tax cost of debt |
| `C14` | Target equity weighting |
| `C15` | **WACC** `=C14*C11+(1-C14)*C13` — the source of truth for the rate |
| rows 17–27 | Case A block; EV at `I24`, equity at `I26`, TV% at `I27` |
| rows 29–39 | Case B block; EV `I36`, equity `I38` |
| rows 41–51 | Case C block; EV `I48`, equity `I50` |
| rows 55–60 | Sensitivity grid; column B = applied WACC ± 2-point steps |

**Summary**

| Cell | |
|---|---|
| rows 8–13 | The business today; `C13` is net debt ÷ EBITDA |
| rows 17–22 | Football field; C = low, D = high, E = `AVERAGE(C:D)` |
| `C23`,`D23` | Concluded range, `=MEDIAN(C17:C22)` / `=MEDIAN(D17:D22)` |
| `C24`,`D24` | Client expectation, reads `'Reverse Test'!$C$6` |
| `F24` | `=E24/E23` — his ask as a multiple of our midpoint |
| `G27` | **The raise, ₹2,00,00,000** — drives the whole C column |
| rows 28–32 | Pre-money scenarios; `C=$G$27/($G$27+B)`, `D=1-C`, `F=B/$B$28` |
| `B28` | `=$E$23*100000` — concluded midpoint in rupees |
| `B32` | `=(G27/C32)-G27` — derives the client's real ₹8 Cr pre-money |

**Reverse Test** — `C6` is the ₹10 Cr target, `C8` the required enterprise value
(target + net debt). Rows 13–16 show implied multiples.

## The multiple consistency rule

Match the numerator to the denominator, or the multiple is meaningless.

| Metric | Before or after interest | A multiple of it gives |
|---|---|---|
| Revenue, EBITDA, EBIT | Before | **Enterprise value** → then subtract net debt |
| Profit after tax, book equity | After | **Equity value** directly → do not subtract again |

So `Multiples & NAV` correctly computes `multiple × revenue = EV`, then `− net debt = equity`.
Revenue is earned before the lenders are paid, so it belongs to everyone.

## Editing conventions — follow these exactly

**Edit by direct XML rewrite, never an openpyxl round-trip.** The user works in Excel between
sessions and uploads revised copies; a round-trip risks their formatting. The pattern:

1. Read the xlsx as a zip, map sheet names to `xl/worksheets/sheetN.xml` via `workbook.xml`
   and its rels.
2. For each cell, regex `<c r="REF"((?:\s+[a-zA-Z:]+="[^"]*")*)\s*(?:/>|>.*?</c>)`, keep the
   `s=` style attribute, strip any `t=` for a numeric result, and write
   `<f>FORMULA</f><v>VALUE</v>`.
3. Rezip. Then **verify `styles.xml` is byte-identical** to the source and list which sheet
   parts changed.

Watch for **shared formulas** — `<f t="shared" si="0"/>` carries no formula text. Replace only
the `<v>`, never the `<f>` tag. This caught out one earlier attempt.

**LibreOffice cannot recalculate here** (it times out even on a two-cell file). So compute every
expected value in Python, inject it as a cached `<v>`, set
`<calcPr calcId="0" fullCalcOnLoad="1"/>` in `workbook.xml`, and drop `xl/calcChain.xml` along
with its entries in `[Content_Types].xml` and `workbook.xml.rels`. Always tell the user to open
the file once in Excel to confirm, since we cannot.

**Verify before delivering.** Load the saved file twice — `data_only=True` for values and the
default for formulas — and assert that no formula cell has a `None` cached value.

**Note on `₹`** — ReportLab's core fonts cannot render it; it comes out as a black box. Use
"Rs" in PDFs. It is fine in Excel.


---

# PART 4 — DECISION LOG
Why things are the way they are. Read before reversing any of it.

## Valuation approach

**Built from the audited accounts, not management's spreadsheet.** Their file contains the
defects in `Part 2`, so it is a subject of review rather than a source.

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

**Taking the adviser's fee in equity.** See `Part 1`. Cash.

## Workbook conventions

**No pasted values where a formula belongs.** Adopted after the user caught hardcoded values in
the Reverse Test. Applying it then found two more: the cost-of-equity mismatch, and the two
"implied by the client's expectation" rows disagreeing with each other (one used the equity
target, the other the required enterprise value).

**Edit by XML surgery, preserve formatting.** The user works in Excel between sessions. Every
edit must leave `styles.xml` byte-identical and must preserve their own additions — the `$G$27`
raise cell, the "Justify value x times" column, the row deriving ₹8 Cr pre-money, their written
conclusions, and the deletion of the two Reverse Test routes.


---

# PART 5 — OPEN WORK
Each task below is self-contained. Start a new session and paste the prompt.

---

## BLOCKING — the workbook contradicts itself

Four fixes. Do these before the model is shown to anyone.

> Read `Part 3`. Working on `03-valuation/CURRENT-astral-valuation.xlsx`, by direct
> XML rewrite so formatting and the user's own edits are untouched:
>
> 1. **DCF `C9` to 0.06 and `C10` to 0.04** — size/illiquidity and company-specific premiums.
>    Cost of equity goes to 23.50% and WACC to 18.67%. Refresh every cached value that depends
>    on the rate: all three DCF case blocks, the sensitivity grid, and the Summary football
>    field rows 20–22 plus their mid column.
> 2. **Summary `F23`** still reads "≈ ₹0.45 Cr to ₹2.00 Cr, midpoint ₹1.22 Cr" from an earlier
>    setting. Make it describe the live concluded range, ideally as a formula.
> 3. **Summary `E28`** reads "Promoter loses control" — make it derive from `D28`, e.g.
>    `=IF(D28<0.5,"Promoter loses control",IF(D28<0.6,"Marginal","Workable"))`, so it can never
>    go stale again. `E31` is currently blank; fill it the same way.
> 4. **Reverse Test `D13` and `D14`** divide the ₹10 Cr *equity* target by revenue and EBITDA,
>    which mixes an equity numerator with enterprise denominators. Change both to use `$C$8`,
>    the required enterprise value, giving 18.70x and 50.07x — matching `Multiples & NAV`.
>    `D15` and `D16` are correct as they stand and must not change.
>
> Verify `styles.xml` is byte-identical, no formula cell has a null cached value, and report what
> each number was before and after and which way it moves the valuation. Save as
> `CURRENT-astral-valuation.xlsx`, commit, and tell the user to open it once in Excel.

**Expected after the fix:** Case A ≈ ₹32.7 L, Case B ≈ ₹123.7 L, Case C ≈ ₹208.9 L equity, and
the promoter drops below 50% at the concluded midpoint — which restores the central finding that
₹2 crore cannot be raised as equity without him losing the school.

---

## Reissue the presenter's briefing

Only after the fixes above.

> Read `the top of this file` and `Part 2`. `04-deliverables/Astral_Valuation_Briefing.pdf` was
> built on the pre-fix numbers and carries a fix-list page that is now obsolete. Rebuild it from
> `03-valuation/CURRENT-astral-valuation.xlsx` with the corrected figures, drop the fix-list
> page, and keep everything else — the eight-step meeting flow, the per-tab sections with
> "what's on screen / where the numbers came from / what to say", the hard-questions page and
> the open-items page. Use ReportLab; write "Rs", not the rupee sign.

---

## The findings memo — the first real deliverable

> Read `Part 2` and `Part 1`. Write a client-facing memorandum setting out
> the defects in management's valuation report. For each: the claim, the exact cell or note it
> comes from, the corrected figure, and the effect on value. Order by materiality, and **lead
> with the share-count error because it runs in the client's favour** — it establishes that we
> check things without putting him on the defensive. Close with the nine open questions framed
> as "what could move my number upward". This is what the ₹75,000 buys, so it should look like
> it. PDF.

---

## The debt structure term sheet

> Read `Part 1`. Model and write up the recommended structure: secured NCDs on
> private placement, revenue-linked, with a cap. Size it against the three projection cases with
> tax included, test serviceability year by year, and show investor IRR at a range of revenue-
> share rates and caps. Starting point: ₹85 L–1 Cr, 0.4–0.5% of revenue per ₹10 lakh invested,
> payments beginning FY30, capped at 2.5–3x invested capital, 10-year tenure, company call.
> Include the SportsCo equity piece and the milestone ratchet as the two components alongside.
> Flag clearly what needs a company secretary rather than us.

---

## Resolve the Section 8 question

Not a modelling task — it needs the client and a professional.

> Read `Part 1`. Draft the request to the client for: MCA master-data confirmation
> of the company sub-category against CIN U88900MH2025NPL445351; the certificate of
> incorporation and Section 8 licence; the Memorandum of Association; the land lease agreement;
> the school's recognition certificate; and details of who lent the ₹1.62 crore of unsecured
> borrowings. Explain in one short paragraph each why we need it, without alarming him before
> the facts are in.

---

## Done

- Fee proposal and cost break-up — `05-engagement/Fee_Proposal_Astral_School.xlsx`
- Valuation model built from audited accounts — `03-valuation/`
- All pasted values converted to formulas across the workbook
- Presenter's briefing, pre-fix version — `04-deliverables/`
