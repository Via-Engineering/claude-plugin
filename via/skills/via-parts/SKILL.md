---
name: via-parts
description: Choose electronic components with Via — search parts, read datasheets, compare price and stock, find drop-in alternates, and add parts to a project BOM. Use when the user asks for a part, a part number, a datasheet, pricing, a second source, or wants to build or review a BOM.
---

# Choosing parts with Via

Via's tools come from the `via` MCP server. The first call opens a browser
sign-in to the user's Via account; after that the connection stays signed in.

## Workflow

1. **Shortlist.** Call `search_components` with the requirement in plain
   words (function, key specs, package). Pass `project_id` or `revision_bom_id` when the
   user is working in a Via project, so the search knows what is already on the
   board. Present the shortlist as a markdown comparison table, then a short
   tradeoff paragraph.
2. **Read before designing in.** For any part the user may actually use, call
   `get_component_details` or `get_datasheet_overview`. Read the datasheet at
   `datasheetPdfUrl` before giving support circuitry, component values, or
   calculations. Cite the datasheet section you relied on.
3. **Cost and availability.** Call `get_component_pricing` when cost, MOQ, or
   stock matters. Quote the price tier that matches the user's quantity.
4. **Second sources.** Call `find_alternates` with the part's `uid` from search,
   or an exact part number. Keep the engine's split: drop-ins first, then parts
   to check, each with the reason it is not a drop-in.
5. **Build the BOM.** Use `list_projects` / `get_project_context` to find the
   right BOM, then `add_project_bom_component` with the `component_uid` from
   search or details. Pass `parent_component_id` to group supporting passives
   under the IC they serve.

## Rules

- Never invent part numbers, specs, or prices. If Via has no match, say so.
- Ask before writing to a project, library, or ruleset; reads need no
  confirmation.
- Prefer parts that are in stock and complete over a marginally better spec.
- When the user belongs to several organizations, call `list_organizations`
  and confirm which one before writing.
