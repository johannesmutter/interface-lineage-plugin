# Interface Lineage — Claude plugin

Query the [Interface Lineage](https://interfacelineage.com) corpus over MCP, and
get skills for exploring a design's lineage, citing sources, and reading the
edge vocabulary. Answers come from live examples in the library instead of
averaged-out training data.

## Install

```
/plugin marketplace add johannesmutter/interface-lineage-plugin
/plugin install interface-lineage@interface-lineage
```

The two lines above are slash commands typed **inside Claude Code**, at its
prompt — not in your terminal.

Generate a personal token at <https://interfacelineage.com/account> (open the MCP
access section and press copy) and paste it when the plugin prompts for
`api_token`. Sign-in is by email, no password, and every account gets a token
free. Reading the archive in a browser needs no account at all; the token is
what gives a tool call an owner.

## Connect without the plugin

The MCP endpoint is a plain remote server; any host can use it. **In your
terminal**, for Claude Code:

```
claude mcp add --transport http interface-lineage https://interfacelineage.com/mcp \
  --header "Authorization: Bearer YOUR_TOKEN"
```

For Claude Desktop, Cursor, and Codex, see the per-host setup at
<https://interfacelineage.com/connect>.

## What's inside

**MCP tools**

| Tool | What it does |
| --- | --- |
| `search` | Keyword search across the corpus. |
| `fetch` | The full dossier as Markdown, plus its lineage. |
| `get_lineage` | The explicit typed influence edges for a dossier. |
| `find_related` | Designs similar in feel that aren't already linked. |
| `get_stills` | The dossier's own screenshots, as images. |
| `list_catalog` | Sample a category (interfaces, principles, people, …). |

**Skills**

- `explore-lineage` — pull a design's lineage *and* its unlinked cousins, then
  synthesize the tension and pose generative design questions.
- `query-interface-lineage` — which tool to reach for and how to stay grounded.
- `cite-interface-lineage` — attribute makers and link dossiers.
- `interface-lineage-link-types` — the typed-edge vocabulary and how to read
  edge direction.

**MCP prompt** — the server also exposes an `explore_lineage` prompt, so hosts
that surface MCP prompts get the same workflow without installing the skills.

## Privacy & scope

The tools are read-only. Results pass through the same permission check the
website uses, so an agent sees exactly what its token's owner sees in a browser,
which is the open archive plus anything restricted to them.

One refusal exists: a burst cap of 120 calls a minute. It protects a single
server rather than the corpus, since every dossier is public and already
downloadable without a token. Heavy readers are the point.

Generating a fresh token at <https://interfacelineage.com/account> replaces the
old one, which stops working immediately.
