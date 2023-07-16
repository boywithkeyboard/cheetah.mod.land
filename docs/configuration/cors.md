---
title: CORS
description: Configure CORS for your application.
order: 3
---

cheetah has built-in support for [CORS](https://developer.mozilla.org/en-US/docs/Web/HTTP/CORS). You can configure it according to the [specification](https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/Access-Control-Allow-Origin) of the `Access-Control-Allow-Origin` header.

## Global

```ts
import cheetah from 'https://deno.land/x/cheetah/mod.ts'

const app = new cheetah({
  cors: '*'
})
```

## Per Collection

```ts
import cheetah, { Collection } from 'https://deno.land/x/cheetah/mod.ts'

const collection = new Collection({
  cors: 'example.com'
})
```

## Per Route

```ts
import cheetah from 'https://deno.land/x/cheetah/mod.ts'

const app = new cheetah()

app.get('/foo', {
  cors: 'example.com'
}, () => {
  // handle request
})
```
