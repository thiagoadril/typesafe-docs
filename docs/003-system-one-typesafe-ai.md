---
title: "System One - TypeSafe AI"
date: "2026-09-17T11:55:10.949Z"
description: "System One models make fast, structured decisions for software. Jev is TypeSafe’s flagship model and the first System One model."
url: "https://docs.typesafe.ai/concepts/system-one"
publisher: "TypeSafe AI"
lang: "en"
logo_url: "https://docs.typesafe.ai/mintlify-assets/_mintlify/favicons/ts-docs/zg2v0DiYB7xPw0I2/_generated/favicon/android-chrome-192x192.png"
logo_type: "png"
logo_size: 8885
logo_height: 192
logo_width: 192
logo_size_pretty: "8.88 kB"
image_url: "https://ts-docs.mintlify.app/mintlify-assets/_next/image?url=%2F_mintlify%2Fapi%2Fog%3Fdivision%3DTypeSafe%2Bconcepts%26title%3DSystem%2BOne%26description%3DSystem%2BOne%2Bmodels%2Bmake%2Bfast%252C%2Bstructured%2Bdecisions%2Bfor%2Bsoftware.%2BJev%2Bis%2BTypeSafe%2527s%2Bflagship%2Bmodel%2Band%2Bthe%2Bfirst%2BSystem%2BOne%2Bmodel.%26theme%3Df0580ae664a0195833f0555d&w=1200&q=100"
image_type: "png"
image_size: 39905
image_height: 630
image_width: 1200
image_size_pretty: "39.9 kB"
word_count: 510
reading_time: "2 min read"
---

[← Back to Index](../README.md)

## Last Pages

- [Introduction - TypeSafe AI](./001-introduction-typesafe-ai.md)
- [Quick start - TypeSafe AI](./002-quick-start-typesafe-ai.md)

## Table of Contents

- [How it differs from an LLM](#how-it-differs-from-an-llm)
- [Fast judgments inside a larger workflow](#fast-judgments-inside-a-larger-workflow)
- [Call a System One model](#call-a-system-one-model)
- [On this page](#on-this-page)

---

TypeSafe concepts

System One models make fast, structured decisions for software. Jev is TypeSafe’s flagship model and the first System One model.

System One models are a class of AI models built to make fast, structured decisions that software can use directly. A System One model evaluates a [state](https://docs.typesafe.ai/concepts/state) and returns typed answers and probabilities.

Jev is TypeSafe’s flagship model and the first System One model.

Like an LLM, a System One model understands natural-language input. It returns typed decisions and probabilities rather than generated text.

Jev currently accepts text input only. It evaluates strings, JSON objects, and arrays of text. Images, audio, and video are not supported (yet).

## How it differs from an LLM

System One models are trained for calibrated decisions: their probabilities are optimized against outcomes to reflect uncertainty. Calibration is measured across groups of predictions; it does not guarantee that an individual answer is correct.

System One models do not write replies, produce code, or generate explanations of their reasoning. You define the possible answers through [primitives](https://docs.typesafe.ai/primitives):

| Primitive                                            | Question                              | Example answer space                          | Example output      |
| ---------------------------------------------------- | ------------------------------------- | --------------------------------------------- | ------------------- |
| [Choice](https://docs.typesafe.ai/primitives/choice) | Which team should handle this ticket? | `billing`, `technical`, or `account`          | `choice: "billing"` |
| [Score](https://docs.typesafe.ai/primitives/score)   | How frustrated is this customer?      | 0 = calm, 1 = frustrated, 2 = very frustrated | `score: 1.4`        |
| [Noul](https://docs.typesafe.ai/primitives/noul)     | Does this message request a refund?   | True or false                                 | `noul: 0.95`        |

These are illustrative configurations and values. The primitive pages describe the available configuration options and full response fields.

Read the [AI primer](https://docs.typesafe.ai/introduction/machine-learning-primer) to learn how System One models work and how they are trained.

The System One name comes from the concept Daniel Kahneman popularized in his book *Thinking, Fast and Slow*. System 1 thinking is fast and intuitive. System 2 is slower and more deliberate. Here, the emphasis is on fast, focused judgments.

## Fast judgments inside a larger workflow

For a refund request, your application can:

1.  Build a state containing the customer’s message, the relevant transactions, and the refund policy.
2.  Ask independent questions together: whether a refund was requested, whether the evidence indicates a duplicate charge, and whether the policy supports a refund.
3.  Combine the answers with deterministic checks in code, then route the case for action or review.

Once you have seen the primitives in action, you can combine them into a larger system. Because System One models return typed, constrained outputs rather than free-form text, your code can inspect and combine its answers into predictable workflows. See [How to build with TypeSafe](https://docs.typesafe.ai/concepts/how-to-build-with-system-one) for the full workflow.

Answers from System One models also include [confidence](https://docs.typesafe.ai/confidence), so you can decide when to act and when to escalate to a person or a reasoning model.

## Call a System One model

Call a System One model through one of our [client SDKs](https://docs.typesafe.ai/sdk) or `POST /v1/systemone` in the [HTTP API](https://docs.typesafe.ai/api). The `model` field selects which model handles the request. The examples in these docs use `jev-latest`, which is also the SDK default. See [Models](https://docs.typesafe.ai/models) for the available models, their prices, and their aliases.

Start with [State](https://docs.typesafe.ai/concepts/state) to prepare the input and [Primitives (Questions)](https://docs.typesafe.ai/primitives) to explore the types of questions you can ask.

Was this page helpful?

[Quick start](https://docs.typesafe.ai/introduction/quickstart)

[Previous](https://docs.typesafe.ai/introduction/quickstart) [State Next](https://docs.typesafe.ai/concepts/state)





## Next Page

- [State - TypeSafe AI](./004-state-typesafe-ai.md)
- [Primitives (Questions) - TypeSafe AI](./005-primitives-questions-typesafe-ai.md)
- [Choice - TypeSafe AI](./006-choice-typesafe-ai.md)




