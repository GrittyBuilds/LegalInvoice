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
- Multiple matters per client, each with its own file number and default rate.
- Per-client discount profile: **None**, **Flat %**, or **Tiered** prompt-payment.

**Tiered / variable discounts**
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

**Invoices** — pick a client, one or more matters, and the unbilled entries to
include. Printable (browser Print → *Save as PDF*), with:
- Separate **Hourly Fees**, **Fixed Fees**, and **Expenses** sections + subtotals.
- Prompt-payment discount schedule, prior balance, payments, and balance due.
- **Apply Trust** to draw the client's trust/IOLTA balance against the invoice.

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
