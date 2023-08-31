---
title: OAuth
order: 9
---

## Sneak Peek

Please don't forget to set the `JWT_SECRET` environment variable if you want to use the oauth module. {.tip}

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

## Security

The oauth module stores the token by default in a http-only, secure cookie (named `token`). The JWT, cookie and session have a max age of 7d. The session stores the IP address of the user on login and if it doesn't match on a `getSessionData()`, `getSessionId()`, or `isSignedIn()` call, the session will automatically be terminated and the cookie deleted.

We therefore strongly recommend to listen for sign out events, by adding a listener:

```ts
const app = new cheetah({
  oauth: {
    ...,
    onSignOut(c, identifier) { // < the identifier of the terminated session
      // do something
    }
  }
})
```

## Stores

- `kv` (leverages Deno KV or Cloudflare KV, depending on the runtime)

  **Environment variable:** `oauth` *(only for Cloudflare KV)*

- `upstash` (uses [Upstash Redis](https://github.com/upstash/upstash-redis))

  **Environment variables:** `UPSTASH_URL`, `UPSTASH_TOKEN`

## Providers

- `GitHub`

  **Environment variables:** `GITHUB_CLIENT_ID`, `GITHUB_CLIENT_SECRET`

- `Google`

  **Environment variables:** `GOOGLE_CLIENT_ID`, `GOOGLE_CLIENT_SECRET`

## `getSessionData`

Get the data associated with the current session if logged in.

```ts
const data = await getSessionData(c)

console.log(data) // object | undefined
```

## `getSessionId`

Get the session identifier and verify it.

```ts
const id = await getSessionId(c)

console.log(id) // string | undefined
```

## `getSessionToken`

Get the session token without verifying the session.

```ts
const token = await getSessionToken(c)

console.log(token) // string | undefined
```

## `handleCallback`

Complete the login flow.

```ts
await handleCallback(c, GitHub)
```

## `isSignedIn`

Check if the user is logged in.

```ts
await isSignedIn(c) ? 'signed in' : 'signed out'
```

## `signIn`

Start the login flow by redirecting the user.

```ts
await signIn(c, GitHub, {
  redirectUri: '...',
  scopes: ['...']
})
```

## `signOut`

Sign the user out if they're logged in.

```ts
await signOut(c)
```
