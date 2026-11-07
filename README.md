# Your Rides plugin

Plan motorbike rides by chatting with Claude, ChatGPT or Grok. Ask for "a 3-hour curvy loop from home" or "a route to Český Krumlov avoiding motorways" and the assistant plans it with the [Your Rides](https://rides.kodspear.com) motorcycle routing engine, which favours twisty roads. The route appears on an interactive map where you can change curviness, avoid motorways or tolls, add or reorder stops, or change the loop length and plan again. Save it to your account and start it from the Your Rides phone app with turn-by-turn navigation. The assistant can also review the rides you have recorded.

## What's inside

| Part | What it does |
|---|---|
| **MCP connector** (`https://api.kodspear.com/mcp`) | 12 tools: rider context, place search, A→B and round-trip planning with an interactive map (MCP Apps), saving routes, and read-only access to your saved routes, rides and stats. |
| `skills/plan-motorbike-route` | How to plan an enjoyable ride: budget, scenic anchors, validating with the engine, presenting and saving. |
| `skills/multi-day-trip` | Splits tours and trips over 300 km into daily legs, each saved as its own route. |
| `skills/ride-review` | Answers questions about your riding history and suggests what to ride next. |

## Requirements

- A free Your Rides account (sign up at [rides.kodspear.com](https://rides.kodspear.com) or in the iOS / Android app). Guest accounts can't connect.
- You sign in with OAuth on first use and approve access on the Your Rides consent screen. The assistant never sees your password.

## Install

**Claude Code**

```bash
/plugin marketplace add jorgeCollinet/your-rides-plugin
/plugin install your-rides@your-rides
```

Then run `/mcp`, pick `plugin:your-rides:your-rides` and sign in.

or add the connector alone:

```bash
claude mcp add --transport http your-rides https://api.kodspear.com/mcp
```

**Codex**

```bash
codex plugin marketplace add jorgeCollinet/your-rides-plugin
codex plugin add your-rides@your-rides
codex mcp login your-rides
```

The last command opens your browser to sign in.

**Grok Build**

```bash
grok mcp add --transport http your-rides https://api.kodspear.com/mcp
```

Grok opens your browser to sign in the first time it uses the connector. If you already installed the plugin in Claude Code, Grok Build picks it up automatically.

**Grok (grok.com)** — Connectors → add a custom connector with `https://api.kodspear.com/mcp` (custom connectors need a paid Grok plan).

**Claude (claude.ai / desktop)** — Settings → Connectors → find Your Rides, or add a custom connector with `https://api.kodspear.com/mcp`.

**ChatGPT** — find Your Rides in the apps directory and click Connect.

## Permissions

Every tool runs as you, with your own permissions. All tools are read-only except **Save route**, which creates a new private route only when you ask. The plugin can't edit or delete anything, post, or message. Disconnect any time under Profile → Connected apps on the web.

## Limits

- Up to 300 km per route; longer trips are split into legs.
- Best coverage in Germany, Austria and the Czech Republic.

## Publisher

Published by **Your Rides**. Who operates the service, how your data is handled and how to exercise your rights are described in the [privacy policy](https://rides.kodspear.com/privacy).

## Links

- Setup guide: https://rides.kodspear.com/ai
- Privacy policy: https://rides.kodspear.com/privacy
- Terms: https://rides.kodspear.com/terms
- Support: support@kodspear.com

## License

Free to use, modify and share — including adapting it to other AI assistants — as long as it is used with the Your Rides service, is not sold or built into a paid or competing product, and keeps this licence. See [LICENSE](LICENSE). Use of the Your Rides service itself is covered by the [Terms of Service](https://rides.kodspear.com/terms).
