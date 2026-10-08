# Via plugin for Claude

Gives Claude access to [Via](https://viabom.com): electronic component search,
datasheets, distributor pricing and stock, drop-in alternates, and your Via
project BOMs.

## Install (Claude Code)

```
/plugin marketplace add Via-Engineering/claude-plugin
/plugin install via@via
```

Then run `/mcp`, choose `via`, and sign in with your Via account in the
browser. No API key is needed.

## What's included

| Path | What it is |
| --- | --- |
| `via/.mcp.json` | Connects to Via's hosted MCP server, `https://api.viabom.com/mcp` |
| `via/skills/via-parts/` | Guides Claude from search to datasheet, pricing, alternates and BOM |
| `via/commands/find-part.md` | `/via:find-part <requirement>`, e.g. `/via:find-part 3.3 V LDO, 500 mA, SOT-23-5` |

## Other MCP clients

Any MCP client that supports remote servers with OAuth can connect directly to
`https://api.viabom.com/mcp`.

## Support

hello@viabom.com
