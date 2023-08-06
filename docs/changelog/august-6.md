---
title: v1.2
order: 1
---

## New `files` extension

This extension allows you to serve static files from either a Cloudflare R2 bucket or from a local directory.

```ts
import cheetah from 'https://deno.land/x/cheetah@v1.2.0/mod.ts'
import { files } from 'https://deno.land/x/cheetah@v1.2.0/ext/files.ts'

const app = new cheetah()
  // this serves the files in the 'static' directory,
  //   e.g. /prefix/image.png resolves to ./static/image.png
  .use('/prefix', files({
    directory: './static'
  }))

  .serve()
```

## New `onPlugIn` event handler for extensions

This event is meant to be used to perform a action only once and comes with a simple `setRoute` method to dynamically set a new route via the Extensions API.

## You can now access the prefix from an extension

The prefix is now passed to the context object of each event handler of an extension.

## Rewritten setup script

The setup script now uses the repository [boywithkeyboard/templates](https://github.com/boywithkeyboard/templates) as reference and downloads all files to the current working directory instead of a directory you had to rename manually.

The starter template should also be now easier to understand.
