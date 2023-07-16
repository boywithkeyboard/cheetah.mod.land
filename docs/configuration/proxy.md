---
title: Proxy
order: 5
---

If you're using Cloudflare as a proxy, you should confirm it with this setting in order to unleash the full potential of cheetah.

```ts
import cheetah from 'https://deno.land/x/cheetah/mod.ts'

const app = new cheetah({
  proxy: 'cloudflare'
})
```
