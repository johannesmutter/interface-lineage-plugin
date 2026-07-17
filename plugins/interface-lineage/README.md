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

Public dossiers work with no configuration. To reach member-only dossiers,
generate a personal token at <https://interfacelineage.com/account> and paste it
when the plugin prompts for `api_token` (or set it later in plugin settings).

## Connect without the plugin

The MCP endpoint is a plain remote server; any host can use it.

```
# public dossiers only
claude mcp add --transport http interface-lineage https://interfacelineage.com/mcp

# with member access
claude mcp add --transport http interface-lineage https://interfacelineage.com/mcp \
  --header "Authorization: Bearer YOUR_TOKEN"
```

For Claude Desktop or other hosts, add an HTTP MCP server pointing at
`https://interfacelineage.com/mcp` and send your token as
`Authorization: Bearer <token>

## What's inside

**MCP tools**

| Tool | What it does |
| --- | --- |
| `search` | Keyword search across the corpus. |
| `fetch` | The full dossier as Markdown, plus its lineage. |
| `get_lineage` | The explicit typed influence edges for a dossier. |
| `find_related` | Designs similar in feel that aren't already linked. |
| `list_catalog` | Browse a whole category (interfaces, principles, people, …). |

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

The tools are read-only. A token scopes results to exactly what its owner can
see on the website — no token means public dossiers only. Tokens are revocable
at <https://interfacelineage.com/account>.
