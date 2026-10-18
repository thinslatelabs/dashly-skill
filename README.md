# Dashly for AI assistants

**[Dashly](https://dashly.si)**: track everything. Give structure to your AI conversations.

Your AI already knows everything about you. Why outsource your tracking to another app? Dashly replaces your calorie
counter, habit tracker, mood journal, budget app and to-do list with the AI assistant you already talk to. Tell
ChatGPT or Claude what you ate, how you slept, what you spent, which habit you kept or what you need to do, and Dashly
logs it and shows each thing as a live tile against your goal. Use it as an AI calorie tracker, a ChatGPT or Claude
habit tracker, a mood tracker, an expense tracker or a task list, or track anything you want.

This repo connects an AI app to Dashly. It holds no product code: a Claude Code plugin that adds the Dashly MCP
server, and a skill that tells an assistant how to log well.

## Connect Dashly as an MCP server

Dashly runs a remote MCP server (streamable HTTP, OAuth 2.1):

```
https://dashly.si/mcp
```

Add it to any app that supports MCP connectors, sign in with your Dashly account, and start telling it what you
track. There is no key to copy.

### Claude Code (this plugin)

```shell
/plugin marketplace add thinslatelabs/dashly-skill
/plugin install dashly@dashly
```

Then run `/mcp`, pick **dashly**, and sign in in the browser window that opens.

Without the plugin, the same thing is one command:

```shell
claude mcp add --transport http dashly https://dashly.si/mcp
```

### Claude, ChatGPT and other apps

Step-by-step guides: [Connect ChatGPT, Claude or any AI to Dashly](https://dashly.si/connect).

## What it can do

24 tools, each marked read-only or destructive: create the things you track with units, goals and limits; log
entries one at a time or in batches; edit, delete and query entries; summarize a day or a range; skip or pause
days; build and change dashboards. Try:

- "Track my water, goal 2 litres a day. I just had 500 ml."
- "Log lunch: chicken salad, about 550 kcal and 40 g protein."
- "How did I do on my habits this week?"
- "Add renew passport to my tasks, due Friday."

## The skill

[`plugins/dashly/skills/dashly-tracking/SKILL.md`](./plugins/dashly/skills/dashly-tracking/SKILL.md) summarizes how
to log well with the Dashly tools. Other agent runtimes that read `~/.agents/skills/` can copy it in:

```bash
git clone https://github.com/thinslatelabs/dashly-skill.git /tmp/dashly-skill
cp -r /tmp/dashly-skill/plugins/dashly/skills/dashly-tracking ~/.agents/skills/dashly-tracking
```

## Learn more

- Website: https://dashly.si
- Pricing: https://dashly.si/pricing (from $4.99 a month, 7-day trial)
- Machine index: https://dashly.si/llms.txt
- Official MCP Registry: `si.dashly/dashly`

## License

[MIT](./LICENSE) © ThinSlate Labs
