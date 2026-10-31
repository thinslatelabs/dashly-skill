# Dashly

Dashly gives structure to your conversations with Claude. Tell Claude what you ate, how you slept, what you spent,
which habit you kept or what you need to do, and Dashly logs it and shows each thing you track as a live tile
against your goal at [dashly.si](https://dashly.si).

Use it as a calorie and protein tracker, a habit tracker that keeps your streaks, a mood journal, a workout and
weight log, an expense tracker with a monthly budget or a task list. Or track anything you can describe. Every day
lands on a calendar, and every tracked thing has its own page with a graph and its history. Ask "how was my week?"
and Claude answers from your own numbers.

Try:

- "Track my water, goal 2 litres a day. I just had 500 ml."
- "Log lunch: chicken salad, about 550 kcal and 40 g protein."
- "How did I do on my habits this week?"
- "Add renew passport to my tasks, due Friday."

## What this plugin contains

- **The Dashly MCP server** at `https://dashly.si/mcp` (remote, streamable HTTP). The first time you use it, you sign
  in to your Dashly account in the browser and approve access. There is no key to copy. What you log is sent to and
  stored by Dashly, under the [privacy policy](https://dashly.si/privacy).
- **A skill, `dashly-tracking`,** that tells Claude how to log well: matching what you say to the right tracked
  thing, units and goals, and reading before it changes anything.

The plugin runs nothing on your computer and sends nothing anywhere except to the Dashly server you sign in to.
Claude reads before it changes anything, and asks before it deletes, merges or archives what you logged.

## Links

- Guides for Claude, ChatGPT and other apps: https://dashly.si/connect
- Pricing: https://dashly.si/pricing (7-day trial)
- Support: contact@thinslatelabs.us

Made by Thinslate Labs LLC. MIT licence.
