---
title: v1.1
order: 1
---

## New `favicon` & `pretty` extension

The [`favicon`](/docs/extensions/favicon/) extension serves a favicon for `/favicon.ico` and the [`pretty`](/docs/extensions/pretty/) extension jazzes up your (JSON) response body by adding indentation and sorting the keys alphabetically.

## `transform` option has been moved to `c.req.body()`

The old way has been deprecated and will be removed in v2.0! {.tip}

<lume-code>

```ts { title="Now" }
import cheetah from 'https://deno.land/x/cheetah/mod.ts'
import { z } from 'https://deno.land/x/zod/mod.ts'

const app = new cheetah()

app.get('/', {
  body: z.object({
    foo: z.string()
  })
}, async (c) => {
  console.log(await c.req.body({ transform: true })) // e.g. { foo: 'bar' }
})
```

```ts { title="Before" }
import cheetah from 'https://deno.land/x/cheetah/mod.ts'
import { z } from 'https://deno.land/x/zod/mod.ts'

const app = new cheetah()

app.get('/', {
  body: z.object({
    foo: z.string()
  }),
  transform: true
}, async (c) => {
  console.log(await c.req.body()) // e.g. { foo: 'bar' }
})
```

</lume-code>

## New `c.req.json()` and `c.req.text()` methods

These methods are intended for *unsafe* parsing, so use them only if you haven't specified a validation scheme.

## App context now includes querystring and pathname

When working on an extension, you can now access the querystring and pathname of the incoming request directly from the app context.
