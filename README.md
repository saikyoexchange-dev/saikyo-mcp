# SAIKYO MCP server

Remote [Model Context Protocol](https://modelcontextprotocol.io) server of **SAIKYO Exchange** (saikyo.exchange): live USDT/RUB rate, exchange quotes, wallet AML screening and guides to paying for foreign services from Russia. Free, read-only, no API key.

- **Server URL (Streamable HTTP):** `https://saikyo.exchange/api/mcp`
- **Docs:** https://saikyo.exchange/en/mcp-server (RU: https://saikyo.exchange/mcp-server)
- **OpenAPI 3.1 (REST equivalents, works with Custom GPT Actions):** https://saikyo.exchange/openapi.json
- **Official MCP Registry:** `exchange.saikyo/saikyo`
- **llms.txt:** https://saikyo.exchange/llms.txt

## Connect

```json
{
  "mcpServers": {
    "saikyo": { "url": "https://saikyo.exchange/api/mcp" }
  }
}
```

Claude Code: `claude mcp add --transport http saikyo https://saikyo.exchange/api/mcp`

## Tools

| Tool | What it returns |
| --- | --- |
| `get_usdt_rub_rate` | SAIKYO rate for buying USDT (TRC20) with rubles via SBP QR + market reference |
| `list_exchange_directions` | Verified exchange directions with live rate, limits, reserve and order link |
| `find_exchange_route` | Resolves RU/EN currency terms (рубли, СБП, USDT, TRC20) to a live quote |
| `calculate_exchange` | Exact quote: rate, amounts, limits, reserve, order link |
| `start_exchange_order` | Live quote + prefilled order link; the user confirms on the site (the agent never submits orders) |
| `check_wallet_aml` | Indicative AML screening for TRON, EVM, Bitcoin and TON addresses (rate-limited) |
| `get_exchanger_info` | Published SAIKYO facts with source URLs: domains, support, hours, AML/KYC |
| `get_foreign_card_terms` | Omega Wallet virtual Visa terms for residents of Russia |
| `how_to_pay_from_russia` | Payment options and guides for 1,000+ foreign services |
| `get_payment_passport` | Payment facts for 900+ services from official pages |
| `travel_card_for_country` | Card payment tips for travel destinations |
| `search_saikyo_shop` | Saikyo Shop digital goods priced in rubles |

Quotes are indicative; the final rate and amount are shown in the order form before payment. Only the verified direction (RUB via SBP QR → USDT TRC20) is quoted, so the agent never invents prices for other pairs.

## REST

Same data over GET, JSON responses, CORS enabled, e.g. `https://saikyo.exchange/api/public/exchange-quote?amount=10000`.

## Terms

Free and read-only: orders, payments and personal data are not accessible through it. Requests are rate-limited. When citing, credit the source: SAIKYO (saikyo.exchange).
