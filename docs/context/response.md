---
title: res
order: 2
---

## Set Body

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

## Set Status Code

**By default, the status code is `200`** - if an error occurs, it will be `500`
(unknown error) or `400` (validation error).

- Explicitly:

  ```ts
  c.res.code = 100
  ```

- Implicitly:

  If your response body is a JSON object, you can also add a `code` key to it to set the status code of the response that way.

  cheetah won't remove the `code` field from your JSON object! {.tip}

  ```ts
  app.get('/', () => {
    return {
      foo: 'bar',
      code: 100
    }
  })
  ```

## Attach Header

```ts
c.res.header('foo', 'bar')
```

## Set Cookie

```ts
c.res.setCookie('foo', 'bar', options)
```

### Options:

- _expires_ `Date`
- _maxAge_ `number`
- _domain_ `string`
- _path_ `string`
- _secure_ `boolean`
- _httpOnly_ `boolean`
- _sameSite_ `string`

## Delete Cookie

This method attaches an empty `Set-Cookie` header to delete the cookie.

```ts
c.res.deleteCookie('foo', options)
```

### Options:

- _domain_ `string`
- _path_ `string`

## Make a Redirect

The status code is by default set to `307` (temporary redirect).

```ts
c.res.redirect(destination, code)
```

Example:

```ts
c.res.redirect('https://google.com', 301)
```

## Calculate Size of Body

A vague estimate of the size of the response body (`-1` if it cannot be calculated).

```ts
c.res.bodySize
```
