# Obelus

In Italy, invoicing is often one person's job.

Not a department. One person. Usually self-taught, working from memory, learning by trial and error. When they leave, someone new starts from scratch. The webinar exists. The documentation exists. But nobody hands it to the new person on day one.

The result is a quiet, expensive problem. Invoices that are fully SDI-compliant — meeting every government requirement — still get stuck in Amazon's system. Because SDI compliance and Amazon format compliance are two different things, and nobody advertises that gap clearly.

By the time a vendor realizes something is wrong, weeks have passed. Sometimes months. The invoice gets corrected, resubmitted, and fails again on a different rule. Meanwhile a small company is waiting on payment they've already earned.

I couldn't find a tool that checked Amazon's specific requirements before submission. So I built one.

---

## What Obelus does

You open it in a browser. You drop in your XML invoice files. It tells you what's wrong before you find out the hard way.

No installation. No server. No account. No data leaving your machine. One HTML file that runs locally, immediately, on anything.

It runs two layers of checks.

**Header checks** — the things Amazon's system will reject without telling you why. Recipient codes, entity names, VAT numbers, document types. Each one returns a clear PASS, FAIL, or WARN with the exact field to fix if something's wrong.

**OFA routing checks** — for credit and debit notes (TD04/TD05), it checks that the original invoice reference is present and that the reason code is one Amazon actually accepts. Without these, auto-clearing won't happen.

**Batch checks** — when you drop in multiple files at once, it flags duplicate invoice numbers and verifies that credit/debit note amounts match their originals.

**Line-item analysis** — for every line it extracts the description, ASIN or EAN, PO reference, VAT rate, and any discounts. Not to validate them — it can't check Vendor Central — but to surface them clearly so you can.

---

## The part it can't do

Obelus can't access Vendor Central. So two things always need a human check: whether the PO numbers are open and correct, and whether the product codes match your active catalog.

After every validation, the tool surfaces these explicitly in their own panel. Not buried. Front and center. It shows you what it found. You confirm it's right.

---

## What it doesn't replace

Obelus validates Amazon's formatting and routing requirements. It doesn't do deep SDI schema validation — XSD compliance, digital signature verification, transmission envelope checks. That's handled upstream by your invoicing software and by the SDI system itself.

---

## History and export

Every invoice checked is logged locally — timestamped, with invoice number, document type, PO numbers, ASIN/EAN codes, and result. You can view it, export it as CSV, or clear it. It lives in your browser's localStorage, on your machine, not anywhere else.

The CSV is structured to be useful beyond your own review. Each check has its own column with its own resolution instruction. If something fails and you need to hand it to IT or raise it with Amazon, the file works as a self-contained fault report without any extra formatting.

---

## How to use it

1. Download `Obelus1.0.html`
2. Open it in any modern browser
3. Drop in one or more `.xml` invoice files
4. Review the results
5. Export CSV if you need a record or need to share it

That's it.

---

## Supported document types

| Code | Type |
|------|------|
| TD01 | Standard invoice |
| TD04 | Credit note |
| TD05 | Debit note |
| TD24 | Deferred invoice |
| TD25 | Deferred credit note |

---

## SDI recipient codes

| Code | Channel |
|------|---------|
| XR6XN0E | Retail |
| ERI9GSW | Dropship |
| ZDHP2W8 | Advantage |

---

## Privacy

Everything runs in your browser. No invoice data is transmitted, stored remotely, or logged outside your machine. The file never leaves your device.

---

## Requirements

Any modern browser. No installation. No dependencies. No internet connection required.

---

*Provided as-is for internal vendor use. Not affiliated with or endorsed by Amazon.*
