---
title: "Composite scoring - TypeSafe AI"
date: "2026-09-12T04:42:47.148Z"
description: "Break a complex judgment into atomic scores, combine with weights you control in code."
url: "https://docs.typesafe.ai/patterns/composite-scoring"
publisher: "TypeSafe AI"
lang: "en"
logo_url: "https://docs.typesafe.ai/mintlify-assets/_mintlify/favicons/ts-docs/zg2v0DiYB7xPw0I2/_generated/favicon/android-chrome-192x192.png"
logo_type: "png"
logo_size: 8885
logo_height: 192
logo_width: 192
logo_size_pretty: "8.88 kB"
image_url: "https://ts-docs.mintlify.app/mintlify-assets/_next/image?url=%2F_mintlify%2Fapi%2Fog%3Fdivision%3DPatterns%26title%3DComposite%2Bscoring%26description%3DBreak%2Ba%2Bcomplex%2Bjudgment%2Binto%2Batomic%2Bscores%252C%2Bcombine%2Bwith%2Bweights%2Byou%2Bcontrol%2Bin%2Bcode.%26theme%3Df0580ae664a0195833f0555d&w=1200&q=100"
image_type: "png"
image_size: 38456
image_height: 630
image_width: 1200
image_size_pretty: "38.5 kB"
word_count: 615
reading_time: "3 min read"
---

[← Voltar ao índice](./README.md)


## Table of Contents

- [Example: resume screening](#example-resume-screening)
  - [Step 1: score each dimension independently](#step-1-score-each-dimension-independently)
  - [Step 2: combine with weights](#step-2-combine-with-weights)
- [On this page](#on-this-page)

---

Patterns

Break a complex judgment into atomic scores, combine with weights you control in code.

Oftentimes we want to rank a set of items based on several criteria at once. Composite scoring is an easy way to think about this: break the judgment into independent dimensions, score each one separately, and combine them with weights you control in code.

## Example: resume screening

Let’s imagine you are processing resumes for engineering roles. You want to rank the candidates based on several criteria, and ultimately select the top X candidates for further review.

### Step 1: score each dimension independently

questions

```json
{
  "python_depth": {
    "type": "score",
    "instructions": "How much depth of python experience does this candidate have, based on the supplied resume?",
    "criteria": [
      "No Python experience mentioned",
      "Mentioned but no detail",
      "Used in projects, some specifics",
      "Primary language, multiple projects",
      "Deep expertise: architecture, performance, libraries"
    ]
  },
  "team_leadership": {
    "type": "score",
    "instructions": "How much experience does this candidate have managing or leading engineering teams?",
    "criteria": [
      "No management experience mentioned",
      "Informal mentorship or tech lead role",
      "Led a small team or project",
      "Managed a team with direct reports",
      "Managed multiple teams or an engineering org"
    ]
  },
  "system_design": {
    "type": "score",
    "instructions": "How much experience does this candidate have designing large-scale or distributed systems?",
    "criteria": [
      "No architecture work mentioned",
      "Contributed to design discussions",
      "Designed components of a larger system",
      "Owned architecture of a significant system",
      "Designed systems at scale across multiple domains"
    ]
  },
  "generalist": {
    "type": "score",
    "instructions": "How much evidence is there that this candidate picks up unfamiliar tools, roles, or domains outside their core specialty?",
    "criteria": [
      "Only one domain or role mentioned",
      "Some variety but within a narrow field",
      "Worked across a few different areas or tech stacks",
      "Regularly moved between domains, wore many hats",
      "Track record of ramping up in unfamiliar areas and delivering"
    ]
  }
}
```

[Try it in the Playground →](https://console.typesafe.ai/decode#share/N4IghgDglgagpgJwM5QPYDsQC4QDcCMIANCACaoDGArgLZzoAuAKnAB4PYjEgQKo0QGSFu07AAOugAEU8TwCeDABYYA+qTiClcrFInSZskA3kQ4Oo0gqoE54pMNGo6JAwRUKDNC4tyAEqgA7lI0HkpSGlpSqABmUhCKKtJsZghQ9BRwEahwSFLKUHkUYOikUKRgDFlKYLhwRFIARmBIcKTR0spZSFQQEAA26e22PXQA-HJEDoZyFGlVaWAWANrTjnIAcqhSAAqJGFIpiOnomSH0Xhhtk2szIACyF95tTVQMUujbGgxgUP03BnWIAAqq12s54nwAFZwTxIBpIfjdMwUKAxKAUJAAxwyOQ7NI0MAIeRSfolADmVDA5PqISo-S8AyyvFQMLh2JxcgAInBNIdWKkvK1dESKEooFVPFRbA1UjEbITTrTBo0EET0liQLcALrTAC+UwMciqYBoqn6cDAGmQ4ogFn0QJMZl8ICsNjshqBzlc7k83k1un8QTpYv5qROZ3IuXy4qKJTKFSqUhqdRCJWpznJ0QQpMtZXQWfo5OcvLSBfylpoSAm9kBRjmEuOS2wUlWddxIC2afQ1LgdEYYeOGSy-cu6GutZxRgAkuh5QhCf1zowbEhbdmK6GLVapHwLRygQAZF5gKRIRdLk00DcstkMA93e7pmntU9XqSBCXhMq2Ty7zQ2EID4dk+PYvnSDJQEyFamnkNhSCUhwFiWxzljY5JyDq+qepY8iuH26i5FA5LoPatzGqYdiBq61i2A+cjem4HhjgGRgBMEoShkcaTDtk0YFHGpTlJU1S1FkGgoCRmakkSNIALRWGAFobmUPpQI0bwvEgeFVFWNY4R2DYLFAza6G2U6bNsoripKDDSlkgQ2AA1suY4TgZdwAMIYG46mae0DBfERJERIU1BICgGCah5HY8pJ47tNYAhXIwcFxKeZIIDSObafhNDAUYADygQJQhCBio2Uq2NE6VnsR6BohiJTvLlukFdywWla1fZ5JUZ7FMpYBzKgEUQYyynkIS3qYXWuoGAa0xyDS45qoMrhkXWFHOi2chunRk53IxvosS67EhuEcC4OUvGFDGiBZMofUCVIxRCYmzIYk5eS9FIVBzqafwmTmgWoP08K7qDuQNPBk2-C40RvCgGh3VAOa0cisImQy8j6eRIBGU2Ky3B2hXoP0JJXNkU3SPBe4jk8VykO1IAAMpIlIuDqnAJivO8n4FNIp49ggfDBOicD9EzB1AgA6s5J7DaNp4xHAwRlDEKu2AORKWnBwOwuErhDV9zMAEpwJSmXkyEqB1O0jTc4EvLSLD3oNI51WKiSNRAdLdxMGqFAub+NjtLEu6mtA5Y-RCf0xADgxEmVusIaUEQS1AdRlhhWqzfqkh6iAepAA)

### Step 2: combine with weights

Each dimension is normalized to 0–1 and weighted. The weights give you an easy way to adjust the relative importance of each dimension, without losing any of the nuance of the individual scores.

scoring.py

```python
py      = response.answers["python_depth"].score / 4
lead    = response.answers["team_leadership"].score / 4
arch    = response.answers["system_design"].score / 4
general = response.answers["generalist"].score / 4
# Senior IC
ic_score = (0.40 * py) + (0.10 * lead) + (0.40 * arch) + (0.10 * general)
# Engineering Manager
em_score = (0.15 * py) + (0.40 * lead) + (0.20 * arch) + (0.25 * general)
```

This gives you the ability to rank the candidates based on the composite score. But more importantly, it gives you visibility into how exactly the final score is being calculated. If the highest ranking candidates are not matching your expectations, you can adjust the weights to find the right balance.

Was this page helpful?

[Confidence-gated routing](https://docs.typesafe.ai/patterns/confidence-routing)

[Previous](https://docs.typesafe.ai/patterns/confidence-routing) [Intent routing Next](https://docs.typesafe.ai/patterns/intent-routing)

[github](https://github.com/typesafe-ai) [discord](https://discord.gg/typesafe) [x](https://x.com/typesafeai)

[Powered byThis documentation is built and hosted on Mintlify, a developer documentation platform](https://www.mintlify.com/?utm_campaign=poweredBy&utm_medium=referral&utm_source=ts-docs)

## On this page

- [Example: resume screening](https://docs.typesafe.ai/patterns/composite-scoring#example-resume-screening)
  - [Step 1: score each dimension independently](https://docs.typesafe.ai/patterns/composite-scoring#step-1-score-each-dimension-independently)
  - [Step 2: combine with weights](https://docs.typesafe.ai/patterns/composite-scoring#step-2-combine-with-weights)

[github](https://github.com/typesafe-ai)[discord](https://discord.gg/typesafe)[x](https://x.com/typesafeai)

[Powered byThis documentation is built and hosted on Mintlify, a developer documentation platform](https://www.mintlify.com/?utm_campaign=poweredBy&utm_medium=referral&utm_source=ts-docs)