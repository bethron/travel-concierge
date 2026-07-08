---
name: sync-calendar
description: >
  This skill should be used whenever the user wants the trip in their
  calendar — phrases like "add it to my calendar", "put the flights in
  Google Calendar", "calendar the itinerary", "block out the trip", "remind
  me about check-in", or proactively (as an offer, once) when an itinerary
  reaches Settled status.
metadata:
  version: "0.1.0"
---

# Sync Calendar

Push the trip into **Google Calendar** so the itinerary lives where the
traveller already looks.

## What to create

Offer two levels and let the traveller choose:

1. **Just the essentials** — flights (with flight numbers and terminals in
   the title), stay check-in/check-out, and any timed, booked activities or
   reservations.
2. **The full itinerary** — the essentials plus one all-day event per trip
   day carrying that day's plan in the description, and timed events for
   each scheduled item.

Always propose adding an all-day "Trip: <title>" event spanning the whole
trip, and useful reminders (online check-in opens, advance-booking
deadlines from the itinerary notes).

## How to do it well

- Read `itinerary.md` as the source of truth; sync its current state, never
  a remembered one.
- **Time zones matter most here**: create events in the destination's local
  time zone; flights use departure-airport local time for departure and
  arrival-airport local time for arrival. State the time zones used.
- Set sensible reminders: 3 hours before flights, 1 day before
  advance-booking deadlines, none for all-day summary events.
- Put booking references, addresses and links in the event description, and
  the venue address in the location field so maps work from the event.
- List the user's calendars first if they have several, and ask which to use.

## Updates and changes

When the itinerary changes after a sync, offer to update the calendar too:
find the existing events for the changed items and update rather than
duplicate. If the trip is cancelled, offer to delete the trip's events —
confirm before deleting anything.

## Care points

- Create nothing without the traveller's go-ahead on the level of detail.
- Never store payment details in event descriptions; booking references are
  fine.
