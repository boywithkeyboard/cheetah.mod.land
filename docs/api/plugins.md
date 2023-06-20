---
title: Plugins
order: 6
---

This feature is still in an early stage. It is stable, but will undergo breaking syntactical changes before v1.0. {.tip}

## Official Plugins

We provide a set of plugins that are guaranteed to work with cheetah.

- [helmet](https://github.com/azurystudio/cheetah/blob/dev/guide/plugins/helmet.md)

## Introduction

If you want to add additional functionality to your application on a global, per collection, or per path level, plugins suit your needs.

Plugins let you create and publish reusable functions for your own and open source purposes.

```ts
import cheetah, { createPlugin } from 'https://deno.land/x/cheetah@v0.10.0/mod.ts'

export const myPlugin = createPlugin<{
  option: string // < settings the user can pass to the plugin
}>(settings => { // < will be a object with the key 'option'
  return {
    beforeParsing(c) { // access context to modify request/response
      ...
    }
  }
})

// You can then use it in your app just like that:

const app = new cheetah()
  .use(myPlugin({
    option: 'example'
  }))
```

Alternatively, you can create one without settings:

```ts
import cheetah, { createPlugin } from 'https://deno.land/x/cheetah@v0.10.0/mod.ts'

export const myPlugin = createPlugin({
  beforeParsing(c) { // access context to modify request/response
    ...
  }
})

// You can then use it in your app just like that:

const app = new cheetah()
  .use(myPlugin)
```

## Attach a Plugin to a Collection

You can add as many plugins as you want.

```ts
const app = new cheetah()
  .use('/prefix-for-collection', someCollection, somePlugin, anotherPlugin)
```

## Attach a Plugin by a Prefix

These plugins will fire on every route that starts with `/prefix`. You can add as many as you want.

```ts
const app = new cheetah()
  .use('/prefix', somePlugin, anotherPlugin)
```

## Execution Order

Plugins won't stop the execution. If you want to stop the execution and respond before the actual route handlers, you should throw a error and handle that error in your custom error handler. {.tip}

1. cache *(built-in)*
2. preflight response *(built-in)*
3. `beforeParsing`
4. validation & advanced parsing *(built-in)*
6. `beforeHandling`
7. route handlers *(the methods you define inside a `.get`, `.post` etc. method)*
8. `beforeResponding`
