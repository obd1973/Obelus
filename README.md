🇮🇹 [Leggi in italiano](README_IT.md)

# Obelus 1.0 — Amazon Invoice Validator

In Italy, invoicing is often one person's job.

Not a department. One person. Usually self-taught, working from memory, learning by trial and error. When they leave, someone new starts from scratch. The webinar exists. The documentation exists. But nobody hands it to the new person on day one.

The result is a quiet, expensive problem. Invoices that are fully SDI-compliant — meeting every government requirement — still get stuck in Amazon's system. Because SDI compliance and Amazon format compliance are two different things, and nobody advertises that gap clearly.

By the time a vendor realizes something is wrong, weeks have passed. Sometimes months. The invoice gets corrected, resubmitted, and fails again on a different rule. Meanwhile a small company is waiting on payment they've already earned.

Obelus was built to close that gap before it opens.

It checks Amazon's specific formatting and routing requirements locally, instantly, before a single invoice is submitted. No IT roadmap. No installation. No data leaving your machine.

It won't replace judgment. But it will tell you exactly what to verify before you find out the hard way.

---

## What It Does

Obelus is a single-file HTML validation engine. Open it in any browser, drop in one or more XML invoice files, and it runs two layers of checks.

### Automated Header Checks

Each check returns a clear status (PASS / FAIL / WARN) with the extracted value and, for any failure, a specific resolution instruction pointing to the exact XML field to fix.

- **Invoice Number** — presence and uniqueness within a batch
- **SDI Recipient Code** (`CodiceDestinatario`) — validated against Amazon's known codes for Retail, Dropship, and Advantage channels
- **PEC Address** — checked against Amazon's registered legal mail address
- **Entity Name** — exact match against the required Amazon EU entity name
- **VAT Number** — country prefix and fiscal code verified against Amazon's Italian VAT registration
- **Document Type** — accepted types: TD01, TD04, TD05, TD24, TD25
- **Total Amount** — presence and numeric validity

### OFA Routing Checks (Credit/Debit Notes — TD04/TD05)

- **Linked Document** (`DatiFattureCollegate`) — checks that the original invoice reference is present, required for OFA auto-clearing
- **Causale Code** — validates the reason code against accepted values (PQV, PPV, QPD)

### Batch-Level Checks (Multi-file mode)

- **Duplicate Invoice Numbers** — flags any invoice number appearing more than once in the batch
- **Amount Matching** — pairs each TD04/TD05 with its original invoice and verifies the totals match

### Line-Item Analysis

For every line in the invoice the tool extracts and displays:

- **Description** — the line item description from `<Descrizione>`
- **ASIN / EAN / Product Code** — extracted from `<CodiceArticolo>`, with code type shown (ASIN, EAN, etc.)
- **PO Reference** — extracted from `<DatiOrdineAcquisto>` at document level and from line-level product codes where present
- **VAT Rate** — from `<AliquotaIVA>`
- **Discount** — from `<ScontoMaggiorazione>`, percentage or amount

### Manual Verification Panel

Because the tool cannot access Vendor Central, two things always require a human check. After validation the tool surfaces these explicitly in a dedicated panel — not buried in the results:

- **Purchase Order(s) found** — the PO numbers extracted from the XML, with an instruction to confirm they are open and correct in Vendor Central before submitting
- **ASIN / EAN codes found** — all product codes extracted from the XML, with an instruction to cross-check each against the active catalog in Vendor Central

The tool shows you what it found. You confirm it is right.

---

## What It Does Not Do

Obelus validates Amazon's formatting and routing requirements. It does not perform deep SDI schema validation (XSD compliance, digital signature verification, or transmission envelope checks). Those are handled by the SDI system itself and by compliant invoicing software upstream.

---

## Validation History

Every invoice checked is automatically logged to a local history. Click the **History** button in the header to view a timestamped record of all validations on this machine, including invoice number, document type, PO numbers, ASIN/EAN codes, and overall result.

The history can be exported as a CSV at any time and cleared on demand. It is stored in browser localStorage — tied to the current browser on the current machine, not shared or transmitted anywhere.

---

## CSV Export

The export produces a structured matrix designed to serve four purposes at once:

1. **Quick review** — overall and per-check status at a glance
2. **Error location** — each check has its own column pair, so failures are isolated, not mixed into a single comment field
3. **Resolution guidance** — a dedicated Resolution column sits next to each failed check with a specific instruction on what to fix and where in the XML
4. **Ticket creation** — the file can be shared directly with IT or an Amazon contact as a self-contained fault report

The column structure is:

| Block | Columns |
|-------|---------|
| Fixed metadata | Checked At · File · Invoice # · DocType · Total Amount · Linked To · PO Number(s) · ASIN/EAN(s) · Header Status · Overall Status |
| Per check (repeated for each check) | `[Check] — Status` · `[Check] — Detail` · `[Check] — Resolution` |

Status cells contain PASS, FAIL, WARN, or NA. Resolution cells are populated only on FAIL or WARN. The file is UTF-8 with BOM for correct rendering in Excel.

Export is available from both single-invoice view and batch view.

---

## How to Use It

1. Download `Obelus1.0.html`
2. Open it in any modern browser (Chrome, Firefox, Edge, Safari)
3. Drag and drop one or more `.xml` invoice files onto the upload zone
4. Review results — header checks with resolution hints, line-item breakdown, and the manual verification panel
5. Export a CSV to file, share with a colleague, or attach to a support ticket

No server. No upload. No account. Everything runs locally in your browser.

---

## Supported Document Types

| Code | Type |
|------|------|
| TD01 | Standard invoice |
| TD04 | Credit note |
| TD05 | Debit note |
| TD24 | Deferred invoice |
| TD25 | Deferred credit note |

---

## SDI Recipient Codes

| Code | Channel |
|------|---------|
| `XR6XN0E` | Retail |
| `ERI9GSW` | Dropship |
| `ZDHP2W8` | Advantage |

---

## Privacy

All processing happens in your browser. No invoice data is transmitted, stored remotely, or logged anywhere outside your machine. The file never leaves your device.

---

## Requirements

Any modern browser. No installation. No dependencies. No internet connection required.

---

## License

Provided as-is for internal vendor use. Not affiliated with or endorsed by Amazon.
