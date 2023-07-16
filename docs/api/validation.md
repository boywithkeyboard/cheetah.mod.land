---
title: Validation & Parsing
order: 3
---

## `transform`

This enables the conversion of a FormData request body into a JSON object _(if
the request body has the MIME type `multipart/form-data`)_.

```ts
import cheetah from 'https://deno.land/x/cheetah/mod.ts'
import z from 'https://deno.land/x/zod@v3.21.4/mod.ts'

const app = new cheetah()

app.get('/', {
  body: z.object({
    foo: z.string()
  }),
  transform: true
}, async (c) => {
  console.log(await c.req.body()) // e.g. { foo: 'bar' }
})
```

## Parse & Validate Body

<lume-code>

```ts { title="JSON" }
// ZodObject
app.post('/', {
  body: z.object({
    key: z.string()
  })
}, (c) => {
  console.log(await c.req.body())
})

// ZodRecord
app.post('/', {
  body: z.record(z.string(), z.number())
}, (c) => {
  console.log(await c.req.body())
})

// ZodUnion
app.post('/', {
  body: z.union([z.object({
    foo: z.string()
  }), z.object({
    bar: z.string()
  })])
}, (c) => {
  console.log(await c.req.body())
})

app.post('/', {
  body: z.object({
    foo: z.string()
  }).or(z.object({
    bar: z.string()
  }))
}, (c) => {
  console.log(await c.req.body())
})
```

```ts { title="Text" }
// ZodObject
app.post('/', {
  body: z.string().min(4).max(16)
}, (c) => {
  console.log(await c.req.body())
})

// ZodUnion
app.post('/', {
  body: z.union([
    z.string().min(4).max(16),
    z.string().email()
  ])
}, (c) => {
  console.log(await c.req.body())
})

app.post('/', {
  body: z.string().min(4).max(16)
    .or(z.string().email())
}, (c) => {
  console.log(await c.req.body())
})
```

</lume-code>

## Parse & Validate Query Parameters

```ts
app.get('/', {
  query: z.object({
    foo: z.boolean()
  })
}, (c) => {
  console.log(c.req.query)
})
```

## Parse & Validate Headers

If you don't specify a schema for the headers, they will nevertheless be parsed automatically and have the type `Record<string, string | undefined>`. {.tip}

```ts
app.get('/', {
  headers: z.object({
    foo: z.string()
  })
}, (c) => {
  console.log(c.req.headers)
})
```

## Parse & Validate Cookies

```ts
app.get('/', {
  cookies: z.object({
    foo: z.string()
  })
}, (c) => {
  console.log(c.req.cookies)
})
```
