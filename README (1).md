# OlaChill for DeepSeek Harness

Find and price Japan travel services from [OlaChill](https://olachill.com) inside
[DeepSeek Harness (dsh)](https://github.com/deepseek-ai/deepseek-harness): tours and day trips,
activities, attraction and transport tickets, ryokan, private airport transfers, cars with
driver, charter buses, helicopter flights, golf and Japan eSIM.

It uses dsh's built-in MCP client (`@deepseek-ai/dsh-mcp-client`) to connect to OlaChill's
public MCP server at `https://olachill.com/mcp`. No API key is needed.

## Install

Add this entry to your `cordis.yml` (or a profile patch such as
`~/.dsh/profiles/web/cordis.patch.yml`), then restart dsh:

```yaml
- id: mcp-olachill
  name: '@deepseek-ai/dsh-mcp-client'
  config:
    serverName: olachill
    transport: streamable-http
    url: https://olachill.com/mcp
    toolCallTimeoutMs: 30000
```

The same snippet is in [`cordis.olachill.yml`](cordis.olachill.yml).
The model then sees 13 tools named `mcp__olachill__<tool>`.

## Example prompts

- "Private transfer from Kansai Airport to Namba for 4 people"
- "Day tour to Mt Fuji from Tokyo next Saturday for 2 adults"
- "Helicopter night flight over Tokyo"
- "Alphard with driver for a full day in Kyoto for 5 people"
- "Unlimited data eSIM for 10 days in Japan"
- "东京到富士山一日游，2位成人"
- "成田机场到新宿的专车接送，3人"

## Tools

| Tool | What it does |
|---|---|
| `recommend_japan_travel_options` | Shortlist of tours, activities, tickets or ryokan from preferences |
| `search_travel_products` | Search tours, activities, tickets and ryokan |
| `check_product_availability` | Dates and availability for a product |
| `search_helicopter_experiences` | Helicopter sightseeing, charter and transfer |
| `search_private_transfers` | Private airport transfers with driver |
| `search_charter_vehicles` | Buses, coaches, minibuses and vans with driver |
| `get_charter_quote` | Estimate for a charter itinerary |
| `request_charter_quote` | Send a quote request (only after the traveller agrees) |
| `search_chauffeur_services` | Cars with driver by the day or hour |
| `search_golf_packages` | Golf rounds and golf trips |
| `search_esim_plans` | Japan eSIM data plans |
| `get_booking_status` | Status of an existing booking or request |
| `list_olachill_services` | Overview of OlaChill services |

Prices are "from" prices or estimates; final price and availability are confirmed on
olachill.com. Only send a quote request after the traveller explicitly agrees.

## Contact

partners@olachill.com · https://olachill.com
