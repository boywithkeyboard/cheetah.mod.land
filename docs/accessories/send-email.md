---
title: Send E-Mails
order: 3
---

This module is specifically designed for Cloudflare Workers as it uses [mailchannels](https://blog.cloudflare.com/sending-email-from-workers-with-mailchannels) under the hood, which is free if you deploy your app to Cloudflare Workers. {.tip}

```ts
import { sendMail } from 'cheetah/x/mod.ts'

await sendMail({
  subject: 'Hello!',
  message: 'Hello, this is just an example.',
  from: {
    name: 'You',
    email: 'you@domain.com'
  },
  to: 'stranger@domain.com'
})
```
