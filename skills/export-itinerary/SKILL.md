---
name: export-itinerary
description: >
  This skill should be used whenever the user wants a shareable or printable
  version of their trip plan — phrases like "export the itinerary", "make a
  PDF", "Word version", "something I can print", "send it to my partner",
  "download the plan", or when an itinerary reaches Settled status and a
  polished document would help.
metadata:
  version: "0.1.0"
---

# Export Itinerary

Turn the living `itinerary.md` into a polished, downloadable document (Word
`.docx` by default; PDF on request).

## Before generating

- Read the current `itinerary.md`, `trip-brief.md` and `budget.md` — export
  the file's state, never a remembered version.
- If the itinerary status is still Draft, mention it and confirm the
  traveller wants to export anyway.
- Use the platform's document-creation capability (docx/pdf skills where
  available) and follow its guidance for professional output.

## Document structure

1. **Cover** — trip title, dates, travellers, destination; one-line summary.
2. **Trip overview** — the "At a glance" table.
3. **Key bookings** — flights (with times and references), stay (with
   address, check-in/out), booked activities with dates and any ticket notes.
4. **Day-by-day** — one section per day mirroring `itinerary.md`, cleaned of
   internal markers: booked items in bold, suggestions phrased as
   suggestions, backup options in a short note.
5. **Budget summary** — committed vs estimated vs ceiling, from `budget.md`.
6. **Practical notes** — advance-booking deadlines, packing-list pointer,
   emergency numbers for the destination, plug type, currency.

## Style

- Clean and legible in print: clear headings, generous spacing, no emoji.
- Times in 24-hour format; prices with currency symbols.
- Neutral, warm tone — this document may be shared with travel companions.

## Delivery

Save the document to the outputs location and present it to the user.
Offer a PDF version if the traveller asked for Word, and vice versa.
