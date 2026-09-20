---
title: "Interface: ChoiceResponse<T> - TypeSafe AI"
date: "2026-09-18T09:14:15.508Z"
url: "https://docs.typesafe.ai/sdk/javascript/api/interfaces/ChoiceResponse"
publisher: "TypeSafe AI"
lang: "en"
description: "A selected label and its probabilities."
logo_url: "https://docs.typesafe.ai/mintlify-assets/_mintlify/favicons/ts-docs/zg2v0DiYB7xPw0I2/_generated/favicon/android-chrome-192x192.png"
logo_type: "png"
logo_size: 8885
logo_height: 192
logo_width: 192
logo_size_pretty: "8.88 kB"
image_url: "https://ts-docs.mintlify.app/mintlify-assets/_next/image?url=%2F_mintlify%2Fapi%2Fog%3Fdivision%3DInterfaces%26title%3DInterface%253A%2BChoiceResponse%253CT%253E%26theme%3Df0580ae664a0195833f0555d&w=1200&q=100"
image_type: "png"
image_size: 30429
image_height: 630
image_width: 1200
image_size_pretty: "30.4 kB"
word_count: 148
reading_time: "1 min read"
---

[← Voltar ao índice](./README.md)


## Table of Contents

- [Type Parameters](#type-parameters)
  - [T](#t)
- [Properties](#properties)
  - [choice](#choice)
  - [confidence](#confidence)
  - [probabilities](#probabilities)
  - [type](#type)
- [On this page](#on-this-page)

---

Interfaces

A selected label and its probabilities.

## Type Parameters

### T

`T` *extends* [`ChoiceCriteria`](https://docs.typesafe.ai/sdk/javascript/api/type-aliases/ChoiceCriteria) = [`ChoiceCriteria`](https://docs.typesafe.ai/sdk/javascript/api/type-aliases/ChoiceCriteria)

## Properties

### choice

```typescript
readonly choice: keyof T & string;
```

The selected label.

------------------------------------------------------------------------

### confidence

```typescript
readonly confidence: number;
```

Reported confidence in the selected label.

------------------------------------------------------------------------

### probabilities

```typescript
readonly probabilities: { readonly [label in string | number | symbol]: number };
```

Probabilities keyed by label.

------------------------------------------------------------------------

### type

```typescript
readonly type: "choice";
```

Was this page helpful?

[Interface: ChoiceQuestion\<T\>](https://docs.typesafe.ai/sdk/javascript/api/interfaces/ChoiceQuestion)

[Previous](https://docs.typesafe.ai/sdk/javascript/api/interfaces/ChoiceQuestion) [Interface: Logger Next](https://docs.typesafe.ai/sdk/javascript/api/interfaces/Logger)

[github](https://github.com/typesafe-ai) [discord](https://discord.gg/typesafe) [x](https://x.com/typesafeai)

[Powered byThis documentation is built and hosted on Mintlify, a developer documentation platform](https://www.mintlify.com/?utm_campaign=poweredBy&utm_medium=referral&utm_source=ts-docs)

## On this page

- [Type Parameters](https://docs.typesafe.ai/sdk/javascript/api/interfaces/ChoiceResponse#type-parameters)
  - [T](https://docs.typesafe.ai/sdk/javascript/api/interfaces/ChoiceResponse#t)
- [Properties](https://docs.typesafe.ai/sdk/javascript/api/interfaces/ChoiceResponse#properties)
  - [choice](https://docs.typesafe.ai/sdk/javascript/api/interfaces/ChoiceResponse#choice)
  - [confidence](https://docs.typesafe.ai/sdk/javascript/api/interfaces/ChoiceResponse#confidence)
  - [probabilities](https://docs.typesafe.ai/sdk/javascript/api/interfaces/ChoiceResponse#probabilities)
  - [type](https://docs.typesafe.ai/sdk/javascript/api/interfaces/ChoiceResponse#type)

[github](https://github.com/typesafe-ai)[discord](https://discord.gg/typesafe)[x](https://x.com/typesafeai)

[Powered byThis documentation is built and hosted on Mintlify, a developer documentation platform](https://www.mintlify.com/?utm_campaign=poweredBy&utm_medium=referral&utm_source=ts-docs)