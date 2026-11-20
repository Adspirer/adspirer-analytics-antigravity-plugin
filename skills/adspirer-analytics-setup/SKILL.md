---
name: adspirer-analytics-setup
description: "Connect and choose the ad accounts, GA4 properties, Search Console sites and Tag Manager containers to report on. Use when the user asks what is connected, which account or property to use, how to link a platform, or sees a not-connected or auth error."
---

# Account and property setup

Load adspirer-analytics-tools. Let the user finish browser OAuth; never request credentials in chat.
Call get_connections_status to see connected ad accounts and analytics properties. Where a platform
needs resolution, use its read router's list/discovery operation (for example list accounts,
list properties, list sites) to find the real id.

Resolve the intended account, marketplace, currency, timezone, GA4 property, Search Console site or
GTM container the user wants reported on. Picking which account to read from is not a write and
needs no activation: just pass the chosen id to the read tools. This connector has no
activate/switch-account tool.

Direct connection questions to https://adspirer.ai/connections and current official docs. Ad
platforms and Google Analytics use OAuth; do not describe every connection identically, and point
users to Settings → Connections to authorize a platform or analytics property they haven't linked.

## First run

1. Call get_connections_status. If it fails because the connector is not signed in, tell the user
   to sign in to Adspirer Marketing Analytics (in Antigravity: open Customizations, then Installed, then MCP Servers, and choose Authenticate),
   then stop and wait. Never ask for a password or token in chat.
2. List what is connected: ad accounts by platform, GA4 properties, Search Console sites and Tag
   Manager containers.
3. If something the user wants is missing, give them https://adspirer.ai/connections and wait.
4. Take a first look at the last 30 days on each connected ad platform, using the campaign
   performance operation for that platform (see references/common-operations.md in
   adspirer-analytics-platform-reports). Skip a platform that is not connected; do not invent
   numbers for it.
5. Finish with a short summary: what is connected, what is not, spend and conversions for each
   platform, and what to try next: /adspirer-analytics-performance-review for a cross-channel
   scorecard, /adspirer-analytics-wasted-spend, or /adspirer-analytics-tracking-audit.

## Optional workspace

Do not require setup for a simple question. Read only user-designated brand/product files; never
recursively ingest unrelated files or secrets.
With explicit permission, create or update BRAND.md and STRATEGY.md while preserving existing
content. Ask before appending to unrelated files. Record accounts, properties, currency, timezone,
goals, target metrics and attribution conventions as reporting context, not as authorization to
change anything.
Use actual read-only snapshots; mark missing data. Create a private decision log only on request,
never credentials or raw personal data.
Finish with connections, evidence, gaps and actual files saved, then resume the original request.
