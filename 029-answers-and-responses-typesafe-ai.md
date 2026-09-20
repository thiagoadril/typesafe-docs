---
title: "Answers and responses - TypeSafe AI"
date: "2026-09-18T09:14:15.519Z"
description: "Read answers, confidence scores, token usage, and available models returned by the TypeSafe API."
url: "https://docs.typesafe.ai/sdk/python/api/types/responses"
publisher: "TypeSafe AI"
lang: "en"
logo_url: "https://docs.typesafe.ai/mintlify-assets/_mintlify/favicons/ts-docs/zg2v0DiYB7xPw0I2/_generated/favicon/android-chrome-192x192.png"
logo_type: "png"
logo_size: 8885
logo_height: 192
logo_width: 192
logo_size_pretty: "8.88 kB"
image_url: "https://ts-docs.mintlify.app/mintlify-assets/_next/image?url=%2F_mintlify%2Fapi%2Fog%3Fdivision%3DTypes%26title%3DAnswers%2Band%2Bresponses%26description%3DRead%2Banswers%252C%2Bconfidence%2Bscores%252C%2Btoken%2Busage%252C%2Band%2Bavailable%2Bmodels%2Breturned%2Bby%2Bthe%2BTypeSafe%2BAPI.%26theme%3Df0580ae664a0195833f0555d&w=1200&q=100"
image_type: "png"
image_size: 41264
image_height: 630
image_width: 1200
image_size_pretty: "41.3 kB"
word_count: 2304
reading_time: "9 min read"
---

[← Voltar ao índice](./README.md)


## Table of Contents

- [Response](#response)
- [typesafe_sdk.SystemOneResponse](#typesafe_sdksystemoneresponse)
  - [request_id](#request_id)
  - [raw_http_response](#raw_http_response)
  - [model_config](#model_config)
  - [model](#model)
  - [usage](#usage)
  - [answers](#answers)
  - [nouls](#nouls)
  - [choices](#choices)
  - [scores](#scores)
- [typesafe_sdk.Usage](#typesafe_sdkusage)
  - [model_config](#model_config-1)
  - [input_tokens](#input_tokens)
  - [output_tokens](#output_tokens)
- [Answers](#answers)
- [typesafe_sdk.NoulAnswer](#typesafe_sdknoulanswer)
  - [noul](#noul)
  - [model_config](#model_config-2)
- [typesafe_sdk.ChoiceAnswer](#typesafe_sdkchoiceanswer)
  - [choice](#choice)
  - [confidence](#confidence)
  - [probabilities](#probabilities)
  - [model_config](#model_config-3)
- [typesafe_sdk.ScoreAnswer](#typesafe_sdkscoreanswer)
  - [score](#score)
  - [confidence](#confidence-1)
  - [model_config](#model_config-4)
  - [legend](#legend)
  - [probabilities](#probabilities-1)
- [typesafe_sdk.Answer](#typesafe_sdkanswer)
- [Available models](#available-models)
- [typesafe_sdk.ListModelsResponse](#typesafe_sdklistmodelsresponse)
  - [request_id](#request_id-1)
  - [raw_http_response](#raw_http_response-1)
  - [model_config](#model_config-5)
  - [models](#models)
- [typesafe_sdk.ModelMetadata](#typesafe_sdkmodelmetadata)
  - [name](#name)
  - [description](#description)
  - [release_date](#release_date)
- [On this page](#on-this-page)

---

Types

Read answers, confidence scores, token usage, and available models returned by the TypeSafe API.

## Response

## typesafe_sdk.SystemOneResponse

`pydantic-model`

Bases: `Response`

Answers grouped by question type with model and usage metadata.

See [System One](https://docs.typesafe.ai/concepts/system-one) for details.

**Show JSON schema:**

Details

```json
{
  "$defs": {
    "ChoiceAnswer": {
      "description": "A selected label and its probabilities.\n\nSee the [choice primitive](https://docs.typesafe.ai/primitives/choice) for details.",
      "properties": {
        "type": {
          "const": "choice",
          "default": "choice",
          "title": "Type",
          "type": "string"
        },
        "choice": {
          "description": "The name of the choice with the highest probability among the question's criteria.",
          "examples": [
            "angry"
          ],
          "title": "Choice",
          "type": "string"
        },
        "confidence": {
          "description": "Confidence in the selected choice, from 0 to 1. Higher values indicate greater certainty; use lower values to flag uncertain selections for review.",
          "examples": [
            0.9
          ],
          "title": "Confidence",
          "type": "number"
        },
        "probabilities": {
          "additionalProperties": {
            "type": "number"
          },
          "description": "Probability of each choice in criteria, keyed by choice name, from 0 to 1. Shows how likely the alternatives are; values sum to approximately 1.",
          "examples": [
            {
              "angry": 0.8,
              "calm": 0.1,
              "excited": 0.1
            }
          ],
          "title": "Probabilities",
          "type": "object"
        }
      },
      "required": [
        "choice",
        "confidence",
        "probabilities"
      ],
      "title": "ChoiceAnswer",
      "type": "object"
    },
    "NoulAnswer": {
      "description": "A yes/no answer.\n\nSee the [noul primitive](https://docs.typesafe.ai/primitives/noul) for details.",
      "properties": {
        "type": {
          "const": "noul",
          "default": "noul",
          "title": "Type",
          "type": "string"
        },
        "noul": {
          "description": "Probability of a yes answer or a true statement, from 0 to 1. Values near 1 favor yes or true, values near 0 favor no or false, and values near 0.5 indicate uncertainty.",
          "examples": [
            0.98
          ],
          "title": "Noul",
          "type": "number"
        }
      },
      "required": [
        "noul"
      ],
      "title": "NoulAnswer",
      "type": "object"
    },
    "ScoreAnswer": {
      "description": "An expected score with its rubric and probabilities.\n\nSee the [score primitive](https://docs.typesafe.ai/primitives/score) for details.",
      "properties": {
        "type": {
          "const": "score",
          "default": "score",
          "title": "Type",
          "type": "string"
        },
        "score": {
          "description": "Expected score: the probability-weighted average of the rubric levels. May fall between integer levels.",
          "examples": [
            1.7
          ],
          "title": "Score",
          "type": "number"
        },
        "confidence": {
          "description": "Confidence in the score, from 0 to 1. Higher values indicate greater certainty; use lower values to flag uncertain ratings for review.",
          "examples": [
            0.9
          ],
          "title": "Confidence",
          "type": "number"
        },
        "legend": {
          "additionalProperties": {
            "anyOf": [
              {
                "type": "string"
              },
              {
                "additionalProperties": true,
                "type": "object"
              },
              {
                "items": {},
                "type": "array"
              }
            ]
          },
          "title": "Legend",
          "type": "object"
        },
        "probabilities": {
          "additionalProperties": {
            "type": "number"
          },
          "title": "Probabilities",
          "type": "object"
        }
      },
      "required": [
        "score",
        "confidence",
        "legend",
        "probabilities"
      ],
      "title": "ScoreAnswer",
      "type": "object"
    },
    "Usage": {
      "description": "Token counts for a request, when reported by the API.",
      "properties": {
        "input_tokens": {
          "anyOf": [
            {
              "type": "integer"
            },
            {
              "type": "null"
            }
          ],
          "default": null,
          "title": "Input Tokens"
        },
        "output_tokens": {
          "anyOf": [
            {
              "type": "integer"
            },
            {
              "type": "null"
            }
          ],
          "default": null,
          "title": "Output Tokens"
        }
      },
      "title": "Usage",
      "type": "object"
    }
  },
  "description": "Answers grouped by question type with model and usage metadata.\n\nSee [System One](https://docs.typesafe.ai/concepts/system-one) for details.",
  "properties": {
    "model": {
      "title": "Model",
      "type": "string"
    },
    "usage": {
      "$ref": "#/$defs/Usage"
    },
    "answers": {
      "additionalProperties": {
        "discriminator": {
          "mapping": {
            "choice": "#/$defs/ChoiceAnswer",
            "noul": "#/$defs/NoulAnswer",
            "score": "#/$defs/ScoreAnswer"
          },
          "propertyName": "type"
        },
        "oneOf": [
          {
            "$ref": "#/$defs/NoulAnswer"
          },
          {
            "$ref": "#/$defs/ChoiceAnswer"
          },
          {
            "$ref": "#/$defs/ScoreAnswer"
          }
        ]
      },
      "title": "Answers",
      "type": "object"
    }
  },
  "required": [
    "model",
    "usage"
  ],
  "title": "SystemOneResponse",
  "type": "object"
}
```

Config:

- `extra`: `ignore`
- `frozen`: `True`
- `strict`: `True`

Fields:

- `model` (`str`)
- `usage` (`Usage`)
- `answers` (`dict[str, Answer]`)

### request_id

`cached` `property`

```
request_id: str
```

The `x-typesafe-request-id` response header.

### raw_http_response

`property`

```python
raw_http_response: httpx2.Response
```

The underlying `httpx2.Response`, exposing status, headers, and body.

### model_config

`class-attribute` `instance-attribute`

```python
model_config = ConfigDict(
    extra="ignore", frozen=True, strict=True
)
```

### model

`pydantic-field`

```
model: str
```

The model used to answer the request.

### usage

`pydantic-field`

```
usage: Usage
```

Token usage for the request.

### answers

`pydantic-field`

```
answers: dict[str, Answer]
```

All answer objects keyed by question name.

### nouls

`cached` `property`

```
nouls: dict[str, NoulAnswer]
```

Yes/no answers keyed by question name.

### choices

`cached` `property`

```
choices: dict[str, ChoiceAnswer]
```

Choice answers keyed by question name.

### scores

`cached` `property`

```
scores: dict[str, ScoreAnswer]
```

Score answers keyed by question name.

## typesafe_sdk.Usage

`pydantic-model`

Bases: `wire.Usage`

Token counts for a request, when reported by the API.

**Show JSON schema:**

Details

```json
{
  "description": "Token counts for a request, when reported by the API.",
  "properties": {
    "input_tokens": {
      "anyOf": [
        {
          "type": "integer"
        },
        {
          "type": "null"
        }
      ],
      "default": null,
      "title": "Input Tokens"
    },
    "output_tokens": {
      "anyOf": [
        {
          "type": "integer"
        },
        {
          "type": "null"
        }
      ],
      "default": null,
      "title": "Output Tokens"
    }
  },
  "title": "Usage",
  "type": "object"
}
```

Config:

- `extra`: `ignore`
- `frozen`: `True`
- `strict`: `True`

Fields:

- `input_tokens` (`int | None`)
- `output_tokens` (`int | None`)

### model_config

`class-attribute` `instance-attribute`

```python
model_config = ConfigDict(
    extra="ignore", frozen=True, strict=True
)
```

### input_tokens

`pydantic-field`

```
input_tokens: int | None = None
```

Number of input tokens used, or `None` when the API did not report it.

### output_tokens

`pydantic-field`

```
output_tokens: int | None = None
```

Number of output tokens used, or `None` when the API did not report it.

## Answers

## typesafe_sdk.NoulAnswer

`pydantic-model`

Bases: `wire.NoulAnswer`

A yes/no answer.

See the [noul primitive](https://docs.typesafe.ai/primitives/noul) for details.

**Show JSON schema:**

Details

```json
{
  "description": "A yes/no answer.\n\nSee the [noul primitive](https://docs.typesafe.ai/primitives/noul) for details.",
  "properties": {
    "type": {
      "const": "noul",
      "default": "noul",
      "title": "Type",
      "type": "string"
    },
    "noul": {
      "description": "Probability of a yes answer or a true statement, from 0 to 1. Values near 1 favor yes or true, values near 0 favor no or false, and values near 0.5 indicate uncertainty.",
      "examples": [
        0.98
      ],
      "title": "Noul",
      "type": "number"
    }
  },
  "required": [
    "noul"
  ],
  "title": "NoulAnswer",
  "type": "object"
}
```

Config:

- `extra`: `ignore`
- `frozen`: `True`
- `strict`: `True`

Fields:

- `noul` (`float`)
- `type` (`Literal[‘noul’]`)

### noul

`pydantic-field`

```
noul: float
```

Probability of a yes answer or a true statement, from 0 to 1. Values near 1 favor yes or true, values near 0 favor no or false, and values near 0.5 indicate uncertainty.

### model_config

`class-attribute` `instance-attribute`

```python
model_config = ConfigDict(
    extra="ignore", frozen=True, strict=True
)
```

## typesafe_sdk.ChoiceAnswer

`pydantic-model`

Bases: `wire.ChoiceAnswer`

A selected label and its probabilities.

See the [choice primitive](https://docs.typesafe.ai/primitives/choice) for details.

**Show JSON schema:**

Details

```json
{
  "description": "A selected label and its probabilities.\n\nSee the [choice primitive](https://docs.typesafe.ai/primitives/choice) for details.",
  "properties": {
    "type": {
      "const": "choice",
      "default": "choice",
      "title": "Type",
      "type": "string"
    },
    "choice": {
      "description": "The name of the choice with the highest probability among the question's criteria.",
      "examples": [
        "angry"
      ],
      "title": "Choice",
      "type": "string"
    },
    "confidence": {
      "description": "Confidence in the selected choice, from 0 to 1. Higher values indicate greater certainty; use lower values to flag uncertain selections for review.",
      "examples": [
        0.9
      ],
      "title": "Confidence",
      "type": "number"
    },
    "probabilities": {
      "additionalProperties": {
        "type": "number"
      },
      "description": "Probability of each choice in criteria, keyed by choice name, from 0 to 1. Shows how likely the alternatives are; values sum to approximately 1.",
      "examples": [
        {
          "angry": 0.8,
          "calm": 0.1,
          "excited": 0.1
        }
      ],
      "title": "Probabilities",
      "type": "object"
    }
  },
  "required": [
    "choice",
    "confidence",
    "probabilities"
  ],
  "title": "ChoiceAnswer",
  "type": "object"
}
```

Config:

- `extra`: `ignore`
- `frozen`: `True`
- `strict`: `True`

Fields:

- `choice` (`str`)
- `confidence` (`float`)
- `probabilities` (`dict[str, float]`)
- `type` (`Literal[‘choice’]`)

### choice

`pydantic-field`

```
choice: str
```

The name of the choice with the highest probability among the question’s criteria.

### confidence

`pydantic-field`

```
confidence: float
```

Confidence in the selected choice, from 0 to 1. Higher values indicate greater certainty; use lower values to flag uncertain selections for review.

### probabilities

`pydantic-field`

```
probabilities: dict[str, float]
```

Probability of each choice in criteria, keyed by choice name, from 0 to 1. Shows how likely the alternatives are; values sum to approximately 1.

### model_config

`class-attribute` `instance-attribute`

```python
model_config = ConfigDict(
    extra="ignore", frozen=True, strict=True
)
```

## typesafe_sdk.ScoreAnswer

`pydantic-model`

Bases: `wire.ScoreAnswer`

An expected score with its rubric and probabilities.

See the [score primitive](https://docs.typesafe.ai/primitives/score) for details.

**Show JSON schema:**

Details

```json
{
  "description": "An expected score with its rubric and probabilities.\n\nSee the [score primitive](https://docs.typesafe.ai/primitives/score) for details.",
  "properties": {
    "type": {
      "const": "score",
      "default": "score",
      "title": "Type",
      "type": "string"
    },
    "score": {
      "description": "Expected score: the probability-weighted average of the rubric levels. May fall between integer levels.",
      "examples": [
        1.7
      ],
      "title": "Score",
      "type": "number"
    },
    "confidence": {
      "description": "Confidence in the score, from 0 to 1. Higher values indicate greater certainty; use lower values to flag uncertain ratings for review.",
      "examples": [
        0.9
      ],
      "title": "Confidence",
      "type": "number"
    },
    "legend": {
      "additionalProperties": {
        "anyOf": [
          {
            "type": "string"
          },
          {
            "additionalProperties": true,
            "type": "object"
          },
          {
            "items": {},
            "type": "array"
          }
        ]
      },
      "title": "Legend",
      "type": "object"
    },
    "probabilities": {
      "additionalProperties": {
        "type": "number"
      },
      "title": "Probabilities",
      "type": "object"
    }
  },
  "required": [
    "score",
    "confidence",
    "legend",
    "probabilities"
  ],
  "title": "ScoreAnswer",
  "type": "object"
}
```

Config:

- `extra`: `ignore`
- `frozen`: `True`
- `strict`: `True`

Fields:

- `score` (`float`)
- `confidence` (`float`)
- `type` (`Literal[‘score’]`)
- `legend` (`dict[int, str | dict[str, Any] | list[Any]]`)
- `probabilities` (`dict[int, float]`)

### score

`pydantic-field`

```
score: float
```

Expected score: the probability-weighted average of the rubric levels. May fall between integer levels.

### confidence

`pydantic-field`

```
confidence: float
```

Confidence in the score, from 0 to 1. Higher values indicate greater certainty; use lower values to flag uncertain ratings for review.

### model_config

`class-attribute` `instance-attribute`

```python
model_config = ConfigDict(
    extra="ignore", frozen=True, strict=True
)
```

### legend

`pydantic-field`

```
legend: dict[
    int, str | dict[str, Any] | list[Any]
]
```

Rubric descriptions keyed by integer score.

### probabilities

`pydantic-field`

```
probabilities: dict[int, float]
```

Probabilities keyed by integer score.

## typesafe_sdk.Answer

`module-attribute`

```
Answer: TypeAlias = Annotated[
    NoulAnswer | ChoiceAnswer | ScoreAnswer,
    Field(discriminator="type"),
]
```

An answer to a single question, identified by its `type`.

## Available models

## typesafe_sdk.ListModelsResponse

`pydantic-model`

Bases: `Response`

The models available to the account.

**Show JSON schema:**

Details

```json
{
  "$defs": {
    "ModelMetadata": {
      "description": "Metadata describing a single available model.",
      "properties": {
        "name": {
          "title": "Name",
          "type": "string"
        },
        "description": {
          "title": "Description",
          "type": "string"
        },
        "release_date": {
          "title": "Release Date",
          "type": "string"
        }
      },
      "required": [
        "name",
        "description",
        "release_date"
      ],
      "title": "ModelMetadata",
      "type": "object"
    }
  },
  "description": "The models available to the account.",
  "properties": {
    "models": {
      "items": {
        "$ref": "#/$defs/ModelMetadata"
      },
      "title": "Models",
      "type": "array"
    }
  },
  "required": [
    "models"
  ],
  "title": "ListModelsResponse",
  "type": "object"
}
```

Fields:

- `models` (`tuple[ModelMetadata, …]`)

### request_id

`cached` `property`

```
request_id: str
```

The `x-typesafe-request-id` response header.

### raw_http_response

`property`

```python
raw_http_response: httpx2.Response
```

The underlying `httpx2.Response`, exposing status, headers, and body.

### model_config

`class-attribute` `instance-attribute`

```python
model_config = ConfigDict(
    extra="ignore", frozen=True, strict=True
)
```

### models

`pydantic-field`

```
models: tuple[ModelMetadata, ...]
```

The available models.

## typesafe_sdk.ModelMetadata

`pydantic-model`

Bases: `Schema`

Metadata describing a single available model.

**Show JSON schema:**

Details

```json
{
  "description": "Metadata describing a single available model.",
  "properties": {
    "name": {
      "title": "Name",
      "type": "string"
    },
    "description": {
      "title": "Description",
      "type": "string"
    },
    "release_date": {
      "title": "Release Date",
      "type": "string"
    }
  },
  "required": [
    "name",
    "description",
    "release_date"
  ],
  "title": "ModelMetadata",
  "type": "object"
}
```

Fields:

- `name` (`str`)
- `description` (`str`)
- `release_date` (`str`)

### name

`pydantic-field`

```
name: str
```

Model name or alias accepted by a request’s model field.

### description

`pydantic-field`

```
description: str
```

Human-readable description of the model and its capabilities.

### release_date

`pydantic-field`

```
release_date: str
```

Model release date, formatted as YYYY-MM-DD.

Was this page helpful?

[Questions](https://docs.typesafe.ai/sdk/python/api/types/questions)

[Previous](https://docs.typesafe.ai/sdk/python/api/types/questions) [Retries Next](https://docs.typesafe.ai/sdk/python/api/retries)

[github](https://github.com/typesafe-ai) [discord](https://discord.gg/typesafe) [x](https://x.com/typesafeai)

[Powered byThis documentation is built and hosted on Mintlify, a developer documentation platform](https://www.mintlify.com/?utm_campaign=poweredBy&utm_medium=referral&utm_source=ts-docs)

## On this page

- [Response](https://docs.typesafe.ai/sdk/python/api/types/responses#response)
- [typesafe_sdk.SystemOneResponse](https://docs.typesafe.ai/sdk/python/api/types/responses#typesafe_sdk.SystemOneResponse)
  - [request_id](https://docs.typesafe.ai/sdk/python/api/types/responses#typesafe_sdk.SystemOneResponse.request_id)
  - [raw_http_response](https://docs.typesafe.ai/sdk/python/api/types/responses#typesafe_sdk.SystemOneResponse.raw_http_response)
  - [model_config](https://docs.typesafe.ai/sdk/python/api/types/responses#typesafe_sdk.SystemOneResponse.model_config)
  - [model](https://docs.typesafe.ai/sdk/python/api/types/responses#typesafe_sdk.SystemOneResponse.model)
  - [usage](https://docs.typesafe.ai/sdk/python/api/types/responses#typesafe_sdk.SystemOneResponse.usage)
  - [answers](https://docs.typesafe.ai/sdk/python/api/types/responses#typesafe_sdk.SystemOneResponse.answers)
  - [nouls](https://docs.typesafe.ai/sdk/python/api/types/responses#typesafe_sdk.SystemOneResponse.nouls)
  - [choices](https://docs.typesafe.ai/sdk/python/api/types/responses#typesafe_sdk.SystemOneResponse.choices)
  - [scores](https://docs.typesafe.ai/sdk/python/api/types/responses#typesafe_sdk.SystemOneResponse.scores)
- [typesafe_sdk.Usage](https://docs.typesafe.ai/sdk/python/api/types/responses#typesafe_sdk.Usage)
  - [model_config](https://docs.typesafe.ai/sdk/python/api/types/responses#typesafe_sdk.Usage.model_config)
  - [input_tokens](https://docs.typesafe.ai/sdk/python/api/types/responses#typesafe_sdk.Usage.input_tokens)
  - [output_tokens](https://docs.typesafe.ai/sdk/python/api/types/responses#typesafe_sdk.Usage.output_tokens)
- [Answers](https://docs.typesafe.ai/sdk/python/api/types/responses#answers)
- [typesafe_sdk.NoulAnswer](https://docs.typesafe.ai/sdk/python/api/types/responses#typesafe_sdk.NoulAnswer)
  - [noul](https://docs.typesafe.ai/sdk/python/api/types/responses#typesafe_sdk.NoulAnswer.noul)
  - [model_config](https://docs.typesafe.ai/sdk/python/api/types/responses#typesafe_sdk.NoulAnswer.model_config)
- [typesafe_sdk.ChoiceAnswer](https://docs.typesafe.ai/sdk/python/api/types/responses#typesafe_sdk.ChoiceAnswer)
  - [choice](https://docs.typesafe.ai/sdk/python/api/types/responses#typesafe_sdk.ChoiceAnswer.choice)
  - [confidence](https://docs.typesafe.ai/sdk/python/api/types/responses#typesafe_sdk.ChoiceAnswer.confidence)
  - [probabilities](https://docs.typesafe.ai/sdk/python/api/types/responses#typesafe_sdk.ChoiceAnswer.probabilities)
  - [model_config](https://docs.typesafe.ai/sdk/python/api/types/responses#typesafe_sdk.ChoiceAnswer.model_config)
- [typesafe_sdk.ScoreAnswer](https://docs.typesafe.ai/sdk/python/api/types/responses#typesafe_sdk.ScoreAnswer)
  - [score](https://docs.typesafe.ai/sdk/python/api/types/responses#typesafe_sdk.ScoreAnswer.score)
  - [confidence](https://docs.typesafe.ai/sdk/python/api/types/responses#typesafe_sdk.ScoreAnswer.confidence)
  - [model_config](https://docs.typesafe.ai/sdk/python/api/types/responses#typesafe_sdk.ScoreAnswer.model_config)
  - [legend](https://docs.typesafe.ai/sdk/python/api/types/responses#typesafe_sdk.ScoreAnswer.legend)
  - [probabilities](https://docs.typesafe.ai/sdk/python/api/types/responses#typesafe_sdk.ScoreAnswer.probabilities)
- [typesafe_sdk.Answer](https://docs.typesafe.ai/sdk/python/api/types/responses#typesafe_sdk.Answer)
- [Available models](https://docs.typesafe.ai/sdk/python/api/types/responses#available-models)
- [typesafe_sdk.ListModelsResponse](https://docs.typesafe.ai/sdk/python/api/types/responses#typesafe_sdk.ListModelsResponse)
  - [request_id](https://docs.typesafe.ai/sdk/python/api/types/responses#typesafe_sdk.ListModelsResponse.request_id)
  - [raw_http_response](https://docs.typesafe.ai/sdk/python/api/types/responses#typesafe_sdk.ListModelsResponse.raw_http_response)
  - [model_config](https://docs.typesafe.ai/sdk/python/api/types/responses#typesafe_sdk.ListModelsResponse.model_config)
  - [models](https://docs.typesafe.ai/sdk/python/api/types/responses#typesafe_sdk.ListModelsResponse.models)
- [typesafe_sdk.ModelMetadata](https://docs.typesafe.ai/sdk/python/api/types/responses#typesafe_sdk.ModelMetadata)
  - [name](https://docs.typesafe.ai/sdk/python/api/types/responses#typesafe_sdk.ModelMetadata.name)
  - [description](https://docs.typesafe.ai/sdk/python/api/types/responses#typesafe_sdk.ModelMetadata.description)
  - [release_date](https://docs.typesafe.ai/sdk/python/api/types/responses#typesafe_sdk.ModelMetadata.release_date)

[github](https://github.com/typesafe-ai)[discord](https://discord.gg/typesafe)[x](https://x.com/typesafeai)

[Powered byThis documentation is built and hosted on Mintlify, a developer documentation platform](https://www.mintlify.com/?utm_campaign=poweredBy&utm_medium=referral&utm_source=ts-docs)