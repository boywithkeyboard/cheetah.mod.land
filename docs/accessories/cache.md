---
title: Cache
order: 2
---

This module offers you a convenient way to store and retrieve data from the [Cache API](https://developer.mozilla.org/en-US/docs/Web/API/Cache).

This module is specifically designed for Cloudflare Workers as Deno Deploy doesn't support the [Cache API](https://developer.mozilla.org/en-US/docs/Web/API/Cache) at the moment. {.tip}

## Initialize cache

```ts
import cheetah from 'https://deno.land/x/cheetah/mod.ts'
import { Cache } from 'https://deno.land/x/cheetah/x/mod.ts'

const app = new cheetah()

app.get('/', (c) => {
  const cache = new Cache({
    name: 'custom',
    maxAge: 900
  })
})
```

### Options:

- `name` - A unique name for your cache (defaults to `cheetah`).
- `maxAge` - Duration in seconds for how long a response should be cached (defaults to `600`).

## Add item to cache

```ts
await cache.set('custom', { foo: 'bar' })
```

## Retrieve item from cache

```ts
const value = await cache.get<{ foo: 'bar' }>('custom', 'json')

console.log(value) // { foo: 'bar' }
```

## Check whether cache has item

```ts
console.log(await cache.has('custom')) // true
console.log(await cache.has('non-existent')) // false
```

## Remove item from cache

```ts
await cache.delete('custom')
```
