---
title: "Noul - TypeSafe AI"
date: "2026-09-16T21:01:13.493Z"
description: "A Noul question asks the model to evaluate a yes/no question and return the probability that the answer is yes."
url: "https://docs.typesafe.ai/primitives/noul"
publisher: "TypeSafe AI"
lang: "en"
logo_url: "https://docs.typesafe.ai/mintlify-assets/_mintlify/favicons/ts-docs/zg2v0DiYB7xPw0I2/_generated/favicon/android-chrome-192x192.png"
logo_type: "png"
logo_size: 8885
logo_height: 192
logo_width: 192
logo_size_pretty: "8.88 kB"
image_url: "https://ts-docs.mintlify.app/mintlify-assets/_next/image?url=%2F_mintlify%2Fapi%2Fog%3Fdivision%3DPrimitives%2B%2528Questions%2529%26title%3DNoul%26description%3DA%2BNoul%2Bquestion%2Basks%2Bthe%2Bmodel%2Bto%2Bevaluate%2Ba%2Byes%252Fno%2Bquestion%2Band%2Breturn%2Bthe%2Bprobability%2Bthat%2Bthe%2Banswer%2Bis%2Byes.%26theme%3Df0580ae664a0195833f0555d&w=1200&q=100"
image_type: "png"
image_size: 37086
image_height: 630
image_width: 1200
image_size_pretty: "37.1 kB"
word_count: 555
reading_time: "3 min read"
---

[← Back to Index](../README.md)

## Last Pages

- [Primitives (Questions) - TypeSafe AI](./005-primitives-questions-typesafe-ai.md)
- [Choice - TypeSafe AI](./006-choice-typesafe-ai.md)
- [Score - TypeSafe AI](./007-score-typesafe-ai.md)

## Table of Contents

- [Writing a Noul question](#writing-a-noul-question)
- [Request](#request)
- [Response](#response)
- [Noul does not return a separate confidence value](#noul-does-not-return-a-separate-confidence-value)
- [Example questions](#example-questions)
- [Tips and advanced usage](#tips-and-advanced-usage)
- [On this page](#on-this-page)

---

Primitives (Questions)

A Noul question asks the model to evaluate a yes/no question and return the probability that the answer is yes.

Use a Noul when the answer is yes or no. For example, does this message ask for a refund, does this resume mention distributed systems, does this comment contain personal data. If the answer is one of several options, use a [Choice](https://docs.typesafe.ai/primitives/choice). If it’s a position on a spectrum, use a [Score](https://docs.typesafe.ai/primitives/score). [Choose a question type](https://docs.typesafe.ai/primitives#choose-a-question-type) compares all three.

A Noul answer is a single number, `noul`, the probability that the answer is yes.

## Writing a Noul question

A Noul question evaluates a single yes/no question (or statement). It is defined by its `instructions`: the yes/no question to evaluate. It’s good practice to phrase it so a high probability means “yes”, so that the returned answer is unambiguous in its meaning.

You can optionally add `criteria` with `true` and `false` descriptions to clarify what each outcome means, which can be helpful when the question itself has more nuance to explain. Try your Noul question prompts with and without criteria to see which works better in your use-case.

## Request

| Field          | Required | Description                                                                  |
| -------------- | -------- | ---------------------------------------------------------------------------- |
| `type`         | Yes      | Must be `"noul"`.                                                            |
| `instructions` | Yes      | The yes/no question or statement to evaluate.                                |
| `criteria`     | No       | Optional `{ true, false }` descriptions clarifying what a yes and a no mean. |

request

```json
{
  "state": "I have asked three times now. Can I please just talk to a real person?",
  "questions": {
    "is_human_escalation": {
      "type": "noul",
      "instructions": "Is the customer asking for a human agent?"
    },
    "is_repeat_contact": {
      "type": "noul",
      "instructions": "Has the customer contacted support about this before?",
      "criteria": {
        "true": "Mentions a prior attempt, ticket, or that they have asked before",
        "false": "No sign of any previous contact"
      }
    }
  }
}
```

[Try it in the Playground →](https://console.typesafe.ai/decode#share/N4IghgDglgagpgJwM5QPYDsQC4QDcCMIANCACaoDGArgLZzoAuAKnAB4PYgCSABABZhccHmCQBrOKR4M+COMIZQ6SHulQB3AHQ8AwmHQ9eEADZxRwgFZUkDaWGNjpqETzn2eEREgwB+YiAgEVBoIBiQWdk5gAB0DHmiQKCQAfT5afWS4JAp7MEUMBKweGLieeJAGAE9PQvK1KmMEoliysoSodBsEKgp8ztqErhUZYWobYMQRcQ6Acx4AM1QEFzSafREZ+gYfBJaeAF9muPaUuU885IoMBjBe2pLW8qqa7DrUBqa9tsTOhm7etD9V4JAASomkfFG1gYE2WV0YtwYkh4SCoEAgS1sYAARu9bDIkjxsXBFnIdsQvuUKAgoEiaWB7pTvn8qHABiAALJbQEqMAeGlLEQMJEhBhEaRQCgSMU8QUyPIQuCVfiCYSiCRSYmktkU0qtBLzexIHVFBIAOWcKBmBlQ8xE6GVgTguDQ1h48JudxAlP2e196H2-mNpl6kg5qFIcGMSGwAG0QBZnQBaYx5LIcAC6+yAA)

## Response

```json
{
  "model": "jev-latest",
  "answers": {
    "is_human_escalation": {
      "type": "noul",
      "noul": 0.99
    },
    "is_repeat_contact": {
      "type": "noul",
      "noul": 0.93
    }
  },
  "usage": {
    "input_tokens": 360,
    "output_tokens": 39
  }
}
```

`noul` ranges from 0 to 1, representing the probability that the answer is **yes**. Most often you will threshold it into a boolean when your code needs a hard decision.

## Noul does not return a separate confidence value

A value near 1 means a strong yes. A value near 0 means a strong no. A value near 0.5 gives yes and no similar probability.

For “Is the candidate strong in Python?”, define what “strong” means. An unclear definition makes the probability hard to interpret. A value of 0.5 does not mean medium skill. Use a [Score](https://docs.typesafe.ai/primitives/score) to measure skill along defined levels. [Choose a question type](https://docs.typesafe.ai/primitives#choose-a-question-type) explains the distinction.

## Example questions

```text
"Is the customer requesting a refund?"
"Does this resume mention experience with distributed systems?"
"Does the message contain personally identifiable information?"
"Does the room have a minifridge?"
```

## Tips and advanced usage

- **Phrasing.** Beyond a plain question, you can phrase the instruction as a statement for the model to evaluate for truthfulness. For “the customer is requesting a refund”, a value near 1 means the statement is true. Try both phrasings with your own data to see what works best.
- **Optional `criteria`.** The instruction is enough for most Noul questions, but when the boundary between yes and no is subtle, pass `criteria` with `true` and `false` descriptions to pin down what each outcome means — as shown in the request example above.

Was this page helpful?

[Score](https://docs.typesafe.ai/primitives/score)

[Previous](https://docs.typesafe.ai/primitives/score) [Advanced: structure Next](https://docs.typesafe.ai/primitives/advanced)





## Next Page

- [Advanced: structure - TypeSafe AI](./009-advanced-structure-typesafe-ai.md)
- [AI primer - TypeSafe AI](./010-ai-primer-typesafe-ai.md)
- [Confidence - TypeSafe AI](./011-confidence-typesafe-ai.md)




