---
title: Multiple Handlers
order: 5
---

You can also have an infinite amount of handlers on a single route, such as:

```ts
app.get('/', (c) => {
  // do something
}, (c) => {
  // ...
})
```

If you set a response body but want to execute the next handler, you must call the `next()` method.

```ts
app.get('/', (c, next) => {
  next()
}, (c) => {
  // ...
})
```
