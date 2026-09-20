---
title: "Function: choice() - TypeSafe AI"
date: "2026-09-18T09:14:15.511Z"
url: "https://docs.typesafe.ai/sdk/javascript/api/functions/choice"
publisher: "TypeSafe AI"
lang: "en"
description: "Create a question that selects between named alternatives."
logo_url: "https://docs.typesafe.ai/mintlify-assets/_mintlify/favicons/ts-docs/zg2v0DiYB7xPw0I2/_generated/favicon/android-chrome-192x192.png"
logo_type: "png"
logo_size: 8885
logo_height: 192
logo_width: 192
logo_size_pretty: "8.88 kB"
image_url: "https://ts-docs.mintlify.app/mintlify-assets/_next/image?url=%2F_mintlify%2Fapi%2Fog%3Fdivision%3DFunctions%26title%3DFunction%253A%2Bchoice%2528%2529%26theme%3Df0580ae664a0195833f0555d&w=1200&q=100"
image_type: "png"
image_size: 26919
image_height: 630
image_width: 1200
image_size_pretty: "26.9 kB"
word_count: 168
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
function choice<T>(instructions, criteria): ChoiceQuestion<T>;
```

Create a question that selects between named alternatives.

## Type Parameters

### T

`T` *extends* [`ChoiceCriteria`](https://docs.typesafe.ai/sdk/javascript/api/type-aliases/ChoiceCriteria)

## Parameters

### instructions

[`EntryType`](https://docs.typesafe.ai/sdk/javascript/api/type-aliases/EntryType)

The question as text, a JSON object or array, or `null`.

### criteria

`T`

Labels mapped to descriptions, or `null` for undescribed labels.

## Returns

[`ChoiceQuestion`](https://docs.typesafe.ai/sdk/javascript/api/interfaces/ChoiceQuestion) \<`T`\>

Was this page helpful?

[Variable: VERSION](https://docs.typesafe.ai/sdk/javascript/api/variables/VERSION)

[Previous](https://docs.typesafe.ai/sdk/javascript/api/variables/VERSION) [Function: noul() Next](https://docs.typesafe.ai/sdk/javascript/api/functions/noul)

[github](https://github.com/typesafe-ai) [discord](https://discord.gg/typesafe) [x](https://x.com/typesafeai)

[Powered byThis documentation is built and hosted on Mintlify, a developer documentation platform](https://www.mintlify.com/?utm_campaign=poweredBy&utm_medium=referral&utm_source=ts-docs)

## On this page

- [Type Parameters](https://docs.typesafe.ai/sdk/javascript/api/functions/choice#type-parameters)
  - [T](https://docs.typesafe.ai/sdk/javascript/api/functions/choice#t)
- [Parameters](https://docs.typesafe.ai/sdk/javascript/api/functions/choice#parameters)
  - [instructions](https://docs.typesafe.ai/sdk/javascript/api/functions/choice#instructions)
  - [criteria](https://docs.typesafe.ai/sdk/javascript/api/functions/choice#criteria)
- [Returns](https://docs.typesafe.ai/sdk/javascript/api/functions/choice#returns)

[github](https://github.com/typesafe-ai)[discord](https://discord.gg/typesafe)[x](https://x.com/typesafeai)

[Powered byThis documentation is built and hosted on Mintlify, a developer documentation platform](https://www.mintlify.com/?utm_campaign=poweredBy&utm_medium=referral&utm_source=ts-docs)