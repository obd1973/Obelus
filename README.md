# Obelus (ὀβελός) 🛡️
**Tactical Validation Utility for Italian SDI Invoicing**

## 🇮🇹 Mission
Navigating the Italian **Sistema di Interscambio (SDI)** can be a significant administrative burden for vendors. **Obelus** is an independent, open-source utility designed to help suppliers validate their invoicing metadata against public requirements before submission. 

Our goal is to reduce the "bounce rate" of electronic invoices by catching common formatting and recipient-code errors locally and privately.

## 📌 Overview
Obelus is a lightweight "no-install" engine. It is specifically tuned for vendors submitting invoices to major digital marketplaces in Italy (such as Amazon) that require precise **Codice Destinatario** (recipient code) and **Factoring** assignment logic.

## 🚀 Key Features
- **Privacy-First:** Your data never leaves your machine. All logic is executed locally in your browser.
- **SDI Validation:** Verifies the 7-character recipient code and Italian VAT formatting.
- **Factoring Support:** Identifies "Assignment of Credit" markers to ensure correct routing.
- **Zero-Install:** A single `.html` file that runs in Chrome, Edge, or Safari.

## 🛠️ How to Use
1. Download the `obelus.html` file.
2. Open it in any modern web browser.
3. Paste the invoice data you wish to check.
4. Review the validation report for any CTI (Category/Type/Item) routing suggestions.

## ⚖️ License & Disclaimer
Distributed under the **MIT License**. 
*Note: This is an independent project and is not affiliated with, endorsed by, or an official product of any retail platform mentioned. Use of this tool does not guarantee invoice acceptance by the SDI or the recipient.*

---
**Maintained by [Your Name]**
