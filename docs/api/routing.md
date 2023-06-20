---
title: Routing
order: 4
---

## 🔗 Chaining

```ts
import cheetah from 'https://deno.land/x/cheetah/mod.ts'

const app = new cheetah()
  .get('/cake', () => '🎂') // GET '/cake'
  .patch('/cookie', () => '🍪') // PATCH '/cookie'
  .put('/donut', () => '🍩') // PUT '/donut'
```

## 🪹 Nesting

```ts
import cheetah, { Collection } from 'https://deno.land/x/cheetah/mod.ts'

const fastFood = new Collection()
  .get('/burger', () => '🍔') // GET '/fast-food/burger'

const app = new cheetah()
  .use('/fast-food', fastFood)
  .patch('/pancakes', () => '🥞') // PATCH '/pancakes'
```
