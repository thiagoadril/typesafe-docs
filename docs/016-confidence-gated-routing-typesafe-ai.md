---
title: "Confidence-gated routing - TypeSafe AI"
date: "2026-09-12T04:42:47.138Z"
description: "Use confidence as a second axis. The answer tells you what; confidence tells you whether to act."
url: "https://docs.typesafe.ai/patterns/confidence-routing"
publisher: "TypeSafe AI"
lang: "en"
logo_url: "https://docs.typesafe.ai/mintlify-assets/_mintlify/favicons/ts-docs/zg2v0DiYB7xPw0I2/_generated/favicon/android-chrome-192x192.png"
logo_type: "png"
logo_size: 8885
logo_height: 192
logo_width: 192
logo_size_pretty: "8.88 kB"
image_url: "https://ts-docs.mintlify.app/mintlify-assets/_next/image?url=%2F_mintlify%2Fapi%2Fog%3Fdivision%3DPatterns%26title%3DConfidence-gated%2Brouting%26description%3DUse%2Bconfidence%2Bas%2Ba%2Bsecond%2Baxis.%2BThe%2Banswer%2Btells%2Byou%2Bwhat%253B%2Bconfidence%2Btells%2Byou%2Bwhether%2Bto%2Bact.%26theme%3Df0580ae664a0195833f0555d&w=1200&q=100"
image_type: "png"
image_size: 40942
image_height: 630
image_width: 1200
image_size_pretty: "40.9 kB"
word_count: 480
reading_time: "2 min read"
---

[← Back to Index](../README.md)

## Last Pages

- [Example use cases - TypeSafe AI](./013-example-use-cases-typesafe-ai.md)
- [Patterns - TypeSafe AI](./014-patterns-typesafe-ai.md)
- [Speculative fan-out - TypeSafe AI](./015-speculative-fan-out-typesafe-ai.md)

## Table of Contents

- [Example: voice banking commands](#example-voice-banking-commands)
  - [Step 1: determine the user’s intent](#step-1-determine-the-users-intent)
  - [Step 2: confidence-gated routing](#step-2-confidence-gated-routing)
- [On this page](#on-this-page)

---

Patterns

Use confidence as a second axis. The answer tells you what; confidence tells you whether to act.

One of TypeSafe’s most powerful features is [confidence](https://docs.typesafe.ai/confidence). By being intentional with the way you gate decisions on confidence, you can build systems that are both reliable and safe.

## Example: voice banking commands

Let’s imagine you are building a voice banking interface to allow the user to interact with their account verbally. While you always want to have reasonable confidence in interpreting the user’s intent, some actions are riskier than others and thus demand a higher confidence threshold.

### Step 1: determine the user’s intent

questions

```json
{
  "intent": {
    "type": "choice",
    "instructions": "What action is the user requesting?",
    "criteria": {
      "check_balance": "Check the balance of an account",
      "approve_transfer": "Approve the pending transfer request",
      "other": "Something else"
    }
  }
}
```

[Try it in the Playground →](https://console.typesafe.ai/decode#share/N4IghgDglgagpgJwM5QPYDsQC4QDcCMIANCACaoDGArgLZzoAuAKnAB4PYjEgQKo0QGSFu07AAOugAEU8SCiN6DOVikTpM2SAYBPCHBVaKAC1RQKB4pM1aFSBgioUGadEkNyA6sbAMpYZ1cpKCQpBmM4KSokRCkEOABHKjh7BQBzAH45ImtNOQoEKAZEKDBDdRsZfIiKAGsAfQAjMAAbMHQLDxAAYRrasIipZraOyNQAM39pAIpUKkZs3Js5SF5UXDh6h3akccQugEEINY2ByP10UnSwhB29hDjE5PtFjWWQVHD97C0AZX44OFrnAWjE5EspABfXLQ9CQkCQoA)

### Step 2: confidence-gated routing

```python
action = response.answers["intent"]
# Below 0.6 confidence on any action, route to a human
if action.confidence < 0.6:
    route_to_support_agent(account_id)
elif action.choice == "check_balance":
    # Low stakes. 0.6 confidence is sufficient.
    show_balance(account_id)
elif action.choice == "approve_transfer":
    if action.confidence > 0.85:
        # High stakes, but high confidence. Safe to act automatically.
        approve_transfer(account_id)
    else:
        # High stakes, moderate confidence. Verify intent first.
        ask_user_to_confirm("Just to confirm: you would like to approve this transfer, is that correct?")
else:
    route_to_support_agent(account_id)
```

The 0.6 floor catches anything the model is genuinely uncertain about. Above that floor, each action type has its own threshold based on the consequences of acting on a wrong classification. Checking a balance at 0.6 is fine because the worst case is the user having to listen to the balance read-out. But approving a transfer requires very high confidence (\>0.85), otherwise the system should ask the user to confirm.

See [Confidence](https://docs.typesafe.ai/confidence) for more details on how to think about confidence in your systems.

Was this page helpful?

[Speculative fan-out](https://docs.typesafe.ai/patterns/fan-out)

[Previous](https://docs.typesafe.ai/patterns/fan-out) [Composite scoring Next](https://docs.typesafe.ai/patterns/composite-scoring)





## Next Page

- [Composite scoring - TypeSafe AI](./017-composite-scoring-typesafe-ai.md)
- [Intent routing - TypeSafe AI](./018-intent-routing-typesafe-ai.md)
- [Demos - TypeSafe AI](./019-demos-typesafe-ai.md)




