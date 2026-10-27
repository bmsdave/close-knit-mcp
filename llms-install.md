# Installing Close Knit

Close Knit is a remote MCP server. There is nothing to clone, build or install, and no API key or account.

- URL: `https://getcloseknit.com/mcp`
- Transport: Streamable HTTP
- Authentication: none

## Cline

Add this to `cline_mcp_settings.json` (or use the Remote Servers tab: any name, the URL above, transport Streamable HTTP):

```json
{
  "mcpServers": {
    "close-knit": {
      "type": "streamableHttp",
      "url": "https://getcloseknit.com/mcp"
    }
  }
}
```

## Check it works

Once connected, the server lists 24 read-only tools plus `send_feedback`. Try `search_places` with `King's Cross` or `find_areas` for a short list of neighbourhoods.

Every answer is an evidence envelope (`value`, `confidence`, `evidence[]`, `sources[]`, `caveats[]`); cite the sources and keep the caveats. Only call `send_feedback` after the user agrees.

Docs for assistants: https://getcloseknit.com/agents. Privacy: https://getcloseknit.com/privacy.
