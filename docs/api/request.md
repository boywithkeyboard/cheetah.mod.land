---
title: Request
order: 1
---

Please also read the [Parsing & Validation](/docs/api/validation/) guide for a full overview. {.tip}

## Get IP address

```ts
c.req.ip
```

## Get request method

The method of the incoming request.

e.g. `GET`

```ts
c.req.method
```

## Get request parameters

A method to retrieve the corresponding value of a parameter.

```ts
c.req.param('...')
```

## Get raw request

Retrieve the unmodified [Request](https://developer.mozilla.org/en-US/docs/Web/API/Request) object.

The body stream might already be consumed. {.tip}

```ts
c.req.raw
```

## Get request body

These methods all have a default time limit of _3s_ for added security. If
the function cannot complete within _3s_ or fails to parse the body, it
will return `null`.

Don't use these methods if you have specified a validation schema for your body! {.tip}

- `ArrayBuffer`

  ```ts
  const data = await c.req.buffer()
  ```

- `Blob`

  ```ts
  const data = await c.req.blob()
  ```

- `FormData`

  ```ts
  const data = await c.req.formData()
  ```

- `ReadableStream`

  ```ts
  const data = c.req.stream()
  ```

- `String`

  ```ts
  const data = await c.req.text()
  ```

- `JSON`

  ```ts
  const data = await c.req.json()
  ```
