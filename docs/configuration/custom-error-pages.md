---
title: Custom Error Pages
description: Optionally, you can customize error messages.
order: 4
---

## Custom Error Handler

```ts
import cheetah from 'https://deno.land/x/cheetah/mod.ts'

const app = new cheetah({
  error(error, request) {
    if (error instanceof Error)
      return new Response(error.message)

    return new Response('Unknown Error')
  }
})
```

## Custom Not Found Handler

```ts
import cheetah from 'https://deno.land/x/cheetah/mod.ts'

const app = new cheetah({
  notFound(request) {
    return new Response('Not Found')
  }
})
```
