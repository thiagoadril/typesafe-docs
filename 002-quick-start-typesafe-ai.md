---
title: "Quick start - TypeSafe AI"
date: "2026-09-19T04:54:44.597Z"
description: "Prefer to just dive in? Here’s everything you need to get started immediately."
url: "https://docs.typesafe.ai/introduction/quickstart"
publisher: "TypeSafe AI"
lang: "en"
logo_url: "https://docs.typesafe.ai/mintlify-assets/_mintlify/favicons/ts-docs/zg2v0DiYB7xPw0I2/_generated/favicon/android-chrome-192x192.png"
logo_type: "png"
logo_size: 8885
logo_height: 192
logo_width: 192
logo_size_pretty: "8.88 kB"
image_url: "https://ts-docs.mintlify.app/mintlify-assets/_next/image?url=%2F_mintlify%2Fapi%2Fog%3Fdivision%3DIntroduction%26title%3DQuick%2Bstart%26description%3DPrefer%2Bto%2Bjust%2Bdive%2Bin%253F%2BHere%2527s%2Beverything%2Byou%2Bneed%2Bto%2Bget%2Bstarted%2Bimmediately.%26theme%3Df0580ae664a0195833f0555d&w=1200&q=100"
image_type: "png"
image_size: 34858
image_height: 630
image_width: 1200
image_size_pretty: "34.9 kB"
word_count: 992
reading_time: "4 min read"
---

[← Voltar ao índice](./README.md)


## Table of Contents

- [Try it: the Playground](#try-it-the-playground)
- [Call it: the API](#call-it-the-api)
  - [Sample cURL command](#sample-curl-command)
  - [Request body](#request-body)
  - [Response body](#response-body)
- [Code it: the Python SDK](#code-it-the-python-sdk)
- [Vibe it: the agent skill](#vibe-it-the-agent-skill)
- [On this page](#on-this-page)

---

Introduction

Prefer to just dive in? Here’s everything you need to get started immediately.

## Try it: the Playground

1.  **Open the [Playground](https://console.typesafe.ai/playground)** and log in.
2.  **Paste any text** as the state.

Sample state

```text
Hi, I've been trying to connect my Stripe account for 3 days and it keeps failing. I'm losing sales. Please help ASAP.
```

3.  **Add a question.** Try a Noul question: `"Does this message express urgency?"`

```json
{
  "urgency": {
    "type": "noul",
    "instructions": "Does this message express urgency?"
  }
}
```

4.  **Add more questions.** Mix Noul, Choice, and Score in one call and see all results at once.

## Call it: the API

1.  **Get your API key** from the [dashboard](https://console.typesafe.ai/keys)
2.  **Make a POST request** to the API endpoint
3.  **Review the [API Reference](https://docs.typesafe.ai/api)** for all the details.

```http
POST https://api.typesafe.ai/v1/systemone
Authorization: Bearer <API_KEY>
Content-Type: application/json
```

### Sample cURL command

```shellscript
curl -X POST https://api.typesafe.ai/v1/systemone \
  -H "Authorization: Bearer $TYPESAFE_API_KEY" \
  -H "Content-Type: application/json" \
  -d @- <<'EOF'
  {
    "state": "Hi, I've been trying to connect my Stripe account for 3 days and it keeps failing. I'm losing sales. Please help ASAP.",
    "model": "jev-latest",
    "questions": {
      "urgency": {
        "type": "noul",
        "instructions": "Does this message express urgency?"
      }
    }
  }
EOF
```

### Request body

```json
{
  "state": "Hi, I've been trying to connect my Stripe account for 3 days and it keeps failing. I'm losing sales. Please help ASAP.",
  "model": "jev-latest",
  "questions": {
    "department": {
      "type": "choice",
      "instructions": "Which team should handle this",
      "criteria": {
        "billing": "Payment or subscription issues",
        "technical": "Bugs or integration problems",
        "sales": "Pricing or account questions"
      }
    },
    "frustration": {
      "type": "score",
      "instructions": "How frustrated the customer appears",
      "criteria": [
        "Calm, just stating facts",
        "Frustrated but civil",
        "Very angry, strong language"
      ]
    },
    "is_urgent": {
      "type": "noul",
      "instructions": "The message conveys urgency or time-sensitivity"
    }
  }
}
```

### Response body

```json
{
  "model": "jev-latest",
  "answers": {
    "department": {
      "type": "choice",
      "choice": "billing",
      "probabilities": {
        "billing": 0.84,
        "technical": 0.159,
        "sales": 0.001
      },
      "confidence": 0.596
    },
    "frustration": {
      "type": "score",
      "score": 1.035,
      "legend": {
        "0": "Calm, just stating facts",
        "1": "Frustrated but civil",
        "2": "Very angry, strong language"
      },
      "confidence": 0.842
    },
    "is_urgent": {
      "type": "noul",
      "noul": 0.999
    }
  },
  "usage": {
    "input_tokens": 312,
    "output_tokens": 48
  }
}
```

See the [API Reference](https://docs.typesafe.ai/api) for all the details.

## Code it: the Python SDK

1.  **Install the SDK** (requires Python \>= 3.10).

With pip

```shellscript
pip install typesafe-sdk
```

With uv

```shellscript
uv add typesafe-sdk
```

2.  **Use the SDK.** The client reads `TYPESAFE_API_KEY` from the environment and calls `jev-latest` by default.

```python
from typesafe_sdk import Choice, Noul, Score, TypeSafeClient
client = TypeSafeClient()
ticket = "Hi, I've been trying to connect my Stripe account for 3 days and it keeps failing. I'm losing sales. Please help ASAP."
response = client.system_one(
    state=ticket,
    questions={
        "department": Choice(
            instructions="Which team should handle this",
            criteria={
                "billing": "Payment or subscription issues",
                "technical": "Bugs or integration problems",
                "sales": "Pricing or account questions",
            },
        ),
        "frustration": Score(
            instructions="How frustrated the customer appears",
            criteria=[
                "Calm, just stating facts",
                "Frustrated but civil",
                "Very angry, strong language",
            ],
        ),
        "is_urgent": Noul(
            instructions="The message conveys urgency or time-sensitivity",
        ),
    },
)
print(response.answers["department"].choice)  # "billing"
print(response.answers["frustration"].score)  # 1.035
print(response.answers["is_urgent"].noul)     # 0.999
```

See [client SDKs](https://docs.typesafe.ai/sdk) for installation options and detailed usage.

## Vibe it: the agent skill

1.  **[Install the TypeSafe skill](https://docs.typesafe.ai/agent-skill#installation)** using the Claude Code plugin or `npx skills add typesafe-ai/skills --skill typesafe-ai`. You can also [read SKILL.md on GitHub](https://github.com/typesafe-ai/skills/blob/main/skills/typesafe-ai/SKILL.md).

Run these two commands in your terminal:

```shellscript
claude plugin marketplace add typesafe-ai/skills
claude plugin install typesafe@typesafe-ai
```

```shellscript
npx skills add typesafe-ai/skills --skill typesafe-ai
```

Choose your agent when prompted. Installation is project-local by default; add `-g` to install globally.

Paste this prompt into your coding agent:

```text
Install the TypeSafe skill. If you're in Claude Code, run `claude plugin marketplace add typesafe-ai/skills`, then `claude plugin install typesafe@typesafe-ai`. If you're in another agent, run `npx skills add typesafe-ai/skills --skill typesafe-ai` and select your agent. Use one installation method. You can read the skill directly at https://github.com/typesafe-ai/skills/blob/main/skills/typesafe-ai/SKILL.md (raw: https://raw.githubusercontent.com/typesafe-ai/skills/main/skills/typesafe-ai/SKILL.md). Then use the TypeSafe skill when working on this project.
```

2.  **Tell your coding agent** to use the TypeSafe skill as you build!

Coding agent prompt

```text
Let's build a simple CLI that uses the TypeSafe API to evaluate a set of supplied documents on multiple dimensions. Use the TypeSafe skill to understand how to use the TypeSafe API and how to structure the system. Ask me questions about what kinds of documents I want to evaluate and on what dimensions.
```

See the [Agent Skill](https://docs.typesafe.ai/agent-skill) page for more details.

Was this page helpful?

[Introduction](https://docs.typesafe.ai/introduction)

[Previous](https://docs.typesafe.ai/introduction) [System One Next](https://docs.typesafe.ai/concepts/system-one)

[github](https://github.com/typesafe-ai) [discord](https://discord.gg/typesafe) [x](https://x.com/typesafeai)

[Powered byThis documentation is built and hosted on Mintlify, a developer documentation platform](https://www.mintlify.com/?utm_campaign=poweredBy&utm_medium=referral&utm_source=ts-docs)

## On this page

- [Try it: the Playground](https://docs.typesafe.ai/introduction/quickstart#try-it-the-playground)
- [Call it: the API](https://docs.typesafe.ai/introduction/quickstart#call-it-the-api)
  - [Sample cURL command](https://docs.typesafe.ai/introduction/quickstart#sample-curl-command)
  - [Request body](https://docs.typesafe.ai/introduction/quickstart#request-body)
  - [Response body](https://docs.typesafe.ai/introduction/quickstart#response-body)
- [Code it: the Python SDK](https://docs.typesafe.ai/introduction/quickstart#code-it-the-python-sdk)
- [Vibe it: the agent skill](https://docs.typesafe.ai/introduction/quickstart#vibe-it-the-agent-skill)

[github](https://github.com/typesafe-ai)[discord](https://discord.gg/typesafe)[x](https://x.com/typesafeai)

[Powered byThis documentation is built and hosted on Mintlify, a developer documentation platform](https://www.mintlify.com/?utm_campaign=poweredBy&utm_medium=referral&utm_source=ts-docs)