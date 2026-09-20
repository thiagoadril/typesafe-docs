---
title: "Interface: TypeSafeClientConfig - TypeSafe AI"
date: "2026-09-18T09:14:15.487Z"
url: "https://docs.typesafe.ai/sdk/javascript/api/interfaces/TypeSafeClientConfig"
publisher: "TypeSafe AI"
lang: "en"
description: "Client options. Explicit values take precedence over environment variables, then SDK defaults."
logo_url: "https://docs.typesafe.ai/mintlify-assets/_mintlify/favicons/ts-docs/zg2v0DiYB7xPw0I2/_generated/favicon/android-chrome-192x192.png"
logo_type: "png"
logo_size: 8885
logo_height: 192
logo_width: 192
logo_size_pretty: "8.88 kB"
image_url: "https://ts-docs.mintlify.app/mintlify-assets/_next/image?url=%2F_mintlify%2Fapi%2Fog%3Fdivision%3DInterfaces%26title%3DInterface%253A%2BTypeSafeClientConfig%26theme%3Df0580ae664a0195833f0555d&w=1200&q=100"
image_type: "png"
image_size: 31845
image_height: 630
image_width: 1200
image_size_pretty: "31.8 kB"
word_count: 297
reading_time: "2 min read"
---

[← Voltar ao índice](./README.md)


## Table of Contents

- [Properties](#properties)
  - [apiKey?](#apikey)
  - [baseURL?](#baseurl)
  - [dangerouslyAllowBrowser?](#dangerouslyallowbrowser)
  - [defaultHeaders?](#defaultheaders)
  - [defaultModel?](#defaultmodel)
  - [fetch?](#fetch)
  - [logger?](#logger)
  - [logLevel?](#loglevel)
  - [retry?](#retry)
  - [timeout?](#timeout)
- [On this page](#on-this-page)

---

Interfaces

Client options. Explicit values take precedence over environment variables, then SDK defaults.

## Properties

### apiKey?

```typescript
optional apiKey?: string;
```

Required API key; falls back to `TYPESAFE_API_KEY`.

------------------------------------------------------------------------

### baseURL?

```typescript
optional baseURL?: string;
```

API root; falls back to `TYPESAFE_BASE_URL`, then `https://api.typesafe.ai`.

------------------------------------------------------------------------

### dangerouslyAllowBrowser?

```typescript
optional dangerouslyAllowBrowser?: boolean;
```

Allow browser use, exposing the API key to page users. Default: false.

------------------------------------------------------------------------

### defaultHeaders?

```typescript
optional defaultHeaders?: Record<string, string>;
```

Additional request headers; per-call headers take precedence.

------------------------------------------------------------------------

### defaultModel?

```typescript
optional defaultModel?: string;
```

Default model; falls back to `TYPESAFE_DEFAULT_MODEL`, then `jev-latest`.

------------------------------------------------------------------------

### fetch?

```typescript
optional fetch?: Fetch;
```

Custom HTTP fetch implementation for transport configuration or tests. Default: global `fetch`.

------------------------------------------------------------------------

### logger?

```typescript
optional logger?: Logger;
```

Logger filtered to `logLevel` and above. Default: prefixed `console`.

------------------------------------------------------------------------

### logLevel?

```typescript
optional logLevel?: LogLevel;
```

Log level; falls back to `TYPESAFE_LOG_LEVEL`, then `warn`. `info` logs request summaries; `debug` adds headers and bodies. Known credential headers are redacted; bodies are not.

------------------------------------------------------------------------

### retry?

```typescript
optional retry?: Partial<RetryPolicy>;
```

Retry overrides; omitted fields use the defaults in `RetryPolicy`.

------------------------------------------------------------------------

### timeout?

```typescript
optional timeout?: number;
```

Timeout per attempt in milliseconds, without a total retry budget. Default: 10000.

Was this page helpful?

[Interface: SystemOneResult\<Q\>](https://docs.typesafe.ai/sdk/javascript/api/interfaces/SystemOneResult)

[Previous](https://docs.typesafe.ai/sdk/javascript/api/interfaces/SystemOneResult) [Interface: Usage Next](https://docs.typesafe.ai/sdk/javascript/api/interfaces/Usage)

[github](https://github.com/typesafe-ai) [discord](https://discord.gg/typesafe) [x](https://x.com/typesafeai)

[Powered byThis documentation is built and hosted on Mintlify, a developer documentation platform](https://www.mintlify.com/?utm_campaign=poweredBy&utm_medium=referral&utm_source=ts-docs)

## On this page

- [Properties](https://docs.typesafe.ai/sdk/javascript/api/interfaces/TypeSafeClientConfig#properties)
  - [apiKey?](https://docs.typesafe.ai/sdk/javascript/api/interfaces/TypeSafeClientConfig#apikey)
  - [baseURL?](https://docs.typesafe.ai/sdk/javascript/api/interfaces/TypeSafeClientConfig#baseurl)
  - [dangerouslyAllowBrowser?](https://docs.typesafe.ai/sdk/javascript/api/interfaces/TypeSafeClientConfig#dangerouslyallowbrowser)
  - [defaultHeaders?](https://docs.typesafe.ai/sdk/javascript/api/interfaces/TypeSafeClientConfig#defaultheaders)
  - [defaultModel?](https://docs.typesafe.ai/sdk/javascript/api/interfaces/TypeSafeClientConfig#defaultmodel)
  - [fetch?](https://docs.typesafe.ai/sdk/javascript/api/interfaces/TypeSafeClientConfig#fetch)
  - [logger?](https://docs.typesafe.ai/sdk/javascript/api/interfaces/TypeSafeClientConfig#logger)
  - [logLevel?](https://docs.typesafe.ai/sdk/javascript/api/interfaces/TypeSafeClientConfig#loglevel)
  - [retry?](https://docs.typesafe.ai/sdk/javascript/api/interfaces/TypeSafeClientConfig#retry)
  - [timeout?](https://docs.typesafe.ai/sdk/javascript/api/interfaces/TypeSafeClientConfig#timeout)

[github](https://github.com/typesafe-ai)[discord](https://discord.gg/typesafe)[x](https://x.com/typesafeai)

[Powered byThis documentation is built and hosted on Mintlify, a developer documentation platform](https://www.mintlify.com/?utm_campaign=poweredBy&utm_medium=referral&utm_source=ts-docs)