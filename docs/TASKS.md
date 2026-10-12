# Open work

Each task below is self-contained. Start a new session, paste the prompt, and the session will
pick up `CLAUDE.md` automatically and read only the doc it needs.

---

## BLOCKING — the workbook contradicts itself

Four fixes. Do these before the model is shown to anyone.

> Read `docs/MODEL-MAP.md`. Working on `03-valuation/CURRENT-astral-valuation.xlsx`, by direct
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

> Read `CLAUDE.md` and `docs/FINDINGS.md`. `04-deliverables/Astral_Valuation_Briefing.pdf` was
> built on the pre-fix numbers and carries a fix-list page that is now obsolete. Rebuild it from
> `03-valuation/CURRENT-astral-valuation.xlsx` with the corrected figures, drop the fix-list
> page, and keep everything else — the eight-step meeting flow, the per-tab sections with
> "what's on screen / where the numbers came from / what to say", the hard-questions page and
> the open-items page. Use ReportLab; write "Rs", not the rupee sign.

---

## The findings memo — the first real deliverable

> Read `docs/FINDINGS.md` and `docs/ENGAGEMENT.md`. Write a client-facing memorandum setting out
> the defects in management's valuation report. For each: the claim, the exact cell or note it
> comes from, the corrected figure, and the effect on value. Order by materiality, and **lead
> with the share-count error because it runs in the client's favour** — it establishes that we
> check things without putting him on the defensive. Close with the nine open questions framed
> as "what could move my number upward". This is what the ₹75,000 buys, so it should look like
> it. PDF.

---

## The debt structure term sheet

> Read `docs/ENGAGEMENT.md`. Model and write up the recommended structure: secured NCDs on
> private placement, revenue-linked, with a cap. Size it against the three projection cases with
> tax included, test serviceability year by year, and show investor IRR at a range of revenue-
> share rates and caps. Starting point: ₹85 L–1 Cr, 0.4–0.5% of revenue per ₹10 lakh invested,
> payments beginning FY30, capped at 2.5–3x invested capital, 10-year tenure, company call.
> Include the SportsCo equity piece and the milestone ratchet as the two components alongside.
> Flag clearly what needs a company secretary rather than us.

---

## Resolve the Section 8 question

Not a modelling task — it needs the client and a professional.

> Read `docs/ENGAGEMENT.md`. Draft the request to the client for: MCA master-data confirmation
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
