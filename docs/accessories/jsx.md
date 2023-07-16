---
title: jsx
order: 3
---

## Configure Deno

Add the following to your `deno.json` or `deno.jsonc` file to enable JSX.

```json
{
  "compilerOptions": {
    "jsxFactory": "h",
    "jsxFragmentFactory": "Fragment"
  }
}
```

You probably also need to import the JSX factory for it to work.

```ts
/** @jsx h */
import { h } from 'https://esm.sh/preact@10.16.0'
```

##  Basic example

```tsx
import cheetah from 'https://deno.land/x/cheetah/mod.ts'
import { jsx } from 'https://deno.land/x/cheetah/x/mod.ts'

const app = new cheetah()

function Custom() {
  return <h1>Hello World</h1>
}

app.get('/', (c) => jsx(c, Custom))
```

## Pass data to the component

```tsx
import cheetah from 'https://deno.land/x/cheetah/mod.ts'
import { jsx } from 'https://deno.land/x/cheetah/x/mod.ts'

const app = new cheetah()

function User({ name }: { name: string }) {
  return <h1>Hey, {name}!</h1>
}

app.get('/users/:name', (c) => {
  jsx(c, <User name={c.req.param('name')} />)
})
```


