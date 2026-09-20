---
title: "Intent routing - TypeSafe AI"
date: "2026-09-12T04:42:47.128Z"
description: "Classify incoming requests and route each to the optimal handler: deterministic logic, a specialist LLM, or a human."
url: "https://docs.typesafe.ai/patterns/intent-routing"
publisher: "TypeSafe AI"
lang: "en"
logo_url: "https://docs.typesafe.ai/mintlify-assets/_mintlify/favicons/ts-docs/zg2v0DiYB7xPw0I2/_generated/favicon/android-chrome-192x192.png"
logo_type: "png"
logo_size: 8885
logo_height: 192
logo_width: 192
logo_size_pretty: "8.88 kB"
image_url: "https://ts-docs.mintlify.app/mintlify-assets/_next/image?url=%2F_mintlify%2Fapi%2Fog%3Fdivision%3DPatterns%26title%3DIntent%2Brouting%26description%3DClassify%2Bincoming%2Brequests%2Band%2Broute%2Beach%2Bto%2Bthe%2Boptimal%2Bhandler%253A%2Bdeterministic%2Blogic%252C%2Ba%2Bspecialist%2BLLM%252C%2Bor%2Ba%2Bhuman.%26theme%3Df0580ae664a0195833f0555d&w=1200&q=100"
image_type: "png"
image_size: 37023
image_height: 630
image_width: 1200
image_size_pretty: "37 kB"
word_count: 603
reading_time: "3 min read"
---

[← Voltar ao índice](./README.md)


## Table of Contents

- [Example: customer service routing](#example-customer-service-routing)
  - [Step 1: classify intent and complexity](#step-1-classify-intent-and-complexity)
  - [Step 2: route to the optimal handler](#step-2-route-to-the-optimal-handler)
- [On this page](#on-this-page)

---

Patterns

Classify incoming requests and route each to the optimal handler: deterministic logic, a specialist LLM, or a human.

Not every user request needs the same kind of handler. Some can be answered with a database lookup. Some need an LLM with domain-specific context. Some need a human. TypeSafe can sit in front of all of these as a fast, cheap classifier that determines which handler to invoke.

## Example: customer service routing

Let’s imagine you are building a customer service system. Messages come in and need to be routed to the right handler. Rather than sending every message through an expensive LLM to figure out what kind of request it is, you classify first and route accordingly.

### Step 1: classify intent and complexity

questions

```json
{
  "intent": {
    "type": "choice",
    "instructions": "The primary intent of this customer message",
    "criteria": {
      "order_status": "Asking about an existing order",
      "product_question": "Asking about a product before buying",
      "return_exchange": "Wants to return or exchange something",
      "complaint": "Unhappy with experience, wants resolution"
    }
  },
  "complexity": {
    "type": "score",
    "instructions": "How complex is this request to resolve",
    "criteria": [
      "Simple lookup or standard procedure",
      "Requires some judgment or multi-step process",
      "Unusual situation, edge case, or escalation needed"
    ]
  }
}
```

[Try it in the Playground →](https://console.typesafe.ai/decode#share/N4IghgDglgagpgJwM5QPYDsQC4QDcCMIANCACaoDGArgLZzoAuAKnAB4PYjEgQKo0QGSFu07AAOugAEU8SCiN6DOVikTpM2SAYBPCHBVaKAC1RQKB4pM1aFSBgioUGadEkNymxuFN5QaYAg6UgoMSlKoAGZSDMZQSFLU9vyIUnRISGAA5pZE1ppyFAhQYcVghuo2MnKoCKSIAPr2YAxU7thaAIJIANYKWVJgAEaoVAyD0mzxLugDtfUIcnkaNnK8qKRODA0AjlRw9q4eIN19s4MjY4O+fJvOUkNwkbU+Q1Q6-Uv5qyAIcK0IdANNgmMCzSyqOQAdTBQhiqCkfwB0lqUhBxjBOSkSBSsU+VhWBRAFH4EAANmBQscAKroDEQCDBADuJWMaNY+mK9AsRCkTNhCT+OLJYyOIG+UgAvvlJctqsTSWSproKhK5Lp9MckCS-l9CXI7A4tq52pCQAAJVBMxKKtghBJ4wVwPYHcYMBFC1Bk3C5NXE4qlKDlDoAbQl8oAyv5yT4yahUD0qBAIghsQwwaRAqQbpQ4JtdQSqloAErOqhQIXYlJSABWVFIWTojBTaSoZJcAFp7HBk+sLBk9UW5LS2lQwGTsSUxy4MLy81iKGAkHBeaiDouKTPpOg4Hm83IJQBdGWSSUgSVAA)

### Step 2: route to the optimal handler

routing.py

```python
def route_ticket(ticket_id, response):
    intent = response.answers["intent"]
    complexity = response.answers["complexity"]
    if intent.confidence < 0.5:
        # If we don't have enough confidence to classify, route to a human agent
        return route_to_human_agent(ticket_id)
    if intent.choice == "order_status":
        handle_order_status(ticket_id)
    elif intent.choice == "product_question":
        handle_with_llm(ticket_id, PRODUCT_SPECIALIST)
    elif intent.choice == "return_exchange":
        handle_with_llm(ticket_id, RETURNS_SPECIALIST)
    elif intent.choice == "complaint":
        low_confidence = complexity.confidence < 0.5
        # A higher complexity.score leans toward the "escalation needed" end of the scale.
        if complexity.score > 1 or low_confidence:
            # Too complex for safe automation, or we're not sure about the complexity; route to a human.
            route_to_human_agent(ticket_id)
        else:
            handle_with_llm(ticket_id, COMPLAINT_RESOLUTION)
```

One intent routes to deterministic code with no LLM involved. Two route to different specialist LLMs, each loaded with different context. One uses the complexity score to decide between an LLM and a human. TypeSafe handles the classification all in a single quick call; the expensive resources only get invoked for the requests that actually need them.

Note the additional confidence check on the complexity score. As discussed in [Confidence](https://docs.typesafe.ai/confidence), it is always important to consider the meaning of a low confidence score in the context of the system and the stakes of the decision.

Was this page helpful?

[Composite scoring](https://docs.typesafe.ai/patterns/composite-scoring)

[Previous](https://docs.typesafe.ai/patterns/composite-scoring) [Demos Next](https://docs.typesafe.ai/demos)

[github](https://github.com/typesafe-ai) [discord](https://discord.gg/typesafe) [x](https://x.com/typesafeai)

[Powered byThis documentation is built and hosted on Mintlify, a developer documentation platform](https://www.mintlify.com/?utm_campaign=poweredBy&utm_medium=referral&utm_source=ts-docs)

## On this page

- [Example: customer service routing](https://docs.typesafe.ai/patterns/intent-routing#example-customer-service-routing)
  - [Step 1: classify intent and complexity](https://docs.typesafe.ai/patterns/intent-routing#step-1-classify-intent-and-complexity)
  - [Step 2: route to the optimal handler](https://docs.typesafe.ai/patterns/intent-routing#step-2-route-to-the-optimal-handler)

[github](https://github.com/typesafe-ai)[discord](https://discord.gg/typesafe)[x](https://x.com/typesafeai)

[Powered byThis documentation is built and hosted on Mintlify, a developer documentation platform](https://www.mintlify.com/?utm_campaign=poweredBy&utm_medium=referral&utm_source=ts-docs)