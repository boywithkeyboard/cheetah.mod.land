---
title: Custom Error Pages
description: Optionally, you can customize error messages.
order: 3
---

## Custom Error Handler

```ts
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
const app = new cheetah({
  notFound(request) {
    return new Response('Not Found')
  }
})
```
