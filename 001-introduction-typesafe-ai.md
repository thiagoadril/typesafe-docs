---
title: "Introduction - TypeSafe AI"
date: "2026-09-14T08:52:32.400Z"
description: "Jev is TypeSafe’s flagship model and the first System One model. Send state and typed questions; get structured answers your code can use directly."
url: "https://docs.typesafe.ai/introduction"
publisher: "TypeSafe AI"
lang: "en"
logo_url: "https://docs.typesafe.ai/mintlify-assets/_mintlify/favicons/ts-docs/zg2v0DiYB7xPw0I2/_generated/favicon/android-chrome-192x192.png"
logo_type: "png"
logo_size: 8885
logo_height: 192
logo_width: 192
logo_size_pretty: "8.88 kB"
image_url: "https://ts-docs.mintlify.app/mintlify-assets/_next/image?url=%2F_mintlify%2Fapi%2Fog%3Fdivision%3DIntroduction%26title%3DIntroduction%26description%3DJev%2Bis%2BTypeSafe%2527s%2Bflagship%2Bmodel%2Band%2Bthe%2Bfirst%2BSystem%2BOne%2Bmodel.%2BSend%2Bstate%2Band%2Btyped%2Bquestions%253B%2Bget%2Bstructured%2Banswers%2Byour%2Bcode%2Bcan%2Buse%2Bdirectly.%26theme%3Df0580ae664a0195833f0555d&w=1200&q=100"
image_type: "png"
image_size: 37467
image_height: 630
image_width: 1200
image_size_pretty: "37.5 kB"
word_count: 399
reading_time: "2 min read"
---

[← Voltar ao índice](./README.md)


## Table of Contents

- [TypeSafe primitives](#typesafe-primitives)
- [Atomic questions, composed in code](#atomic-questions-composed-in-code)
- [Next steps](#next-steps)
- [On this page](#on-this-page)

---

Introduction

Jev is TypeSafe’s flagship model and the first System One model. Send state and typed questions; get structured answers your code can use directly.

Large language models (LLMs) are designed to produce text for humans to read. When you need a model to make a judgment that your code will consume, that creates a mismatch: you are coercing a text-generation system into outputting structured decisions, then parsing the results back into something your code can depend on.

Jev is TypeSafe’s flagship model and the first [System One model](https://docs.typesafe.ai/concepts/system-one). System One models are built to make fast, structured decisions that software can use directly. Jev evaluates typed *questions* against a *state* and returns structured results directly. No text generation, no parsing. You get typed values and probability distributions that your code can branch on, sort by, and route with.

## TypeSafe primitives

TypeSafe exposes three *AI primitives*. Similar to software primitives, our AI primitives are modular, composable, structured, reliable, and fast. Each asks a different type of *question* and returns a different type of answer.

| Question type                                        | Goal                         | Returns                                 |
| ---------------------------------------------------- | ---------------------------- | --------------------------------------- |
| [Choice](https://docs.typesafe.ai/primitives/choice) | Choose an option from a list | `choice`, `probabilities`, `confidence` |
| [Score](https://docs.typesafe.ai/primitives/score)   | Score the state on a rubric  | `score`, `probabilities`, `confidence`  |
| [Noul](https://docs.typesafe.ai/primitives/noul)     | Is this statement true?      | `noul` (0–1)                            |

All three *question* types can be mixed in a single API call. Every *question* is evaluated in parallel and in isolation against the same *state* in one go. Adding questions barely changes the response time. Each question is evaluated independently, so adding more questions does not create context-rot.

## Atomic questions, composed in code

System One models work best when each question asks one specific, well-scoped thing. Think of each question as a gut-check determination: the kind of judgment a highly knowledgeable person could make in a few seconds given the right context.

If the question you want to ask would require extended reasoning or weighs multiple independent factors, decompose it. Ask each factor as a separate question, then combine the results with logic in your code. This keeps each individual evaluation reliable and gives you full control over how dimensions are weighted.

For example, instead of “rate this startup pitch,” ask separately about market size, technical feasibility, and differentiation. Combine the scores with your own formula. When priorities shift, change a coefficient in your code rather than rewriting a prompt.

## Next steps

- [Quick Start](https://docs.typesafe.ai/introduction/quickstart) — Everything you need to get started immediately.
- [AI Primer](https://docs.typesafe.ai/introduction/machine-learning-primer) — Why TypeSafe trains models for calibrated decisions instead of generated text.
- [Primitives (Questions)](https://docs.typesafe.ai/primitives) — How to define questions, choose between Choice, Score, and Noul, and ask several at once.
- [Confidence](https://docs.typesafe.ai/confidence) — How TypeSafe reports certainty, and how to use it architecturally.
- [Patterns](https://docs.typesafe.ai/patterns) — Common patterns for building systems with TypeSafe.

Was this page helpful?

[Quick start](https://docs.typesafe.ai/introduction/quickstart)

[Next](https://docs.typesafe.ai/introduction/quickstart)

[github](https://github.com/typesafe-ai) [discord](https://discord.gg/typesafe) [x](https://x.com/typesafeai)

[Powered byThis documentation is built and hosted on Mintlify, a developer documentation platform](https://www.mintlify.com/?utm_campaign=poweredBy&utm_medium=referral&utm_source=ts-docs)

## On this page

- [TypeSafe primitives](https://docs.typesafe.ai/introduction#typesafe-primitives)
- [Atomic questions, composed in code](https://docs.typesafe.ai/introduction#atomic-questions-composed-in-code)
- [Next steps](https://docs.typesafe.ai/introduction#next-steps)

[github](https://github.com/typesafe-ai)[discord](https://discord.gg/typesafe)[x](https://x.com/typesafeai)

[Powered byThis documentation is built and hosted on Mintlify, a developer documentation platform](https://www.mintlify.com/?utm_campaign=poweredBy&utm_medium=referral&utm_source=ts-docs)