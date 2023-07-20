---
title: favicon
description: An extension to set a neat [favicon](https://en.wikipedia.org/wiki/Favicon) for your app.
order: 4
---

```ts
import cheetah from 'https://deno.land/x/cheetah/mod.ts'
import { favicon } from 'https://deno.land/x/cheetah/ext/favicon.ts'

const app = new cheetah()
  .use(
    favicon({
      source: Deno.readFileSync('./cheetah.ico')
    })
  )
```

## Configuration

- `headers`

  You may optionally specify headers to be attached to the response.

  ```ts
  favicon({
    headers: {
      'cache-control': 'max-age=604800'
    }
  })
  ```

- `source`

  The source for your favicon can be either a URL or a buffer.

  ```ts
  // url
  favicon({
    source: 'https://cheetah.mod.land/cheetah.ico'
  })

  // buffer
  favicon({
    source: Deno.readFileSync('./cheetah.ico')
  })
  ```
