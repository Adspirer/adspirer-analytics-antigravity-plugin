# Adspirer Marketing Analytics for Antigravity

Ask the agent how your marketing is doing and get answers from your real accounts. Adspirer Marketing Analytics is read-only: it reports spend, clicks, conversions, CPA and ROAS by channel and blended across channels, diagnoses funnels and attribution, audits conversion tracking, and reads Google Analytics 4, Search Console and Tag Manager. It cannot create, change, pause or delete anything.

## Use it for

- **Cross-channel reporting:** spend, conversions, CPA and ROAS by channel with a blended total, for any period you name.
- **Attribution and funnels:** find where the funnel breaks, from ad click to site conversion.
- **Web analytics:** Google Analytics 4 traffic and conversions, Search Console queries and pages, and Tag Manager setup.
- **Tracking audits:** grade conversion tracking across ad platforms, GA4, Tag Manager and the Meta Pixel.
- **Wasted spend:** search terms, keywords, placements and audiences spending without converting.
- **Competitors:** the public ads a competitor is running now.

## Install

**Antigravity app:** open **Customizations**, find **Adspirer Marketing Analytics** in the
Marketplace, and install it.

**Antigravity CLI:**

```text
agy plugin install https://github.com/Adspirer/adspirer-analytics-antigravity-plugin
```

**Manual:** clone this repository into your plugins folder.

```text
git clone https://github.com/Adspirer/adspirer-analytics-antigravity-plugin ~/.gemini/config/plugins/adspirer-analytics
```

Then sign in: open **Customizations**, then **Installed**, then **MCP Servers**, and choose
**Authenticate** next to the Adspirer server. Sign in to Adspirer in the browser, then connect the
accounts you want to report on at [adspirer.ai/connections](https://adspirer.ai/connections). No
API key or client secret is required. An Adspirer account is required, and plan usage limits apply.

## Get started

Ask:

```text
Show spend, conversions, CPA and ROAS by channel for the last complete 30 days, with a blended total.
Which Search Console queries and pages lost the most clicks this month?
Walk my conversion funnel and tell me where it breaks.
Audit my GA4 and Meta Pixel tracking.
```

Or start with a skill by name:

| Skill | What it does |
| --- | --- |
| `/adspirer-analytics-setup` | Connect your accounts and get a first look |
| `/adspirer-analytics-status` | Connected accounts and remaining plan usage |
| `/adspirer-analytics-performance-review` | Scorecard against the previous period, with the top changes |
| `/adspirer-analytics-wasted-spend` | Spend that is not converting, with a fix proposed for each item |
| `/adspirer-analytics-tracking-audit` | Grade conversion tracking and list the gaps |

Add a platform and period if you want, for example `/adspirer-analytics-performance-review last 7 days`.

## What it covers

| Area | Capabilities |
| --- | --- |
| Ad platforms | Google, Meta, TikTok, LinkedIn, Amazon, Microsoft, ChatGPT and Walmart Ads performance |
| Web analytics | Google Analytics 4, Search Console and Tag Manager |
| Diagnostics | Funnel diagnosis, conversion-tracking audit, and wasted-spend analysis |
| Competitor research | Public competitor ads |

This plugin is read-only by design. Requests to create, pause, change budgets, submit URLs for
indexing or edit tags are declined.

## What's included

- **Skills** (`skills/`): the five entry points above, plus `adspirer-analytics-attribution`,
  `adspirer-analytics-competitor-research`, `adspirer-analytics-conversion-tracking`,
  `adspirer-analytics-cross-channel`, `adspirer-analytics-platform-reports`,
  `adspirer-analytics-product-help`, `adspirer-analytics-strategy`, `adspirer-analytics-tools` and
  `adspirer-analytics-web-analytics`, which the agent loads when a request needs them.
- **A rule** (`rules/adspirer-analytics.md`) that loads only for marketing-analytics requests and
  keeps the agent read-only.
- **The Adspirer Marketing Analytics MCP server** connection (`mcp_config.json`).

The hosted server is the source of truth for tool names and schemas. The skills teach the agent to
discover the current tools and their parameters instead of hardcoding every operation.

## Safety

- **No writes.** The plugin cannot create, change, pause, resume or delete anything.
- **No purchases.** The agent never buys, upgrades or renews a plan or paid feature. If a plan limit
  is reached, it stops and explains the limit.
- **Confirmation first** before quota-heavy runs, such as reporting on every account or property.
- **Honest numbers.** Currency, dates, attribution window and data freshness are stated; ratios are
  computed from totals; missing data is never reported as zero; platform-attributed revenue is not
  treated as incremental profit; competitor research covers public ads only.

## MCP and authentication

```json
{
  "mcpServers": {
    "analytics": {
      "url": "https://mcp.adspirer.com/analytics"
    }
  }
}
```

The server speaks Streamable HTTP. Authentication uses OAuth 2.1 with PKCE and dynamic client
registration, so Antigravity handles the browser sign-in and the plugin contains no API keys,
tokens, client secrets, or configuration variables. Ad-platform credentials stay server-side with
Adspirer and are scoped to the accounts you connect.

## Network and execution surface

The plugin's only MCP server is `https://mcp.adspirer.com/analytics`. It contains no hooks,
scripts, telemetry, local executables, or bundled server code. Skills and the rule are Markdown
guidance. Beyond the Adspirer server, the skills may ask the agent to read Adspirer's public
documentation at `adspirer.com/docs` to answer questions about plans and setup.

## Privacy, support, and source

- Privacy policy: [adspirer.com/privacy](https://www.adspirer.com/privacy)
- Terms: [adspirer.com/terms](https://www.adspirer.com/terms)
- Documentation: [adspirer.com/docs](https://www.adspirer.com/docs)
- Support: [support@adspirer.com](mailto:support@adspirer.com)
- Issues: [github.com/Adspirer/adspirer-analytics-antigravity-plugin/issues](https://github.com/Adspirer/adspirer-analytics-antigravity-plugin/issues)

## License

MIT. See [LICENSE](LICENSE).
