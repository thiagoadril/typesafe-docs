---
title: "Interface: ChoiceQuestion<T> - TypeSafe AI"
date: "2026-09-18T09:14:15.486Z"
url: "https://docs.typesafe.ai/sdk/javascript/api/interfaces/ChoiceQuestion"
publisher: "TypeSafe AI"
lang: "en"
description: "A question that selects between named alternatives."
logo_url: "https://docs.typesafe.ai/mintlify-assets/_mintlify/favicons/ts-docs/zg2v0DiYB7xPw0I2/_generated/favicon/android-chrome-192x192.png"
logo_type: "png"
logo_size: 8885
logo_height: 192
logo_width: 192
logo_size_pretty: "8.88 kB"
image_url: "https://ts-docs.mintlify.app/mintlify-assets/_next/image?url=%2F_mintlify%2Fapi%2Fog%3Fdivision%3DInterfaces%26title%3DInterface%253A%2BChoiceQuestion%253CT%253E%26theme%3Df0580ae664a0195833f0555d&w=1200&q=100"
image_type: "png"
image_size: 30128
image_height: 630
image_width: 1200
image_size_pretty: "30.1 kB"
word_count: 132
reading_time: "1 min read"
---

[← Voltar ao índice](./README.md)


## Table of Contents

- [Type Parameters](#type-parameters)
  - [T](#t)
- [Properties](#properties)
  - [criteria](#criteria)
  - [instructions?](#instructions)
  - [type](#type)
- [On this page](#on-this-page)

---

Interfaces

A question that selects between named alternatives.

## Type Parameters

### T

`T` *extends* [`ChoiceCriteria`](https://docs.typesafe.ai/sdk/javascript/api/type-aliases/ChoiceCriteria) = [`ChoiceCriteria`](https://docs.typesafe.ai/sdk/javascript/api/type-aliases/ChoiceCriteria)

## Properties

### criteria

```typescript
criteria: T;
```

Descriptions of the available outcomes.

------------------------------------------------------------------------

### instructions?

```typescript
optional instructions?: EntryType;
```

The question as text, a JSON object, or an array; optional or `null`.

------------------------------------------------------------------------

### type

```typescript
type: "choice";
```

Was this page helpful?

[Class: UnprocessableEntityError](https://docs.typesafe.ai/sdk/javascript/api/classes/UnprocessableEntityError)

[Previous](https://docs.typesafe.ai/sdk/javascript/api/classes/UnprocessableEntityError) [Interface: ChoiceResponse\<T\> Next](https://docs.typesafe.ai/sdk/javascript/api/interfaces/ChoiceResponse)

[github](https://github.com/typesafe-ai) [discord](https://discord.gg/typesafe) [x](https://x.com/typesafeai)

[Powered byThis documentation is built and hosted on Mintlify, a developer documentation platform](https://www.mintlify.com/?utm_campaign=poweredBy&utm_medium=referral&utm_source=ts-docs)

## On this page

- [Type Parameters](https://docs.typesafe.ai/sdk/javascript/api/interfaces/ChoiceQuestion#type-parameters)
  - [T](https://docs.typesafe.ai/sdk/javascript/api/interfaces/ChoiceQuestion#t)
- [Properties](https://docs.typesafe.ai/sdk/javascript/api/interfaces/ChoiceQuestion#properties)
  - [criteria](https://docs.typesafe.ai/sdk/javascript/api/interfaces/ChoiceQuestion#criteria)
  - [instructions?](https://docs.typesafe.ai/sdk/javascript/api/interfaces/ChoiceQuestion#instructions)
  - [type](https://docs.typesafe.ai/sdk/javascript/api/interfaces/ChoiceQuestion#type)

[github](https://github.com/typesafe-ai)[discord](https://discord.gg/typesafe)[x](https://x.com/typesafeai)

[Powered byThis documentation is built and hosted on Mintlify, a developer documentation platform](https://www.mintlify.com/?utm_campaign=poweredBy&utm_medium=referral&utm_source=ts-docs)