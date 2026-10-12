# Astral School valuation — project memory

Independent valuation and fundraising advisory for **Astral School**, Nagre Nagar, Nashik,
run under **Excelerate Learning Foundation**, CIN `U88900MH2025NPL445351`.
The client wants to raise **₹2 crore** by selling a stake. The adviser (the user) is retained
to produce an independent valuation and then place the stake with investors.

**This file is loaded in every session. Read only the one doc your task needs — see Task routing.**

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
   inject them as cached `<v>` values, and set `fullCalcOnLoad`. See `docs/MODEL-MAP.md`.
6. **Flag, don't fix silently.** When a number moves, say which direction and who it favours.

---

## File map

```
00-source/          client documents, untouched
03-valuation/       CURRENT-astral-valuation.xlsx  <- the live model
                    (older versions kept for history)
04-deliverables/    Astral_Valuation_Briefing.pdf  <- presenter's briefing
05-engagement/      Fee_Proposal_Astral_School.xlsx
docs/               ENGAGEMENT.md, FINDINGS.md, MODEL-MAP.md, DECISIONS.md, TASKS.md
```

Branch: `claude/friendly-lamport-fmzemh`. Commit as work completes; push only when asked.

## Task routing — read only what you need

| If the task is about | Read |
|---|---|
| The deal, the client, our fee, the Section 8 problem | `docs/ENGAGEMENT.md` |
| Defects in the client's report, open questions for management | `docs/FINDINGS.md` |
| Editing the workbook, cell references, formula conventions | `docs/MODEL-MAP.md` |
| Why something was decided the way it was | `docs/DECISIONS.md` |
| What to do next | `docs/TASKS.md` |

## State as of the last session

The live workbook has both risk premiums set to **0%**, giving a 13.50% cost of equity and an
11.67% WACC. That is a listed-company rate for an unlisted single school, and at it the central
finding reverses — the promoter appears to keep a majority. **Four fixes are outstanding and are
listed at the top of `docs/TASKS.md`.** Do not present the model until they are done.
