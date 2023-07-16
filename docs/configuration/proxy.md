---
title: Proxy
order: 5
---

If you're using Cloudflare as a proxy, you should confirm it with this setting in order to unleash the full potential of cheetah.

This setting is mandatory to get the proper geolocation data with the [`LocationData`](/docs/accessories/location-data/) module and to retrieve the correct IP address with [`c.req.ip`](/docs/api/request/#get-ip-address). {.tip}

```ts
import cheetah from 'https://deno.land/x/cheetah/mod.ts'

const app = new cheetah({
  proxy: 'cloudflare'
})
```
