---
title: Versioning
order: 8
---

It's quite easy to setup versioning for your app.

1. At first, you need to set the current version of your API and what type of versioning you prefer. This can either be `uri` or `header`.

    ```ts
    const app = new cheetah({
      versioning: {
        current: 'v4',
        type: 'uri'
      }
    })
    ```

2. To access the version the client requested, you can use the `c.req.gateway` variable.

    ```ts
    app.get('/', c => {
      const gateway = c.req.gateway // e.g. v3
    })
    ```

3. You can also specify a version range by passing a `gateway` option to the route.

    ```ts
    app.get('/', {
      gateway: '>= v3'
    }, c => {
      const gateway = c.req.gateway // either v3 or v4
    })
    ```
