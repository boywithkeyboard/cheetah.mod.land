---
title: req
order: 1
---

## Get IP Address

Don't forget to set the [`proxy`]() option if you're using Cloudflare's CDN and/or DDoS protection. {.tip}

```ts
c.req.ip
```

## Get Method

The method of the incoming request.

e.g. `GET`

```ts
c.req.method
```

## Get Parameters

This method validates the parameter according to your scheme, if you have defined one. It'll throw an [`exception`](/docs/context/exception/) if the parameter doesn't match your specified schema. {.tip}

A method to retrieve the corresponding value of a parameter.

```ts
c.req.param('...')
```

## Get Raw Request

Retrieve the unmodified [Request](https://developer.mozilla.org/en-US/docs/Web/API/Request) object.

Please note that the body stream might already be consumed. {.tip}

```ts
c.req.raw
```

## Get Body

<!-- ## `transform`

This enables the conversion of a FormData request body into a JSON object _(if
the request body has the MIME type `multipart/form-data`)_.

```ts
import cheetah from 'https://deno.land/x/cheetah/mod.ts'
import { z } from 'https://deno.land/x/zod/mod.ts'

const app = new cheetah()

app.get('/', {
  body: z.object({
    foo: z.string()
  })
}, async c => {
  console.log(await c.req.body({ transform: true })) // e.g. { foo: 'bar' }
})
``` -->

This method has a time limit of _3s_ for added security. If
the function cannot complete within _3s_ or fails to parse the body and therefore doesn't match your specified scheme, it'll throw an [`exception`](/docs/context/exception/).

```ts
const body = await c.req.body()
```

<lume-code>

```ts { title="Text" }
// ZodObject
app.post('/', {
  body: z.string().min(4).max(16)
}, c => {
  console.log(await c.req.body())
})

// ZodUnion
app.post('/', {
  body: z.union([
    z.string().min(4).max(16),
    z.string().email()
  ])
}, c => {
  console.log(await c.req.body())
})

app.post('/', {
  body: z.string().min(4).max(16)
    .or(z.string().email())
}, c => {
  console.log(await c.req.body())
})
```

```ts { title="JSON" }
// ZodObject
app.post('/', {
  body: z.object({
    key: z.string()
  })
}, c => {
  console.log(await c.req.body())
})

// ZodRecord
app.post('/', {
  body: z.record(z.string(), z.number())
}, c => {
  console.log(await c.req.body())
})

// ZodUnion
app.post('/', {
  body: z.union([z.object({
    foo: z.string()
  }), z.object({
    bar: z.string()
  })])
}, c => {
  console.log(await c.req.body())
})

app.post('/', {
  body: z.object({
    foo: z.string()
  }).or(z.object({
    bar: z.string()
  }))
}, c => {
  console.log(await c.req.body())
})
```

</lume-code>

## Get Cookies

This method validates the cookies according to your scheme, if you have defined one. It'll throw an [`exception`](/docs/context/exception/) if the cookies doesn't match your specified schema. {.tip}

```ts
app.get('/', {
  cookies: z.object({
    foo: z.string()
  })
}, c => {
  const cookies = c.req.cookies // e.g. { foo: 'bar' }
})
```

## Get Headers

This method validates the headers according to your scheme, if you have defined one. It'll throw an [`exception`](/docs/context/exception/) if the headers doesn't match your specified schema.<br><br> If you didn't specify a scheme for the headers, they will nevertheless be parsed and have the type `Record<string, string | undefined>`. {.tip}

```ts
app.get('/', {
  headers: z.object({
    bar: z.string()
  })
}, c => {
  const headers = c.req.headers // e.g. { bar: 'foo' }
})
```

## Get Query Parameters

This method validates the query parameters according to your scheme, if you have defined one. It'll throw an [`exception`](/docs/context/exception/) if the query parameters doesn't match your specified schema.<br><br> If you didn't specify a scheme for the query parameters, they will nevertheless be parsed and have the type `Record<string, unknown>`. {.tip}

```ts
app.get('/', {
  query: z.object({
    foo: z.boolean()
  })
}, c => {
  const query = c.req.query // e.g. { foo: true }
})
```
