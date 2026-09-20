---
title: "Interface: SystemOneResult<Q> - TypeSafe AI"
date: "2026-09-18T09:14:15.479Z"
url: "https://docs.typesafe.ai/sdk/javascript/api/interfaces/SystemOneResult"
publisher: "TypeSafe AI"
lang: "en"
description: "Answers keyed by question name, with model and usage metadata."
logo_url: "https://docs.typesafe.ai/mintlify-assets/_mintlify/favicons/ts-docs/zg2v0DiYB7xPw0I2/_generated/favicon/android-chrome-192x192.png"
logo_type: "png"
logo_size: 8885
logo_height: 192
logo_width: 192
logo_size_pretty: "8.88 kB"
image_url: "https://ts-docs.mintlify.app/mintlify-assets/_next/image?url=%2F_mintlify%2Fapi%2Fog%3Fdivision%3DInterfaces%26title%3DInterface%253A%2BSystemOneResult%253CQ%253E%26theme%3Df0580ae664a0195833f0555d&w=1200&q=100"
image_type: "png"
image_size: 30659
image_height: 630
image_width: 1200
image_size_pretty: "30.7 kB"
word_count: 131
reading_time: "1 min read"
---

[← Voltar ao índice](./README.md)


## Table of Contents

- [Type Parameters](#type-parameters)
  - [Q](#q)
- [Properties](#properties)
  - [answers](#answers)
  - [model](#model)
  - [usage](#usage)
- [On this page](#on-this-page)

---

Interfaces

Answers keyed by question name, with model and usage metadata.

## Type Parameters

### Q

`Q` *extends* [`Questions`](https://docs.typesafe.ai/sdk/javascript/api/interfaces/Questions)

## Properties

### answers

```typescript
readonly answers: { readonly [K in string | number | symbol]: ResultFor<Q[K]> };
```

Answers with types inferred from the supplied questions.

------------------------------------------------------------------------

### model

```typescript
readonly model: string;
```

The model used to answer the request.

------------------------------------------------------------------------

### usage

```typescript
readonly usage: Usage;
```

Token usage for the request.

Was this page helpful?

[Interface: SystemOneRequestPayload](https://docs.typesafe.ai/sdk/javascript/api/interfaces/SystemOneRequestPayload)

[Previous](https://docs.typesafe.ai/sdk/javascript/api/interfaces/SystemOneRequestPayload) [Interface: TypeSafeClientConfig Next](https://docs.typesafe.ai/sdk/javascript/api/interfaces/TypeSafeClientConfig)

[github](https://github.com/typesafe-ai) [discord](https://discord.gg/typesafe) [x](https://x.com/typesafeai)

[Powered byThis documentation is built and hosted on Mintlify, a developer documentation platform](https://www.mintlify.com/?utm_campaign=poweredBy&utm_medium=referral&utm_source=ts-docs)

## On this page

- [Type Parameters](https://docs.typesafe.ai/sdk/javascript/api/interfaces/SystemOneResult#type-parameters)
  - [Q](https://docs.typesafe.ai/sdk/javascript/api/interfaces/SystemOneResult#q)
- [Properties](https://docs.typesafe.ai/sdk/javascript/api/interfaces/SystemOneResult#properties)
  - [answers](https://docs.typesafe.ai/sdk/javascript/api/interfaces/SystemOneResult#answers)
  - [model](https://docs.typesafe.ai/sdk/javascript/api/interfaces/SystemOneResult#model)
  - [usage](https://docs.typesafe.ai/sdk/javascript/api/interfaces/SystemOneResult#usage)

[github](https://github.com/typesafe-ai)[discord](https://discord.gg/typesafe)[x](https://x.com/typesafeai)

[Powered byThis documentation is built and hosted on Mintlify, a developer documentation platform](https://www.mintlify.com/?utm_campaign=poweredBy&utm_medium=referral&utm_source=ts-docs)