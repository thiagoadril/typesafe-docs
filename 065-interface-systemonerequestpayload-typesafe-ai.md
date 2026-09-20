---
title: "Interface: SystemOneRequestPayload - TypeSafe AI"
date: "2026-09-18T09:14:15.484Z"
url: "https://docs.typesafe.ai/sdk/javascript/api/interfaces/SystemOneRequestPayload"
publisher: "TypeSafe AI"
lang: "en"
description: "Request body for POST /v1/systemone, with the model resolved."
logo_url: "https://docs.typesafe.ai/mintlify-assets/_mintlify/favicons/ts-docs/zg2v0DiYB7xPw0I2/_generated/favicon/android-chrome-192x192.png"
logo_type: "png"
logo_size: 8885
logo_height: 192
logo_width: 192
logo_size_pretty: "8.88 kB"
image_url: "https://ts-docs.mintlify.app/mintlify-assets/_next/image?url=%2F_mintlify%2Fapi%2Fog%3Fdivision%3DInterfaces%26title%3DInterface%253A%2BSystemOneRequestPayload%26theme%3Df0580ae664a0195833f0555d&w=1200&q=100"
image_type: "png"
image_size: 33842
image_height: 630
image_width: 1200
image_size_pretty: "33.8 kB"
word_count: 172
reading_time: "1 min read"
---

[← Voltar ao índice](./README.md)


## Table of Contents

- [Extends](#extends)
- [Properties](#properties)
  - [model](#model)
    - [Overrides](#overrides)
  - [questions](#questions)
    - [Inherited from](#inherited-from)
  - [state](#state)
    - [Inherited from](#inherited-from-1)
- [On this page](#on-this-page)

---

Interfaces

Request body for `POST /v1/systemone`, with the model resolved.

## Extends

- [`SystemOneRequest`](https://docs.typesafe.ai/sdk/javascript/api/interfaces/SystemOneRequest)

## Properties

### model

```typescript
model: string;
```

Model override; omitted values inherit `defaultModel`.

#### Overrides

[`SystemOneRequest`](https://docs.typesafe.ai/sdk/javascript/api/interfaces/SystemOneRequest).[`model`](https://docs.typesafe.ai/sdk/javascript/api/interfaces/SystemOneRequest#sdk-model)

------------------------------------------------------------------------

### questions

```typescript
questions: Questions;
```

Nonempty questions keyed by the names used to identify their answers.

#### Inherited from

[`SystemOneRequest`](https://docs.typesafe.ai/sdk/javascript/api/interfaces/SystemOneRequest).[`questions`](https://docs.typesafe.ai/sdk/javascript/api/interfaces/SystemOneRequest#sdk-questions)

------------------------------------------------------------------------

### state

```typescript
state: EntryType;
```

Text, a JSON object or array, or `null` to evaluate.

#### Inherited from

[`SystemOneRequest`](https://docs.typesafe.ai/sdk/javascript/api/interfaces/SystemOneRequest).[`state`](https://docs.typesafe.ai/sdk/javascript/api/interfaces/SystemOneRequest#sdk-state)

Was this page helpful?

[Interface: SystemOneRequest\<Q\>](https://docs.typesafe.ai/sdk/javascript/api/interfaces/SystemOneRequest)

[Previous](https://docs.typesafe.ai/sdk/javascript/api/interfaces/SystemOneRequest) [Interface: SystemOneResult\<Q\> Next](https://docs.typesafe.ai/sdk/javascript/api/interfaces/SystemOneResult)

[github](https://github.com/typesafe-ai) [discord](https://discord.gg/typesafe) [x](https://x.com/typesafeai)

[Powered byThis documentation is built and hosted on Mintlify, a developer documentation platform](https://www.mintlify.com/?utm_campaign=poweredBy&utm_medium=referral&utm_source=ts-docs)

## On this page

- [Extends](https://docs.typesafe.ai/sdk/javascript/api/interfaces/SystemOneRequestPayload#extends)
- [Properties](https://docs.typesafe.ai/sdk/javascript/api/interfaces/SystemOneRequestPayload#properties)
  - [model](https://docs.typesafe.ai/sdk/javascript/api/interfaces/SystemOneRequestPayload#model)
  - [Overrides](https://docs.typesafe.ai/sdk/javascript/api/interfaces/SystemOneRequestPayload#overrides)
  - [questions](https://docs.typesafe.ai/sdk/javascript/api/interfaces/SystemOneRequestPayload#questions)
  - [Inherited from](https://docs.typesafe.ai/sdk/javascript/api/interfaces/SystemOneRequestPayload#inherited-from)
  - [state](https://docs.typesafe.ai/sdk/javascript/api/interfaces/SystemOneRequestPayload#state)
  - [Inherited from](https://docs.typesafe.ai/sdk/javascript/api/interfaces/SystemOneRequestPayload#inherited-from-2)

[github](https://github.com/typesafe-ai)[discord](https://discord.gg/typesafe)[x](https://x.com/typesafeai)

[Powered byThis documentation is built and hosted on Mintlify, a developer documentation platform](https://www.mintlify.com/?utm_campaign=poweredBy&utm_medium=referral&utm_source=ts-docs)