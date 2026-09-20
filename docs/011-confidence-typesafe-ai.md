---
title: "Confidence - TypeSafe AI"
date: "2026-09-12T04:42:52.639Z"
description: "How TypeSafe reports certainty, how it differs from probability, and how to use it to control system behavior."
url: "https://docs.typesafe.ai/confidence"
publisher: "TypeSafe AI"
lang: "en"
logo_url: "https://docs.typesafe.ai/mintlify-assets/_mintlify/favicons/ts-docs/zg2v0DiYB7xPw0I2/_generated/favicon/android-chrome-192x192.png"
logo_type: "png"
logo_size: 8885
logo_height: 192
logo_width: 192
logo_size_pretty: "8.88 kB"
image_url: "https://ts-docs.mintlify.app/mintlify-assets/_next/image?url=%2F_mintlify%2Fapi%2Fog%3Fdivision%3DTypeSafe%2Bfoundations%26title%3DConfidence%26description%3DHow%2BTypeSafe%2Breports%2Bcertainty%252C%2Bhow%2Bit%2Bdiffers%2Bfrom%2Bprobability%252C%2Band%2Bhow%2Bto%2Buse%2Bit%2Bto%2Bcontrol%2Bsystem%2Bbehavior.%26theme%3Df0580ae664a0195833f0555d&w=1200&q=100"
image_type: "png"
image_size: 39506
image_height: 630
image_width: 1200
image_size_pretty: "39.5 kB"
word_count: 895
reading_time: "4 min read"
---

[← Back to Index](../README.md)

## Last Pages

- [Noul - TypeSafe AI](./008-noul-typesafe-ai.md)
- [Advanced: structure - TypeSafe AI](./009-advanced-structure-typesafe-ai.md)
- [AI primer - TypeSafe AI](./010-ai-primer-typesafe-ai.md)

## Table of Contents

- [Confidence is derived from the probabilities](#confidence-is-derived-from-the-probabilities)
- [”I don’t know” is a useful signal](#i-dont-know-is-a-useful-signal)
- [Three paths for using confidence in your code](#three-paths-for-using-confidence-in-your-code)
- [Thresholds scale with risk](#thresholds-scale-with-risk)
- [On this page](#on-this-page)

---

TypeSafe foundations

How TypeSafe reports certainty, how it differs from probability, and how to use it to control system behavior.

All Score and Choice answers from TypeSafe include a `probabilities` property representing the probability distribution across the options (for Choice) or levels (for Score). The *shape* of that distribution is what tells you how certain the model is: concentrated on one outcome means a confident answer, spread out means an uncertain one.

The answer’s `confidence` property collapses that shape into a single number from 0 to 1, so you can threshold on it without doing the math yourself. (Noul answers don’t carry one.)

## Confidence is derived from the probabilities

`confidence` is a statistic computed from the probability distribution the answer already gives you. TypeSafe computes it for you and returns it on every Choice and Score answer, so the common case needs no extra work on your side.

**A solid default:** We provide `confidence` as a convenient measure that fits most use-cases, but you are never locked into our definition. Depending on what you are evaluating, a different measure may serve you better, which is exactly why we give you the full `probabilities` in the response. The pros and cons of different computations is a specialized topic that we’ll keep to a separate cookbook rather than this page, and will add the link here when we do!

For a [Choice](https://docs.typesafe.ai/primitives/choice), the distribution is `probabilities` across your options. For a [Score](https://docs.typesafe.ai/primitives/score), it is the distribution across your levels. In both cases a flatter distribution means lower confidence: low confidence on a Choice often means none of the options are a clear winner over the others, and low confidence on a Score often means the levels are ambiguous, multi-dimensional, or the state doesn’t contain enough to go on.

## ”I don’t know” is a useful signal

If an intelligent system, whether human or machine, cannot express honest uncertainty, the system cannot be trusted.

Confidence gives you a built-in mechanism for the model to say “I’m not sure about this one.” This lets your code implement different behavior for different levels of certainty, which is the foundation for building systems you can actually rely on.

## Three paths for using confidence in your code

A useful starting pattern is to divide confidence into three ranges, each producing a different system behavior:

**High confidence:** Act automatically. The model has a clear read and you can proceed without human involvement.

**Medium confidence:** Proceed with caution. The model has a reasonable answer but is not certain. Depending on context, you might ask the user to confirm, flag for review, or gather more information before acting.

**Low confidence:** Do not act. Route to a human, request clarification, or fall back to a different system. The model is telling you it does not have enough information or the question is not a good fit.

Where you draw those boundaries depends on the stakes.

## Thresholds scale with risk

A confidence threshold is not one number. Different actions within the same system should be gated at different levels depending on the consequences of getting it wrong.

```python
response = client.system_one(
    state=user_message,
    questions={
        "action": Choice(
            instructions="What is the user trying to do?",
            criteria={
                "check_balance": "View account balance",
                "approve_transfer": "Approve the pending withdrawal request",
                "support": "Get help with an issue",
            },
        ),
    },
)
action = response.answers["action"]
confidence = action.confidence
if confidence < 0.5:
    # Model is genuinely unsure. Don't guess.
    route_to_human(user_message)
elif action.choice == "check_balance":
    # Low stakes. Showing the wrong screen is recoverable.
    show_balance(account_id)
elif action.choice == "approve_transfer":
    if confidence > 0.9:
        # High stakes, high confidence. Proceed with confirmation.
        confirm_then_execute(account_id)
    else:
        # High stakes, moderate confidence. Verify first.
        ask_user_to_confirm(account_id)
```

The 0.5 confidence floor catches anything the model reports as genuinely uncertain. Above that, the threshold for acting without confirmation is higher for a destructive operation than for a read-only one. Your code encodes the risk tolerance.

The correct threshold values depend on your domain and the performance of the model for your use case. Start with conservative thresholds, test with your own data, and adjust as you observe results.

Was this page helpful?

[AI primer](https://docs.typesafe.ai/introduction/machine-learning-primer)

[Previous](https://docs.typesafe.ai/introduction/machine-learning-primer) [How to build with TypeSafe Next](https://docs.typesafe.ai/concepts/how-to-build-with-system-one)





## Next Page

- [How to build with TypeSafe - TypeSafe AI](./012-how-to-build-with-typesafe-typesafe-ai.md)
- [Example use cases - TypeSafe AI](./013-example-use-cases-typesafe-ai.md)
- [Patterns - TypeSafe AI](./014-patterns-typesafe-ai.md)




