---
name: summarise-events
description: Summarise the Operations calendar for a date range, including confirmed and quoted events, branding, venue addresses, machine allocation gaps, overseas machine bookings and setup-to-breakdown schedules.
---

If the live read tools are missing or request authentication in ChatGPT desktop, use the client’s connection action or its sign-in link for `operations` when offered. If neither appears, direct the teammate to the installed plugin details. Report a missing action or the sign-in error and the data you could not check. Never generate a login URL, suggest terminal commands or require a workspace admin for this personal installation.

Resolve relative dates in Europe/London. “Next week” runs Monday through Sunday. For a service-week summary, call `list_jobs` with inclusive `service_date_from` and `service_date_to`. Apply a requested status filter at query time. Follow every cursor or say which part of the results you could verify.

Count each job ID once, including multi-day service already underway. Group by status and show service dates and source links. Label setup, delivery and collection separately from service. Mention missing or unknown times when they affect the answer. Keep similar records separate and flag possible duplication when it affects staffing.

Report staff required, assigned and confirmed separately. Identify equipment shortages by type. Use assignment details when names or asset numbers matter. A staffing summary is read-only. If the connection fails, say which dates you could not check.

Choose the query window for the requested report:

- **Branding:** Use service dates. List each event’s positive quantities for branded cups, branded bars, branded machines, stencils and aprons, and list unbranded bars separately. Identify events with no recorded requirements. Keep quoted quantities separate from confirmed totals.
- **Venue addresses:** Use service dates. Include every event with its recorded address. Flag missing addresses or entries that only name a city.
- **Machine allocations:** Use service dates and `needs_machine: true`. Show machines required, assigned and still needed for each job.
- **Machines abroad:** Set `machines_abroad_on` to today in Europe/London, without a service-date filter. This matches machines booked outside the UK from delivery through collection, including open-ended reservations. From the returned equipment assignments list only machines, with asset label, job, country, booking status and reservation dates. Group repeated assets by equipment ID. “OTHER” means the specific overseas country was not recorded. This is a booking report; an unknown country cannot establish an overseas booking.
- **Schedule with setups and breakdowns:** Use both `activity_date_from` and `activity_date_to` instead of service-date filters. Build a chronological agenda from setup, daily service and pack-up (breakdown). Include only activities inside the requested window, including same-day setup and breakdown as separate entries. Use recorded times and identify missing times. A job can have an activity this week even when all its service dates are outside it.

If the installed server lacks the requested reporting fields, identify the gap before presenting a partial result.
