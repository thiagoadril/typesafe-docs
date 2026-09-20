---
title: "Interface: RequestOptions - TypeSafe AI"
date: "2026-09-18T09:14:15.489Z"
url: "https://docs.typesafe.ai/sdk/javascript/api/interfaces/RequestOptions"
publisher: "TypeSafe AI"
lang: "en"
description: "Per-call options that override client settings."
logo_url: "https://docs.typesafe.ai/mintlify-assets/_mintlify/favicons/ts-docs/zg2v0DiYB7xPw0I2/_generated/favicon/android-chrome-192x192.png"
logo_type: "png"
logo_size: 8885
logo_height: 192
logo_width: 192
logo_size_pretty: "8.88 kB"
image_url: "https://ts-docs.mintlify.app/mintlify-assets/_next/image?url=%2F_mintlify%2Fapi%2Fog%3Fdivision%3DInterfaces%26title%3DInterface%253A%2BRequestOptions%26theme%3Df0580ae664a0195833f0555d&w=1200&q=100"
image_type: "png"
image_size: 30301
image_height: 630
image_width: 1200
image_size_pretty: "30.3 kB"
word_count: 145
reading_time: "1 min read"
---

[← Voltar ao índice](./README.md)


## Table of Contents

- [Properties](#properties)
  - [headers?](#headers)
  - [retry?](#retry)
  - [signal?](#signal)
  - [timeout?](#timeout)
- [On this page](#on-this-page)

---

Interfaces

Per-call options that override client settings.

## Properties

### headers?

```typescript
optional headers?: Record<string, string>;
```

Additional headers, merged over `defaultHeaders`.

------------------------------------------------------------------------

### retry?

```typescript
optional retry?: Partial<RetryPolicy>;
```

Retry overrides for this call; omitted fields inherit client settings.

------------------------------------------------------------------------

### signal?

```typescript
optional signal?: AbortSignal;
```

Cancellation signal for the request and pending retries.

------------------------------------------------------------------------

### timeout?

```typescript
optional timeout?: number;
```

Timeout per attempt in milliseconds; there is no total retry budget.

Was this page helpful?

[Interface: Questions](https://docs.typesafe.ai/sdk/javascript/api/interfaces/Questions)

[Previous](https://docs.typesafe.ai/sdk/javascript/api/interfaces/Questions) [Interface: RetryPolicy Next](https://docs.typesafe.ai/sdk/javascript/api/interfaces/RetryPolicy)

[github](https://github.com/typesafe-ai) [discord](https://discord.gg/typesafe) [x](https://x.com/typesafeai)

[Powered byThis documentation is built and hosted on Mintlify, a developer documentation platform](https://www.mintlify.com/?utm_campaign=poweredBy&utm_medium=referral&utm_source=ts-docs)

## On this page

- [Properties](https://docs.typesafe.ai/sdk/javascript/api/interfaces/RequestOptions#properties)
  - [headers?](https://docs.typesafe.ai/sdk/javascript/api/interfaces/RequestOptions#headers)
  - [retry?](https://docs.typesafe.ai/sdk/javascript/api/interfaces/RequestOptions#retry)
  - [signal?](https://docs.typesafe.ai/sdk/javascript/api/interfaces/RequestOptions#signal)
  - [timeout?](https://docs.typesafe.ai/sdk/javascript/api/interfaces/RequestOptions#timeout)

[github](https://github.com/typesafe-ai)[discord](https://discord.gg/typesafe)[x](https://x.com/typesafeai)

[Powered byThis documentation is built and hosted on Mintlify, a developer documentation platform](https://www.mintlify.com/?utm_campaign=poweredBy&utm_medium=referral&utm_source=ts-docs)