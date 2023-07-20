---
title: pretty
description: An extension to jazz up the response body by adding indentation and sorting the keys alphabetically.
order: 5
---

```ts
import cheetah from 'https://deno.land/x/cheetah/mod.ts'
import { pretty } from 'https://deno.land/x/cheetah/ext/pretty.ts'

const app = new cheetah()
  .use(pretty())
```

## Configuration

- `indentSize`

  Apply indentation to your response body. Set it to `0` to disable indentation.

  ```ts
  pretty({
    indentSize: 4 // 2 by default
  })
  ```

- `sort`

  Whether to sort the fields alphabetically.

  ```ts
  pretty({
    sort: true // disabled by default
  })
  ```

## Example

### Without `pretty`

```json
{"lastname": "Doe","firstname": "John","data": {"height": 180,"age": 20}}
```

### With `pretty` (sorting enabled)

```json
{
  "data": {
    "age": 20,
    "height": 180
  },
  "firstname": "John",
  "lastname": "Doe"
}
```

### With `pretty` (sorting disabled)

```json
{
  "lastname": "Doe",
  "firstname": "John",
  "data": {
    "height": 180,
    "age": 20
  }
}
```
