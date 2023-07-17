---
title: Exception
order: 5
---

The `Exception` class constructs a response based on the `Accept` header.

If the header contains the MIME type `application/json` or `*/*` (any MIME type), the response body will be a JSON object, otherwise it'll be plain text. This behavior also applies to the default ***error*** and ***not found*** responses.

## Schema

If you don't specify a code, it will fall back to `400`.

```ts
new Exception(message, code)
```

There are a few [built-in error messages/codes](https://github.com/azurystudio/cheetah/blob/dev/exception.ts).

```ts
new Exception('Not Found') // -> message: Not Found, code: 404
new Exception(404) // -> message: Not Found, code: 404
```

## Example

```ts
import { Exception } from 'https://deno.land/x/cheetah/exception.ts'

app.get('/example', (c) => {
  if (condition)
    throw new Exception('No Weed', 420)
})
```
