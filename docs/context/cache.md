---
title: cache
order: 4
---

The cache utility can only be used on Cloudflare Workers at the moment. {.tip}

Before using it, you should set a unique name for your cache:

```ts
const app = new cheetah({
  cache: {
    name: 'example.com'
  }
})
```

## `set()`

```ts
c.cache.set(key, value, options)
```

```ts
app.get('/', c => {
  await c.cache.set('foo', 'bar', { maxAge: 600 }) // expires after 10 minutes

  await c.cache.set('foo', 'bar') // expires after 5 minutes
})
```

## `get()`

```ts
c.cache.get(key, type)
```

```ts
app.get('/', c => {
  await c.cache.get('foo', 'json')
})
```

## `has()`

```ts
c.cache.has(key)
```

```ts
app.get('/', c => {
  await c.cache.has('foo')
})
```

## `delete()`

```ts
c.cache.delete(key)
```

```ts
app.get('/', c => {
  await c.cache.delete('foo')
})
```
