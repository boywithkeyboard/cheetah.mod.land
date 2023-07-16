---
title: debug
description: An extension to log every response (that didn't throw an exception).
order: 3
---

```ts
import cheetah from 'https://deno.land/x/cheetah/mod.ts'
import { debug } from 'https://deno.land/x/cheetah/ext/debug.ts'

const app = new cheetah()
  .use(debug())
```
