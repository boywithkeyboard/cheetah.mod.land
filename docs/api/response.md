---
title: Response
order: 2
---

## Set response body

You can either set the body of the response explicitly...

```ts
c.res.body = { foo: 'bar' }
```

...or just return it:

```ts
app.get('/', () => {
  return { foo: 'bar' }
})
```

## Set response code

**By default, the status code is `200`** - if an error occurs, it will be `500`
(unknown error) or `400` (validation error).

### Explicitly

```ts
c.res.code = 100
```

### Implicitly

If your response body is a JSON object, you can also add a `code` key to it to set the status code of the response.

cheetah won't remove the `code` field from your JSON object! {.tip}

```ts
app.get('/', () => {
  return {
    foo: 'bar',
    code: 100
  }
})
```

## Attach a header

```ts
c.res.header('name', 'value')
```

## Attach a cookie

```ts
c.res.cookie('name', 'value', options)
```

### Options:

- _expiresAt_ `Date`
- _maxAge_ `number`
- _domain_ `string`
- _path_ `string`
- _secure_ `boolean`
- _httpOnly_ `boolean`
- _sameSite_ `string`

## Make a Redirect

The status code is by default set to `307` (temporary redirect).

```ts
c.res.redirect(destination, code)
```

## Calculate size of body

```ts
c.res.bodySize
```
