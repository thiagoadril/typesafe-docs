---
title: "AI primer - TypeSafe AI"
date: "2026-09-05T03:03:56.868Z"
description: "Why TypeSafe trains decision models with calibrated probabilities instead of optimizing for generated text."
url: "https://docs.typesafe.ai/introduction/machine-learning-primer"
publisher: "TypeSafe AI"
lang: "en"
logo_url: "https://docs.typesafe.ai/mintlify-assets/_mintlify/favicons/ts-docs/zg2v0DiYB7xPw0I2/_generated/favicon/android-chrome-192x192.png"
logo_type: "png"
logo_size: 8885
logo_height: 192
logo_width: 192
logo_size_pretty: "8.88 kB"
image_url: "https://ts-docs.mintlify.app/mintlify-assets/_next/image?url=%2F_mintlify%2Fapi%2Fog%3Fdivision%3DTypeSafe%2Bfoundations%26title%3DAI%2Bprimer%26description%3DWhy%2BTypeSafe%2Btrains%2Bdecision%2Bmodels%2Bwith%2Bcalibrated%2Bprobabilities%2Binstead%2Bof%2Boptimizing%2Bfor%2Bgenerated%2Btext.%26theme%3Df0580ae664a0195833f0555d&w=1200&q=100"
image_type: "png"
image_size: 37739
image_height: 630
image_width: 1200
image_size_pretty: "37.7 kB"
word_count: 892
reading_time: "4 min read"
---

[← Back to Index](../README.md)

## Last Pages

- [Score - TypeSafe AI](./007-score-typesafe-ai.md)
- [Noul - TypeSafe AI](./008-noul-typesafe-ai.md)
- [Advanced: structure - TypeSafe AI](./009-advanced-structure-typesafe-ai.md)

## Table of Contents

- [Building prod, not God](#building-prod-not-god)
- [Three post-training approaches](#three-post-training-approaches)
- [RLHF](#rlhf)
- [RLVR](#rlvr)
- [RLCD](#rlcd)
- [RLCD and calibrated decisions](#rlcd-and-calibrated-decisions)
- [The problems with RLHF](#the-problems-with-rlhf)
- [On this page](#on-this-page)

---

TypeSafe foundations

Why TypeSafe trains decision models with calibrated probabilities instead of optimizing for generated text.

Most AI products are built around a conversation between a model and a person. TypeSafe starts from a different bet: large-scale automation will be dominated by AI-to-AI and AI-to-software interactions, so the machine interface matters more than the chat interface.

> **We call this Machine Native Intelligence:**
>
> AI with software-like properties such as structure, reliability, observability, testability, speed, consistency, and low cost.

## Building prod, not God

TypeSafe is not trying to build a model that does everything. It is designed for production systems where code needs a narrow decision it can inspect and act on.

Our expectation is that large-scale AI automation will be closer to 99% machine-to-machine interactions and 1% human interaction. That shifts the design target from responses that feel good to read toward outputs that behave predictably inside software.

Read the [TypeSafe manifesto](https://typesafe.ai/manifesto).

## Three post-training approaches

Pretrained language models have been adapted in two major ways. TypeSafe adds a third. RLHF and RLVR are shown here for context; TypeSafe’s training path is RLCD.

## RLHF

**Reinforcement learning from human feedback** turned pretrained models into chatbots. It trains models to produce responses people prefer.

## RLVR

**Reinforcement learning with verifiable rewards** created reasoning models that are strong at tasks such as mathematics, but slower and more expensive.

## RLCD

**Reinforcement learning for calibrated decisions** trains TypeSafe to return decisions and calibrated probabilities instead of generated text.

RLHF was used to train InstructGPT and ChatGPT and was [co-invented by Diogo Almeida](https://scholar.google.com/citations?user=0T4y07QAAAAJ&hl=en), cofounder of TypeSafe.

![Pretrained language models branch into muted RLHF and RLVR paths and an emphasized RLCD decision-model path.](https://mintcdn.com/ts-docs/aFVnpmCIX68NpsV1/images/ai-primer/training-paths-light.webp?fit=max&amp;auto=format&amp;n=aFVnpmCIX68NpsV1&amp;q=85&amp;s=61898215ac31388d3be15bf583b743ee)

Pretrained language models branch into muted RLHF and RLVR paths and an emphasized RLCD decision-model path.

![Pretrained language models branch into muted RLHF and RLVR paths and an emphasized RLCD decision-model path.](https://mintcdn.com/ts-docs/aFVnpmCIX68NpsV1/images/ai-primer/training-paths-dark.webp?fit=max&amp;auto=format&amp;n=aFVnpmCIX68NpsV1&amp;q=85&amp;s=2747633edb0e54fa3f14a8aba830f4fd)

Pretrained language models branch into muted RLHF and RLVR paths and an emphasized RLCD decision-model path.

## RLCD and calibrated decisions

RLCD optimizes for a different output contract:

- The model does not generate text.
- It returns decisions and probabilities.
- Higher probability should correspond to a greater chance that the answer is correct.

Calibration makes uncertainty usable by software. Across many predictions from a well-calibrated model:

- Outcomes assigned a probability of `0.2` should occur about 20% of the time.
- Outcomes assigned a probability of `0.8` should occur about 80% of the time.
- Outcomes assigned a probability of `1.0` should occur 100% of the time.

These rates describe groups of predictions, not a guarantee about any single answer. See [Confidence](https://docs.typesafe.ai/confidence) for guidance on deciding when software should act or escalate.

## The problems with RLHF

RLHF teaches a model to say things that people prefer. That objective works well for chatbots, but it can also reward sycophancy and confident-sounding hallucinations.

Preference optimization also causes **mode dropping**: the model learns to favor a particular style, such as instruction following, while reducing the probability of other possible outputs.

![The probability distribution of a base model compared with a narrowed, mode-dropped distribution after RLHF.](https://mintcdn.com/ts-docs/aFVnpmCIX68NpsV1/images/ai-primer/mode-dropping-light.webp?fit=max&amp;auto=format&amp;n=aFVnpmCIX68NpsV1&amp;q=85&amp;s=d51758a6212b526fc243cc9a81572cc7)

The probability distribution of a base model compared with a narrowed, mode-dropped distribution after RLHF.

![The probability distribution of a base model compared with a narrowed, mode-dropped distribution after RLHF.](https://mintcdn.com/ts-docs/aFVnpmCIX68NpsV1/images/ai-primer/mode-dropping-dark.webp?fit=max&amp;auto=format&amp;n=aFVnpmCIX68NpsV1&amp;q=85&amp;s=4330e6251ca335515a61f61794f21389)

The probability distribution of a base model compared with a narrowed, mode-dropped distribution after RLHF.

An output can be compelling to a person without being reliable enough for unattended automation. Human preference and machine trustworthiness are different optimization targets.

Mode dropping is a milder version of **mode collapse**. In the classic generative-adversarial-network failure mode, a generator learns to produce the same kind of output repeatedly because that output continues to fool the discriminator.

Mode collapse analogy

![Repeated characters illustrate a GAN suffering from mode collapse.](https://mintcdn.com/ts-docs/aFVnpmCIX68NpsV1/images/ai-primer/mode-collapse-light.webp?fit=max&amp;auto=format&amp;n=aFVnpmCIX68NpsV1&amp;q=85&amp;s=2896f125ad1a5835b31b088fbc64eff1)

Repeated characters illustrate a GAN suffering from mode collapse.

![Repeated characters illustrate a GAN suffering from mode collapse.](https://mintcdn.com/ts-docs/aFVnpmCIX68NpsV1/images/ai-primer/mode-collapse-dark.webp?fit=max&amp;auto=format&amp;n=aFVnpmCIX68NpsV1&amp;q=85&amp;s=95645bdefd0bb3fa093edc3dd9308337)

Repeated characters illustrate a GAN suffering from mode collapse.

RLHF remains a good fit for conversational models. TypeSafe’s position is that production automation needs a different training objective—one centered on constrained decisions and calibrated uncertainty.

Was this page helpful?

[Advanced: structure](https://docs.typesafe.ai/primitives/advanced)

[Previous](https://docs.typesafe.ai/primitives/advanced) [Confidence Next](https://docs.typesafe.ai/confidence)





## Next Page

- [Confidence - TypeSafe AI](./011-confidence-typesafe-ai.md)
- [How to build with TypeSafe - TypeSafe AI](./012-how-to-build-with-typesafe-typesafe-ai.md)
- [Example use cases - TypeSafe AI](./013-example-use-cases-typesafe-ai.md)




