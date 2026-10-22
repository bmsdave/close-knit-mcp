# Close Knit MCP server

Close Knit gives AI assistants evidence about London neighbourhoods and homes, to help people choose where to live. It is a remote MCP server: recorded sale prices, rents, crime, schools, flood risk, commute times, noise and more, from official open data. Every tool answer is an evidence envelope with a `value`, a `confidence`, the `evidence[]` behind it, its `sources[]` (with licence) and `caveats[]`. Coverage is London only today. It is free for people to use.

```
https://getcloseknit.com/mcp
```

- Transport: Streamable HTTP
- Authentication: none (no account, no OAuth, no API key)
- MCP Registry name: `com.getcloseknit/close-knit`

## Tools

| Group | Tool | What it does |
| --- | --- | --- |
| Home search | `find_areas` | Shortlist neighbourhoods for a household: budget, bedrooms, places they travel to, weighted priorities. |
| | `match_areas` | Score every area against a household's ordered criteria. |
| | `find_similar_areas` | Neighbourhoods like one the user liked, optionally only cheaper ones. |
| | `open_shared_search` | Open a search shared from the Close Knit site (a `#profile=` link). |
| | `search_places` | Resolve a station, borough, neighbourhood, postcode or street the user mentions. |
| | `get_commute` | Door-to-door weekday-morning minutes from an area to the user's places (public transport, bike and more). |
| Areas | `search_areas` | Resolve free text (area name, ONS code, postcode, street) to area ids. |
| | `get_area_overview` | One neighbourhood in detail: local market, schools, noise, price trend. |
| | `get_area_evidence_pack` | One cited evidence pack for an area: market depth, crime, noise, schools and more. |
| | `list_metrics` | Every area metric served, with unit, direction, periods and provenance. |
| | `get_area_metric` | One metric for one area and month, with London and England percentiles. |
| | `rank_areas_by_metric` | Rank all areas by one metric and return the top N. |
| | `get_flood_risk` | Flood bands for an area's land and, with a UPRN, for one home. |
| | `get_rent_levels` | Median monthly rent by bedroom count. |
| Homes and prices | `get_home_prices` | One home's recorded sales and the range of prices in its area today. |
| | `get_address_history` | Recorded sale prices for one address (HM Land Registry). |
| | `get_nearby_sales_summary` | Counts and median £/m² of recorded sales in the same building and street. |
| | `get_market_depth` | Local market depth: sales in the last 12 months, turnover, leasehold share. |
| Listings | `get_listing_search_links` | Pre-filtered portal searches for the postcode districts of shortlisted areas. |
| | `assess_listing` | Check one listing's asking price and facts against local evidence. |
| | `build_watch_spec` | Turn a finished search into a watch for new listings. |
| Your own criteria | `list_custom_presets` | Ready-made criteria built from places on OpenStreetMap. |
| | `evaluate_custom_criterion` | Evaluate a criterion such as "more cafés than kebab shops" for every neighbourhood. |
| Feedback | `send_feedback` | Send feedback to the Close Knit team, only after the user agrees. |

## Add Close Knit to your assistant

### Claude (claude.ai)

1. Open **Customize > Connectors**.
2. Click **+ Add**, then **Add custom connector**.
3. Name: `Close Knit`. Remote MCP server URL: `https://getcloseknit.com/mcp`. Click **Continue**.
4. Under **Authentication**, choose no sign in, then click **Add**.
5. In a chat, click **+** at the lower left, choose **Connectors** and turn Close Knit on.

On Team and Enterprise plans an owner adds it under **Organization settings > Connectors**. Free plans allow one custom connector.

### Claude Code

```bash
claude mcp add --transport http close-knit https://getcloseknit.com/mcp
```

### ChatGPT

1. Open **Plugins** at chatgpt.com/plugins.
2. Select the plus button, then **Add custom MCP server**.
3. Name: `Close Knit`. Under **Connection**, Server URL: `https://getcloseknit.com/mcp`.
4. Authentication: **No authentication**.
5. Review the warning, select **I understand and want to continue**, then **Create as a plugin**.
6. Install the plugin, then type `@` in the prompt box and select Close Knit.

Custom MCP servers are available on ChatGPT web; which plans and workspaces allow them depends on your account and workspace settings.

### Gemini CLI

```bash
gemini extensions install https://github.com/bmsdave/close-knit-mcp
```

This repository is a Gemini CLI extension: `gemini-extension.json` connects the remote server and `GEMINI.md` gives the model short guidance. Restart Gemini CLI after installing.

### Gemini app

1. At gemini.google.com, click **Settings**, then **Connected Apps**.
2. Under **Custom apps**, click **Add a custom app**.
3. Enter `https://getcloseknit.com/mcp` and click **Next**, then follow the on-screen steps.
4. In a prompt, type `@` and select Close Knit.

Google currently limits custom apps to people aged 18 or over in the US, signed in with a personal Google Account, with Keep Activity on.

### Cursor

[![Add Close Knit to Cursor](https://cursor.com/deeplink/mcp-install-dark.svg)](https://cursor.com/install-mcp?name=close-knit&config=eyJ1cmwiOiJodHRwczovL2dldGNsb3Nla25pdC5jb20vbWNwIn0%3D)

The same install link in Cursor's own format:

```
cursor://anysphere.cursor-deeplink/mcp/install?name=close-knit&config=eyJ1cmwiOiJodHRwczovL2dldGNsb3Nla25pdC5jb20vbWNwIn0%3D
```

Or add it to `mcp.json`:

```json
{
  "mcpServers": {
    "close-knit": {
      "url": "https://getcloseknit.com/mcp"
    }
  }
}
```

### VS Code

[![Install in VS Code](https://img.shields.io/badge/VS_Code-Install_Close_Knit-0098FF?logo=visualstudiocode&logoColor=white)](https://vscode.dev/redirect/mcp/install?name=close-knit&config=%7B%22type%22%3A%22http%22%2C%22url%22%3A%22https%3A%2F%2Fgetcloseknit.com%2Fmcp%22%7D)

Or run **MCP: Add Server** from the Command Palette, choose **HTTP**, and enter `https://getcloseknit.com/mcp`. In `.vscode/mcp.json`:

```json
{
  "servers": {
    "close-knit": {
      "type": "http",
      "url": "https://getcloseknit.com/mcp"
    }
  }
}
```

### Perplexity

1. Open **Plugins** in the sidebar (or **Customize > Connectors**).
2. Select **Add custom**, then **Connector**, then **Add MCP connector**, and choose **Remote**.
3. Name: `Close Knit`. MCP Server URL: `https://getcloseknit.com/mcp`.
4. Authentication: **None**. Transport: **Streamable HTTP**.
5. Tick the acknowledgement box, click **Add**, then click the connector card to enable it.

### Mistral Le Chat

1. Open the **Connectors** page.
2. Click **+ Add Connector** and switch to the **Custom MCP Connector** tab.
3. Connector name: `closeknit`. Server URL: `https://getcloseknit.com/mcp`.
4. Click **Connect**. No authentication is needed.

Adding a connector needs an administrator; on Free, Pro and Student plans the account owner is the administrator.

### Grok

1. Go to grok.com/connectors.
2. Click **New Connector**, then select **Custom**.
3. Enter `https://getcloseknit.com/mcp`.

On Business and Enterprise plans a team admin adds connectors first.

### Windsurf (Devin Desktop)

In the Cascade panel, open the **...** menu, and in the MCPs section click **Open MCP config file**. Add:

```json
{
  "mcpServers": {
    "close-knit": {
      "serverUrl": "https://getcloseknit.com/mcp"
    }
  }
}
```

Save the file.

### Goose

Desktop: open **Extensions** in the sidebar, click **Add custom extension**, choose the Streamable HTTP type and enter `https://getcloseknit.com/mcp`.

CLI: run `goose configure`, choose **Add Extension**, then **Remote Extension (Streamable HTTP)**, and enter the URL. For a single session:

```bash
goose session --with-streamable-http-extension "https://getcloseknit.com/mcp"
```

### LM Studio

[![Add Close Knit to LM Studio](https://files.lmstudio.ai/deeplink/mcp-install-dark.svg)](https://lmstudio.ai/install-mcp?name=close-knit&config=eyJ1cmwiOiJodHRwczovL2dldGNsb3Nla25pdC5jb20vbWNwIn0%3D)

Or open the **Program** tab in the right-hand sidebar, click **Install > Edit mcp.json**, and add:

```json
{
  "mcpServers": {
    "close-knit": {
      "url": "https://getcloseknit.com/mcp"
    }
  }
}
```

## Data and licences

The answers come from official open data, mostly under the Open Government Licence v3.0: HM Land Registry Price Paid Data and UK House Price Index, ONS Census 2021 and other ONS statistics, police.uk street crime, Ofsted and Department for Education school data, Environment Agency flood risk, Defra noise maps, Ordnance Survey OpenData, Transport for London open data ("Powered by TfL Open Data") and OpenStreetMap (© OpenStreetMap contributors, ODbL 1.0). Each answer lists its own sources and licences in `sources[]`; keep those attributions when you reuse the data.

The MIT licence in this repository covers the files in this repository only. The data served by the MCP server keeps its own licences.

## Privacy

No account and no personal data are needed. `send_feedback` only sends what you write, and only after you agree.

## Licence

[MIT](LICENSE)
