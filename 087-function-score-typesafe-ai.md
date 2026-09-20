---
title: "Function: score() - TypeSafe AI"
date: "2026-09-18T09:14:15.516Z"
url: "https://docs.typesafe.ai/sdk/javascript/api/functions/score"
publisher: "TypeSafe AI"
lang: "en"
description: "Create a score question using an ordered rubric."
logo_url: "https://docs.typesafe.ai/mintlify-assets/_mintlify/favicons/ts-docs/zg2v0DiYB7xPw0I2/_generated/favicon/android-chrome-192x192.png"
logo_type: "png"
logo_size: 8885
logo_height: 192
logo_width: 192
logo_size_pretty: "8.88 kB"
image_url: "https://ts-docs.mintlify.app/mintlify-assets/_next/image?url=%2F_mintlify%2Fapi%2Fog%3Fdivision%3DFunctions%26title%3DFunction%253A%2Bscore%2528%2529%26theme%3Df0580ae664a0195833f0555d&w=1200&q=100"
image_type: "png"
image_size: 26759
image_height: 630
image_width: 1200
image_size_pretty: "26.8 kB"
word_count: 172
reading_time: "1 min read"
---

[← Voltar ao índice](./README.md)


## Table of Contents

- [Type Parameters](#type-parameters)
  - [T](#t)
- [Parameters](#parameters)
  - [instructions](#instructions)
  - [criteria](#criteria)
- [Returns](#returns)
- [On this page](#on-this-page)

---

Functions

```typescript
function score<T>(instructions, criteria): ScoreQuestion<T>;
```

Create a score question using an ordered rubric.

## Type Parameters

### T

`T` *extends* [`ScoreCriteria`](https://docs.typesafe.ai/sdk/javascript/api/type-aliases/ScoreCriteria)

## Parameters

### instructions

[`EntryType`](https://docs.typesafe.ai/sdk/javascript/api/type-aliases/EntryType)

The question as text, a JSON object or array, or `null`.

### criteria

`T`

At least two descriptions indexed by score from zero; entries may be `null`.

## Returns

[`ScoreQuestion`](https://docs.typesafe.ai/sdk/javascript/api/interfaces/ScoreQuestion) \<`T`\>

Was this page helpful?

[Function: noul()](https://docs.typesafe.ai/sdk/javascript/api/functions/noul)

[Previous](https://docs.typesafe.ai/sdk/javascript/api/functions/noul) [Models Next](https://docs.typesafe.ai/models)

[github](https://github.com/typesafe-ai) [discord](https://discord.gg/typesafe) [x](https://x.com/typesafeai)

[Powered byThis documentation is built and hosted on Mintlify, a developer documentation platform](https://www.mintlify.com/?utm_campaign=poweredBy&utm_medium=referral&utm_source=ts-docs)

## On this page

- [Type Parameters](https://docs.typesafe.ai/sdk/javascript/api/functions/score#type-parameters)
  - [T](https://docs.typesafe.ai/sdk/javascript/api/functions/score#t)
- [Parameters](https://docs.typesafe.ai/sdk/javascript/api/functions/score#parameters)
  - [instructions](https://docs.typesafe.ai/sdk/javascript/api/functions/score#instructions)
  - [criteria](https://docs.typesafe.ai/sdk/javascript/api/functions/score#criteria)
- [Returns](https://docs.typesafe.ai/sdk/javascript/api/functions/score#returns)

[github](https://github.com/typesafe-ai)[discord](https://discord.gg/typesafe)[x](https://x.com/typesafeai)

[Powered byThis documentation is built and hosted on Mintlify, a developer documentation platform](https://www.mintlify.com/?utm_campaign=poweredBy&utm_medium=referral&utm_source=ts-docs)