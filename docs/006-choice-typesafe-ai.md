---
title: "Choice - TypeSafe AI"
date: "2026-09-16T21:01:13.495Z"
description: "A Choice is a System One question type for selecting one option from a defined set. The answer includes the selected option, a probability for each option, and confidence."
url: "https://docs.typesafe.ai/primitives/choice"
publisher: "TypeSafe AI"
lang: "en"
logo_url: "https://docs.typesafe.ai/mintlify-assets/_mintlify/favicons/ts-docs/zg2v0DiYB7xPw0I2/_generated/favicon/android-chrome-192x192.png"
logo_type: "png"
logo_size: 8885
logo_height: 192
logo_width: 192
logo_size_pretty: "8.88 kB"
image_url: "https://ts-docs.mintlify.app/mintlify-assets/_next/image?url=%2F_mintlify%2Fapi%2Fog%3Fdivision%3DPrimitives%2B%2528Questions%2529%26title%3DChoice%26description%3DA%2BChoice%2Bis%2Ba%2BSystem%2BOne%2Bquestion%2Btype%2Bfor%2Bselecting%2Bone%2Boption%2Bfrom%2Ba%2Bdefined%2Bset.%2BThe%2Banswer%2Bincludes%2Bthe%2Bselected%2Boption%252C%2Ba%2Bprobability%2Bfor%2Beach%2Boption%252C%2Band%2B%26theme%3Df0580ae664a0195833f0555d&w=1200&q=100"
image_type: "png"
image_size: 37240
image_height: 630
image_width: 1200
image_size_pretty: "37.2 kB"
word_count: 2654
reading_time: "11 min read"
---

[← Back to Index](../README.md)

## Last Pages

- [System One - TypeSafe AI](./003-system-one-typesafe-ai.md)
- [State - TypeSafe AI](./004-state-typesafe-ai.md)
- [Primitives (Questions) - TypeSafe AI](./005-primitives-questions-typesafe-ai.md)

## Table of Contents

- [Request structure](#request-structure)
- [Response structure](#response-structure)
- [Good practice: ask more than one question per call](#good-practice-ask-more-than-one-question-per-call)
- [A more complex example](#a-more-complex-example)
- [Structured instructions and criteria](#structured-instructions-and-criteria)
- [On this page](#on-this-page)

---

Primitives (Questions)

A Choice is a System One question type for selecting one option from a defined set. The answer includes the selected option, a probability for each option, and confidence.

Use a Choice when the answer is one of a fixed set of options. For example, which team handles a ticket, which category a product belongs to, or which language a code snippet is written in. If the answer is a position on a spectrum, use a [Score](https://docs.typesafe.ai/primitives/score). If it’s a yes or no, use a [Noul](https://docs.typesafe.ai/primitives/noul). [Choose a question type](https://docs.typesafe.ai/primitives#choose-a-question-type) compares all three.

A Choice answer is the selected option in `choice`. The model also returns a probability for every option in `probabilities`, and a `confidence` value for the selected option.

Example questions:

```text
"What programming language is this code written in"
  → options: python, javascript, typescript, go, rust, other
"What type of meeting is this based on the title and description"
  → options: standup, planning, retrospective, one on one, brainstorm, none of the above
"Which product category does this item belong to"
  → options: electronics, clothing, home garden, food and beverage
```

## Request structure

The POST request body to the [TypeSafe API](https://docs.typesafe.ai/api) has a specific structure. The top level has three fields: `state`, the content to evaluate; `model`; and `questions`, a map from question ids you choose to question objects. Each Choice question has the following fields:

- `type`: Always `"choice"`.
- `instructions`: The question the model answers.
- `criteria`: The answer options, as a map. Each key is an option name and each value is a description of that option.

Below is a request where the state is a support ticket from an online shoe store and the question is which team should handle it:

request

```json
{
  "state": "My running shoes arrived in the wrong size. Can I swap them for a size 10?",
  "questions": {
    "department": {
      "type": "choice",
      "instructions": "Which team should handle this?",
      "criteria": {
        "returns": "Exchanges, refunds, wrong or damaged items",
        "shipping": "Delivery status, delays, lost packages",
        "billing": "Charges, invoices, payment problems"
      }
    }
  }
}
```

[Try it in the Playground →](https://console.typesafe.ai/decode#share/N4IghgDglgagpgJwM5QPYDsQC4QDcCMIANCACaoDGArgLZzoAuAKnAB4PYgCyAngAQIq6dFHQBzPkgAWqOEj5gECKLjik+ovgylw+AdwQYJKAF5wAdHwDCYdHwCSkvZC06afAGaoECyVDN8+AAMAPzEIBCGNBAMSCzsnMAAOnZ8SWRwEIoMdIzpWHzJqXxpIAw8EHD5pRQyUBRVxCklJemiSAyCFAxo6EjV6QDqUvVSWnBg7tKoVAA26lK2pLO62lBIIelEzS3pFMoMiFBg1UUtuyAIcAxUCH0DIACirLW2YnJEAnAeQqRInwYjHxvHxSJMwO91FBDjR+k1ihdpFAINBxA8ACJwWYqRD8DpgG7-UFYsA8ImzVAdPhZCgAawhci2O3O6QARlBZti0dhSlZFgh3kTRLhUPUPtTSbkGNTDKyVrD0sy+ABfHaq9DK8JILFwbpqLioUhYpDYADaIAAVnBcABaWYEuQcAC6yqAA)

You choose the question id, `department` in this case. The answer is returned under the same id. The model never sees the question id. The option names and their descriptions are both sent to the model, so write descriptions that separate the options from each other.

Our [client SDKs](https://docs.typesafe.ai/sdk) provide typed questions. In Python, the same question is a `Choice`:

```python
from typesafe_sdk import Choice, TypeSafeClient
with TypeSafeClient() as client:
    response = client.system_one(
        state="My running shoes arrived in the wrong size. Can I swap them for a size 10?",
        questions={
            "department": Choice(
                instructions="Which team should handle this?",
                criteria={
                    "returns": "Exchanges, refunds, wrong or damaged items",
                    "shipping": "Delivery status, delays, lost packages",
                    "billing": "Charges, invoices, payment problems",
                },
            ),
        },
    )
    print(response.answers["department"].choice)
```

Use the `system_one` method or the `https://api.typesafe.ai/v1/systemone` endpoint to call a System One model. The `model` field selects which model handles the request. [How to build with TypeSafe](https://docs.typesafe.ai/concepts/how-to-build-with-system-one) covers where in your code to call it.

Use one of our [client SDKs](https://docs.typesafe.ai/sdk) or call the [HTTP API](https://docs.typesafe.ai/api) directly. If a coding agent is writing the integration for you, install the [TypeSafe agent skill](https://docs.typesafe.ai/agent-skill#installation) first so it knows the request and response shapes.

`instructions` and each entry in `criteria` can be a string, an object, or an array. Start with a string. Use an object when a description needs several kinds of guidance, such as what an option covers, what it doesn’t cover, and some examples. See [Structured instructions and criteria](https://docs.typesafe.ai/primitives/choice#structured-instructions-and-criteria) below and the [API reference](https://docs.typesafe.ai/api#param-instructions-1).

## Response structure

The response has one entry in `answers` per question, under the ids from the request. This is the response to the example request above:

```json
{
  "model": "jev-latest",
  "answers": {
    "department": {
      "type": "choice",
      "choice": "returns",
      "confidence": 1.0,
      "probabilities": {
        "shipping": 0.0,
        "returns": 1.0,
        "billing": 0.0
      }
    }
  },
  "usage": {
    "input_tokens": 330,
    "output_tokens": 34
  }
}
```

Besides `type`, each Choice answer has three values:

- `choice`: The option with the highest probability.
- `probabilities`: The full probability distribution across every option. The sum of all values is 1.
- [`confidence`](https://docs.typesafe.ai/confidence): A number from 0 to 1 computed from how `probabilities` is spread. A flat shape, with probability spread across several options, means low confidence. A single peak on one option means high confidence.

This ticket is an easy one, so all of the probability is on `returns` and confidence is 1.0. A ticket that mentions a wrong size and a missing refund would split probability between `returns` and `billing`, and confidence would drop.

## Good practice: ask more than one question per call

Ask every Choice question your code might need in a single request rather than one request per question. Questions are evaluated in parallel. Adding questions barely changes the response time, and the code can ignore answers it doesn’t need. Extra questions still cost tokens. [Ask multiple questions together](https://docs.typesafe.ai/primitives#ask-multiple-questions-together) explains this in full; the next section shows five Choice questions in one call.

The same logic applies to the options inside a single Choice question. A Choice question accepts up to 255 options, and adding options costs a few tokens each, so give the model the full list of teams, categories, or products rather than a shortlist. Add an `other` or `none of the above` option when the list might not cover every input, so the model can say none of the others fit.

To classify documents through a deep hierarchy or large taxonomy, chain Choice questions level by level. The [Hierarchical Classification cookbook](https://docs.typesafe.ai/cookbooks/hierarchical_classification) shows how to run a beam search over Choice probabilities, keeping the best `K` candidate paths at each level instead of committing to a single greedy path.

## A more complex example

The basic example above routes a ticket to a team. A bigger support system might also need the return reason, the delivery problem, what the customer wants, and the customer’s tone.

The request below asks five Choice questions about a ticket that is more ambiguous than the first: it involves three teams and doesn’t say what the customer wants.

request

```json
{
  "state": "Shoes arrived two weeks late and in the wrong size. Also I see two charges on my card. What are you going to do about this?",
  "questions": {
    "department": {
      "type": "choice",
      "instructions": "Which team should handle this?",
      "criteria": {
        "returns": "Exchanges, refunds, wrong or damaged items",
        "shipping": "Delivery status, delays, lost packages",
        "billing": "Charges, invoices, payment problems"
      }
    },
    "return_reason": {
      "type": "choice",
      "instructions": "If the customer wants to return something, why?",
      "criteria": {
        "wrong_size": "The item doesn't fit",
        "wrong_item": "A different product was delivered",
        "damaged": "The item arrived broken or faulty",
        "changed_mind": "The item is fine, the customer no longer wants it",
        "other": "A return reason that fits none of the above"
      }
    },
    "shipping_issue": {
      "type": "choice",
      "instructions": "If this is a shipping problem, which kind is it?",
      "criteria": {
        "not_delivered": "The package never arrived",
        "delayed": "The package is late but still on its way",
        "wrong_address": "The package went to the wrong place",
        "damaged_in_transit": "The package arrived damaged",
        "other": "A shipping problem that fits none of the above"
      }
    },
    "requested_resolution": {
      "type": "choice",
      "instructions": "What does the customer want to happen?",
      "criteria": {
        "exchange": "Swap the item for a different one",
        "refund": "Money back",
        "replacement": "The same item sent again",
        "information": "Just an answer, no action needed"
      }
    },
    "tone": {
      "type": "choice",
      "instructions": "What is the customer's tone?",
      "criteria": {
        "calm": null,
        "frustrated": null,
        "angry": null
      }
    }
  }
}
```

[Try it in the Playground →](https://console.typesafe.ai/decode#share/N4IghgDglgagpgJwM5QPYDsQC4QDcCMIANCACaoDGArgLZzoAuAKnAB4PYgDKAFqnEgAEYBAii44pQQwDuqQTLhwA1kIA2YBnGHopUdNJ7aZCDAHNBKAF5wAdIICCapPICSlpdLmCKPEWYFBDEEaAE8fEVJ7AHU-BmEEbVDUKkEzVH0LBnlyYQAjFPiGHigkAH5iEAhTGggGJBZ2TmAAHQNBFrI4CBEGOkZOrEFW9sEOkAZQiDhB8d8MihniNrGxzv0kBgQqCgY0dCRZztioX2k4MBpLPio1KT9dNW1i0rLOohXVzooxLTEwWYjVZfECJBhUBAHI4gACirF8YHQASQREEiQAZlRdCiFKYkUEEIJSJcwAE9FoaIdlqMQUgShBoEjoQAROBqcSIcKbTRUHGkNlgUI4tSoTaCHoUZSkgTvT7Azp5KBqdlM7DjADCfgQyNR+lwCwEqJ6oX68WqqDyT0pnTlggAvp87R92p0wRD0AB9RJgFzoQG2zqTabQ+anJbO+UgDZbHZ7DBUoadVzowzaaibVB0QkyRH1aTyN2QyyZuAvJGomQ8UJvamRn5QP5QAFqoHA8Ymcwe6xLRMgJhGQQNuBXcgCdAAcni6IbsppaxAHaRHqHNGhDiJUHR6MQ9DNplIsYUPqJbI5iVIs7b42JNGlF7VnX72hXCTEEikeVMynoBME6LAtyTJebbfA8ZIejQ+j3r2T6DhSg5CNO6BwKixRpry2RZoI6DyCKSKIEejBCDOtYgSAqBoQga5oqW7o0T6wTFJof4NkIOHIUEKZofkqASDaNIOu0TqfJ0dJQAymTLkgSBUD2wwBhMUxyaBBrAfO0bbLs+wJuMyaGKUCHCNc4mMhY5qWsOFYlGcyhQYZDY1hGIL1o2zZDK2kY4QwHr8uyEjntCsESlKATYXA-mvhy95OZGvmCpIgUDsF0qGRoWiCHkVDxJsSpqEEBisUeoRqSCi5mB6YCkKQiTSYl2jJaFiiMPmqa4uY4oaIsJXzjed7Lp6WyIigDB1eKYCSilIhvpIRIkmS3XjBRRhUQ+IDrmJEn4uZVqGMx055ux2ioFxA5gAUfEgLagljMJLqgnAACOsmbJIXoCKgahZfs-o0oGSkhnwYYlesBwxlp8bQrEzGjkI3HpphBE5s12SCH4DL0I5CkuYgTY-VenRsAi+HQlwOYQK1L7oqghJgBuW47s1GDhra84Yli0HjAAskz4R5ONygLa63SdcOu6jUglzPvBSC7sIZhgPogtRugVMILecZ+qtABSGE6DoSCKAgqI4cI4MGMhkgJZdAmOk5gZM3jIJBspIChl1pHqaDmkazpxxxIZcMYSWCDjrDTOY79ru-DjbnyXOcxgGoq5qugtxqDFILotsmwIJoVtDKnyoZ-OiJmAgxUp2nV2Om0dqVDLTy7JI3O+Ug2AANogAAVuFAC0aUCBwAC6dpAA)

Two of these Choice questions are speculative: `return_reason` only matters if the `department` is `returns`, and `shipping_issue` only matters if it’s `shipping`. The `tone` question uses `null` descriptions because the option names are clear on their own.

The TypeSafe response:

```json
{
  "model": "jev-latest",
  "answers": {
    "department": {
      "type": "choice",
      "choice": "returns",
      "confidence": 0.39,
      "probabilities": {
        "shipping": 0.02,
        "billing": 0.38,
        "returns": 0.6
      }
    },
    "return_reason": {
      "type": "choice",
      "choice": "wrong_size",
      "confidence": 1.0,
      "probabilities": {
        "wrong_size": 1.0,
        "wrong_item": 0.0,
        "other": 0.0,
        "changed_mind": 0.0,
        "damaged": 0.0
      }
    },
    "shipping_issue": {
      "type": "choice",
      "choice": "delayed",
      "confidence": 0.53,
      "probabilities": {
        "delayed": 0.63,
        "other": 0.37,
        "damaged_in_transit": 0.0,
        "not_delivered": 0.0,
        "wrong_address": 0.0
      }
    },
    "requested_resolution": {
      "type": "choice",
      "choice": "exchange",
      "confidence": 0.16,
      "probabilities": {
        "information": 0.1,
        "exchange": 0.37,
        "replacement": 0.24,
        "refund": 0.29
      }
    },
    "tone": {
      "type": "choice",
      "choice": "frustrated",
      "confidence": 0.88,
      "probabilities": {
        "angry": 0.08,
        "frustrated": 0.92,
        "calm": 0.0
      }
    }
  },
  "usage": {
    "input_tokens": 588,
    "output_tokens": 212
  }
}
```

Each question is answered on its own against the ticket:

- The `department` answer is `returns` with a 0.60 probability, but `billing` has 0.38 probability because of the double charge. This lowers the confidence to 0.39. The top option is clear enough to act on, but the second option is not noise.
- The `return_reason` is `wrong_size` with a confidence of 1.0, which is expected because it says this clearly in the ticket.
- The `shipping_issue` answer is split between `delayed` and `other`. It’s a speculative question and `department` didn’t come back as shipping, so it can be ignored by the code, as shown in the example code snippet below.
- The `requested_resolution` confidence is 0.16 because of the flat probability distribution of the answers. This is because the customer didn’t say what they want.
- The `tone` answer is `frustrated` with a probability of 0.92 and a confidence of 0.88.

The example code below reads the answers it needs, ignores the rest, and treats a low-confidence answer as a reason to ask rather than act:

```python
from typesafe_sdk import Choice, TypeSafeClient
TRIAGE_QUESTIONS = {
    "department": Choice(
        instructions="Which team should handle this?",
        criteria={
            "returns": "Exchanges, refunds, wrong or damaged items",
            "shipping": "Delivery status, delays, lost packages",
            "billing": "Charges, invoices, payment problems",
        },
    ),
    "return_reason": Choice(
        instructions="If the customer wants to return something, why?",
        criteria={
            "wrong_size": "The item doesn't fit",
            "wrong_item": "A different product was delivered",
            "damaged": "The item arrived broken or faulty",
            "changed_mind": "The item is fine, the customer no longer wants it",
            "other": "A return reason that fits none of the above",
        },
    ),
    "shipping_issue": Choice(
        instructions="If this is a shipping problem, which kind is it?",
        criteria={
            "not_delivered": "The package never arrived",
            "delayed": "The package is late but still on its way",
            "wrong_address": "The package went to the wrong place",
            "damaged_in_transit": "The package arrived damaged",
            "other": "A shipping problem that fits none of the above",
        },
    ),
    "requested_resolution": Choice(
        instructions="What does the customer want to happen?",
        criteria={
            "exchange": "Swap the item for a different one",
            "refund": "Money back",
            "replacement": "The same item sent again",
            "information": "Just an answer, no action needed",
        },
    ),
    "tone": Choice(
        instructions="What is the customer's tone?",
        criteria={"calm": None, "frustrated": None, "angry": None},
    ),
}
def triage(ticket: str) -> None:
    with TypeSafeClient() as client:
        response = client.system_one(
            state=ticket,
            questions=TRIAGE_QUESTIONS,
        )
    answers = response.answers
    department = answers["department"]
    if department.confidence < 0.3:
        # Not clear which team to send to. Let a person decide.
        send_to_manual_triage(ticket)
        return
    if department.choice == "returns":
        # return_reason answer is only used here
        assign(ticket, team="returns", issue=answers["return_reason"].choice)
    elif department.choice == "shipping":
        # shipping_issue answer is only used here
        assign(ticket, team="shipping", issue=answers["shipping_issue"].choice)
    else:
        assign(ticket, team="billing")
    # A second team with a real share of the probability gets a copy
    for team, probability in department.probabilities.items():
        if team != department.choice and probability > 0.25:
            notify(ticket, team=team)
    resolution = answers["requested_resolution"]
    if resolution.confidence < 0.5:
        # The customer hasn't said what they want. Ask, don't guess.
        ask_customer_what_they_want(ticket)
    elif resolution.choice == "refund":
        flag_for_refund_approval(ticket)
    if answers["tone"].choice == "angry":
        flag_for_senior_agent(ticket)
```

For the ticket above, this assigns the ticket to the returns team with issue `wrong_size`, sends the billing team a copy, and asks the customer what they want. The code does not use the `shipping_issue` answer.

One request, five answers, and the routing logic is ordinary `if` statements. If you later need to know the customer’s language, or which product the ticket is about, add another Choice question to `TRIAGE_QUESTIONS`; the request count stays at one.

The [smart home assistant demo](https://docs.typesafe.ai/demos/smart-home) evaluates every user request against a long list of Choice questions in one call: the request category, the room, the device, and the action. Most of those questions are irrelevant to any one request and the code ignores them.

## Structured instructions and criteria

Start with a one-line description per option. When two options are similar and the model keeps confusing them, describe each one with an object instead of a string. Give it fields for what the option covers, what belongs to a neighboring option instead, and a few example inputs.

The two answer options below, return_policy and return_status, are easy to confuse. A ticket about either one can mention returns and refunds, so each option says what it is not for.

request

```json
{
  "state": "I sent the shoes back a week ago. When do I get my money?",
  "questions": {
    "return_topic": {
      "type": "choice",
      "instructions": {
        "question": "Which returns topic is the customer asking about?",
        "focus": "Classify the information the customer wants."
      },
      "criteria": {
        "return_policy": {
          "what": "Whether and how an item can be returned",
          "not_for": "Progress of a return already sent",
          "examples": [
            "Can I return shoes I've worn once?",
            "How long do I have to return an order?"
          ]
        },
        "return_status": {
          "what": "Progress of a return already sent",
          "not_for": "Whether and how an item can be returned",
          "examples": [
            "Has my return arrived yet?",
            "When will my refund be paid?"
          ]
        }
      }
    }
  }
}
```

[Try it in the Playground →](https://console.typesafe.ai/decode#share/N4IghgDglgagpgJwM5QPYDsQC4QDcCMIANCACaoDGArgLZzoAuAKnAB4PYgCSABEvQx4MAFnD7DUcJDwBGYCgGseYHgHc4cJWADmqAHQ8A6qPQ9yPXtriCaATx40McWwH5iICAlQ0IDJC3ZOYAAdUx5gkARrKgR0AH0GVGgKCKweELCecJAGWwg4VOyKCSgKAuJQrKyIqHQkBgQqCgY0OsKMqqqIgEcqKRaMQojjUuEeKIYYuqEk0p4oaRExanrvRGUkBVrtZRlUKgYXCKJKzuyAM0oqJCGQAGEAGzAkFHP7Jfn0S4QaMAHTD4rRJ0BBqMCMJB6CKnLIAXxOmSKCCgDEQUDA7RhXUi0VicQgqAepVsmMRnQiqmEf1uxmsolB4NIPAkqmUphRcBoPAo4NkYgmUzgpGOWPJIHQqAYcW+twACl5tFEXjxUOdlONcaYwA8omBSPZ+IwRWTsWwwD4HlJCgBtUVnCJ3Xm8AWxcSSaRcADkuDEqlQrowZSOFRNYoAEqhWQ8MDtzLwqT6ZhrJq7ef7SIhg3asgBdO3wu0RF3xep-a6ks7YynU7DZeWoRVSaSq9XF5Q6uB6g0CY2V6riyXS-000RLBnoJkstnzVFcnmmGT8zVC3t9iJmi1W2u20PYsPPBz2NtgBDIn1M2zWYMIvvY2mmVRQB4PQ8a85UCd8ngQMBQUhZ3c8xNWEsRAsIwNhdx+EtZohQAWVQDMHiQbBrRAAArOBcAAWieVF6hAHNYSAA)

The response is `return_status` at confidence 1.0:

```json
{
  "model": "jev-latest",
  "answers": {
    "return_topic": {
      "type": "choice",
      "choice": "return_status",
      "confidence": 1.0,
      "probabilities": {
        "return_policy": 0.0,
        "return_status": 1.0
      }
    }
  },
  "usage": {
    "input_tokens": 407,
    "output_tokens": 32
  }
}
```

The field names `question`, `focus`, `what`, `not_for`, and `examples` are not part of the API, and none are reserved. You choose them, the same way you choose option names. The model sees the names along with the values, so use short names that label what follows.

Was this page helpful?

[Primitives (Questions)](https://docs.typesafe.ai/primitives)

[Previous](https://docs.typesafe.ai/primitives) [Score Next](https://docs.typesafe.ai/primitives/score)





## Next Page

- [Score - TypeSafe AI](./007-score-typesafe-ai.md)
- [Noul - TypeSafe AI](./008-noul-typesafe-ai.md)
- [Advanced: structure - TypeSafe AI](./009-advanced-structure-typesafe-ai.md)




