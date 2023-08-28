---
title: Introduction
order: 1
---

If you want to get started with a basic template, run the below command in your favorite terminal.

You usually have to navigate into the generated subfolder.

```bash
deno run -Ar https://deno.land/x/cheetah/setup.ts
```

If you don't want to use one of the templates, you can follow the manual for [Deno](/docs/setup/deno/) or for [Cloudflare Workers](/docs/setup/cloudflare-workers/).

If you're using Cloudflare as a proxy, please specify it through the [`proxy`](/docs/configuration/proxy/) option. {.tip}

Also, if you haven't already enabled Deno for your workspace, make sure to check out [Deno's manual](https://deno.land/manual/getting_started/setup_your_environment) to learn more.

## Disclaimer

Throughout this entire guide we specify imports without a version tag due to simplicity.

```ts
// e.g.
import cheetah from 'https://deno.land/x/cheetah/mod.ts'
```

**Please do not import the modules this way!** Instead, add the latest version (e.g. `v1.0.0` as of July 16th) after `x/cheetah` like this:

```ts
import cheetah from 'https://deno.land/x/cheetah@v1.0.0/mod.ts'
```
