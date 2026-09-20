---
title: "Patterns - TypeSafe AI"
date: "2026-08-31T20:22:39.515Z"
description: "Architectural patterns for building systems with TypeSafe."
url: "https://docs.typesafe.ai/patterns"
publisher: "TypeSafe AI"
lang: "en"
logo_url: "https://docs.typesafe.ai/mintlify-assets/_mintlify/favicons/ts-docs/zg2v0DiYB7xPw0I2/_generated/favicon/android-chrome-192x192.png"
logo_type: "png"
logo_size: 8885
logo_height: 192
logo_width: 192
logo_size_pretty: "8.88 kB"
image_url: "https://ts-docs.mintlify.app/mintlify-assets/_next/image?url=%2F_mintlify%2Fapi%2Fog%3Fdivision%3DPatterns%26title%3DPatterns%26description%3DArchitectural%2Bpatterns%2Bfor%2Bbuilding%2Bsystems%2Bwith%2BTypeSafe.%26theme%3Df0580ae664a0195833f0555d&w=1200&q=100"
image_type: "png"
image_size: 31598
image_height: 630
image_width: 1200
image_size_pretty: "31.6 kB"
word_count: 198
reading_time: "1 min read"
---

[← Voltar ao índice](./README.md)


## Table of Contents

- [The patterns](#the-patterns)
- [On this page](#on-this-page)

---

Patterns

Architectural patterns for building systems with TypeSafe.

TypeSafe is designed to sit within a larger system, powering decisions with AI. Learning to think in terms of discrete, atomic decisions that compose into complex system behavior is a key skill for getting the most out of TypeSafe.

This section assumes you know the [TypeSafe primitives](https://docs.typesafe.ai/primitives) and understand [how confidence works](https://docs.typesafe.ai/confidence). If not, read those first.

## The patterns

| Pattern                                                                          | What it does                                                                                               | Benefits                 |
| -------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------- | ------------------------ |
| [Speculative Fan-Out](https://docs.typesafe.ai/patterns/fan-out)                 | Send many questions in a single call, including speculative ones, and let your code decide what’s relevant | Cost, Speed              |
| [Confidence-Gated Routing](https://docs.typesafe.ai/patterns/confidence-routing) | Utilize confidence as a second decision axis to build safer systems                                        | Reliability, Safety      |
| [Composite Scoring](https://docs.typesafe.ai/patterns/composite-scoring)         | Combine several dimensions of analysis into a single score                                                 | Cost, Reliability, Speed |
| [Intent Routing](https://docs.typesafe.ai/patterns/intent-routing)               | Classify a user’s intent and route to the appropriate handler                                              | Cost, Speed              |

We’re always keen to learn how people are making use of our primitives. If you’ve found a killer use case you think should be mentioned here, feel free to drop us a note!

Was this page helpful?

[Example use cases](https://docs.typesafe.ai/concepts/use-case-map)

[Previous](https://docs.typesafe.ai/concepts/use-case-map) [Speculative fan-out Next](https://docs.typesafe.ai/patterns/fan-out)

[github](https://github.com/typesafe-ai) [discord](https://discord.gg/typesafe) [x](https://x.com/typesafeai)

[Powered byThis documentation is built and hosted on Mintlify, a developer documentation platform](https://www.mintlify.com/?utm_campaign=poweredBy&utm_medium=referral&utm_source=ts-docs)

## On this page

- [The patterns](https://docs.typesafe.ai/patterns#the-patterns)

[github](https://github.com/typesafe-ai)[discord](https://discord.gg/typesafe)[x](https://x.com/typesafeai)

[Powered byThis documentation is built and hosted on Mintlify, a developer documentation platform](https://www.mintlify.com/?utm_campaign=poweredBy&utm_medium=referral&utm_source=ts-docs)