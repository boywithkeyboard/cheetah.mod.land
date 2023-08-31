---
title: Build for Cloudflare Workers
order: 4
---

Create a entry file for your API, preferably `mod.ts` with the following content:

```ts
import cheetah from 'https://deno.land/x/cheetah/mod.ts'

const { fetch } = new cheetah()
  .get('/', () => 'Hey there!')

export default { fetch }
```

Create a `deno.json` file similar to the following:

```json
{
  "tasks": {
    "build": "deno run -A https://deno.land/x/cheetah/build.ts",
    "publish": "npx wrangler@3 deploy mod.js"
  }
}
```

And a `wrangler.toml` file:

```toml
name = "<name>"
account_id = "<account_id>"
route = "<route>"
compatibility_date = "2023-03-24"

[build]
command = "deno task build"
```

## Building your app

You can build your app by running [`cheetah build`](), which uses cheetah's build script.

## Deploying your app

Please make sure to install wrangler (globally) before: `npm i -g wrangler@3` {.tip}

Now you only need to run `deno task publish`.

Congratulations, you've taken the first step to writing an API with cheetah! 🥳🎉
