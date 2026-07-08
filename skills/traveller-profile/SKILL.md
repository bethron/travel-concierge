---
name: traveller-profile
description: >
  This skill should be used when the user wants their travel preferences
  remembered or changed — phrases like "remember that I", "set up my
  traveller profile", "my home airport is", "I'm vegetarian", "update my
  preferences", "always aisle seat" — and at the start of any trip plan to
  load an existing profile so questions aren't repeated.
metadata:
  version: "0.1.0"
---

# Traveller Profile

Maintain an **optional** preferences file at `travel/traveller-profile.md`
that persists across trips. The profile is opt-in: offer it once (typically
at the end of a first trip plan), and never nag if declined.

## File format

```markdown
# Traveller Profile
**Last updated:** yyyy-mm-dd

- **Home airport / city:** London (LHR preferred, LGW ok)
- **Nationality / passport:** UK (for visa checks)
- **Usual party:** couple
- **Style:** mid-range, food-led
- **Pace:** balanced
- **Flight preferences:** direct where possible; aisle seat
- **Stay preferences:** central location over size; breakfast included
- **Dietary needs:** vegetarian
- **Accessibility / medical:** —
- **Loves:** markets, hiking, live music
- **Avoids:** early starts, coach tours
```

## Rules

- **Load first**: at the start of any planning session, check whether the
  file exists and apply it silently — then say briefly which preferences were
  applied so the traveller can override for this trip.
- **Trip overrides profile**: anything said in the current conversation beats
  the stored value; update the file only if the traveller says the change is
  permanent ("actually I always…").
- **Write on request or with consent**: create or update after phrases like
  "remember that…", or ask once — "Shall I save these preferences for next
  time?" — when a trip wraps up.
- Show the profile in full when asked; delete it immediately on request.
- Keep it short: preferences, not a biography. Never store payment details
  or passport numbers.
