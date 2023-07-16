---
title: Use Extension
order: 7
---

## Introduction

If you want to add additional functionality to your application on a global, per collection, or per pathname level, extensions suit your needs.

Extensions let you create and publish reusable functions for you and other people.

## Attach a extension to a collection

You can add as many extensions as you want.

```ts
const app = new cheetah()
  .use('/prefix', someCollection, someExtension, anotherExtension)
```

## Attach a extension by a prefix

These extensions will fire on every route that starts with `/prefix`. You can add as many as you want.

```ts
const app = new cheetah()
  .use('/prefix', someExtension, anotherExtension)
```

## Execution

Extensions won't typically stop execution. If you want to stop the execution and respond before the actual route handlers, you should throw an error and handle that error in your custom error handler.

The only exception is that if you return a [`Response`](https://developer.mozilla.org/en-US/docs/Web/API/Response) in the `onRequest` listener, it will be returned without further modification and execution will stop.
