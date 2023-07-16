---
title: env
order: 1
---

This module offers you a convenient and type-safe way to retrieve environment variables on Cloudflare Workers (and Deno).

This module is specifically designed for Cloudflare Workers. {.tip}

```ts
import app from 'https://deno.land/x/cheetah/mod.ts'
import { env } from 'https://deno.land/x/cheetah/x/env.ts'

const app = new cheetah()

app.get('/', (c) => {
  const { foo } = env<{ foo: string }>(c)

  console.log(foo) // e.g. 'bar'
})
```
