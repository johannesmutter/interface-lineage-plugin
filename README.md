# Interface Lineage — Claude plugin & MCP

A Claude Code plugin (and standalone MCP server) for
[Interface Lineage](https://interfacelineage.com) — a curated corpus that takes
interfaces apart for designers: dissected interfaces, the design principles they
embody, the people who made them, and the typed lineage between them.

Ask questions in Claude or Cursor and get answers pulled from live examples in
the library instead of averaged-out training data.

## Install

```
/plugin marketplace add johannesmutter/interface-lineage-plugin
/plugin install interface-lineage@interface-lineage
```

Public dossiers work with no configuration. For member-only dossiers, generate a
personal token at <https://interfacelineage.com/account> and paste it when the
plugin prompts for `api_token`.

## Or connect the MCP server directly

```
# public dossiers only
claude mcp add --transport http interface-lineage https://interfacelineage.com/mcp

# with member access
claude mcp add --transport http interface-lineage https://interfacelineage.com/mcp \
  --header "Authorization: Bearer il_your_token_here"
```

For Claude Desktop or any other host, add an HTTP MCP server pointing at
`https://interfacelineage.com/mcp`.

## What's inside

**MCP tools** — `search`, `fetch`, `get_lineage`, `find_related`, `list_catalog`
(read-only, scoped to what your token can see).

**Skills**

- `explore-lineage` — pull a design's acknowledged lineage *and* its unlinked
  cousins, then synthesize the tension and pose generative design questions.
- `query-interface-lineage` — which tool to reach for and how to stay grounded.
- `cite-interface-lineage` — attribute makers and link dossiers.
- `interface-lineage-link-types` — the typed-edge vocabulary and how to read
  edge direction.

See [plugins/interface-lineage/README.md](plugins/interface-lineage/README.md)
for details. The tools are read-only; a token scopes results to exactly what its
owner can see on the site, and is revocable at
<https://interfacelineage.com/account>.
