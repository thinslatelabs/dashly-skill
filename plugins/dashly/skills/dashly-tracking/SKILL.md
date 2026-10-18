---
name: dashly-tracking
description: Use when a person wants to track something by telling you (meals and calories, water, habits, mood, workouts, weight, their cycle, spending, tasks) and see it on a dashboard, and the Dashly MCP tools (list_topics, log_entry, log_entries, summarize_day and the rest) are available, or when they ask how to connect Dashly.
---

# Tracking with Dashly

Dashly keeps what a person tracks as **topics** with dated **entries**, and shows each topic as a live tile on their
dashboard at https://dashly.si, against the goal they set. You log what they tell you; Dashly does the rest. The
server also sends these rules as its own instructions when you connect, so treat this file as a summary.

## Connect

Dashly is a remote MCP server (streamable HTTP, OAuth 2.1):

```
https://dashly.si/mcp
```

- **Claude Code:** `claude mcp add --transport http dashly https://dashly.si/mcp`, then run `/mcp`, pick
  **dashly** and sign in. With a personal token (Settings in the Dashly app, it starts `dsh_`) you can skip the
  browser: add `--header "Authorization: Bearer <token>"`.
- **Claude, ChatGPT and other apps:** add it as a custom connector. Guides: https://dashly.si/connect

Dashly needs an account with an active plan (from $4.99 a month, 7-day trial).

## How to log well

1. Call `list_topics` once at the start and remember the ids. Reuse a topic that matches; create one with
   `create_topic` only when nothing fits.
2. Every topic has one unit. Convert the person's amount into it before logging (a glass of water is about 250 ml).
3. A goal has a direction: `at_least` for a target (water, protein), `at_most` for a limit (calories, spending),
   `between` for a range (sleep). It repeats per day, week, month or year, or runs until a date (`by`). If the person
   gives a number without saying which, ask.
4. Things to avoid (headaches, cigarettes) are topics with `polarity: avoid`, so a quiet day counts as a good one.
   Mood, energy and pain are rating topics with a scale.
5. Money entries are spending unless `values.flow` is `in`.
6. Several things at once go in one `log_entries` call, not many `log_entry` calls.
7. Sick, resting or away: `skip_day` for one topic, `pause_days` for everything, so the day does not count against
   them.
8. "How was my day?" is `summarize_day`. "How was my week?" is `summarize_topic`. Use `query_entries` only when you
   need the individual entries.
9. `archive_topic`, `merge_topics`, `archive_dashboard` and `delete_entry` are hard to undo: ask and wait for a yes.
10. When a tool returns an error, it names the field and the allowed values. Fix the input and try again.

## Dashboards

Every person has a home dashboard with a card for each topic. A new topic gets its card there on its own. Custom
dashboards (Dashly Plus) group a few topics by theme; call `get_capabilities` once before changing one, and keep each
to a handful of cards. To put a dashboard on a TV or tablet, the person pairs the screen at dashly.si/pair; you
cannot do that for them.

## Tools

`list_topics`, `create_topic`, `update_topic`, `archive_topic`, `merge_topics`, `log_entry`, `log_entries`,
`update_entry`, `delete_entry`, `query_entries`, `summarize_topic`, `skip_day`, `pause_days`, `unskip`,
`summarize_day`, `list_dashboards`, `get_dashboard`, `create_dashboard`, `update_dashboard`, `archive_dashboard`,
`get_capabilities`, `get_account`, `update_account`, `set_companion`.

## Examples

- "Track my water, goal 2 litres a day. I just had 500 ml."
- "Log lunch: chicken salad, about 550 kcal and 40 g protein."
- "I spent $24 on groceries. How much of my monthly budget is left?"
- "How did I do on my habits this week?"
