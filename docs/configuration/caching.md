---
title: Caching
description: Configure caching for your application.
order: 2
---

cheetah doesn't support caching for Deno at this time because it isn't yet implemented in Deno Deploy. {.tip}

cheetah has out-of-the-box support for caching using the [Cache API](https://developer.mozilla.org/en-US/docs/Web/API/Cache).

## Global

```ts
new cheetah({
  cache: {
    name: 'foo',
    maxAge: 600
  }
})
```

## Per Collection

```ts
new Collection({
  cache: {
    maxAge: 300
  }
})
```

## Per Route

```ts
.get('/foo', {
  cache: {
    maxAge: 0
  }
}, () => {
  // handle request
})
```
