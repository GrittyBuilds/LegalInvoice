# Legal Billing &amp; Trust Manager

A single-file, **locally-stored** (no server, no internet required) web app for a
Michigan legal practice. Open `index.html` in any modern browser — all data is
saved in that browser's `localStorage`. Nothing is transmitted anywhere.

> Built with the Michigan Rules of Professional Conduct in mind — itemized,
> reasonable fees (**MRPC 1.5**) and safekeeping of client funds in a client
> trust / IOLTA account (**MRPC 1.15**). It is billing software, not legal advice;
> confirm your own compliance.

## How to run

Double-click `index.html` (or drag it into a browser). That's it. To move it to
another machine, copy the file and use **Firm Settings → Export backup** to carry
your data over.

## What it does

**Clients &amp; Matters**
- Multiple matters per client, each with its own **auto-assigned file number** and
  default rate. Clients and matters can be **deleted** when they have no financial
  history (invoices/payments/trust).
- **Per-matter discount profile**: **None**, **Flat %**, or **Tiered** — set on each
  matter. A single invoice spanning several matters applies each matter's own
  discount and aggregates them.

**Tiered / variable discounts** (configured per matter)
- Each tier has a percent, a condition, and a deadline computed from the invoice:
  - *within N days of the invoice*, or
  - *by the end of the invoice month*.
- Applies to **hourly fees only** (default) or **all fees**.
- The invoice prints every tier with its deadline and resulting total.
- **Override** (per invoice, from the invoice screen → *Discount options*):
  - Automatic (best in-deadline tier), force a specific tier, a custom %, or none.
  - **Extend eligibility** keeps a discount available after its deadline — for
    when the firm chooses to honor it anyway.
- The customizable *"Paid in full"* note prints on the invoice.

**Time &amp; Fees** — three entry types kept in separate invoice sections:
- **Hourly** — date, timekeeper, description, hours × rate.
  - **No Charge** flag: the entry still prints in the Hourly Fees section, marked
    *No Charge* with a **customizable note**, and is excluded from the total.
- **Fixed Fee** — flat-amount services.
- **Out-of-Pocket Expenses** — costs advanced.
- **Save &amp; New / Save &amp; Duplicate** for fast repeat entry, and **description
  templates** (managed in Firm Settings) inserted from the entry form.

**Invoices** — one invoice per client covering **all of that client's matters by
default** (uncheck any to leave off). Printable (browser Print → *Save as PDF*),
styled to the **CM Advisory Corp brand** (emerald/gold, Poppins, brand lockup
masthead), with:
- A **Current Charges / Previous Balance / Total Balance Due** summary band — every
  invoice shows the client's full **running balance owed**, and itemizes the prior
  outstanding invoices that make up the previous balance. The **previous balance is
  a snapshot captured as of the invoice date** and frozen, so reprinting an old
  invoice shows what was owed then (later payments don't change it).
- When a client has several matters, line items are **grouped by matter**, each with
  its own Hourly/Fixed/Expense sub-sections and a matter subtotal.
- Separate **Hourly Fees**, **Fixed Fees**, and **Expenses** sections + subtotals.
- A **Payments & Credits Applied** section and a detachable **remittance stub**.
- Variable / tiered **discount** schedule (applied to hourly fees) with per-invoice
  override, and **Apply Trust** to draw the client's trust/IOLTA balance.

**Drafts & write-downs** — new invoices start as **drafts** (excluded from A/R).
While a draft you can add/remove lines, **write down** individual lines to a lower
billed amount, and apply an invoice-level adjustment; then **Finalize & Issue** to
lock it and make it a receivable. Issued-but-unpaid invoices can be reopened as
drafts. Printed drafts carry a “DRAFT — NOT YET ISSUED” banner.

**Reports** — **A/R aging** (Current / 1–30 / 31–60 / 61–90 / 90+ per client),
**collections & revenue** for this month / year / all-time (billed, cash collected,
credit memos, refunds; revenue by client), one-click **payment reminders**, and
**CSV export** of invoices, payments, and time. **Finance charges** on past-due
balances can be assessed here when enabled in Firm Settings.

**Recurring & batch billing** — define fixed **monthly recurring charges** (Firm
Settings) and post them each month with one action; **batch-invoice** every client
with unbilled work into drafts in a single pass.

**More billing controls** — configurable **payment terms** (Due on receipt / Net
15/30/45/60, per client or firm default), an optional **sales tax** line, **expense
markup**, **credit memos & refunds**, and an offer to **auto-apply available trust**
when an invoice is issued.

**Payments** — a dedicated section to **apply payments** to a client's account:
- Record a payment (client, date, amount, method, reference) and **allocate it
  across one or more open invoices** — manually or *auto-apply to oldest*.
- Any unallocated amount is held as an **unapplied credit** on the client's
  account and can be applied to invoices later.
- Payment history with applied/unapplied amounts; invoices and statements show
  the payments applied to them.

**Retainers &amp; Trust**
- Printable **Retainer Requests**; mark one *funded* to auto-post a trust deposit.
- **Trust ledger** per client (deposits, applications to invoices, refunds,
  adjustments) with running balances.

**Statements of Account** — per-client roll-up of all invoices, payments,
balances, and current trust balance. Printable.

**Firm Settings** — firm identity, bar number, trust-account details, invoice/
retainer numbering, default terms, timekeepers &amp; rates, and JSON
**export/import backup**.

## Data &amp; backups

Everything lives in `localStorage` under the key `legalBilling.v1`. Clearing the
browser's site data erases it, so **export a JSON backup regularly**
(Firm Settings → *Export backup*). Import restores from that file.
