# Obelus Toolkit

In Italy, invoicing is often one person's job.

Not a department. One person. Usually self-taught, working from memory, learning by trial and error. When they leave, someone new starts from scratch. The webinar exists. The documentation exists. But nobody hands it to the new person on day one.

The result is a quiet, expensive problem. Invoices that are fully SDI-compliant — meeting every government requirement — still get stuck in Amazon's system. Because SDI compliance and Amazon format compliance are two different things, and nobody advertises that gap clearly.

By the time a vendor realizes something is wrong, weeks have passed. Sometimes months. The invoice gets corrected, resubmitted, and fails again on a different rule. Meanwhile, a small company is waiting on payment they've already earned.

I couldn't find a solution that bridged the gap between Amazon's robotic rules and the vendor's human workflow. So I built one.

Obelus is no longer just a validator. It is a complete, four-part self-service ecosystem designed to diagnose errors, teach the rules, and provide flawless examples — all locally, in your browser.

---

## The Toolkit

The Obelus ecosystem is built on four components working together:

### 1. Obelus Validator (`Obelusv1.8XL.html`)
The core diagnostic engine. You open it in a browser and drop in your XML files. It runs a strict suite of Amazon-specific compliance checks (Routing codes, Entity names, VAT numbers, Document types, and Credit/Debit Note OFA matching). It tells you exactly what is wrong, which line in the XML failed, and how to fix it before you submit to SDI.

### 2. Obelus Mentor (`ObelusMentor1.2.html`)
The "Rosetta Stone." When the Validator flags an error, it links directly to Mentor. Mentor explains *why* the rule exists in plain English (and Italian). Crucially, it includes a **Software Locator** that translates raw XML tags into the actual field names used by popular Italian invoicing software (e.g., "Look for *Codice Univoco* in your *Anagrafica Clienti*"). It even provides copy-paste scripts vendors can send to their software's helpdesk.

### 3. Annotated XML Templates
Instructional blueprints. These are perfectly structured XML files containing explicit instructions, warnings, and checklists. They exist to be read and studied, showing exactly where Amazon's required constants must go.

### 4. The Golden Dummy (`Golden_Example_100_Percent_Pass.xml`)
A functional prototype. This is a pristine XML file filled with fake company data that is guaranteed to pass Obelus with 100% green checks. Vendors can use it to build trust in the Validator and compare it side-by-side with their broken files to visually spot the differences.

---

## Why It Works

* **Zero Dependencies:** No installation. No server. No account. Just download the HTML files and open them. They run instantly on any machine.
* **Total Privacy:** Everything runs locally using JavaScript and your browser's `localStorage`. Your financial data never leaves your device.
* **Fix-It Reports:** The Validator exports a highly actionable CSV report. It acts as a self-contained fault report with clear resolution instructions, perfect for handing off to an IT department or software vendor.
* **Batch Processing:** Drop 50 invoices in at once. Obelus cross-references them to flag duplicate invoice numbers and verifies that credit/debit note amounts precisely match their original linked invoices.

---

## The Part It Can't Do

Obelus cannot access Vendor Central. Therefore, two things always require a human check:
1.  **Purchase Orders:** Are the PO numbers open and correct?
2.  **Product Codes:** Do the ASIN/EAN codes match your active catalog?

After every validation, the tool surfaces these elements explicitly in their own panel. Not buried. Front and center. It extracts them so you can confirm them.

---

## What It Doesn't Replace

Obelus validates Amazon's specific formatting and routing requirements. It does not do deep SDI schema validation (XSD compliance, digital signature verification, or transmission envelope checks). That is handled upstream by your invoicing software and the SDI system itself.

---

## How to Use It

1.  Download the complete Obelus folder.
2.  Open `Obelusv1.8XL.html` in any modern browser.
3.  Drag and drop your generated `.xml` invoice files.
4.  Review the results. If an error is flagged, click the **"📖 Learn more in Mentor"** link to see how to fix it in your software.
5.  Export the CSV report if you need a record.

That's it.

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
| XR6XN0E | Retail |
| ERI9GSW | Dropship |
| ZDHP2W8 | Advantage |

---

*Provided as-is for internal vendor use. Not affiliated with or endorsed by Amazon.*
