---
title: v1.4
order: 5
---

## New `c.res.setCookie()` & `c.res.deleteCookie()` methods

Please use `c.res.setCookie()` instead of `c.res.cookie()`.

## New `c.exception()` method

As the original `Exception` class was already used internally in cheetah's core, it only made sense to move a enhanced variant of this method to the context object.

## New `c.dev` variable

If you run your app through the new `cheetah serve` command or enable the `debug` option for your app, this variable will be automatically set to `true`.

## New `c.env()` method

This method gives you a much better way to retrieve environment variables across runtimes.

## New `encrypt()` & `decrypt()` methods

Encrypting and decrypting messages has never been easier.

## New JSX renderer

```tsx
import cheetah, { Renderer } from 'https://deno.land/x/cheetah@v1.4.0/mod.ts'

const { render } = new Renderer()

const app = new cheetah()
  .get('/', c => {
    const Hello = () => {
      return <p>Hello, world!</p>
    }

    render(<Hello />)
  })

  .serve()
```

Under the hood, this module leverages [twind](https://twind.dev) for styling your components.

## Versioning is now available for your API

```ts
import cheetah from 'https://deno.land/x/cheetah@v1.4.0/mod.ts'

const app = new cheetah({
  versioning: {
    current: 'v4',
    type: 'uri'
  }
})
  .get('/', {
    gateway: '> v2'
  }, c => {
    console.log(c.gateway) // 3 | 4
  })

  .serve()
```

## Option to add a validation schema for `c.req.param()`

```ts
import { z } from 'https://deno.land/x/zod@v3.22.2/mod.ts'

app.get('/users/:username', {
  params: {
    username: z.string().min(4).max(16)
  }
}, c => {
  const username = c.req.param('username') // retrieve the validated username

  // do something
})
```

## All accessories are now available in the root directory

The x/ directory has been deprecated & the new modules might differ a bit in their format.

Please import all the utility features directly from the main file, e.g. the `LocationData` class:

```ts
import { LocationData } from 'https://deno.land/x/cheetah@v1.4.0/mod.ts'
```
