---
title: "Interface: WithResponse<T> - TypeSafe AI"
date: "2026-09-18T09:14:15.481Z"
url: "https://docs.typesafe.ai/sdk/javascript/api/interfaces/WithResponse"
publisher: "TypeSafe AI"
lang: "en"
description: "Parsed data with its HTTP response and request ID."
logo_url: "https://docs.typesafe.ai/mintlify-assets/_mintlify/favicons/ts-docs/zg2v0DiYB7xPw0I2/_generated/favicon/android-chrome-192x192.png"
logo_type: "png"
logo_size: 8885
logo_height: 192
logo_width: 192
logo_size_pretty: "8.88 kB"
image_url: "https://ts-docs.mintlify.app/mintlify-assets/_next/image?url=%2F_mintlify%2Fapi%2Fog%3Fdivision%3DInterfaces%26title%3DInterface%253A%2BWithResponse%253CT%253E%26theme%3Df0580ae664a0195833f0555d&w=1200&q=100"
image_type: "png"
image_size: 29841
image_height: 630
image_width: 1200
image_size_pretty: "29.8 kB"
word_count: 141
reading_time: "1 min read"
---

[← Voltar ao índice](./README.md)


## Table of Contents

- [Type Parameters](#type-parameters)
  - [T](#t)
- [Properties](#properties)
  - [data](#data)
  - [requestId](#requestid)
  - [response](#response)
- [On this page](#on-this-page)

---

Interfaces

Parsed data with its HTTP response and request ID.

## Type Parameters

### T

`T`

## Properties

### data

```typescript
data: T;
```

The parsed response body.

------------------------------------------------------------------------

### requestId

```typescript
requestId: string | undefined;
```

Request ID from `x-typesafe-request-id`, or `undefined` when absent.

------------------------------------------------------------------------

### response

```typescript
response: Response;
```

The HTTP response, with its body consumed by parsing.

Was this page helpful?

[Interface: Usage](https://docs.typesafe.ai/sdk/javascript/api/interfaces/Usage)

[Previous](https://docs.typesafe.ai/sdk/javascript/api/interfaces/Usage) [Type Alias: ChoiceCriteria Next](https://docs.typesafe.ai/sdk/javascript/api/type-aliases/ChoiceCriteria)

[github](https://github.com/typesafe-ai) [discord](https://discord.gg/typesafe) [x](https://x.com/typesafeai)

[Powered byThis documentation is built and hosted on Mintlify, a developer documentation platform](https://www.mintlify.com/?utm_campaign=poweredBy&utm_medium=referral&utm_source=ts-docs)

## On this page

- [Type Parameters](https://docs.typesafe.ai/sdk/javascript/api/interfaces/WithResponse#type-parameters)
  - [T](https://docs.typesafe.ai/sdk/javascript/api/interfaces/WithResponse#t)
- [Properties](https://docs.typesafe.ai/sdk/javascript/api/interfaces/WithResponse#properties)
  - [data](https://docs.typesafe.ai/sdk/javascript/api/interfaces/WithResponse#data)
  - [requestId](https://docs.typesafe.ai/sdk/javascript/api/interfaces/WithResponse#requestid)
  - [response](https://docs.typesafe.ai/sdk/javascript/api/interfaces/WithResponse#response)

[github](https://github.com/typesafe-ai)[discord](https://discord.gg/typesafe)[x](https://x.com/typesafeai)

[Powered byThis documentation is built and hosted on Mintlify, a developer documentation platform](https://www.mintlify.com/?utm_campaign=poweredBy&utm_medium=referral&utm_source=ts-docs)