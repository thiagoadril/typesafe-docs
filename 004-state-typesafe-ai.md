---
title: "State - TypeSafe AI"
date: "2026-09-18T00:21:13.840Z"
description: "What state is, how to structure it, and how to give a System One model the context it needs."
url: "https://docs.typesafe.ai/concepts/state"
publisher: "TypeSafe AI"
lang: "en"
logo_url: "https://docs.typesafe.ai/mintlify-assets/_mintlify/favicons/ts-docs/zg2v0DiYB7xPw0I2/_generated/favicon/android-chrome-192x192.png"
logo_type: "png"
logo_size: 8885
logo_height: 192
logo_width: 192
logo_size_pretty: "8.88 kB"
image_url: "https://ts-docs.mintlify.app/mintlify-assets/_next/image?url=%2F_mintlify%2Fapi%2Fog%3Fdivision%3DTypeSafe%2Bconcepts%26title%3DState%26description%3DWhat%2Bstate%2Bis%252C%2Bhow%2Bto%2Bstructure%2Bit%252C%2Band%2Bhow%2Bto%2Bgive%2Ba%2BSystem%2BOne%2Bmodel%2Bthe%2Bcontext%2Bit%2Bneeds.%26theme%3Df0580ae664a0195833f0555d&w=1200&q=100"
image_type: "png"
image_size: 36463
image_height: 630
image_width: 1200
image_size_pretty: "36.5 kB"
word_count: 440
reading_time: "2 min read"
---

[← Voltar ao índice](./README.md)


## Table of Contents

- [State can be as simple as a string](#state-can-be-as-simple-as-a-string)
- [Separate content from questions](#separate-content-from-questions)
- [On this page](#on-this-page)

---

TypeSafe concepts

What state is, how to structure it, and how to give a System One model the context it needs.

**State** is the content you ask a System One model to evaluate. It could be a support message, a passage of text, or the current state of your application. You pass it in the `state` field of an API request, alongside the questions you want answered.

Each request evaluates one state against one or more questions. All questions see the same state and are evaluated independently. You can mix [Choice](https://docs.typesafe.ai/primitives/choice), [Score](https://docs.typesafe.ai/primitives/score), and [Noul](https://docs.typesafe.ai/primitives/noul) questions in one request.

## State can be as simple as a string

The simplest state is a plain string:

```python
state = "My card was charged twice."
```

State can also be a JSON object or array containing related context, examples, and other information that helps the model answer the associated questions. Think of state as the material you would present to a panel of experts before asking them to make a judgment. In Python, pass the corresponding string, dictionary, or list directly to `client.system_one(state=...)`.

| Format | Useful for                                          | Example                                                                 |
| ------ | --------------------------------------------------- | ----------------------------------------------------------------------- |
| String | A message, article, or passage                      | `"My card was charged twice."`                                          |
| Object | Named fields, related records, or application state | `{"message": "My card was charged twice.", "order_id": "A-104"}`        |
| Array  | A sequence of messages or records                   | `["Hi", "My customer number is TS1337.", "My card was charged twice."]` |

Use an object for most requests so each part of the state has a descriptive name and its relationships remain clear. A string is suitable when the use case is simple and requires only one piece of text.

Jev accepts text only. State must be a string, JSON object, or array of text values. Images, audio, and video are not supported (yet). Jev’s primary training language is English; other languages, including CJK scripts, are accepted but currently have lower accuracy — see [Models](https://docs.typesafe.ai/models#language-support).

A support conversation as state

```json
{
  "ticket": {
    "subject": "Duplicate charge",
    "messages": [
      {"from": "customer", "text": "I was charged twice for order A-104. Please refund the duplicate."},
      {"from": "support", "text": "We are checking the charges."}
    ]
  },
  "order": {
    "id": "A-104",
    "charges": [
      {"amount_usd": 49, "status": "captured"},
      {"amount_usd": 49, "status": "captured"}
    ]
  },
  "refund_policy": "Duplicate charges are eligible for a refund."
}
```

This object is one state, even though it contains a conversation, an order, and a policy. Put related information together when the decision requires comparing those parts.

## Separate content from questions

The state contains the content and supporting facts. [Questions](https://docs.typesafe.ai/primitives) define the judgments the model should make about that material. For example, keep the refund request and policy in the state, then ask whether the customer requested a refund and whether the policy supports it.

See [Primitives (Questions)](https://docs.typesafe.ai/primitives) for guidance on instructions, criteria, question types, and asking several questions about one state.

See the [API reference](https://docs.typesafe.ai/api) for the request schema and [client SDKs](https://docs.typesafe.ai/sdk) for installation, typed inputs, and response handling.

Was this page helpful?

[System One](https://docs.typesafe.ai/concepts/system-one)

[Previous](https://docs.typesafe.ai/concepts/system-one) [Primitives (Questions) Next](https://docs.typesafe.ai/primitives)

[github](https://github.com/typesafe-ai) [discord](https://discord.gg/typesafe) [x](https://x.com/typesafeai)

[Powered byThis documentation is built and hosted on Mintlify, a developer documentation platform](https://www.mintlify.com/?utm_campaign=poweredBy&utm_medium=referral&utm_source=ts-docs)

## On this page

- [State can be as simple as a string](https://docs.typesafe.ai/concepts/state#state-can-be-as-simple-as-a-string)
- [Separate content from questions](https://docs.typesafe.ai/concepts/state#separate-content-from-questions)

[github](https://github.com/typesafe-ai)[discord](https://discord.gg/typesafe)[x](https://x.com/typesafeai)

[Powered byThis documentation is built and hosted on Mintlify, a developer documentation platform](https://www.mintlify.com/?utm_campaign=poweredBy&utm_medium=referral&utm_source=ts-docs)