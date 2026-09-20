---
title: "Interface: SystemOneRequest<Q> - TypeSafe AI"
date: "2026-09-18T09:14:15.514Z"
url: "https://docs.typesafe.ai/sdk/javascript/api/interfaces/SystemOneRequest"
publisher: "TypeSafe AI"
lang: "en"
description: "State and named questions for systemOne.
Additional properties on a request variable are forwarded, including null values."
logo_url: "https://docs.typesafe.ai/mintlify-assets/_mintlify/favicons/ts-docs/zg2v0DiYB7xPw0I2/_generated/favicon/android-chrome-192x192.png"
logo_type: "png"
logo_size: 8885
logo_height: 192
logo_width: 192
logo_size_pretty: "8.88 kB"
image_url: "https://ts-docs.mintlify.app/mintlify-assets/_next/image?url=%2F_mintlify%2Fapi%2Fog%3Fdivision%3DInterfaces%26title%3DInterface%253A%2BSystemOneRequest%253CQ%253E%26theme%3Df0580ae664a0195833f0555d&w=1200&q=100"
image_type: "png"
image_size: 31312
image_height: 630
image_width: 1200
image_size_pretty: "31.3 kB"
word_count: 147
reading_time: "1 min read"
---

[← Voltar ao índice](./README.md)


## Table of Contents

- [Extended by](#extended-by)
- [Type Parameters](#type-parameters)
  - [Q](#q)
- [Properties](#properties)
  - [model?](#model)
  - [questions](#questions)
  - [state](#state)
- [On this page](#on-this-page)

---

Interfaces

State and named questions for `systemOne`.

Additional properties on a request variable are forwarded, including `null` values.

## Extended by

- [`SystemOneRequestPayload`](https://docs.typesafe.ai/sdk/javascript/api/interfaces/SystemOneRequestPayload)

## Type Parameters

### Q

`Q` *extends* [`Questions`](https://docs.typesafe.ai/sdk/javascript/api/interfaces/Questions) = [`Questions`](https://docs.typesafe.ai/sdk/javascript/api/interfaces/Questions)

## Properties

### model?

```typescript
optional model?: string;
```

Model override; omitted values inherit `defaultModel`.

------------------------------------------------------------------------

### questions

```typescript
questions: Q;
```

Nonempty questions keyed by the names used to identify their answers.

------------------------------------------------------------------------

### state

```typescript
state: EntryType;
```

Text, a JSON object or array, or `null` to evaluate.

Was this page helpful?

[Interface: ScoreResponse\<T\>](https://docs.typesafe.ai/sdk/javascript/api/interfaces/ScoreResponse)

[Previous](https://docs.typesafe.ai/sdk/javascript/api/interfaces/ScoreResponse) [Interface: SystemOneRequestPayload Next](https://docs.typesafe.ai/sdk/javascript/api/interfaces/SystemOneRequestPayload)

[github](https://github.com/typesafe-ai) [discord](https://discord.gg/typesafe) [x](https://x.com/typesafeai)

[Powered byThis documentation is built and hosted on Mintlify, a developer documentation platform](https://www.mintlify.com/?utm_campaign=poweredBy&utm_medium=referral&utm_source=ts-docs)

## On this page

- [Extended by](https://docs.typesafe.ai/sdk/javascript/api/interfaces/SystemOneRequest#extended-by)
- [Type Parameters](https://docs.typesafe.ai/sdk/javascript/api/interfaces/SystemOneRequest#type-parameters)
  - [Q](https://docs.typesafe.ai/sdk/javascript/api/interfaces/SystemOneRequest#q)
- [Properties](https://docs.typesafe.ai/sdk/javascript/api/interfaces/SystemOneRequest#properties)
  - [model?](https://docs.typesafe.ai/sdk/javascript/api/interfaces/SystemOneRequest#model)
  - [questions](https://docs.typesafe.ai/sdk/javascript/api/interfaces/SystemOneRequest#questions)
  - [state](https://docs.typesafe.ai/sdk/javascript/api/interfaces/SystemOneRequest#state)

[github](https://github.com/typesafe-ai)[discord](https://discord.gg/typesafe)[x](https://x.com/typesafeai)

[Powered byThis documentation is built and hosted on Mintlify, a developer documentation platform](https://www.mintlify.com/?utm_campaign=poweredBy&utm_medium=referral&utm_source=ts-docs)