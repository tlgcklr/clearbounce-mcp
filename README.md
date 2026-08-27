# ClearBounce MCP Server

Official hosted [MCP](https://modelcontextprotocol.io) server for [ClearBounce](https://clearbounce.net) — real-time email verification and business email finding for AI assistants.

**Server URL:** `https://clearbounce.net/mcp` (Streamable HTTP)

## Tools

| Tool | What it does | Cost |
|---|---|---|
| `verify_email` | Real-time deliverability check (syntax, domain, mailbox) with a `deliverable` / `risky` / `undeliverable` verdict | 1 credit |
| `find_email` | Finds likely business email addresses from a name + company domain | Free |
| `check_credits` | Shows the remaining credit balance | Free |

## Authentication

Two options:

- **OAuth** — clients that support MCP OAuth (Claude, ChatGPT, Perplexity, Grok) can connect with no manual setup; you sign in to your ClearBounce account in the browser.
- **API key** — create one at [clearbounce.net/dashboard/api-keys](https://clearbounce.net/dashboard/api-keys) and send it as an `x-api-key` (or `Authorization: Bearer`) header.

New accounts include free credits.

## Connect from your assistant

### Claude (claude.ai / Desktop)

Settings → Connectors → **Add custom connector** → `https://clearbounce.net/mcp` → sign in with OAuth.

### Claude Code

```sh
claude mcp add --transport http clearbounce https://clearbounce.net/mcp
```

### ChatGPT (developer mode)

Settings → Connectors → Developer mode → **Add** → `https://clearbounce.net/mcp`.

### Grok

[grok.com/connectors](https://grok.com/connectors) → **New Connector** → **Custom** → `https://clearbounce.net/mcp`.

### Perplexity (Pro/Max)

Settings → Connectors → **Add connector** → server URL `https://clearbounce.net/mcp` → OAuth or API key.

### Gemini CLI

```sh
gemini extensions install https://github.com/tlgcklr/clearbounce-gemini-extension
export CLEARBOUNCE_API_KEY="cb_..."
```

Or add to `~/.gemini/settings.json`:

```json
{
  "mcpServers": {
    "clearbounce": {
      "httpUrl": "https://clearbounce.net/mcp",
      "headers": { "x-api-key": "$CLEARBOUNCE_API_KEY" }
    }
  }
}
```

## Example prompts

- "Is john.doe@acme.com safe to send to?"
- "Find the email address of Jane Smith at example.com and verify the best match."
- "How many ClearBounce credits do I have left?"

## Links

- Website & pricing: https://clearbounce.net
- API documentation: https://docs.clearbounce.net
- Privacy policy: https://clearbounce.net/privacy
- Support: support@clearbounce.net
