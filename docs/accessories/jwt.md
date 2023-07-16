---
title: jwt
order: 5
---

```ts
import { jwt } from 'https://deno.land/x/cheetah/x/mod.ts'
```

## Generate a secret

You can parse either a [CryptoKey](https://developer.mozilla.org/en-US/docs/Web/API/CryptoKey) as secret to the listed functions below, or use the following method to generate a string which you can store in a database.

This key can then be parsed to the functions.

```ts
import { createKey } from 'https://deno.land/x/cheetah/x/mod.ts'

const key = await createKey()
```

## Sign a payload

 ```ts
const token = await jwt.sign(payload, secret)
```

## Verify the validity of a JWT

The function returns the payload if the token is valid and `undefined` if it isn't.

```ts
const payload = await jwt.verify(token, secret)
```
