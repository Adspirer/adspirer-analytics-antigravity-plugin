---
name: adspirer-analytics-tracking-audit
description: "Read-only audit that grades conversion tracking across ad platforms, GA4, Tag Manager and the Meta Pixel, and lists the gaps to fix. Use when the user asks whether conversions are tracked correctly or why conversion numbers look wrong."
---

# Conversion-tracking audit

Load adspirer-analytics-tools and adspirer-analytics-conversion-tracking.

1. Confirm which channels and, if relevant, which GA4 property and Tag Manager container to
   inspect.
2. Run audit_conversion_tracking. If its card is not visible to the user, summarize it in text.
3. Corroborate with reads: platform conversion actions and recent conversion counts, GA4 key
   events, Tag Manager tags and Meta Pixel stats.
4. Report per channel: what is tracked, the grade, what looks missing or misconfigured, the
   evidence, and the fix the user would apply in their own tools.

Tell "zero conversions" apart from "no tracking". This skill changes no tag, pixel or conversion
action, and cannot confirm a fix until a later read.
