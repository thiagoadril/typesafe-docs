---
title: "Type Alias: ResultFor<T> - TypeSafe AI"
date: "2026-09-18T09:14:15.478Z"
url: "https://docs.typesafe.ai/sdk/javascript/api/type-aliases/ResultFor"
publisher: "TypeSafe AI"
lang: "en"
description: "TypeSafe AI home page"
logo_url: "https://docs.typesafe.ai/mintlify-assets/_mintlify/favicons/ts-docs/zg2v0DiYB7xPw0I2/_generated/favicon/android-chrome-192x192.png"
logo_type: "png"
logo_size: 8885
logo_height: 192
logo_width: 192
logo_size_pretty: "8.88 kB"
image_url: "https://ts-docs.mintlify.app/mintlify-assets/_next/image?url=%2F_mintlify%2Fapi%2Fog%3Fdivision%3DType%2BAliases%26title%3DType%2BAlias%253A%2BResultFor%253CT%253E%26theme%3Df0580ae664a0195833f0555d&w=1200&q=100"
image_type: "png"
image_size: 28758
image_height: 630
image_width: 1200
image_size_pretty: "28.8 kB"
word_count: 141
reading_time: "1 min read"
---

[← Voltar ao índice](./README.md)


## Table of Contents

- [Type Parameters](#type-parameters)
  - [T](#t)
- [On this page](#on-this-page)

---

Type Aliases

```typescript
type ResultFor<T> = T extends NoulQuestion ? NoulResponse : T extends ScoreQuestion<infer S> ? ScoreResponse<S> : T extends ChoiceQuestion<infer E> ? ChoiceResponse<E> : never;
```

The answer type for a question, preserving its criteria keys.

## Type Parameters

### T

`T` *extends* [`Question`](https://docs.typesafe.ai/sdk/javascript/api/type-aliases/Question)

Was this page helpful?

[Type Alias: Question](https://docs.typesafe.ai/sdk/javascript/api/type-aliases/Question)

[Previous](https://docs.typesafe.ai/sdk/javascript/api/type-aliases/Question) [Type Alias: ScoreCriteria Next](https://docs.typesafe.ai/sdk/javascript/api/type-aliases/ScoreCriteria)

[github](https://github.com/typesafe-ai) [discord](https://discord.gg/typesafe) [x](https://x.com/typesafeai)

[Powered byThis documentation is built and hosted on Mintlify, a developer documentation platform](https://www.mintlify.com/?utm_campaign=poweredBy&utm_medium=referral&utm_source=ts-docs)

## On this page

- [Type Parameters](https://docs.typesafe.ai/sdk/javascript/api/type-aliases/ResultFor#type-parameters)
  - [T](https://docs.typesafe.ai/sdk/javascript/api/type-aliases/ResultFor#t)

[github](https://github.com/typesafe-ai)[discord](https://discord.gg/typesafe)[x](https://x.com/typesafeai)

[Powered byThis documentation is built and hosted on Mintlify, a developer documentation platform](https://www.mintlify.com/?utm_campaign=poweredBy&utm_medium=referral&utm_source=ts-docs)