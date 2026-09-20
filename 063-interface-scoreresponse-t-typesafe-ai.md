---
title: "Interface: ScoreResponse<T> - TypeSafe AI"
date: "2026-09-18T09:14:15.484Z"
url: "https://docs.typesafe.ai/sdk/javascript/api/interfaces/ScoreResponse"
publisher: "TypeSafe AI"
lang: "en"
description: "An expected score with its rubric and probabilities."
logo_url: "https://docs.typesafe.ai/mintlify-assets/_mintlify/favicons/ts-docs/zg2v0DiYB7xPw0I2/_generated/favicon/android-chrome-192x192.png"
logo_type: "png"
logo_size: 8885
logo_height: 192
logo_width: 192
logo_size_pretty: "8.88 kB"
image_url: "https://ts-docs.mintlify.app/mintlify-assets/_next/image?url=%2F_mintlify%2Fapi%2Fog%3Fdivision%3DInterfaces%26title%3DInterface%253A%2BScoreResponse%253CT%253E%26theme%3Df0580ae664a0195833f0555d&w=1200&q=100"
image_type: "png"
image_size: 30264
image_height: 630
image_width: 1200
image_size_pretty: "30.3 kB"
word_count: 166
reading_time: "1 min read"
---

[← Voltar ao índice](./README.md)


## Table of Contents

- [Type Parameters](#type-parameters)
  - [T](#t)
- [Properties](#properties)
  - [confidence](#confidence)
  - [legend](#legend)
  - [probabilities](#probabilities)
  - [score](#score)
  - [type](#type)
- [On this page](#on-this-page)

---

Interfaces

An expected score with its rubric and probabilities.

## Type Parameters

### T

`T` *extends* [`ScoreCriteria`](https://docs.typesafe.ai/sdk/javascript/api/type-aliases/ScoreCriteria) = [`ScoreCriteria`](https://docs.typesafe.ai/sdk/javascript/api/type-aliases/ScoreCriteria)

## Properties

### confidence

```typescript
readonly confidence: number;
```

Reported confidence in the score.

------------------------------------------------------------------------

### legend

```typescript
readonly legend: ScoreLegend<T>;
```

Rubric descriptions keyed by score.

------------------------------------------------------------------------

### probabilities

```typescript
readonly probabilities: { readonly [score in number | `${number}`]: number };
```

Probabilities keyed by score.

------------------------------------------------------------------------

### score

```typescript
readonly score: number;
```

Expected score, which may fall between integer rubric levels.

------------------------------------------------------------------------

### type

```typescript
readonly type: "score";
```

Was this page helpful?

[Interface: ScoreQuestion\<T\>](https://docs.typesafe.ai/sdk/javascript/api/interfaces/ScoreQuestion)

[Previous](https://docs.typesafe.ai/sdk/javascript/api/interfaces/ScoreQuestion) [Interface: SystemOneRequest\<Q\> Next](https://docs.typesafe.ai/sdk/javascript/api/interfaces/SystemOneRequest)

[github](https://github.com/typesafe-ai) [discord](https://discord.gg/typesafe) [x](https://x.com/typesafeai)

[Powered byThis documentation is built and hosted on Mintlify, a developer documentation platform](https://www.mintlify.com/?utm_campaign=poweredBy&utm_medium=referral&utm_source=ts-docs)

## On this page

- [Type Parameters](https://docs.typesafe.ai/sdk/javascript/api/interfaces/ScoreResponse#type-parameters)
  - [T](https://docs.typesafe.ai/sdk/javascript/api/interfaces/ScoreResponse#t)
- [Properties](https://docs.typesafe.ai/sdk/javascript/api/interfaces/ScoreResponse#properties)
  - [confidence](https://docs.typesafe.ai/sdk/javascript/api/interfaces/ScoreResponse#confidence)
  - [legend](https://docs.typesafe.ai/sdk/javascript/api/interfaces/ScoreResponse#legend)
  - [probabilities](https://docs.typesafe.ai/sdk/javascript/api/interfaces/ScoreResponse#probabilities)
  - [score](https://docs.typesafe.ai/sdk/javascript/api/interfaces/ScoreResponse#score)
  - [type](https://docs.typesafe.ai/sdk/javascript/api/interfaces/ScoreResponse#type)

[github](https://github.com/typesafe-ai)[discord](https://discord.gg/typesafe)[x](https://x.com/typesafeai)

[Powered byThis documentation is built and hosted on Mintlify, a developer documentation platform](https://www.mintlify.com/?utm_campaign=poweredBy&utm_medium=referral&utm_source=ts-docs)