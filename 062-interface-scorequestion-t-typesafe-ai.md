---
title: "Interface: ScoreQuestion<T> - TypeSafe AI"
date: "2026-09-18T09:14:15.478Z"
url: "https://docs.typesafe.ai/sdk/javascript/api/interfaces/ScoreQuestion"
publisher: "TypeSafe AI"
lang: "en"
description: "A question that assigns a score using an ordered rubric."
logo_url: "https://docs.typesafe.ai/mintlify-assets/_mintlify/favicons/ts-docs/zg2v0DiYB7xPw0I2/_generated/favicon/android-chrome-192x192.png"
logo_type: "png"
logo_size: 8885
logo_height: 192
logo_width: 192
logo_size_pretty: "8.88 kB"
image_url: "https://ts-docs.mintlify.app/mintlify-assets/_next/image?url=%2F_mintlify%2Fapi%2Fog%3Fdivision%3DInterfaces%26title%3DInterface%253A%2BScoreQuestion%253CT%253E%26theme%3Df0580ae664a0195833f0555d&w=1200&q=100"
image_type: "png"
image_size: 29891
image_height: 630
image_width: 1200
image_size_pretty: "29.9 kB"
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

A question that assigns a score using an ordered rubric.

## Type Parameters

### T

`T` *extends* [`ScoreCriteria`](https://docs.typesafe.ai/sdk/javascript/api/type-aliases/ScoreCriteria) = [`ScoreCriteria`](https://docs.typesafe.ai/sdk/javascript/api/type-aliases/ScoreCriteria)

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
type: "score";
```

Was this page helpful?

[Interface: RetryPolicy](https://docs.typesafe.ai/sdk/javascript/api/interfaces/RetryPolicy)

[Previous](https://docs.typesafe.ai/sdk/javascript/api/interfaces/RetryPolicy) [Interface: ScoreResponse\<T\> Next](https://docs.typesafe.ai/sdk/javascript/api/interfaces/ScoreResponse)

[github](https://github.com/typesafe-ai) [discord](https://discord.gg/typesafe) [x](https://x.com/typesafeai)

[Powered byThis documentation is built and hosted on Mintlify, a developer documentation platform](https://www.mintlify.com/?utm_campaign=poweredBy&utm_medium=referral&utm_source=ts-docs)

## On this page

- [Type Parameters](https://docs.typesafe.ai/sdk/javascript/api/interfaces/ScoreQuestion#type-parameters)
  - [T](https://docs.typesafe.ai/sdk/javascript/api/interfaces/ScoreQuestion#t)
- [Properties](https://docs.typesafe.ai/sdk/javascript/api/interfaces/ScoreQuestion#properties)
  - [criteria](https://docs.typesafe.ai/sdk/javascript/api/interfaces/ScoreQuestion#criteria)
  - [instructions?](https://docs.typesafe.ai/sdk/javascript/api/interfaces/ScoreQuestion#instructions)
  - [type](https://docs.typesafe.ai/sdk/javascript/api/interfaces/ScoreQuestion#type)

[github](https://github.com/typesafe-ai)[discord](https://discord.gg/typesafe)[x](https://x.com/typesafeai)

[Powered byThis documentation is built and hosted on Mintlify, a developer documentation platform](https://www.mintlify.com/?utm_campaign=poweredBy&utm_medium=referral&utm_source=ts-docs)