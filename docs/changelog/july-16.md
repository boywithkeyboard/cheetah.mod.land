---
title: v1.0
order: 2
---

## `cache` option is no longer available ⚠️

This option is vulnerable to misuse and can therefore cause serious vulnerabilities in your application. If you want to use the [Cache API](https://developer.mozilla.org/en-US/docs/Web/API/Cache) in a more human way, please use the new [`Cache` module](/docs/accessories/cache/).

## Removed helper functions from `c.res` ⚠️

`c.res.blob()`, `c.res.buffer()`, `c.res.formData()`, `c.res.json()`, `c.res.stream()`, `c.res.string()`, and `c.res.text()` have been removed.

Please use one of the following approaches to set the body of the response.

1. `c.res.body`
    
    ```ts
    app.get('/', (c) => {
      c.res.body = 'Hello World'
    })
    ```
  
2. `return`

    ```ts
    app.get('/', () => {
      return 'Hello World'
    })
    ```

## Removed support for TypeBox ⚠️

The `validator/...` namespace and the `validator` option are no longer available. zod is now used by default without any configuration required.

This change was made to simplify the internal code and allow for future flexibility.

## New Extensions API ⚠️

Plugins are no longer available. Use the new extensions instead, e.g. [`helmet`](/docs/extensions/helmet/):

```ts
import cheetah from 'https://deno.land/x/cheetah/mod.ts'
import { helmet } from 'https://deno.land/x/cheetah/ext/helmet.ts'

const app = new cheetah()
  .use(helmet())
```

> For end users, this really only means a change in the import path. If you're the developer of a extension for cheetah, this change requires a total rewrite of it. {.tip}

## New way to retrieve environment variables ⚠️

If you're using cheetah for Cloudflare Workers, you now have to retrieve environment variables through the new [`env` method](/docs/accessories/env/).

```ts
import { env } from 'https://deno.land/x/cheetah/x/mod.ts'

app.get('/', (c) => {
  const { foo } = env<{ foo: string }>(c)

  // ...
})
```

## Removed `debug` option ⚠️

The `debug` option is no longer available, instead you should use the [`debug` extension](/docs/extensions/debug/).

## No need for using `app.fetch` on Deno

The `app.serve()` function is the successor to `Deno.serve(app.fetch)`.

While `app.serve` is specifically meant for Deno, `app.fetch` is now purely meant for Cloudflare Workers (& for our internal testing).

```ts
import cheetah from 'https://deno.land/x/cheetah/mod.ts'

const app = new cheetah()
  .get('/', () => 'Hello World')

app.serve()
```

## Various new accessories

We've added various new accessories which should make it even easier for you to get started building something great.

- [`Cache`](/docs/accessories/cache/) - the new alternative to the original `cache` option.
- [`env`](/docs/accessories/env/) - a cross-runtime module for retrieving environment variables (especially useful for Cloudflare Workers).
- [`jsx`](/docs/accessories/jsx/) - a module for responding with a JSX component.
- [`LocationData`](/docs/accessories/location-data/) - a typesafe module for retrieving geolocation data.

## Various new extensions

As we've rewritten cheetah's Extensions API, we added several new extensions which might be pretty useful for you:

- [`compress`](/docs/extensions/compress/)
- [`debug`](/docs/extensions/debug/)

## Insignificant Changes

  - You can now retrieve the size of the currently set response body with [`c.res.bodySize`](/docs/api/response/#calculate-size-of-body).

  - You now have the option to retrieve a set of all your routes with `app.routes`.

  - The type of `c.req.method` is now more strict.
