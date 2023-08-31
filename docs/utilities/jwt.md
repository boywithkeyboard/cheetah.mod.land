---
title: JWT
order: 5
---

```ts
import { jwt } from 'https://deno.land/x/cheetah/mod.ts'
```

## Generate a Secret

You can parse either a [CryptoKey](https://developer.mozilla.org/en-US/docs/Web/API/CryptoKey) as secret to the listed functions below, or [use the CLI to generate a random secret](/docs/cli/random/) that can be stored in a database. You can also store the generated secret in the `JWT_SECRET` environment variable and pass the context instead to it as secret.

## Sign a Payload

 ```ts
const token = await jwt.sign(secret, payload)
```

## Verify the Validity of a JWT

The function returns the payload if the token is valid and `undefined` if it isn't.

```ts
const payload = await jwt.verify(secret, token)
```
