---
title: "Questions - TypeSafe AI"
date: "2026-09-18T09:14:15.518Z"
description: "Provide state and ask yes/no, choice, and score questions using objects or dictionaries."
url: "https://docs.typesafe.ai/sdk/python/api/types/questions"
publisher: "TypeSafe AI"
lang: "en"
logo_url: "https://docs.typesafe.ai/mintlify-assets/_mintlify/favicons/ts-docs/zg2v0DiYB7xPw0I2/_generated/favicon/android-chrome-192x192.png"
logo_type: "png"
logo_size: 8885
logo_height: 192
logo_width: 192
logo_size_pretty: "8.88 kB"
image_url: "https://ts-docs.mintlify.app/mintlify-assets/_next/image?url=%2F_mintlify%2Fapi%2Fog%3Fdivision%3DTypes%26title%3DQuestions%26description%3DProvide%2Bstate%2Band%2Bask%2Byes%252Fno%252C%2Bchoice%252C%2Band%2Bscore%2Bquestions%2Busing%2Bobjects%2Bor%2Bdictionaries.%26theme%3Df0580ae664a0195833f0555d&w=1200&q=100"
image_type: "png"
image_size: 36028
image_height: 630
image_width: 1200
image_size_pretty: "36 kB"
word_count: 1507
reading_time: "6 min read"
---

[← Voltar ao índice](./README.md)


## Table of Contents

- [State](#state)
- [Question objects](#question-objects)
- [typesafe_sdk.NoulCriteria](#typesafe_sdknoulcriteria)
  - [true](#true)
  - [false](#false)
- [typesafe_sdk.Noul](#typesafe_sdknoul)
  - [instructions](#instructions)
  - [criteria](#criteria)
- [typesafe_sdk.Choice](#typesafe_sdkchoice)
  - [criteria](#criteria-1)
  - [instructions](#instructions-1)
- [typesafe_sdk.Score](#typesafe_sdkscore)
  - [criteria](#criteria-2)
  - [instructions](#instructions-2)
- [typesafe_sdk.Question](#typesafe_sdkquestion)
- [typesafe_sdk.Questions](#typesafe_sdkquestions)
- [Question dictionaries](#question-dictionaries)
- [typesafe_sdk.NoulModel](#typesafe_sdknoulmodel)
  - [type](#type)
  - [instructions](#instructions-3)
  - [criteria](#criteria-3)
- [typesafe_sdk.ChoiceModel](#typesafe_sdkchoicemodel)
  - [type](#type-1)
  - [instructions](#instructions-4)
  - [criteria](#criteria-4)
- [typesafe_sdk.ScoreModel](#typesafe_sdkscoremodel)
  - [type](#type-2)
  - [instructions](#instructions-5)
  - [criteria](#criteria-5)
- [typesafe_sdk.QuestionModel](#typesafe_sdkquestionmodel)
- [On this page](#on-this-page)

---

Types

Provide state and ask yes/no, choice, and score questions using objects or dictionaries.

## State

`state` is the text or JSON object you want to ask questions about. It cannot be `None`, but values inside an object may be `None`.

## Question objects

Use `Noul`, `Choice`, and `Score` to define questions with named arguments.

## typesafe_sdk.NoulCriteria

Bases: `TypedDict`

Optional descriptions of the yes and no outcomes.

See the [noul primitive](https://docs.typesafe.ai/primitives/noul) for details.

### true

`instance-attribute`

```
true: JSONContent | None
```

Description of the yes outcome as text, a JSON object, or an array; `None` leaves it undescribed.

### false

`instance-attribute`

```
false: JSONContent | None
```

Description of the no outcome as text, a JSON object, or an array; `None` leaves it undescribed.

## typesafe_sdk.Noul

`pydantic-model`

Bases: `_Question`, `wire.NoulQuestion`

A yes/no question with optional descriptions for either outcome.

See the [noul primitive](https://docs.typesafe.ai/primitives/noul) for details.

**Show JSON schema:**

Details

```json
{
  "$defs": {
    "JSONContent": {
      "anyOf": [
        {
          "type": "string"
        },
        {
          "additionalProperties": {
            "anyOf": [
              {
                "$ref": "#/$defs/JSONValue"
              },
              {
                "type": "null"
              }
            ]
          },
          "type": "object"
        },
        {
          "items": {
            "anyOf": [
              {
                "$ref": "#/$defs/JSONValue"
              },
              {
                "type": "null"
              }
            ]
          },
          "type": "array"
        }
      ]
    },
    "JSONValue": {
      "anyOf": [
        {
          "type": "string"
        },
        {
          "type": "integer"
        },
        {
          "type": "number"
        },
        {
          "type": "boolean"
        },
        {
          "items": {
            "anyOf": [
              {
                "$ref": "#/$defs/JSONValue"
              },
              {
                "type": "null"
              }
            ]
          },
          "type": "array"
        },
        {
          "additionalProperties": {
            "anyOf": [
              {
                "$ref": "#/$defs/JSONValue"
              },
              {
                "type": "null"
              }
            ]
          },
          "type": "object"
        }
      ]
    },
    "NoulCriteria": {
      "additionalProperties": false,
      "description": "Optional descriptions of the yes and no outcomes.\n\nSee the [noul primitive](https://docs.typesafe.ai/primitives/noul) for details.",
      "properties": {
        "true": {
          "anyOf": [
            {
              "$ref": "#/$defs/JSONContent"
            },
            {
              "type": "null"
            }
          ]
        },
        "false": {
          "anyOf": [
            {
              "$ref": "#/$defs/JSONContent"
            },
            {
              "type": "null"
            }
          ]
        }
      },
      "title": "NoulCriteria",
      "type": "object"
    }
  },
  "additionalProperties": false,
  "description": "A yes/no question with optional descriptions for either outcome.\n\nSee the [noul primitive](https://docs.typesafe.ai/primitives/noul) for details.",
  "properties": {
    "type": {
      "const": "noul",
      "default": "noul",
      "title": "Type",
      "type": "string"
    },
    "instructions": {
      "anyOf": [
        {
          "$ref": "#/$defs/JSONContent"
        },
        {
          "type": "null"
        }
      ],
      "default": null
    },
    "criteria": {
      "anyOf": [
        {
          "$ref": "#/$defs/NoulCriteria"
        },
        {
          "type": "null"
        }
      ],
      "default": null
    }
  },
  "title": "Noul",
  "type": "object"
}
```

Fields:

- `type` (`Literal[‘noul’]`)
- `instructions` (`JSONContent | None`)
- `criteria` (`NoulCriteria | None`)

### instructions

`pydantic-field`

```
instructions: JSONContent | None = None
```

The question to ask, expressed as text, a JSON object, or an array; optional.

### criteria

`pydantic-field`

```
criteria: NoulCriteria | None = None
```

Optional descriptions of the yes and no outcomes.

## typesafe_sdk.Choice

`pydantic-model`

Bases: `_Question`, `wire.ChoiceQuestion`

A question that selects between named alternatives.

See the [choice primitive](https://docs.typesafe.ai/primitives/choice) for details.

**Show JSON schema:**

Details

```json
{
  "$defs": {
    "JSONContent": {
      "anyOf": [
        {
          "type": "string"
        },
        {
          "additionalProperties": {
            "anyOf": [
              {
                "$ref": "#/$defs/JSONValue"
              },
              {
                "type": "null"
              }
            ]
          },
          "type": "object"
        },
        {
          "items": {
            "anyOf": [
              {
                "$ref": "#/$defs/JSONValue"
              },
              {
                "type": "null"
              }
            ]
          },
          "type": "array"
        }
      ]
    },
    "JSONValue": {
      "anyOf": [
        {
          "type": "string"
        },
        {
          "type": "integer"
        },
        {
          "type": "number"
        },
        {
          "type": "boolean"
        },
        {
          "items": {
            "anyOf": [
              {
                "$ref": "#/$defs/JSONValue"
              },
              {
                "type": "null"
              }
            ]
          },
          "type": "array"
        },
        {
          "additionalProperties": {
            "anyOf": [
              {
                "$ref": "#/$defs/JSONValue"
              },
              {
                "type": "null"
              }
            ]
          },
          "type": "object"
        }
      ]
    }
  },
  "additionalProperties": false,
  "description": "A question that selects between named alternatives.\n\nSee the [choice primitive](https://docs.typesafe.ai/primitives/choice) for details.",
  "properties": {
    "type": {
      "const": "choice",
      "default": "choice",
      "title": "Type",
      "type": "string"
    },
    "instructions": {
      "anyOf": [
        {
          "$ref": "#/$defs/JSONContent"
        },
        {
          "type": "null"
        }
      ],
      "default": null
    },
    "criteria": {
      "additionalProperties": {
        "anyOf": [
          {
            "$ref": "#/$defs/JSONContent"
          },
          {
            "type": "null"
          }
        ]
      },
      "title": "Criteria",
      "type": "object"
    }
  },
  "required": [
    "criteria"
  ],
  "title": "Choice",
  "type": "object"
}
```

Fields:

- `type` (`Literal[‘choice’]`)
- `criteria` (`Mapping[str, JSONContent | None]`)
- `instructions` (`JSONContent | None`)

### criteria

`pydantic-field`

```
criteria: Mapping[str, JSONContent | None]
```

Labels mapped to text, object, or array descriptions, or `None` for undescribed labels.

### instructions

`pydantic-field`

```
instructions: JSONContent | None = None
```

The question to ask, expressed as text, a JSON object, or an array; optional.

## typesafe_sdk.Score

`pydantic-model`

Bases: `_Question`, `wire.ScoreQuestion`

A question that assigns a score using an ordered rubric.

See the [score primitive](https://docs.typesafe.ai/primitives/score) for details.

**Show JSON schema:**

Details

```json
{
  "$defs": {
    "JSONContent": {
      "anyOf": [
        {
          "type": "string"
        },
        {
          "additionalProperties": {
            "anyOf": [
              {
                "$ref": "#/$defs/JSONValue"
              },
              {
                "type": "null"
              }
            ]
          },
          "type": "object"
        },
        {
          "items": {
            "anyOf": [
              {
                "$ref": "#/$defs/JSONValue"
              },
              {
                "type": "null"
              }
            ]
          },
          "type": "array"
        }
      ]
    },
    "JSONValue": {
      "anyOf": [
        {
          "type": "string"
        },
        {
          "type": "integer"
        },
        {
          "type": "number"
        },
        {
          "type": "boolean"
        },
        {
          "items": {
            "anyOf": [
              {
                "$ref": "#/$defs/JSONValue"
              },
              {
                "type": "null"
              }
            ]
          },
          "type": "array"
        },
        {
          "additionalProperties": {
            "anyOf": [
              {
                "$ref": "#/$defs/JSONValue"
              },
              {
                "type": "null"
              }
            ]
          },
          "type": "object"
        }
      ]
    }
  },
  "additionalProperties": false,
  "description": "A question that assigns a score using an ordered rubric.\n\nSee the [score primitive](https://docs.typesafe.ai/primitives/score) for details.",
  "properties": {
    "type": {
      "const": "score",
      "default": "score",
      "title": "Type",
      "type": "string"
    },
    "instructions": {
      "anyOf": [
        {
          "$ref": "#/$defs/JSONContent"
        },
        {
          "type": "null"
        }
      ],
      "default": null
    },
    "criteria": {
      "items": {
        "$ref": "#/$defs/JSONContent"
      },
      "title": "Criteria",
      "type": "array"
    }
  },
  "required": [
    "criteria"
  ],
  "title": "Score",
  "type": "object"
}
```

Fields:

- `type` (`Literal[‘score’]`)
- `criteria` (`Sequence[JSONContent]`)
- `instructions` (`JSONContent | None`)

### criteria

`pydantic-field`

```
criteria: Sequence[JSONContent]
```

A nonempty, ordered list of text, object, or array descriptions, one per score from zero.

### instructions

`pydantic-field`

```
instructions: JSONContent | None = None
```

The question to ask, expressed as text, a JSON object, or an array; optional.

## typesafe_sdk.Question

`module-attribute`

```
Question: TypeAlias = (
    Noul | Choice | Score | QuestionModel
)
```

A question object or question dictionary.

## typesafe_sdk.Questions

`module-attribute`

```
Questions: TypeAlias = Mapping[str, Question]
```

Question inputs keyed by the names used to identify their answers.

## Question dictionaries

Question dictionaries include a `type` key: `"noul"`, `"choice"`, or `"score"`. You can mix dictionaries and question objects in the same request.

## typesafe_sdk.NoulModel

Bases: `TypedDict`

A yes/no question dictionary with `type="noul"`.

See the [noul primitive](https://docs.typesafe.ai/primitives/noul) for details.

### type

`instance-attribute`

```
type: Literal['noul']
```

### instructions

`instance-attribute`

```
instructions: NotRequired[JSONContent | None]
```

The question to ask, expressed as text, a JSON object, or an array; optional.

### criteria

`instance-attribute`

```
criteria: NotRequired[NoulCriteria | None]
```

Optional descriptions of the yes and no outcomes.

## typesafe_sdk.ChoiceModel

Bases: `TypedDict`

A choice question dictionary with `type="choice"`.

See the [choice primitive](https://docs.typesafe.ai/primitives/choice) for details.

### type

`instance-attribute`

```
type: Literal['choice']
```

### instructions

`instance-attribute`

```
instructions: NotRequired[JSONContent | None]
```

The question to ask, expressed as text, a JSON object, or an array; optional.

### criteria

`instance-attribute`

```
criteria: Mapping[str, JSONContent | None]
```

Labels mapped to text, object, or array descriptions, or `None` for undescribed labels.

## typesafe_sdk.ScoreModel

Bases: `TypedDict`

A score question dictionary with `type="score"`.

See the [score primitive](https://docs.typesafe.ai/primitives/score) for details.

### type

`instance-attribute`

```
type: Literal['score']
```

### instructions

`instance-attribute`

```
instructions: NotRequired[JSONContent | None]
```

The question to ask, expressed as text, a JSON object, or an array; optional.

### criteria

`instance-attribute`

```
criteria: Sequence[JSONContent]
```

A nonempty, ordered list of text, object, or array descriptions, one per score from zero.

## typesafe_sdk.QuestionModel

`module-attribute`

```
QuestionModel: TypeAlias = (
    NoulModel | ChoiceModel | ScoreModel
)
```

A question dictionary identified by its `type` key.

Was this page helpful?

[Sync client](https://docs.typesafe.ai/sdk/python/api/clients/sync)

[Previous](https://docs.typesafe.ai/sdk/python/api/clients/sync) [Answers and responses Next](https://docs.typesafe.ai/sdk/python/api/types/responses)

[github](https://github.com/typesafe-ai) [discord](https://discord.gg/typesafe) [x](https://x.com/typesafeai)

[Powered byThis documentation is built and hosted on Mintlify, a developer documentation platform](https://www.mintlify.com/?utm_campaign=poweredBy&utm_medium=referral&utm_source=ts-docs)

## On this page

- [State](https://docs.typesafe.ai/sdk/python/api/types/questions#state)
- [Question objects](https://docs.typesafe.ai/sdk/python/api/types/questions#question-objects)
- [typesafe_sdk.NoulCriteria](https://docs.typesafe.ai/sdk/python/api/types/questions#typesafe_sdk.NoulCriteria)
  - [true](https://docs.typesafe.ai/sdk/python/api/types/questions#typesafe_sdk.NoulCriteria.true)
  - [false](https://docs.typesafe.ai/sdk/python/api/types/questions#typesafe_sdk.NoulCriteria.false)
- [typesafe_sdk.Noul](https://docs.typesafe.ai/sdk/python/api/types/questions#typesafe_sdk.Noul)
  - [instructions](https://docs.typesafe.ai/sdk/python/api/types/questions#typesafe_sdk.Noul.instructions)
  - [criteria](https://docs.typesafe.ai/sdk/python/api/types/questions#typesafe_sdk.Noul.criteria)
- [typesafe_sdk.Choice](https://docs.typesafe.ai/sdk/python/api/types/questions#typesafe_sdk.Choice)
  - [criteria](https://docs.typesafe.ai/sdk/python/api/types/questions#typesafe_sdk.Choice.criteria)
  - [instructions](https://docs.typesafe.ai/sdk/python/api/types/questions#typesafe_sdk.Choice.instructions)
- [typesafe_sdk.Score](https://docs.typesafe.ai/sdk/python/api/types/questions#typesafe_sdk.Score)
  - [criteria](https://docs.typesafe.ai/sdk/python/api/types/questions#typesafe_sdk.Score.criteria)
  - [instructions](https://docs.typesafe.ai/sdk/python/api/types/questions#typesafe_sdk.Score.instructions)
- [typesafe_sdk.Question](https://docs.typesafe.ai/sdk/python/api/types/questions#typesafe_sdk.Question)
- [typesafe_sdk.Questions](https://docs.typesafe.ai/sdk/python/api/types/questions#typesafe_sdk.Questions)
- [Question dictionaries](https://docs.typesafe.ai/sdk/python/api/types/questions#question-dictionaries)
- [typesafe_sdk.NoulModel](https://docs.typesafe.ai/sdk/python/api/types/questions#typesafe_sdk.NoulModel)
  - [type](https://docs.typesafe.ai/sdk/python/api/types/questions#typesafe_sdk.NoulModel.type)
  - [instructions](https://docs.typesafe.ai/sdk/python/api/types/questions#typesafe_sdk.NoulModel.instructions)
  - [criteria](https://docs.typesafe.ai/sdk/python/api/types/questions#typesafe_sdk.NoulModel.criteria)
- [typesafe_sdk.ChoiceModel](https://docs.typesafe.ai/sdk/python/api/types/questions#typesafe_sdk.ChoiceModel)
  - [type](https://docs.typesafe.ai/sdk/python/api/types/questions#typesafe_sdk.ChoiceModel.type)
  - [instructions](https://docs.typesafe.ai/sdk/python/api/types/questions#typesafe_sdk.ChoiceModel.instructions)
  - [criteria](https://docs.typesafe.ai/sdk/python/api/types/questions#typesafe_sdk.ChoiceModel.criteria)
- [typesafe_sdk.ScoreModel](https://docs.typesafe.ai/sdk/python/api/types/questions#typesafe_sdk.ScoreModel)
  - [type](https://docs.typesafe.ai/sdk/python/api/types/questions#typesafe_sdk.ScoreModel.type)
  - [instructions](https://docs.typesafe.ai/sdk/python/api/types/questions#typesafe_sdk.ScoreModel.instructions)
  - [criteria](https://docs.typesafe.ai/sdk/python/api/types/questions#typesafe_sdk.ScoreModel.criteria)
- [typesafe_sdk.QuestionModel](https://docs.typesafe.ai/sdk/python/api/types/questions#typesafe_sdk.QuestionModel)

[github](https://github.com/typesafe-ai)[discord](https://discord.gg/typesafe)[x](https://x.com/typesafeai)

[Powered byThis documentation is built and hosted on Mintlify, a developer documentation platform](https://www.mintlify.com/?utm_campaign=poweredBy&utm_medium=referral&utm_source=ts-docs)