# Findings against management's valuation report

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
of annual net income plus an exit. See `docs/ENGAGEMENT.md` — if the Section 8 reading is right,
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
  calculation. (It is currently a MEDIAN formula — see `docs/DECISIONS.md`.)
