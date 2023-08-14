---
title: v1.3
order: 4
---

## New `oauth` namespace

The new oauth namespace gives you a simple, cross-runtime way to sign users in/out through OAuth 2.0.

```ts
import cheetah from 'https://deno.land/x/cheetah/mod.ts'
import { GitHub, handleCallback, isSignedIn, kv, signIn, signOut } from 'https://deno.land/x/cheetah/oauth/mod.ts'

const app = new cheetah({
  oauth: {
    store: kv // < Deno or Cloudflare KV, depending on the runtime
  }
})

app.get('/', async c => {
  return await isSignedIn(c) ? 'Hey there! ✌️' : 'Please sign in first! 👤'
})

app.get('/oauth/login', async c => {
  await signIn(c, GitHub, {  // <- initialize login with GitHub
    redirectUri: 'http://localhost:8000/oauth/callback'
  })
})

app.get('/oauth/callback', async c => {
  const data = await handleCallback(c, GitHub) // <- complete login with GitHub

  return data
})

app.get('/oauth/logout', async c => {
  await signOut(c)
})

app.serve()
```

You can learn more about it [here](https://cheetah.mod.land/docs/api/oauth/).

## Debug mode

You can now enable error logging.

```ts
const app = new cheetah({
  debug: true
})
```

## New `getVariable()` method

The `x/env.ts` module now has a new `getVariable()` method for retrieving just a single environment variable.

```ts
import { getVariable } from 'https://deno.land/x/cheetah/x/env.ts'

...

app.get('/', c => {
  const value = getVariable<string>(c, 'SOME_VARIABLE')

  ...
})

...
```

## Fixed parsing of connection info on Deno

There was an issue which gave you `null` instead of the actual IP address of the incoming request.

## Fixed types of `c.req.headers` when no schema defined

The `c.req.headers` had the type `any`, which is now resolved.

## `ext/files.ts` now attaches a etag & cache-control header

The `files` extension now attaches a `etag` & `cache-control` header without further action on your side required.


