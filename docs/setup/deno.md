---
title: Deno
order: 2
---

Create a entry file for your API, preferably `mod.ts` with the following content:

```ts
import cheetah from 'https://deno.land/x/cheetah/mod.ts'

const app = new cheetah()
  .get('/', () => 'Hey there!')

  .serve()
```

Then run the script with `deno run -A mod.ts` and open [http://localhost:8000](http://localhost:8000) in your browser. You should see a *"Hey there!"*.

Congratulations, you've taken the first step to writing an API with cheetah! 🥳🎉
