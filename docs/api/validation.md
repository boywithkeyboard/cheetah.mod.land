---
title: Validation & Parsing
order: 3
---

## `transform`

This enables the conversion of a FormData request body into a JSON object _(if
the request body has the MIME type `multipart/form-data`)_.

```ts
import cheetah from 'cheetah/mod.ts'
import zod, { z } from 'cheetah/validator/zod.ts'

const app = new cheetah({
  validator: zod,
})

app.get('/example', {
  body: z.object({
    message: z.string()
  }),
  transform: true
}, async (c) => {
  console.log(body) // e.g. { message: 'Hello!' }
})
```

## TypeBox

### Setup

  ```ts
  import cheetah from 'cheetah/mod.ts'
  import validator, { Type } from 'cheetah/validator/typebox.ts'

  const app = new cheetah({
    validator
  })
  ```

### Parsing & Validating Body

  JSON:

  ```ts
  app.post('/example', {
    body: Type.Object({
      key: Type.String()
    })
  }, (c) => {
    const validatedObject = c.req.body
  })
  ```

  Text:

  ```ts
  app.post('/example', {
    body: Type.String({ minLength: 4, maxLength: 16 })
  }, (c) => {
    const validatedString = c.req.body
  })
  ```

### Parsing & Validating Query Parameters

  ```ts
  app.get('/example', {
    query: Type.Object({
      key: Type.String()
    })
  }, (c) => {
    const validatedObject = c.req.query
  })
  ```

### Parsing & Validating Headers

  ```ts
  app.get('/example', {
    query: Type.Object({
      key: Type.String()
    }, { additionalParameters: true })
  }, (c) => {
    const validatedObject = c.req.query
  })
  ```

### Parsing & Validating Cookies

  ```ts
  app.get('/example', {
    cookies: Type.Object({
      key: Type.String()
    })
  }, (c) => {
    const validatedObject = c.req.cookies
  })
  ```

## Zod

### Setup

  ```ts
  import cheetah from 'cheetah/mod.ts'
  import validator, { z } from 'cheetah/validator/zod.ts'

  const app = new cheetah({
    validator
  })
  ```

### Parsing & Validating Body

  JSON:

  ```ts
  app.post('/example', {
    body: z.object({
      key: z.string()
    })
  }, (c) => {
    const validatedObject = c.req.body
  })
  ```

  Text:

  ```ts
  app.post('/example', {
    body: z.string().min(4).max(16)
  }, (c) => {
    const validatedString = c.req.body
  })
  ```

### Parsing & Validating Query Parameters

  ```ts
  app.get('/example', {
    query: z.object({
      key: z.string()
    }).strict()
  }, (c) => {
    const validatedObject = c.req.query
  })
  ```

### Parsing & Validating Headers

  ```ts
  app.get('/example', {
    query: z.object({
      key: z.string()
    })
  }, (c) => {
    const validatedObject = c.req.query
  })
  ```

### Parsing & Validating Cookies

  ```ts
  app.get('/example', {
    cookies: z.object({
      key: z.string()
    }).strict()
  }, (c) => {
    const validatedObject = c.req.cookies
  })
  ```
