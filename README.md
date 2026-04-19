# Obelus (ὀβελός) 🛡️
**Tactical SDI Invoice Validator for Amazon Vendors**

## Why this exists

In Italy, invoicing is often one person's job.

Not a department. One person. Usually self-taught, working from memory, learning by trial and error. When they leave, someone new starts from scratch. The webinar exists. The documentation exists. But nobody hands it to the new person on day one.

The result is a quiet, expensive problem. Invoices that are fully SDI-compliant — meeting every government requirement — still get stuck in Amazon's system. Because SDI compliance and Amazon format compliance are two different things, and nobody advertises that gap clearly.

By the time a vendor realizes something is wrong, weeks have passed. Sometimes months. The invoice gets corrected, resubmitted, and fails again on a different rule. Meanwhile a small company is waiting on payment they've already earned.

Obelus was built to close that gap before it opens.

It checks both SDI requirements and Amazon's specific formatting rules locally, instantly, before a single invoice is submitted. No IT roadmap. No installation. No data leaving your machine.

It won't replace judgment. But it will tell you what to check before you find out the hard way.

---

## What it does

Obelus is a single-file HTML validation engine. You open it in a browser, drop in an XML invoice file, and it runs two types of checks:

**Automated checks** — things the tool can verify directly from the XML:
- Amazon entity name exact match
- Amazon VAT number
- SDI recipient code validity (Retail, Dropship, Advantage)
- Document type detection and structural routing rules
- Purchase Order presence and correct XML placement
- Line item scan for misplaced PO references
- Zero-value informational line detection

**Manual verification prompts** — things that require a human check against Vendor Central:
- Purchase Order number extracted and flagged for confirmation
- Full item list with ASIN/EAN codes and quantities for cross-reference

The tool surfaces all issues at once, not one at a time. That matters. Finding errors sequentially can add weeks to a resolution. Obelus shows the full picture in one pass.

---

## How to use it

1. Download `Obelus0_1.html`
2. Open it in Chrome or Edge
3. Drop your XML invoice file into the upload zone
4. Review automated checks on the left and manual verification prompts on the right

No installation. No account. No internet connection required.

---

## Privacy & data handling

All validation logic runs entirely in your browser. Your invoice file is never uploaded, transmitted, or stored anywhere outside your local machine.

The only data stored locally is a usage counter saved in your browser's localStorage. This counter tracks how many invoices you have validated and triggers a feedback prompt at 10 and 50 validations. It contains no invoice data. You can clear it at any time by clearing your browser's site data.

---

## What it cannot check

Two things require human verification and cannot be validated locally:

- **Purchase Order validity** — whether the PO exists, is open, and matches the invoice amount in Vendor Central
- **ASIN/EAN accuracy** — whether the item codes and quantities match what Amazon expects on that specific order

Obelus extracts both and presents them clearly for manual review. It tells you what to look at. The verification itself is yours.

---

## Limitations

Obelus is a heuristic tool, not a compliance guarantee. It validates against known Amazon formatting requirements and SDI structural rules as documented in Amazon's vendor guidance. Rules change. If you encounter a rejection that Obelus did not flag, please report it — that is how the logic improves.

This tool is not affiliated with or endorsed by Amazon.

---

## License

MIT License. Free to use, modify, and distribute. If you find it useful, feedback is welcome on [LinkedIn](https://www.linkedin.com/in/oscar-b-43572422/).

---

## Contributing

If you work with Italian Amazon vendors and encounter validation patterns not covered here, open an issue or submit a pull request. The more edge cases the logic handles, the more useful it becomes for everyone.


---
**Maintained by [Oscar Bares]**
