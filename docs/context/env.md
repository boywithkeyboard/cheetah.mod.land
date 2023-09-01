---
title: env
order: 5
---

## Setup

You might want to declare a type for your environment variables. This can be done by creating a file, e.g. `./env.d.ts` with the below content.

```ts
declare global {
  // @ts-ignore:
  export type Variables = {
    // your environment variables here
  }
}

export {}
```

You'd then include the changes you made by specifying it in your Deno configuration file (e.g. `deno.json`) as such:

```json
{
  "compilerOptions": {
    "types": [
      "./env.d.ts"
    ]
  }
}
```

## Usage

After you have successfully went through all the above steps, you can now use the `env` method in a type-safe way.

```ts
app.get('/', c => {
  const value = c.env('foo') // e.g. bar
})
```
