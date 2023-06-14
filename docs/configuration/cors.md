---
title: CORS
description: Configure CORS for your application.
order: 4
---

cheetah has built-in support for [CORS](https://developer.mozilla.org/en-US/docs/Web/HTTP/CORS). You can configure it according to the [specification](https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/Access-Control-Allow-Origin) of the `Access-Control-Allow-Origin` header.

## Global

```ts
new cheetah({
  cors: '*'
})
```

## Per Collection

```ts
new Collection({
  cors: 'foo.com'
})
```

## Per Route

```ts
.get('/foo', {
  cors: 'bar.com'
}, () => {
  // handle request
})
```
