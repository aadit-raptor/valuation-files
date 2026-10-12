# Workbook map and editing conventions

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
