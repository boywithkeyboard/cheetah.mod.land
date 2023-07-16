---
title: Preflight Mode
order: 2
---

If enabled, cheetah will attempt to find the matching `.get()` handler for an incoming HEAD request. Your existing `.head()` handlers won't be impacted.

```ts
import cheetah from 'https://deno.land/x/cheetah/mod.ts'

const app = new cheetah({
  preflight: true
})
```
