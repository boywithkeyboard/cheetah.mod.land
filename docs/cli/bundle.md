---
title: <cheetah> bundle
order: 1
---

Bundle your cheetah app into a single JavaScript file, ready to deploy to Cloudflare Workers.

```bash
deno run -A https://deno.land/x/cheetah/cli/mod.ts bundle ./input.ts ./output.js
```

By default, you don't have to specify an input or output file. cheetah will use your `./mod.ts` as entry point and `./mod.js` as the output file.

## Options

- `--target`, string - The [target environment](https://esbuild.github.io/api/#target).

  *(es2022 by default)*

- `--minify`, boolean - Whether to minify your JavaScript bundle.
  
  *(true by default)*

- `--runtime`, cloudflare | deno - The target runtime for your app.

  *(cloudflare by default)*
