---
title: "Function: noul() - TypeSafe AI"
date: "2026-09-18T09:14:15.517Z"
url: "https://docs.typesafe.ai/sdk/javascript/api/functions/noul"
publisher: "TypeSafe AI"
lang: "en"
description: "Create a yes/no question with optional descriptions for either outcome."
logo_url: "https://docs.typesafe.ai/mintlify-assets/_mintlify/favicons/ts-docs/zg2v0DiYB7xPw0I2/_generated/favicon/android-chrome-192x192.png"
logo_type: "png"
logo_size: 8885
logo_height: 192
logo_width: 192
logo_size_pretty: "8.88 kB"
image_url: "https://ts-docs.mintlify.app/mintlify-assets/_next/image?url=%2F_mintlify%2Fapi%2Fog%3Fdivision%3DFunctions%26title%3DFunction%253A%2Bnoul%2528%2529%26theme%3Df0580ae664a0195833f0555d&w=1200&q=100"
image_type: "png"
image_size: 25881
image_height: 630
image_width: 1200
image_size_pretty: "25.9 kB"
word_count: 112
reading_time: "1 min read"
---

[← Voltar ao índice](./README.md)


## Table of Contents

- [Parameters](#parameters)
  - [instructions?](#instructions)
  - [criteria?](#criteria)
    - [Type Literal](#type-literal)
      - [false?](#false)
      - [true?](#true)
- [Returns](#returns)
- [On this page](#on-this-page)

---

Functions

```typescript
function noul(instructions?, criteria?): NoulQuestion;
```

Create a yes/no question with optional descriptions for either outcome.

## Parameters

### instructions?

[`EntryType`](https://docs.typesafe.ai/sdk/javascript/api/type-aliases/EntryType) = `null`

The question as text, a JSON object or array; defaults to `null`.

### criteria?

\| { `false?`: [`EntryType`](https://docs.typesafe.ai/sdk/javascript/api/type-aliases/EntryType); `true?`: [`EntryType`](https://docs.typesafe.ai/sdk/javascript/api/type-aliases/EntryType); } \| `null`

Optional descriptions of the yes and no outcomes.

#### Type Literal

{ `false?`: [`EntryType`](https://docs.typesafe.ai/sdk/javascript/api/type-aliases/EntryType); `true?`: [`EntryType`](https://docs.typesafe.ai/sdk/javascript/api/type-aliases/EntryType); }

Optional descriptions of the yes and no outcomes.

##### false?

[`EntryType`](https://docs.typesafe.ai/sdk/javascript/api/type-aliases/EntryType)

Description of the no outcome.

##### true?

[`EntryType`](https://docs.typesafe.ai/sdk/javascript/api/type-aliases/EntryType)

Description of the yes outcome.

------------------------------------------------------------------------

`null`

## Returns

[`NoulQuestion`](https://docs.typesafe.ai/sdk/javascript/api/interfaces/NoulQuestion)

Was this page helpful?

[Function: choice()](https://docs.typesafe.ai/sdk/javascript/api/functions/choice)

[Previous](https://docs.typesafe.ai/sdk/javascript/api/functions/choice) [Function: score() Next](https://docs.typesafe.ai/sdk/javascript/api/functions/score)

[github](https://github.com/typesafe-ai) [discord](https://discord.gg/typesafe) [x](https://x.com/typesafeai)

[Powered byThis documentation is built and hosted on Mintlify, a developer documentation platform](https://www.mintlify.com/?utm_campaign=poweredBy&utm_medium=referral&utm_source=ts-docs)

## On this page

- [Parameters](https://docs.typesafe.ai/sdk/javascript/api/functions/noul#parameters)
  - [instructions?](https://docs.typesafe.ai/sdk/javascript/api/functions/noul#instructions)
  - [criteria?](https://docs.typesafe.ai/sdk/javascript/api/functions/noul#criteria)
  - [Type Literal](https://docs.typesafe.ai/sdk/javascript/api/functions/noul#type-literal)
- [Returns](https://docs.typesafe.ai/sdk/javascript/api/functions/noul#returns)

[github](https://github.com/typesafe-ai)[discord](https://discord.gg/typesafe)[x](https://x.com/typesafeai)

[Powered byThis documentation is built and hosted on Mintlify, a developer documentation platform](https://www.mintlify.com/?utm_campaign=poweredBy&utm_medium=referral&utm_source=ts-docs)