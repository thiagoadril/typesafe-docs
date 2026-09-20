---
title: "Interface: NoulQuestion - TypeSafe AI"
date: "2026-09-18T09:14:15.514Z"
url: "https://docs.typesafe.ai/sdk/javascript/api/interfaces/NoulQuestion"
publisher: "TypeSafe AI"
lang: "en"
description: "A yes/no question with optional descriptions for either outcome."
logo_url: "https://docs.typesafe.ai/mintlify-assets/_mintlify/favicons/ts-docs/zg2v0DiYB7xPw0I2/_generated/favicon/android-chrome-192x192.png"
logo_type: "png"
logo_size: 8885
logo_height: 192
logo_width: 192
logo_size_pretty: "8.88 kB"
image_url: "https://ts-docs.mintlify.app/mintlify-assets/_next/image?url=%2F_mintlify%2Fapi%2Fog%3Fdivision%3DInterfaces%26title%3DInterface%253A%2BNoulQuestion%26theme%3Df0580ae664a0195833f0555d&w=1200&q=100"
image_type: "png"
image_size: 29139
image_height: 630
image_width: 1200
image_size_pretty: "29.1 kB"
word_count: 136
reading_time: "1 min read"
---

[← Voltar ao índice](./README.md)


## Table of Contents

- [Properties](#properties)
  - [criteria?](#criteria)
    - [Union Members](#union-members)
      - [Type Literal](#type-literal)
      - [false?](#false)
      - [true?](#true)
  - [instructions?](#instructions)
  - [type](#type)
- [On this page](#on-this-page)

---

Interfaces

A yes/no question with optional descriptions for either outcome.

## Properties

### criteria?

```typescript
optional criteria?:
  | {
  false?: EntryType;
  true?: EntryType;
}
  | null;
```

Optional descriptions of the yes and no outcomes.

#### Union Members

##### Type Literal

```typescript
{
  false?: EntryType;
  true?: EntryType;
}
```

##### false?

```typescript
optional false?: EntryType;
```

Description of the no outcome.

##### true?

```typescript
optional true?: EntryType;
```

Description of the yes outcome.

------------------------------------------------------------------------

`null`

------------------------------------------------------------------------

### instructions?

```typescript
optional instructions?: EntryType;
```

The question as text, a JSON object, or an array; optional or `null`.

------------------------------------------------------------------------

### type

```typescript
type: "noul";
```

Was this page helpful?

[Interface: Models](https://docs.typesafe.ai/sdk/javascript/api/interfaces/Models)

[Previous](https://docs.typesafe.ai/sdk/javascript/api/interfaces/Models) [Interface: NoulResponse Next](https://docs.typesafe.ai/sdk/javascript/api/interfaces/NoulResponse)

[github](https://github.com/typesafe-ai) [discord](https://discord.gg/typesafe) [x](https://x.com/typesafeai)

[Powered byThis documentation is built and hosted on Mintlify, a developer documentation platform](https://www.mintlify.com/?utm_campaign=poweredBy&utm_medium=referral&utm_source=ts-docs)

## On this page

- [Properties](https://docs.typesafe.ai/sdk/javascript/api/interfaces/NoulQuestion#properties)
  - [criteria?](https://docs.typesafe.ai/sdk/javascript/api/interfaces/NoulQuestion#criteria)
  - [Union Members](https://docs.typesafe.ai/sdk/javascript/api/interfaces/NoulQuestion#union-members)
  - [instructions?](https://docs.typesafe.ai/sdk/javascript/api/interfaces/NoulQuestion#instructions)
  - [type](https://docs.typesafe.ai/sdk/javascript/api/interfaces/NoulQuestion#type)

[github](https://github.com/typesafe-ai)[discord](https://discord.gg/typesafe)[x](https://x.com/typesafeai)

[Powered byThis documentation is built and hosted on Mintlify, a developer documentation platform](https://www.mintlify.com/?utm_campaign=poweredBy&utm_medium=referral&utm_source=ts-docs)