---
title: "JavaScript SDK - TypeSafe AI"
date: "2026-09-18T09:14:15.555Z"
url: "https://docs.typesafe.ai/sdk/javascript"
publisher: "TypeSafe AI"
lang: "en"
description: "JavaScript and TypeScript SDK for TypeSafe AI."
logo_url: "https://docs.typesafe.ai/mintlify-assets/_mintlify/favicons/ts-docs/zg2v0DiYB7xPw0I2/_generated/favicon/android-chrome-192x192.png"
logo_type: "png"
logo_size: 8885
logo_height: 192
logo_width: 192
logo_size_pretty: "8.88 kB"
image_url: "https://ts-docs.mintlify.app/mintlify-assets/_next/image?url=%2F_mintlify%2Fapi%2Fog%3Fdivision%3DJavaScript%2BSDK%26title%3DJavaScript%2BSDK%26theme%3Df0580ae664a0195833f0555d&w=1200&q=100"
image_type: "png"
image_size: 27892
image_height: 630
image_width: 1200
image_size_pretty: "27.9 kB"
word_count: 224
reading_time: "1 min read"
---

[← Voltar ao índice](./README.md)


## Table of Contents

- [Quickstart](#quickstart)
- [Documentation](#documentation)
- [On this page](#on-this-page)

---

JavaScript SDK

JavaScript and TypeScript SDK for [TypeSafe AI](https://typesafe.ai/).

## Quickstart

Install the SDK (Node.js 20 or newer):

```shellscript
npm install @typesafe-ai/sdk
```

Set `TYPESAFE_API_KEY` in your environment, then create and use the client:

```typescript
import { choice, TypeSafeClient } from "@typesafe-ai/sdk";
const client = new TypeSafeClient();
const response = await client.systemOne({
  state: { document: "I was charged twice. Please fix this ASAP." },
  questions: {
    category: choice("What is this ticket about?", {
      billing: null,
      technical: null,
      other: null,
    }),
  },
});
console.log(response.answers.category.choice);
```

Answer types are inferred from your questions. The package includes ESM, CommonJS, and TypeScript declarations.

## Documentation

Learn what TypeSafe can do in the [TypeSafe docs](https://docs.typesafe.ai/). See the SDK’s [client](https://github.com/typesafe-ai/typesafe-sdk-js/blob/v0.6.0/src/client.ts) and [types](https://github.com/typesafe-ai/typesafe-sdk-js/blob/v0.6.0/src/types.ts) for API options and defaults.

Was this page helpful?

[Constants](https://docs.typesafe.ai/sdk/python/api/constants)

[Previous](https://docs.typesafe.ai/sdk/python/api/constants) [Changelog Next](https://docs.typesafe.ai/sdk/javascript/changelog)

[github](https://github.com/typesafe-ai) [discord](https://discord.gg/typesafe) [x](https://x.com/typesafeai)

[Powered byThis documentation is built and hosted on Mintlify, a developer documentation platform](https://www.mintlify.com/?utm_campaign=poweredBy&utm_medium=referral&utm_source=ts-docs)

## On this page

- [Quickstart](https://docs.typesafe.ai/sdk/javascript#quickstart)
- [Documentation](https://docs.typesafe.ai/sdk/javascript#documentation)

[github](https://github.com/typesafe-ai)[discord](https://discord.gg/typesafe)[x](https://x.com/typesafeai)

[Powered byThis documentation is built and hosted on Mintlify, a developer documentation platform](https://www.mintlify.com/?utm_campaign=poweredBy&utm_medium=referral&utm_source=ts-docs)