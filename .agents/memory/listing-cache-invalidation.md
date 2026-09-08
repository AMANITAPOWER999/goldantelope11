---
name: Listing cache invalidation
description: Freshness requirements for listings written by background parsers.
---

When a background parser writes a country listings JSON file, invalidate the raw country cache, filtered response cache, combined init cache, and logo cache for that country. Public listing and init responses should not tell browsers to retain stale data.

**Why:** Parsers write files outside the request handlers; clearing only the raw data cache left old listing responses visible for several minutes.

**How to apply:** Route every background write through the shared invalidation helper, and keep client cache headers non-persistent for listing freshness.