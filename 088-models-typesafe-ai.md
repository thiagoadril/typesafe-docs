---
title: "Models - TypeSafe AI"
date: "2026-09-18T09:14:15.554Z"
url: "https://docs.typesafe.ai/models"
publisher: "TypeSafe AI"
lang: "en"
description: "Jev is TypeSafe’s flagship model and the first System One model. Every model on this page is served by the same endpoint, POST /v1/systemone. The request’s model field selects which one handles the call; see the API reference for the full request shape."
logo_url: "https://docs.typesafe.ai/mintlify-assets/_mintlify/favicons/ts-docs/zg2v0DiYB7xPw0I2/_generated/favicon/android-chrome-192x192.png"
logo_type: "png"
logo_size: 8885
logo_height: 192
logo_width: 192
logo_size_pretty: "8.88 kB"
image_url: "https://ts-docs.mintlify.app/mintlify-assets/_next/image?url=%2F_mintlify%2Fapi%2Fog%3Fdivision%3DReference%26title%3DModels%26theme%3Df0580ae664a0195833f0555d&w=1200&q=100"
image_type: "png"
image_size: 24273
image_height: 630
image_width: 1200
image_size_pretty: "24.3 kB"
word_count: 993
reading_time: "4 min read"
---

[← Voltar ao índice](./README.md)


## Table of Contents

- [Current models](#current-models)
- [Aliases](#aliases)
- [Customizing Jev](#customizing-jev)
- [Language support](#language-support)
- [Data handling](#data-handling)
- [Listing models](#listing-models)
- [On this page](#on-this-page)

---

Reference

Jev is TypeSafe’s flagship model and the first [System One model](https://docs.typesafe.ai/concepts/system-one). Every model on this page is served by the same endpoint, `POST /v1/systemone`. The request’s `model` field selects which one handles the call; see the [API reference](https://docs.typesafe.ai/api) for the full request shape.

## Current models

| Jev 1.13                    | `jev-1.13.0`                                                                              |
| --------------------------- | ----------------------------------------------------------------------------------------- |
| Price (per Btok / per Mtok) | \$42 / \$0.042                                                                            |
| Rate limits                 | 250,000 tokens per second / 1,200 requests per minute                                     |
| Context length              | 64k tokens per request; 32k tokens for `state` plus the longest question                  |
| Input                       | Text only. String, JSON object, or array of text values. No image, audio, or video input. |

- **Price:** Charged per input token. Output tokens are free. A Btok is a billion tokens and an Mtok is a million tokens.
- **Rate limits:** Measured in tokens per second and requests per minute. A request over either limit returns `429 Too Many Requests`. Our [client SDKs](https://docs.typesafe.ai/sdk) retry with backoff by default and honor the `retry-after` header when the response carries one. If you call the HTTP API directly, see [Handling rate limits](https://docs.typesafe.ai/api#handling-rate-limits).
- **Context length:** Jev ingests the `state` once and evaluates every question against it in parallel. The 64k budget covers the `state` plus all questions combined; the 32k budget applies to the `state` plus the single longest question. See [Speculative fan-out](https://docs.typesafe.ai/patterns/fan-out) for packing many questions into one request, and [Jev 1.13 jaggedness](https://docs.typesafe.ai/model-jaggedness/jev-1.13) for how accuracy shifts as the state grows.
- **Input:** Jev evaluates natural-language text. Pre-process non-text inputs (images, audio, video, binaries) into text or structured fields before sending them as `state`. See [State](https://docs.typesafe.ai/concepts/state) for supported shapes.

**Rate limits are adjusting dynamically.** We are serving a very large volume of demand, and the limits above can change without notice while we do, as upcoming large GPU deals land and we let in more users. Once things settle down more, we’ll be able to offer more stable limits. Higher limits are available on custom and enterprise plans. Contact <sales@typesafe.ai>.

## Aliases

An alias is a model name that resolves to a versioned model ID. Send it in the `model` field like any other name.

| Alias         | Points to    | Meaning                                                                                                                       |
| ------------- | ------------ | ----------------------------------------------------------------------------------------------------------------------------- |
| `jev-latest`  | `jev-1.13.0` | The most recent stable, official release. The default in our client SDKs, and the name the examples in these docs use.        |
| `jev-preview` | `jev-1.13.0` | The most recent release, whether or not it is an official one. Moves ahead of `jev-latest` when a preview build is available. |

`jev-preview` currently points to the same model as `jev-latest`. There is no preview build available right now.

An alias moves when a new release ships, so the answers behind it can change without a change on your side. The response’s `model` field reports the versioned ID that answered, so you can log which model produced each result. If you have tuned confidence thresholds against a specific version, pin that version’s ID instead of the alias and move to the new one on your own schedule.

## Customizing Jev

Jev is not fine-tuned or LoRA-adapted with customer data. It is trained with [RLCD](https://docs.typesafe.ai/introduction/machine-learning-primer) to return calibrated decisions, and the same weights serve every account. You shape its answers to your domain through the request rather than through per-account weights:

- Put your proprietary content, records, and reference material in the `state` field. See [State](https://docs.typesafe.ai/concepts/state).
- Encode your domain rules and boundary cases in the `instructions` and `criteria` of each question. See [How to build with TypeSafe](https://docs.typesafe.ai/concepts/how-to-build-with-system-one) and [Advanced: structure](https://docs.typesafe.ai/primitives/advanced).
- Decompose broad judgments into atomic questions and combine the outputs in code. See [Composite scoring](https://docs.typesafe.ai/patterns/composite-scoring) and the [AutoResearch cookbook](https://docs.typesafe.ai/cookbooks/autoresearch_feature_discovery) for training a downstream classical model on Jev’s probabilities.

## Language support

Jev accepts natural-language text. English is the primary training language and where accuracy is currently best. Other languages, including CJK scripts, are handled but not equally well; test on your own content before relying on Jev for a non-English workload, and pay close attention to [Confidence](https://docs.typesafe.ai/confidence) when routing.

## Data handling

Jev is not trained on customer requests or responses. See [Legal](https://docs.typesafe.ai/legal) for the Data Processing Agreement, the Privacy Policy, and details on zero data retention (ZDR) for enterprise customers.

## Listing models

`GET /v1/models` returns the names your account can send in the `model` field, with a description and release date for each. It currently lists the aliases. Versioned IDs such as `jev-1.13.0` are accepted by the `model` field whether or not they appear in the list.

```shellscript
curl https://api.typesafe.ai/v1/models \
  -H "Authorization: Bearer $TYPESAFE_API_KEY"
```

```python
from typesafe_sdk import TypeSafeClient
with TypeSafeClient() as client:
    for model in client.models.list().models:
        print(model.name, model.release_date, model.description)
```

```typescript
import { TypeSafeClient } from "@typesafe-ai/sdk";
const client = new TypeSafeClient();
const models = await client.models.list();
for (const model of models) {
  console.log(model.name, model.release_date, model.description);
}
```

[Navigate to header: models](https://docs.typesafe.ai/models#param-models)

array

required

One entry per model or alias.

Show properties

[Navigate to header: name](https://docs.typesafe.ai/models#param-name)

string

required

The model ID or alias, as accepted by the `model` field.

[Navigate to header: description](https://docs.typesafe.ai/models#param-description)

string

required

What the model is for.

[Navigate to header: release_date](https://docs.typesafe.ai/models#param-release-date)

string

required

When the model or alias was released.

See the [Python](https://docs.typesafe.ai/sdk/python/api/clients/sync#typesafe_sdk.Models.list) and [JavaScript](https://docs.typesafe.ai/sdk/javascript/api/interfaces/Models) SDK references for the full method signatures.

Was this page helpful?

[Function: score()](https://docs.typesafe.ai/sdk/javascript/api/functions/score)

[Previous](https://docs.typesafe.ai/sdk/javascript/api/functions/score) [API reference Next](https://docs.typesafe.ai/api)

[github](https://github.com/typesafe-ai) [discord](https://discord.gg/typesafe) [x](https://x.com/typesafeai)

[Powered byThis documentation is built and hosted on Mintlify, a developer documentation platform](https://www.mintlify.com/?utm_campaign=poweredBy&utm_medium=referral&utm_source=ts-docs)

## On this page

- [Current models](https://docs.typesafe.ai/models#current-models)
- [Aliases](https://docs.typesafe.ai/models#aliases)
- [Customizing Jev](https://docs.typesafe.ai/models#customizing-jev)
- [Language support](https://docs.typesafe.ai/models#language-support)
- [Data handling](https://docs.typesafe.ai/models#data-handling)
- [Listing models](https://docs.typesafe.ai/models#listing-models)

[github](https://github.com/typesafe-ai)[discord](https://discord.gg/typesafe)[x](https://x.com/typesafeai)

[Powered byThis documentation is built and hosted on Mintlify, a developer documentation platform](https://www.mintlify.com/?utm_campaign=poweredBy&utm_medium=referral&utm_source=ts-docs)