<p align="center"><img src="deepread-icon.png" width="96" alt="Deepread"></p>

# Deepread MCP server

**Customer and commercial intelligence for BigCommerce stores, in your AI assistant.** Ask Claude (or any MCP client) who is likely to stop buying, who is due to reorder, what each customer is worth, what to upsell, which products sell together, why revenue changed, where profit leaks, and which B2B accounts to call today. Retail (B2C) and wholesale (B2B) customers are always answered separately.

This is a **hosted, remote MCP server** (Streamable HTTP, OAuth 2.1). There is nothing to install or run locally. This repository holds the listing and documentation only; the server itself is operated by Fundas LLC.

```
https://riseiq-bigcommerce-production.up.railway.app/mcp
```

## What you need

1. A **BigCommerce** store (retail, Multi-Storefront or B2B Edition).
2. The **Deepread** app installed from the [BigCommerce App Marketplace](https://www.bigcommerce.com/apps/riseiq/), with an active free trial or subscription. Deepread analyzes your order history after install; the connector answers from that analysis.

No API keys or environment variables. You sign in through OAuth and approve the connection inside Deepread.

## Connect

**Claude (web, desktop, mobile):** Settings → Connectors → find **Deepread** in the directory (or *Add custom connector* and paste the URL above) → **Connect**. On Deepread's sign-in page, click **Open Deepread in BigCommerce**, then **Allow** inside Deepread. The Claude window finishes connecting on its own.

**Claude Code:**

```bash
claude mcp add --transport http deepread https://riseiq-bigcommerce-production.up.railway.app/mcp
```

Then run `/mcp` to sign in.

**Other MCP clients (ChatGPT, Cursor and others):** add a remote MCP server with the URL above and follow the same sign-in.

If you are signing in on a different device from your BigCommerce admin, use **Have a connect code instead?** on the sign-in page and generate a one-time code in Deepread → Settings → AI assistants.

## What it can do

Read-only by default:

| Area | Tools |
|---|---|
| Customers | `list_at_risk_customers`, `list_reorder_due`, `list_upsell_opportunities`, `get_value_tracker`, `get_winback_status` |
| Products and revenue | `get_product_affinities`, `get_product_momentum`, `get_sales_patterns`, `explain_revenue_change`, `get_ai_channel_sales`, `get_store_overview` |
| Profit | `get_profit_summary`, `list_margin_leaks`, `get_distribution_kpis` |
| Wholesale (B2B) | `list_accounts_to_call`, `get_company_detail`, `list_payment_risks`, `list_reorder_quote_proposals`, `list_category_drops` |
| Status | `get_deepread_capabilities`, `get_setup_status`, `list_suggested_actions`, `list_flows`, `get_agent_activity` |

If the merchant allows changes when connecting, the assistant can also update lists kept inside Deepread (mark B2B accounts called, pin or snooze them, dismiss or snooze alerts and suggestions, skip quote proposals).

Tools that reach customers or the storefront (Klaviyo campaigns and flows, storefront widgets, recommendation exclusions, B2B Edition reorder quotes) appear only after the merchant turns each group on in Deepread. Every such change is previewed, needs the merchant's explicit yes through a single-use confirmation, has daily limits and is logged.

## Privacy

- Customers are identified by BigCommerce ID unless the merchant turns on names. Names and emails are then fetched live for the rows returned and never stored.
- The connection is tied to one store, chosen inside the merchant's own BigCommerce admin, never by the assistant.
- Merchants can see every assistant call in Deepread → Settings → AI assistants → Activity, and disconnect any assistant there.

[Privacy policy](https://www.fundas.ai/privacy) · [Terms](https://www.fundas.ai/terms-conditions) · [Connector documentation](https://riseiq-bigcommerce-production.up.railway.app/connect-ai)

## Links

- Product: [fundas.ai/deepread](https://www.fundas.ai/deepread)
- BigCommerce app: [bigcommerce.com/apps/riseiq](https://www.bigcommerce.com/apps/riseiq/)
- MCP Registry: `ai.fundas/deepread`
- Support: deepread@fundas.ai

Deepread (formerly RiseIQ) is a product of Fundas LLC.
