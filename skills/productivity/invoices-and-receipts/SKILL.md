---
name: invoices-and-receipts
category: productivity
description: Generate invoices and receipts as markdown/HTML/PDF. Accepts minimal input, uses placeholders, iterates.
trigger: user asks for an invoice, receipt, bill, estimate, or payment request
---

# Invoices and Receipts

## Approach

1. Ask only for format preference (markdown, HTML, PDF, docx).
2. Accept whatever info the user provides. Fill gaps with clear `[bracketed placeholders]`. Do NOT demand all fields upfront.
3. Draft the document immediately with defaults:
   - Invoice number: INV-001 (increment on reuse)
   - Date: today
   - Due date: include only if user provides or requests it
   - Tax: 0% unless specified
   - Payment terms: "Payment is due within 30 days"
4. Present the summary of what's filled and what still needs info. Iterate on user corrections.

## File Delivery (CLI / Termux / Mobile)

On Termux (Android), `$HOME` resolves to a deep AppData path that is NOT navigable from the phone's file manager. After writing the invoice:
1. Copy the file to `/sdcard/Download/` (or `/sdcard/Documents/`): `cp ~/invoice.md /sdcard/Download/invoice.md`
2. The user can then open it from their Downloads app and use the system Share button to send to email, Discord, cloud storage, etc.
3. Always tell the user the file is saved in Downloads so they can find it without navigating Termux paths.

If email delivery is requested, check `which himalaya` and `himalaya account list` -- it requires SMTP credentials to be pre-configured. Without it, the Downloads + Share button approach is the fallback.

## Pitfalls

- Don't present a numbered list of 10 required fields and wait -- users will time out or give partial data. Ask format, accept what they give, draft with placeholders.
- On Termux, `$HOME/invoice.md` is invisible to the phone's file manager. Always copy to `/sdcard/Download/` and tell user to check Downloads.
- Default to a clean single-line-item layout. Only add multi-row tables when the user has multiple services.
- Avoid clutter: no unnecessary fields (due date, PO number, reference codes) unless the user adds them.

## Verification

- Subtotal matches the sum of (qty x unit_price) for all line items.
- TOTAL DUE = Subtotal + Tax - Discount.
- No remaining `$0.00` placeholders in final amounts (but OK for missing contact fields).

## Templates

See `templates/invoice.md` for the base markdown invoice skeleton. Copy and fill or use `write` tool directly.
