---
title: Create Extension
order: 6
---

## Write an extension

If you create a extension that might be useful for other people, make sure to [open a issue](https://github.com/azurystudio/cheetah/issues/new) about it.

```ts
import cheetah, { createExtension } from 'https://deno.land/x/cheetah/mod.ts'

export const ext = createExtension<{
  // The settings for your extension:
  foo: string
}>({
  onRequest({ _, app, req }) {
    ...
  }
})
```

Alternatively, you can create one without settings:

```ts
import cheetah, { createExtension } from 'https://deno.land/x/cheetah/mod.ts'

export const ext = createExtension({
  onRequest({ _, app, req }) { // access context to modify request/response
    ...
  }
})
```

## Events

### `onPlugIn`

This listener gets only executed on the first incoming request (in order to include environment variables on Cloudflare Workers).

### `onRequest`

This listener gets executed **before any routing** to allow for full flexibility.

**The data consists of:**

- `_` - The settings object you've specified. If all fields in your settings object are optional, it might be undefined.
- `app` - The app context including information such as a set of all routes, the IP address of the incoming request, the runtime, environment variables (if runtime is Cloudflare), the querystring & pathname and the proxy.
- `req` - The [`Request`](https://developer.mozilla.org/en-US/docs/Web/API/Request) object.

### `onResponse`

This listener gets executed **just before a response is constructed**.

**The data consists of:**

- `_` - The settings object you've specified. If all fields in your settings object are optional, it might be undefined.
- `app` - The app context including information such as a set of all routes, the IP address of the incoming request, the runtime, environment variables (if runtime is Cloudflare), the querystring & pathname and the proxy.
- `c` - The context (including request, response and other already known features).
