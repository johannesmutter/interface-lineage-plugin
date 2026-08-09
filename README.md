# Interface Lineage — Claude plugin & MCP

A Claude Code plugin (and standalone MCP server) for
[Interface Lineage](https://interfacelineage.com) — a curated corpus that takes
interfaces apart for designers: dissected interfaces, the design principles they
embody, the people who made them, and the typed lineage between them.

Ask questions in Claude or Cursor and get answers pulled from live examples in
the library instead of averaged-out training data.

The archive is open: every dossier is on the web, free to read, no account. What
this adds is the reading itself, done by the agent, plus the hand-authored
lineage graph that no crawl reconstructs.

## Install

First, generate a personal token at <https://interfacelineage.com/account> (open
the MCP access section and press copy). You'll paste it during install. Sign-in
is by email, no password, and every account gets a token free.

Then, **inside Claude Code** — these are slash commands typed at the Claude Code
prompt, not in your terminal:

```
/plugin marketplace add johannesmutter/interface-lineage-plugin
/plugin install interface-lineage@interface-lineage
/reload-plugins
```

Run them one at a time, waiting for each to finish. The install prompts for
`api_token`; paste the token from step one.

A session fixes its list of tools when it starts, so the one you installed from
still shows none. `/reload-plugins` pulls in the new list. In the Claude desktop
app that command isn't available — open a new chat instead.

## Or connect the MCP server directly

Without the plugin, **in your terminal**:

```
claude mcp add --transport http interface-lineage https://interfacelineage.com/mcp \
  --header "Authorization: Bearer YOUR_TOKEN"
```

For Claude Desktop, Cursor, and Codex, see the per-host setup at
<https://interfacelineage.com/connect>.

## What's inside

**MCP tools** — `search`, `fetch`, `get_lineage`, `find_related`, `get_stills`,
`list_catalog`. All read-only.

**Skills**

- `explore-lineage` — pull a design's acknowledged lineage *and* its unlinked
  cousins, then synthesize the tension and pose generative design questions.
- `query-interface-lineage` — which tool to reach for and how to stay grounded.
- `cite-interface-lineage` — attribute makers and link dossiers.
- `interface-lineage-link-types` — the typed-edge vocabulary and how to read
  edge direction.

See [plugins/interface-lineage/README.md](plugins/interface-lineage/README.md)
for details. Results pass through the same permission check the website uses, so
an agent sees what its token's owner sees in a browser. Generating a fresh token
at <https://interfacelineage.com/account> replaces the old one.
