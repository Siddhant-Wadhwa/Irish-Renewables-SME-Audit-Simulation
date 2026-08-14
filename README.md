# Irish Renewables — End-to-End SME Audit Simulation

A full-cycle simulated external audit of a fictional Irish SME (a solar equipment
distributor/installer), built entirely in Xero and then audited using standard substantive
testing procedures. This project simulates both sides of the engagement: building a realistic
set of client books (including deliberately planted errors), then performing the audit that
would be expected to catch them.

## Why this project

Most student audit portfolio pieces analyse a company's *published* financials after the fact.
This project instead builds the underlying transaction-level data from scratch — invoices,
bills, bank statement, payroll, VAT — so the audit testing is performed against a real general
ledger rather than summary figures, the same way a first-year audit associate's fieldwork
actually works.

## What's in this repo

| File | Description |
|---|---|
| `Irish_Renewables_Audit_Working_Papers.xlsx` | Full working papers: materiality, revenue/cut-off testing, bank reconciliation testing, expense/duplicate testing, VAT testing, fixed asset & grant testing, a 13-item findings register, 7 adjusting journal entries, and a fully cross-checked before/after P&L and Balance Sheet bridge |
| `Irish_Renewables_Audit_Summary_Memo.docx` | Client-ready summary memorandum — every finding, basis for judgment, journals, and the final audited financial position |
| `Irish_Renewables_Transaction_Population.xlsx` | The original transaction design source — every planted error, cross-referenced by customer/supplier and amount |
| `Unaudited Financial Statements(Xero)/` | Trial Balance, P&L, Balance Sheet, and Sales Tax Report as originally exported, before any audit adjustments |
| `Audited Financial Statements(Xero)/` | The same four reports, re-exported after all adjusting journals, credit notes, and invoice corrections were posted |
| `source_data/` | `SalesInvoices.csv` and `Bills.csv` — the transaction-level population used for sampling and testing |
| `evidence/` | Curated Xero screenshots — duplicate detection, posted journals, corrected invoices, and cut-off fixes |

## Company profile

**Irish Renewables** — a solar panel/battery distributor and installer operating in Ireland,
FYE 31 December 2025, EUR reporting currency. 30 sales invoices (residential and commercial),
29 supplier bills (including one German EU supplier under reverse-charge VAT), a December 2025
bank statement, an SEAI capital grant, and two capitalised fixed assets (a van and tools)
acquired late in the year.

## Build process

1. Xero trial organisation set up with Irish VAT rates (0% / 23%), full chart of accounts, and
   44 contacts.
2. 30 sales invoices and 29 supplier bills entered and approved, with several errors
   deliberately planted (see Findings below).
3. Payroll recorded as a lump-sum general ledger entry (Xero's payroll module wasn't available
   on the trial license).
4. Fixed asset depreciation calculated and posted via manual journal rather than Xero's native
   Fixed Assets register (which would not accept a 2025 start date on a newly created trial
   org).
5. December 2025 bank statement imported and reconciled against the ledger.
6. Unaudited Trial Balance, P&L, Balance Sheet, and Sales Tax Report exported as the audit's
   starting point.

## Audit approach

Testing followed a standard substantive audit program:

- **Materiality** — set at 5% of Net Profit before tax (€16,417 overall / €12,313 performance /
  €821 clearly trivial).
- **Revenue & cut-off testing** — risk-based sampling of the invoice population, including
  every invoice over €30,000 and every invoice within 10 days of year end.
- **Bank reconciliation testing** — full reconciliation of the December statement, with two
  items requiring investigation.
- **Expense & duplicate testing** — full population scan of the bills export for duplicate
  entries and misclassifications.
- **VAT testing** — recomputed output/input VAT independently from the transaction populations
  and tied out to the Sales Tax control account.
- **Fixed asset & grant testing** — recomputed depreciation independently and assessed the
  grant's accounting treatment against IAS 20 / FRS 102.
- **Source cross-check** — after the audit's first pass was complete, the original transaction
  design source was cross-referenced against the real Xero data by customer name and amount
  (not by invoice number, which had shifted due to a data-entry gap). This caught two further
  material findings the first pass had missed.

## Findings

Fourteen findings were identified across the full engagement, ranging from control-level
duplicates to two material items (each individually exceeding overall materiality) that only
surfaced on a second pass. Findings that would normally require client inquiry were resolved
using standard auditor judgment, since this is a simulated solo engagement with no actual client
to consult — the basis for each judgment call is documented in both the working papers
(Findings Register tab) and the summary memo.

| Ref | Finding | Amount | Resolution |
|---|---|---|---|
| F01 | SEAI capital grant recognised in full rather than deferred | €19,333 | Deferred over remaining asset life |
| F02 | Duplicate bank transfer to a supplier | €12,054 | Correctly isolated as a recoverable balance |
| F03 | Duplicate supplier bill entered twice | €22,600 | Voided — real COGS/VAT effect corrected |
| F04 | Two invoices with VAT rates inconsistent with the population | €3,220 net | Corrected via direct invoice edit |
| F05 | Subsequent credit note relating to a pre-year-end sale | €5,000 | Pulled into the audit period |
| F06 | Fixed asset depreciation not posted for FY2025 | €966.66 | Adjusting journal posted |
| F07 | Capital purchase (laptop) misclassified as an expense | €1,800 | Adjusting journal posted |
| F08 | Trial Balance/Balance Sheet pre-dated bank reconciliation activity | n/a | Closed on re-export |
| F10 | Bank charge posted directly during original reconciliation | €45 | Resolved — posted at time of discovery |
| F13 | Revenue recognised before work was actually completed | €50,500 | Deferred via two credit notes |
| F14 | Missing completion certificate on a material invoice | €22,400 | No adjustment — corroborated by partial cash receipt |
| F15 | Reclassified laptop never had depreciation charged | €100 | Adjusting journal posted |
| F16 | EU reverse-charge VAT not self-accounted | n/a | Disclosure only — net-nil effect |
| F17 | Outstanding cheque, not yet cleared at year end | €4,182 | Informational — genuine timing difference, no action |

## Result

Final audited Net Profit is **€270,482.01**, down from an unaudited €328,347.00 — a 17.6%
decrease once all 14 findings are resolved. Net Assets ties exactly to Net Profit throughout,
confirming the final position is mathematically balanced and internally consistent.

Two things worth calling out from how this played out in practice:

- **A projection that missed something real.** After the first 8 findings were resolved, an
  interim projection of the audited position came in noticeably off the true re-exported
  figures. The gap was fully explained by two effects that hadn't been modelled: voiding an
  unpaid duplicate bill turned out to have a real P&L and VAT effect (it had already posted on
  an accrual basis, regardless of payment status), and the original "unaudited" baseline was
  itself stale, missing several genuinely-recorded transactions that only surfaced once the
  books were fully reconciled.
- **A second pass that found material items the first pass missed.** Cross-referencing the
  completed audit against the original transaction design (by customer and amount, since
  invoice numbers had shifted due to a data-entry gap) surfaced two findings — F13 and F14 —
  each individually larger than overall materiality. Both are now fully resolved. This is
  documented rather than smoothed over, since catching your own gaps is a normal and valuable
  part of real audit work.

Independently verified against a private answer key of officially planted errors: **12 of 12**
were caught and correctly treated across the full engagement.

## Limitations

- Payroll was recorded as a lump-sum general ledger entry (gross wages + employer PRSI) rather
  than run through Xero's payroll module, since it wasn't available on the trial license.
- Fixed asset depreciation for the van and tools was calculated and posted via manual journal
  rather than Xero's native Fixed Assets register, since that register would not accept a 2025
  start date on the newly created trial org.
- This is a simulated solo engagement — findings that would ordinarily be resolved through
  client inquiry were instead resolved using documented auditor judgment (see the Findings
  Register for the basis of each).
- Two findings (F13, F14) were identified on a second pass rather than the first — a real
  reminder that even a complete-feeling audit benefits from an independent cross-check.
