---
title: Request
order: 1
---

## IP Address

```ts
c.req.ip
```

## Request Method

The method of the incoming request.

e.g. `GET`

```ts
c.req.method
```

## Raw Request

Retrieve the unmodified [Request](https://developer.mozilla.org/en-US/docs/Web/API/Request) object with an unread stream of the body.

```ts
c.req.raw()
```

## Request Parameters

A method to retrieve the corresponding value of a parameter.

```ts
const value = c.req.param('...')
```

## Request Body

If you expect a request body of type `application/json` or `plain/text`, we recommend to follow the [Parsing & Validation](https://github.com/azurystudio/cheetah/blob/dev/guide/parsing_and_validation.md) guide. {.tip}

These methods all have a default time limit of _3s_ for added security. If
the function cannot complete within _3s_ or fails to parse the body, it
will return `null`.

- ### Buffer

  ```ts
  const data = await c.req.buffer()
  ```

- ### Blob

  ```ts
  const data = await c.req.blob()
  ```

- ### FormData

  ```ts
  const data = await c.req.formData()
  ```

- ### ReadableStream

  ```ts
  const data = c.req.stream()
  ```

You can always use one of these methods, even if you've already read the body
before - they won't throw an error! {.tip}

## Geo-Location Data

This only works on Cloudflare Workers. {.tip}

```ts
c.req.geo()
```

**A object consisting of...**

- _city_ `string`
- _region_ `string`
- _country_ `string`
- _continent_ `string`
- _regionCode_ `string`
- _latitude_ `string`
- _longitude_ `string`
- _postalCode_ `string`
- _timezone_ `string`
- _datacenter_ `string`
