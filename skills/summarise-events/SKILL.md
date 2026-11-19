---
name: summarise-events
description: Summarise the Operations calendar for a date range, including confirmed and quoted events, overlapping bookings and assignment gaps.
---

Resolve relative dates in Europe/London. “Next week” runs Monday through Sunday. Call `list_jobs` with inclusive `service_date_from` and `service_date_to`. Apply a requested status filter at query time. Follow every cursor or say which part of the results you could verify.

Count each job ID once, including multi-day service already underway. Group by status and show service dates and source links. Label setup, delivery and collection separately from service. Mention missing or unknown times when they affect the answer. Keep similar records separate and flag possible duplication when it affects staffing.

Report staff required, assigned and confirmed separately. Identify equipment shortages by type. Use assignment details when names or asset numbers matter. A staffing summary is read-only. If the connection fails, say which dates you could not check.
