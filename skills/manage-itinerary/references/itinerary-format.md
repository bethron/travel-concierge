# Itinerary File Format

Use this exact structure for `itinerary.md`. It is designed to read well raw,
diff cleanly when edited, and map directly onto the polished export.

```markdown
# <Trip title — e.g. "Lisbon City Break">

**Travellers:** <party> · **Dates:** <dd Mon – dd Mon yyyy> · **Base:** <stay name, area>
**Status:** Draft | Settled · **Last updated:** <yyyy-mm-dd>

## At a glance
| Day | Date | Theme | Booked items |
|---|---|---|---|
| 1 | Mon 07 Sep | Arrival & old town | Flight KL1234, hotel check-in |

## Day 1 — Mon 07 Sep · Arrival & old town
- **11:40** Land LIS (Flight KL1234 from LHR, dep 08:55) ✈ booked
- **12:30** Transfer to hotel — metro, ~35 min, ~€2 pp
- **14:00** Check in: Hotel Exemplo, Baixa 🏨 booked
- **15:30** Wander Alfama & Miradouro de Santa Luzia — free
- **19:30** Dinner: suggestion — Taberna Sal Grosso (petiscos) 💡
- 🌧 Backup: Museu do Fado

## Day 2 — Tue 08 Sep · ...
...

## Notes
- <ticket references, advance-booking deadlines, warnings>
```

## Conventions

- One bullet per timed item: `**HH:MM** <what> — <detail> <marker>`.
- Markers: `✈ booked` / `🏨 booked` / `🎟 booked` for confirmed items,
  `💡` for suggestions, `(est. £xx)` for estimated costs, `🌧 Backup:` for the
  rainy-day alternative.
- Keep travel time between stops in the detail ("tram 28, ~20 min").
- Update the **At a glance** table and **Last updated** on every edit.
- Set **Status: Settled** only when the traveller says the plan is done —
  this is the cue to offer the polished export.
