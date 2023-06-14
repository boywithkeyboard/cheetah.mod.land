---
title: Preflight Mode
order: 6
---

If enabled, cheetah will attempt to find the matching `.get()` handler for an incoming HEAD request. Your existing `.head()` handlers won't be impacted.

```ts
new cheetah({
  preflight: true
})
```
