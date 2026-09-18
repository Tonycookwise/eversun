# Content verification follow-up

The September 2026 refresh preserves every catalog entry and image. Items below require business records, not guesses from the website.

## Product data

- `product-code-review.csv` lists all occurrences of the 95 repeated product codes (2611 entries, 2515 distinct codes). Confirm whether these are variants, repeated presentations or incorrect codes before editing or deleting anything.
- Add verified materials, dimensions, packaging, MOQ and usage conditions to priority products first. No specifications have been invented during the refresh.
- The legacy ambiguous labels “cake service series”, “Cream tool Series” and “Fiber silicone mat” were made more readable as “Baking Accessories”, “Cake Decorating Tools” and “Silicone Baking Mats”. Confirm the intended scope against source product records.
- Kitchen Gadgets and Food Tongs do not have separate sections in the existing catalog. Their homepage links open the full catalog; do not invent category assignments based on images alone.

## Company information

- The phone number is normalized from the existing catalog's `15219359767` to `+86 152 1935 9767`. Confirm that this number is actively registered with WhatsApp. No message was sent during development.
- Confirm the exact registered English company spelling, office address and visiting instructions before adding a street address.
- Earlier claims (3 factories, 200+ staff, 50+ patents, 50+ countries, annual output above 3 million, 99.2% pass rate, under 0.5% defects, 500-piece MOQ, 30–45-day lead time and 24–48-hour quote turnaround) are not independently verified. The refreshed public copy uses project-specific language instead of universal numerical promises. Reintroduce documented figures with date, scope and definitions if desired.
- FDA / LFGB references describe food-contact requirements/testing; amfori BSCI describes social compliance auditing. ISO 9001 and BRCGS require current certificates and applicable site/product scope. Request the actual reports and certificates before adding logos, certificate images, standard editions or blanket claims.
- Fair photos remain exactly four. Their historic dates and booth number were not verified, so visitors are directed to contact the team for upcoming details.

## Inquiry delivery

- The site remains static. The inquiry form prepares a draft and provides an explicit “Open email app” action plus clipboard/manual-copy fallback. It never claims an email has been sent and never clears customer inputs automatically.
- Web-native delivery would require an owner-controlled form backend or email service, its configuration and a delivery test to the company inbox. Do not silently wire a third-party endpoint or expose an email-service secret in HTML.
- WeChat and LinkedIn placeholder links were removed. Restore only with an actual profile URL or owner-supplied QR code.
