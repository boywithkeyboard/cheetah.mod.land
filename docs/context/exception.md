---
title: exception
order: 3
---

The `c.exception()` method constructs a response based on the `Accept` header.

If the header contains the MIME type `application/json` or `*/*` (any MIME type), the response body will be a JSON object, otherwise it'll be plain text. This behavior also applies to the default ***error*** and ***not found*** responses.

## Schema

```ts
c.exception(error, description)
```

## Example

```ts
app.get('/', c => {
  if (condition)
    throw c.exception('Bad Request', 'You did something wrong!')
})
```
