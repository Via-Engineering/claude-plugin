# CircuitField plugin for Claude

Gives Claude access to CircuitField: electronic component search, datasheets,
distributor pricing and stock, drop-in alternates, and your project BOMs.

## Install (Claude Code)

```
/plugin marketplace add Via-Engineering/claude-plugin
/plugin install circuitfield@circuitfield
```

Then run `/mcp`, choose `circuitfield`, and sign in with your account in the
browser. No API key is needed.

## What's included

| Path | What it is |
| --- | --- |
| `circuitfield/.mcp.json` | Connects to the hosted MCP server, `https://api.viabom.com/mcp` |
| `circuitfield/skills/circuitfield-parts/` | Guides Claude from search to datasheet, pricing, alternates and BOM |
| `circuitfield/commands/find-part.md` | `/circuitfield:find-part <requirement>`, e.g. `/circuitfield:find-part 3.3 V LDO, 500 mA, SOT-23-5` |

## Other MCP clients

Any MCP client that supports remote servers with OAuth can connect directly to
`https://api.viabom.com/mcp`.

## Support

hello@viabom.com
