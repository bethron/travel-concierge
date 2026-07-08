# Changelog

## 0.7.0
- fun-facts skill: surprising "did you know?" destination trivia, tailored
  to the trip's flavour (gastronomy, adventure, culture, family, business);
  offered once when a destination is set and on-trip during downtime
- Added Turkish Airlines connector (brand-direct search, Istanbul routings)
- Removed "Publishing tips" section from README (redundant with submission
  guides)

## 0.6.0
- Search-only posture adopted throughout: no in-chat bookings, reservations,
  rides or orders — every purchase is completed on the provider's own site
  or app. Otto Travel, Resy, Uber and Uber Eats are used for search,
  availability and estimates only.

## 0.5.0
- monitor-fares skill: fare watchlist with on-demand re-checks, price
  history and honest book-or-wait advice; /check-fares command
- expense-report skill: .xlsx export with business/personal split, and an
  auditable end-of-trip savings summary ("you saved roughly £X and Y
  hours"); /expense-report command
- Search skills now persist comparison tables to options/ as the savings
  ledger

## 0.4.0
- Devil's-advocate hardening: active-trip resolution rule, destination-local
  time convention, sanitised connector URLs (directory name matching),
  cancellation guidance for in-chat bookings
- New slash commands: /new-trip, /concierge
- README: recommended core connector set to ease onboarding
- Added CHANGELOG

## 0.3.0
- Business travel mode: template, interview branch, triggers, policy cap,
  loyalty programmes, itemised expense logging, bleisure extension

## 0.2.0
- One-stop-shop expansion: on-trip-concierge, find-dining and sync-calendar
  skills; connectors expanded to 17 (AllTrails, DirectBooker, Expedia,
  Google Calendar, lastminute.com, Resy, Tripadvisor, Uber, Uber Eats,
  Viator, Wyndham, Otto Travel)

## 0.1.0
- Initial release: plan-trip, find-flights, find-stays, find-activities,
  manage-itinerary, export-itinerary, trip-budget, trip-checklists,
  traveller-profile; 5 connectors
