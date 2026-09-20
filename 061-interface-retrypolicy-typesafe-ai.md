---
title: "Interface: RetryPolicy - TypeSafe AI"
date: "2026-09-18T09:14:15.508Z"
url: "https://docs.typesafe.ai/sdk/javascript/api/interfaces/RetryPolicy"
publisher: "TypeSafe AI"
lang: "en"
description: "Retry configuration. Partial overrides inherit unset fields from the client or SDK defaults."
logo_url: "https://docs.typesafe.ai/mintlify-assets/_mintlify/favicons/ts-docs/zg2v0DiYB7xPw0I2/_generated/favicon/android-chrome-192x192.png"
logo_type: "png"
logo_size: 8885
logo_height: 192
logo_width: 192
logo_size_pretty: "8.88 kB"
image_url: "https://ts-docs.mintlify.app/mintlify-assets/_next/image?url=%2F_mintlify%2Fapi%2Fog%3Fdivision%3DInterfaces%26title%3DInterface%253A%2BRetryPolicy%26theme%3Df0580ae664a0195833f0555d&w=1200&q=100"
image_type: "png"
image_size: 28697
image_height: 630
image_width: 1200
image_size_pretty: "28.7 kB"
word_count: 251
reading_time: "1 min read"
---

[← Voltar ao índice](./README.md)


## Table of Contents

- [Properties](#properties)
  - [apiConnectionError](#apiconnectionerror)
  - [apiTimeoutError](#apitimeouterror)
  - [backoffInitialMs](#backoffinitialms)
  - [backoffJitter](#backoffjitter)
  - [backoffMaxMs](#backoffmaxms)
  - [httpStatuses](#httpstatuses)
  - [maxRetries](#maxretries)
  - [maxRetryAfterMs](#maxretryafterms)
  - [respectRetryAfter](#respectretryafter)
- [On this page](#on-this-page)

---

Interfaces

Retry configuration. Partial overrides inherit unset fields from the client or SDK defaults.

## Properties

### apiConnectionError

```typescript
readonly apiConnectionError: boolean;
```

Retry connection failures, including interrupted response bodies (`APIConnectionError`). Default: true.

------------------------------------------------------------------------

### apiTimeoutError

```typescript
readonly apiTimeoutError: boolean;
```

Whether to retry `APITimeoutError`. Default: true.

------------------------------------------------------------------------

### backoffInitialMs

```typescript
readonly backoffInitialMs: number;
```

First backoff delay in milliseconds, doubled up to `backoffMaxMs`. Default: 500.

------------------------------------------------------------------------

### backoffJitter

```typescript
readonly backoffJitter: number;
```

Fraction of each backoff delay randomly subtracted, from 0 to 1. Default: 0.25.

------------------------------------------------------------------------

### backoffMaxMs

```typescript
readonly backoffMaxMs: number;
```

Maximum backoff delay in milliseconds. Default: 5000.

------------------------------------------------------------------------

### httpStatuses

```typescript
readonly httpStatuses: ReadonlySet<number>;
```

HTTP status codes to retry. Default: 408, 429, and 500–599.

------------------------------------------------------------------------

### maxRetries

```typescript
readonly maxRetries: number;
```

Maximum retries after the initial attempt; `0` disables retries. Default: 2.

------------------------------------------------------------------------

### maxRetryAfterMs

```typescript
readonly maxRetryAfterMs: number;
```

Maximum server retry delay in milliseconds; longer delays use backoff. Default: 60000.

------------------------------------------------------------------------

### respectRetryAfter

```typescript
readonly respectRetryAfter: boolean;
```

Honor `Retry-After` and `retry-after-ms` up to `maxRetryAfterMs`. Default: true.

Was this page helpful?

[Interface: RequestOptions](https://docs.typesafe.ai/sdk/javascript/api/interfaces/RequestOptions)

[Previous](https://docs.typesafe.ai/sdk/javascript/api/interfaces/RequestOptions) [Interface: ScoreQuestion\<T\> Next](https://docs.typesafe.ai/sdk/javascript/api/interfaces/ScoreQuestion)

[github](https://github.com/typesafe-ai) [discord](https://discord.gg/typesafe) [x](https://x.com/typesafeai)

[Powered byThis documentation is built and hosted on Mintlify, a developer documentation platform](https://www.mintlify.com/?utm_campaign=poweredBy&utm_medium=referral&utm_source=ts-docs)

## On this page

- [Properties](https://docs.typesafe.ai/sdk/javascript/api/interfaces/RetryPolicy#properties)
  - [apiConnectionError](https://docs.typesafe.ai/sdk/javascript/api/interfaces/RetryPolicy#apiconnectionerror)
  - [apiTimeoutError](https://docs.typesafe.ai/sdk/javascript/api/interfaces/RetryPolicy#apitimeouterror)
  - [backoffInitialMs](https://docs.typesafe.ai/sdk/javascript/api/interfaces/RetryPolicy#backoffinitialms)
  - [backoffJitter](https://docs.typesafe.ai/sdk/javascript/api/interfaces/RetryPolicy#backoffjitter)
  - [backoffMaxMs](https://docs.typesafe.ai/sdk/javascript/api/interfaces/RetryPolicy#backoffmaxms)
  - [httpStatuses](https://docs.typesafe.ai/sdk/javascript/api/interfaces/RetryPolicy#httpstatuses)
  - [maxRetries](https://docs.typesafe.ai/sdk/javascript/api/interfaces/RetryPolicy#maxretries)
  - [maxRetryAfterMs](https://docs.typesafe.ai/sdk/javascript/api/interfaces/RetryPolicy#maxretryafterms)
  - [respectRetryAfter](https://docs.typesafe.ai/sdk/javascript/api/interfaces/RetryPolicy#respectretryafter)

[github](https://github.com/typesafe-ai)[discord](https://discord.gg/typesafe)[x](https://x.com/typesafeai)

[Powered byThis documentation is built and hosted on Mintlify, a developer documentation platform](https://www.mintlify.com/?utm_campaign=poweredBy&utm_medium=referral&utm_source=ts-docs)