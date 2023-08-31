---
title: files
description: An extension to serve static files from Cloudflare R2, an S3 bucket, or the local file system.
order: 6
---

```ts
import cheetah from 'https://deno.land/x/cheetah/mod.ts'
import { files } from 'https://deno.land/x/cheetah/ext/files.ts'

const app = new cheetah()
  // this serves the files in the 'static' directory,
  //   e.g. /prefix/image.png resolves to ./static/image.png
  .use('/prefix', files({
    serve: {
      directory: './static'
    }
  }))

  .serve()
```
