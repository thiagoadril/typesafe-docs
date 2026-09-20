---
title: "API reference - TypeSafe AI"
date: "2026-09-17T07:02:51.269Z"
description: "Full HTTP API reference for the TypeSafe evaluation endpoint."
url: "https://docs.typesafe.ai/api"
publisher: "TypeSafe AI"
lang: "en"
logo_url: "https://docs.typesafe.ai/mintlify-assets/_mintlify/favicons/ts-docs/zg2v0DiYB7xPw0I2/_generated/favicon/android-chrome-192x192.png"
logo_type: "png"
logo_size: 8885
logo_height: 192
logo_width: 192
logo_size_pretty: "8.88 kB"
image_url: "https://ts-docs.mintlify.app/mintlify-assets/_next/image?url=%2F_mintlify%2Fapi%2Fog%3Fdivision%3DReference%26title%3DAPI%2Breference%26description%3DFull%2BHTTP%2BAPI%2Breference%2Bfor%2Bthe%2BTypeSafe%2Bevaluation%2Bendpoint.%26theme%3Df0580ae664a0195833f0555d&w=1200&q=100"
image_type: "png"
image_size: 32785
image_height: 630
image_width: 1200
image_size_pretty: "32.8 kB"
word_count: 294
reading_time: "2 min read"
---

[← Voltar ao índice](./README.md)


## Table of Contents

- [Evaluation endpoint](#evaluation-endpoint)
- [Request body](#request-body)
- [Question types](#question-types)
  - [Noul](#noul)
  - [Choice](#choice)
  - [Score](#score)
- [Response body](#response-body)
- [Answer types](#answer-types)
  - [Noul answer](#noul-answer)
  - [Choice answer](#choice-answer)
  - [Score answer](#score-answer)
- [Errors](#errors)
  - [Handling rate limits](#handling-rate-limits)
- [On this page](#on-this-page)

---

Reference

Full HTTP API reference for the TypeSafe evaluation endpoint.

Evaluate a `state` against a map of typed `questions` and get back structured `answers`, one per question. For a guided introduction, start with the [primitives](https://docs.typesafe.ai/primitives).

## Evaluation endpoint

```http
POST https://api.typesafe.ai/v1/systemone
Authorization: Bearer <API_KEY>
Content-Type: application/json
```

## Request body

The top-level shape of every request. Each entry in the `questions` map is a typed question you name.

[Navigate to header: state](https://docs.typesafe.ai/api#param-state)

string \| object \| array

required

The content to evaluate. A plain string for text, or structured data (object/array) for things like chat logs, records, or the current state of your application. See [State](https://docs.typesafe.ai/concepts/state) for formats and best practices.

[Navigate to header: model](https://docs.typesafe.ai/api#param-model)

string

required

The model that handles the request. Use `"jev-latest"`, TypeSafe’s flagship model. See [Models](https://docs.typesafe.ai/models) for the available models and aliases.

[Navigate to header: questions](https://docs.typesafe.ai/api#param-questions)

map\<string, Question\>

required

A map of typed [Question](https://docs.typesafe.ai/api#question-types) objects. You choose each key; answers come back under the same keys.

Show map entries

[Navigate to header: ‹question id›](https://docs.typesafe.ai/api#param-question-id)

Question

A key you choose. The matching [Answer](https://docs.typesafe.ai/api#answer-types) is returned under this same id. The key is not sent to the underlying model and is not used in inference.

Example request

```json
{
  "state": "Help! My payouts have been failing for 3 days.",
  "model": "jev-latest",
  "questions": {
    "is_urgent": {
      "type": "noul",
      "instructions": "Does this convey urgency?"
    }
  }
}
```

## Question types

A `Question` is one of three types, set by its `type` field. All three share `type` and `instructions`; each adds its own `criteria`.

### Noul

A yes/no question. Returns the probability the answer is yes.

[Navigate to header: type](https://docs.typesafe.ai/api#param-type)

"noul"

required

[Navigate to header: instructions](https://docs.typesafe.ai/api#param-instructions)

string \| object \| array

required

The yes/no question to evaluate.

[Navigate to header: criteria](https://docs.typesafe.ai/api#param-criteria)

object

Optional descriptions of what a yes and a no mean.

Show properties

[Navigate to header: true](https://docs.typesafe.ai/api#param-true)

string

What a yes (value near 1) means.

[Navigate to header: false](https://docs.typesafe.ai/api#param-false)

string

What a no (value near 0) means.

Example request

```json
{
  "state": "Help! My payouts have been failing for 3 days.",
  "model": "jev-latest",
  "questions": {
    "is_urgent": {
      "type": "noul",
      "instructions": "Does this convey urgency?",
      "criteria": {
        "true": "Explicitly time-sensitive",
        "false": "No urgency expressed"
      }
    }
  }
}
```

### Choice

Picks one option from a set you define. Returns the chosen option and the full probability distribution.

[Navigate to header: type](https://docs.typesafe.ai/api#param-type-1)

"choice"

required

[Navigate to header: instructions](https://docs.typesafe.ai/api#param-instructions-1)

string \| object \| array

required

What the model should decide.

[Navigate to header: criteria](https://docs.typesafe.ai/api#param-criteria-1)

map\<string, string \| null\>

required

A map of option to rubric description; use null when an option needs no extra detail.

Show map entries

[Navigate to header: ‹option›](https://docs.typesafe.ai/api#param-option)

string \| null

A key you choose. A description of this option.

Example request

```json
{
  "state": "Help! My payouts have been failing for 3 days.",
  "model": "jev-latest",
  "questions": {
    "department": {
      "type": "choice",
      "instructions": "Which team should handle this?",
      "criteria": {
        "billing": "Payments, invoicing, refunds",
        "technical": "Bugs, outages, integrations",
        "sales": "Pricing, upgrades, new accounts"
      }
    }
  }
}
```

### Score

Rates the state along a rubric you define. Returns a probability-weighted value across your levels.

[Navigate to header: type](https://docs.typesafe.ai/api#param-type-2)

"score"

required

[Navigate to header: instructions](https://docs.typesafe.ai/api#param-instructions-2)

string \| object \| array

required

What the model should rate.

[Navigate to header: criteria](https://docs.typesafe.ai/api#param-criteria-2)

array

required

An ordered array of level descriptions. You must include at least two levels.

Example request

```json
{
  "state": "Help! My payouts have been failing for 3 days.",
  "model": "jev-latest",
  "questions": {
    "frustration": {
      "type": "score",
      "instructions": "How frustrated is the customer?",
      "criteria": ["Calm", "Frustrated", "Very angry"]
    }
  }
}
```

## Response body

One answer per question, returned under the same ids you provided.

[Navigate to header: model](https://docs.typesafe.ai/api#param-model-1)

string

required

The model that performed the evaluation.

[Navigate to header: answers](https://docs.typesafe.ai/api#param-answers)

map\<string, Answer\>

required

One [Answer](https://docs.typesafe.ai/api#answer-types) per question, keyed by the same ids you used in questions.

Show map entries

[Navigate to header: ‹question id›](https://docs.typesafe.ai/api#param-question-id-1)

Answer

The same id you chose in questions.

[Navigate to header: usage](https://docs.typesafe.ai/api#param-usage)

object

required

Token usage for the request.

Show properties

[Navigate to header: input_tokens](https://docs.typesafe.ai/api#param-input-tokens)

integer

[Navigate to header: output_tokens](https://docs.typesafe.ai/api#param-output-tokens)

integer

Example response

```json
{
  "model": "jev-latest",
  "answers": {
    "is_urgent": {
      "type": "noul",
      "noul": 0.92
    }
  },
  "usage": { "input_tokens": 312, "output_tokens": 48 }
}
```

## Answer types

Every answer carries a `type` matching its question. Choice and Score answers also carry a `confidence` between 0 to 1, derived from the answer’s probability distribution. See [Confidence](https://docs.typesafe.ai/confidence).

### Noul answer

[Navigate to header: type](https://docs.typesafe.ai/api#param-type-3)

"noul"

required

[Navigate to header: noul](https://docs.typesafe.ai/api#param-noul)

number

required

The yes/no answer on a scale from 0 (no) to 1 (yes).

Example response

```json
{
  "model": "jev-latest",
  "answers": {
    "is_urgent": {
      "type": "noul",
      "noul": 0.92
    }
  },
  "usage": { "input_tokens": 312, "output_tokens": 48 }
}
```

### Choice answer

[Navigate to header: type](https://docs.typesafe.ai/api#param-type-4)

"choice"

required

[Navigate to header: choice](https://docs.typesafe.ai/api#param-choice)

string

required

The highest-probability option.

[Navigate to header: probabilities](https://docs.typesafe.ai/api#param-probabilities)

map\<string, number\>

required

Every option mapped to its probability (floats that sum to 1).

Show map entries

[Navigate to header: ‹option›](https://docs.typesafe.ai/api#param-option-1)

number

An option you defined in criteria.

[Navigate to header: confidence](https://docs.typesafe.ai/api#param-confidence)

number

required

How certain the model is, derived from probabilities.

Example response

```json
{
  "model": "jev-latest",
  "answers": {
    "department": {
      "type": "choice",
      "choice": "technical",
      "probabilities": { "billing": 0.08, "technical": 0.85, "sales": 0.07 },
      "confidence": 0.82
    }
  },
  "usage": { "input_tokens": 312, "output_tokens": 48 }
}
```

### Score answer

[Navigate to header: type](https://docs.typesafe.ai/api#param-type-5)

"score"

required

[Navigate to header: score](https://docs.typesafe.ai/api#param-score)

number

required

The probability-weighted answer across the levels; can land between levels.

[Navigate to header: legend](https://docs.typesafe.ai/api#param-legend)

map\<string, string\>

required

Each level number mapped back to its description.

[Navigate to header: probabilities](https://docs.typesafe.ai/api#param-probabilities-1)

map\<string, number\>

required

Each level (string key) mapped to its probability (floats that sum to 1).

Show map entries

[Navigate to header: ‹level›](https://docs.typesafe.ai/api#param-level)

number

A level index, as a string key matching legend.

[Navigate to header: confidence](https://docs.typesafe.ai/api#param-confidence-1)

number

required

How certain the model is, derived from probabilities.

Example response

```json
{
  "model": "jev-latest",
  "answers": {
    "frustration": {
      "type": "score",
      "score": 1.6,
      "legend": { "0": "Calm", "1": "Frustrated", "2": "Very angry" },
      "probabilities": { "0": 0.05, "1": 0.3, "2": 0.65 },
      "confidence": 0.78
    }
  },
  "usage": { "input_tokens": 312, "output_tokens": 48 }
}
```

## Errors

Errors use standard HTTP status codes with a JSON body describing what went wrong.

| Status                     | Meaning                                                                                                                                  |
| -------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------- |
| `401 Unauthorized`         | Missing or invalid API key. Check the `Authorization` header.                                                                            |
| `422 Unprocessable Entity` | The request body failed validation — for example a missing required field or a malformed question. The body details the offending field. |
| `429 Too Many Requests`    | You have exceeded your rate limit. Back off and retry after a short delay.                                                               |
| `529 Overloaded`           | TypeSafe is temporarily overloaded. Retry after a short delay.                                                                           |

### Handling rate limits

When you receive a `429 Too Many Requests` or `529 Overloaded` response, retry the request with exponential backoff instead of retrying immediately. Our client SDKs handle this automatically, so no extra handling is needed if you use one of our SDKs with its default retry policy.

Was this page helpful?

[Models](https://docs.typesafe.ai/models)

[Previous](https://docs.typesafe.ai/models) [Agent skill Next](https://docs.typesafe.ai/agent-skill)

[github](https://github.com/typesafe-ai) [discord](https://discord.gg/typesafe) [x](https://x.com/typesafeai)

[Powered byThis documentation is built and hosted on Mintlify, a developer documentation platform](https://www.mintlify.com/?utm_campaign=poweredBy&utm_medium=referral&utm_source=ts-docs)

## On this page

- [Evaluation endpoint](https://docs.typesafe.ai/api#evaluation-endpoint)
- [Request body](https://docs.typesafe.ai/api#request-body)
- [Question types](https://docs.typesafe.ai/api#question-types)
  - [Noul](https://docs.typesafe.ai/api#noul)
  - [Choice](https://docs.typesafe.ai/api#choice)
  - [Score](https://docs.typesafe.ai/api#score)
- [Response body](https://docs.typesafe.ai/api#response-body)
- [Answer types](https://docs.typesafe.ai/api#answer-types)
  - [Noul answer](https://docs.typesafe.ai/api#noul-answer)
  - [Choice answer](https://docs.typesafe.ai/api#choice-answer)
  - [Score answer](https://docs.typesafe.ai/api#score-answer)
- [Errors](https://docs.typesafe.ai/api#errors)
  - [Handling rate limits](https://docs.typesafe.ai/api#handling-rate-limits)

[github](https://github.com/typesafe-ai)[discord](https://discord.gg/typesafe)[x](https://x.com/typesafeai)

[Powered byThis documentation is built and hosted on Mintlify, a developer documentation platform](https://www.mintlify.com/?utm_campaign=poweredBy&utm_medium=referral&utm_source=ts-docs)