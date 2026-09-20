---
title: "How to build with TypeSafe - TypeSafe AI"
date: "2026-09-15T00:21:19.060Z"
description: "Design AI-powered software by keeping code in control and giving System One narrow, structured decisions."
url: "https://docs.typesafe.ai/concepts/how-to-build-with-system-one"
publisher: "TypeSafe AI"
lang: "en"
logo_url: "https://docs.typesafe.ai/mintlify-assets/_mintlify/favicons/ts-docs/zg2v0DiYB7xPw0I2/_generated/favicon/android-chrome-192x192.png"
logo_type: "png"
logo_size: 8885
logo_height: 192
logo_width: 192
logo_size_pretty: "8.88 kB"
image_url: "https://ts-docs.mintlify.app/mintlify-assets/_next/image?url=%2F_mintlify%2Fapi%2Fog%3Fdivision%3DTypeSafe%2Bfoundations%26title%3DHow%2Bto%2Bbuild%2Bwith%2BTypeSafe%26description%3DDesign%2BAI-powered%2Bsoftware%2Bby%2Bkeeping%2Bcode%2Bin%2Bcontrol%2Band%2Bgiving%2BSystem%2BOne%2Bnarrow%252C%2Bstructured%2Bdecisions.%26theme%3Df0580ae664a0195833f0555d&w=1200&q=100"
image_type: "png"
image_size: 43841
image_height: 630
image_width: 1200
image_size_pretty: "43.8 kB"
word_count: 1712
reading_time: "7 min read"
---

[← Voltar ao índice](./README.md)


## Table of Contents

- [Three software architectures](#three-software-architectures)
- [What makes System One composable](#what-makes-system-one-composable)
- [Structured](#structured)
- [Parallel](#parallel)
- [Comparable](#comparable)
- [Fast](#fast)
- [Calibrated confidence](#calibrated-confidence)
- [Self-consistent](#self-consistent)
- [Design a System One workflow](#design-a-system-one-workflow)
- [Putting it all together](#putting-it-all-together)
- [On this page](#on-this-page)

---

TypeSafe foundations

Design AI-powered software by keeping code in control and giving System One narrow, structured decisions.

System One is TypeSafe’s model for building AI-powered software, not agents. It does not generate code or choose its own next action. It provides AI primitives that embed into software, so code remains in control while the model handles common-sense judgments over unstructured data.

**Summary:** build a normal software workflow and insert System One only where AI is needed.

- Keep control flow, deterministic rules, and side effects in code.
- Break broad judgments into narrow, typed questions with explicit instructions and criteria.
- Give each question only the context it needs.
- Use probabilities and confidence to act, ask for review, or escalate.
- Ask independent questions together, then compose their answers in code.

## Three software architectures

TypeSafe is designed for building **AI-powered software**, where code owns the workflow and AI handles narrow, structured decisions.

Traditional code is a complex decision tree made from simple software primitives. Because each primitive is reliable, developers can compose them into higher-level abstractions.

An agent processes instructions and chooses its next step. This works well when a person is monitoring the process, but every loop introduces another opportunity to go off the rails.

Code handles deterministic work and owns the control flow. The model appears only where the system needs programmable common sense or needs to interpret unstructured data. Each AI task is kept atomic and constrained.

![Traditional software, agents, and AI-powered software shown as three different system architectures.](https://mintcdn.com/ts-docs/aFVnpmCIX68NpsV1/images/how-to-build-with-typesafe/software-architectures-light.webp?fit=max&amp;auto=format&amp;n=aFVnpmCIX68NpsV1&amp;q=85&amp;s=35c7622176190d1b1f19dc712f2fbf11)

Traditional software, agents, and AI-powered software shown as three different system architectures.

![Traditional software, agents, and AI-powered software shown as three different system architectures.](https://mintcdn.com/ts-docs/aFVnpmCIX68NpsV1/images/how-to-build-with-typesafe/software-architectures-dark.webp?fit=max&amp;auto=format&amp;n=aFVnpmCIX68NpsV1&amp;q=85&amp;s=8e6c2c73bdd4c9b541c4f9294bd829b5)

Traditional software, agents, and AI-powered software shown as three different system architectures.

## What makes System One composable

## Structured

System One is type-safe by construction. Decisions and probabilities conform to the structured software types and JSON schema your code expects, so it never has to recover a value from generated prose.

## Parallel

Questions are evaluated independently and in parallel. One primitive’s result does not become hidden context that changes another primitive’s result.

## Comparable

Outputs are sortable and can drive smart `if` statements, thresholds, and comparisons.

## Fast

Most queries complete in about 100 ms. System One is fast enough for real-time request paths and user interfaces.

## Calibrated confidence

[RLCD](https://docs.typesafe.ai/introduction/machine-learning-primer) communicates uncertainty through calibrated probabilities instead of tending toward overconfidence.

## Self-consistent

System One is designed to return stable answers across repeated evaluations. See the [self-consistency cookbook](https://docs.typesafe.ai/cookbooks/consistency_noul_cookbook).

Because every output is constrained to the supplied options, the model returns a full probability distribution over those options rather than inventing a value outside the schema. TypeSafe’s target is a greater than 100× intelligence-to-speed-and-cost ratio; the underlying bet is that cheaper intelligence will create much more demand.

## Design a System One workflow

Decomposition does not require more round trips. Questions over the same state run in parallel.

## Putting it all together

This support-ticket workflow keeps deterministic work in code, sends only relevant structured context, evaluates many atomic questions in one request, and composes the answers with explicit confidence gates.

triage_ticket.py

```python
from typesafe_sdk import Choice, Noul, NoulCriteria, Score, TypeSafeClient
def triage_ticket(ticket, customer):
    # Handle deterministic states without calling a model.
    if ticket["status"] == "closed":
        return "no_action"
    open_orders = [
        order for order in customer["orders"] if order["status"] != "delivered"
    ]
    # Include only the structured context needed by the questions below.
    state = {
        "ticket": {
            "message": ticket["message"],
            "sender": ticket["sender"],
            "links": ticket["links"],
        },
        "customer": {
            "plan": customer["plan"],
            "open_orders": open_orders,
        },
        "policy": {
            "sensitive_credentials": ["password", "security code", "API key"],
        },
    }
    # Ask structured, atomic questions together so they run in parallel.
    questions = {
        "topic": Choice(
            instructions={
                "question": "Which team should handle `ticket.message`?",
                "focus": "Classify the customer's primary request.",
            },
            criteria={
                "billing": {
                    "what": "Charges, invoices, refunds, or subscriptions",
                    "not_for": "Order tracking or account access",
                    "examples": ["I was charged twice", "Where is my refund?"],
                },
                "orders": {
                    "what": "Order status, delivery, cancellation, or returns",
                    "not_for": "Charges or account access",
                    "examples": ["Where is my order?", "Cancel my shipment"],
                },
                "account": {
                    "what": "Login, profile, permissions, or security",
                    "not_for": "Charges or order tracking",
                    "examples": ["Reset my password", "I cannot sign in"],
                },
            },
        ),
        "requests_credentials": Noul(
            instructions={
                "question": "Does the message request a sensitive credential?",
                "compare": [
                    "`ticket.message`",
                    "`policy.sensitive_credentials`",
                ],
                "focus": "Look for a request to disclose the credential itself.",
            },
            criteria=NoulCriteria(
                true={
                    "what": "Asks the recipient to disclose a listed credential",
                    "examples": [
                        "Reply with your password",
                        "Send us your API key",
                    ],
                },
                false={
                    "what": "Does not ask the recipient to disclose a credential",
                    "not_for": "A legitimate instruction to reset a credential",
                    "examples": ["Use this link to reset your password"],
                },
            ),
        ),
        "sender_identity_mismatch": Noul(
            instructions={
                "question": "Does the claimed sender identity conflict with its domain?",
                "compare": [
                    "`ticket.sender.display_name`",
                    "`ticket.sender.email`",
                ],
                "focus": "Compare the named organization with the email domain.",
            },
            criteria=NoulCriteria(
                true={
                    "what": "Claims an organization unrelated to the email domain",
                    "examples": ["Acme Payroll sent from claim-bonus.example"],
                },
                false={
                    "what": "The identity and domain agree or make no conflicting claim",
                    "examples": ["Acme Payroll sent from acme.example"],
                },
            ),
        ),
        "unexpected_reward": Noul(
            instructions={
                "question": "Does the message announce an unexpected reward?",
                "inspect": "`ticket.message`",
                "focus": "Look for an unsolicited prize, payment, or reward claim.",
            },
            criteria=NoulCriteria(
                true={
                    "what": "Announces an unrequested prize, payment, or reward",
                    "examples": ["You were selected for a $1,000 bonus"],
                },
                false={
                    "what": "Contains no reward claim or discusses an expected payment",
                    "not_for": "A customer asking about a known refund or payroll deposit",
                    "examples": ["When will my approved refund arrive?"],
                },
            ),
        ),
        "refund_requested": Noul(
            instructions={
                "question": "Does the customer explicitly request a refund or credit?",
                "inspect": "`ticket.message`",
                "focus": "Require a requested remedy, not a billing complaint alone.",
            },
            criteria=NoulCriteria(
                true={
                    "what": "Directly asks for money back or an account credit",
                    "examples": ["Please refund the duplicate charge"],
                },
                false={
                    "what": "Does not ask for a refund or credit",
                    "not_for": "A complaint or billing question without a requested remedy",
                    "examples": ["Why was I charged twice?"],
                },
            ),
        ),
        "mentions_open_order": Noul(
            instructions={
                "question": "Does the message refer to a supplied open order?",
                "compare": [
                    "`ticket.message`",
                    "`customer.open_orders`",
                ],
                "focus": "Match an order id or other identifying details.",
            },
            criteria=NoulCriteria(
                true={
                    "what": "Refers to an open order by id or identifying details",
                    "examples": ["Where is order A-104?"],
                },
                false={
                    "what": "Does not identify any supplied open order",
                    "not_for": "A generic order question with no matching details",
                    "examples": ["How long does shipping usually take?"],
                },
            ),
        ),
        "frustration": Score(
            instructions={
                "question": "How frustrated does the customer appear?",
                "inspect": "`ticket.message`",
                "focus": "Judge expressed frustration, not issue severity.",
            },
            criteria=[
                {
                    "what": "Calm and matter-of-fact",
                    "signals": ["Neutral wording", "No complaint about the experience"],
                },
                {
                    "what": "Frustrated but civil",
                    "signals": ["Expresses annoyance", "Remains constructive"],
                },
                {
                    "what": "Very angry or threatening to leave",
                    "signals": ["Hostile language", "Threatens cancellation or churn"],
                },
            ],
        ),
    }
    with TypeSafeClient() as client:
        response = client.system_one(
            state=state,
            questions=questions,
        )
    # Compose independent spam signals with weights controlled by code.
    answers = response.answers
    spam_risk = (
        0.45 * answers["requests_credentials"].noul
        + 0.30 * answers["sender_identity_mismatch"].noul
        + 0.25 * answers["unexpected_reward"].noul
    )
    # Escalate uncertain judgments instead of guessing.
    spam_is_uncertain = 0.4 < spam_risk < 0.6
    if spam_is_uncertain or answers["topic"].confidence < 0.75:
        return route_to_human_review(ticket)
    if spam_risk >= 0.6:
        return quarantine_as_spam(ticket)
    # Let code decide which speculative answers matter on this path.
    if answers["topic"].choice == "billing":
        return route_to_billing(
            ticket,
            refund_requested=answers["refund_requested"].noul >= 0.7,
        )
    if answers["topic"].choice == "orders":
        return route_to_orders(
            ticket,
            mentions_open_order=answers["mentions_open_order"].noul >= 0.7,
        )
    priority = (
        "high"
        if answers["frustration"].confidence >= 0.7
        and answers["frustration"].score >= 1.5
        else "normal"
    )
    return route_to_account_support(ticket, priority=priority)
```

Was this page helpful?

[Confidence](https://docs.typesafe.ai/confidence)

[Previous](https://docs.typesafe.ai/confidence) [Example use cases Next](https://docs.typesafe.ai/concepts/use-case-map)

[github](https://github.com/typesafe-ai) [discord](https://discord.gg/typesafe) [x](https://x.com/typesafeai)

[Powered byThis documentation is built and hosted on Mintlify, a developer documentation platform](https://www.mintlify.com/?utm_campaign=poweredBy&utm_medium=referral&utm_source=ts-docs)

## On this page

- [Three software architectures](https://docs.typesafe.ai/concepts/how-to-build-with-system-one#three-software-architectures)
- [What makes System One composable](https://docs.typesafe.ai/concepts/how-to-build-with-system-one#what-makes-system-one-composable)
- [Design a System One workflow](https://docs.typesafe.ai/concepts/how-to-build-with-system-one#design-a-system-one-workflow)
  - [Use code when you can](https://docs.typesafe.ai/concepts/how-to-build-with-system-one#use-code-when-you-can)
  - [Decompose the input state](https://docs.typesafe.ai/concepts/how-to-build-with-system-one#decompose-the-input-state)
  - [Use structure in the input state](https://docs.typesafe.ai/concepts/how-to-build-with-system-one#use-structure-in-the-input-state)
  - [Decompose the questions](https://docs.typesafe.ai/concepts/how-to-build-with-system-one#decompose-the-questions)
  - [Use structure in the questions](https://docs.typesafe.ai/concepts/how-to-build-with-system-one#use-structure-in-the-questions)
  - [Ask a lot of questions](https://docs.typesafe.ai/concepts/how-to-build-with-system-one#ask-a-lot-of-questions)
  - [Combine question outputs in code (or feed into a classical ML model)](https://docs.typesafe.ai/concepts/how-to-build-with-system-one#combine-question-outputs-in-code-or-feed-into-a-classical-ml-model)
  - [Route on uncertainty](https://docs.typesafe.ai/concepts/how-to-build-with-system-one#route-on-uncertainty)
- [Putting it all together](https://docs.typesafe.ai/concepts/how-to-build-with-system-one#putting-it-all-together)

[github](https://github.com/typesafe-ai)[discord](https://discord.gg/typesafe)[x](https://x.com/typesafeai)

[Powered byThis documentation is built and hosted on Mintlify, a developer documentation platform](https://www.mintlify.com/?utm_campaign=poweredBy&utm_medium=referral&utm_source=ts-docs)