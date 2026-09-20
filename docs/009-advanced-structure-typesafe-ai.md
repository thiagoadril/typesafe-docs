---
title: "Advanced: structure - TypeSafe AI"
date: "2026-09-15T00:21:18.995Z"
description: "Instructions, Choice options, Score levels, and Noul criteria all accept JSON structure."
url: "https://docs.typesafe.ai/primitives/advanced"
publisher: "TypeSafe AI"
lang: "en"
logo_url: "https://docs.typesafe.ai/mintlify-assets/_mintlify/favicons/ts-docs/zg2v0DiYB7xPw0I2/_generated/favicon/android-chrome-192x192.png"
logo_type: "png"
logo_size: 8885
logo_height: 192
logo_width: 192
logo_size_pretty: "8.88 kB"
image_url: "https://ts-docs.mintlify.app/mintlify-assets/_next/image?url=%2F_mintlify%2Fapi%2Fog%3Fdivision%3DPrimitives%2B%2528Questions%2529%26title%3DAdvanced%253A%2Bstructure%26description%3DInstructions%252C%2BChoice%2Boptions%252C%2BScore%2Blevels%252C%2Band%2BNoul%2Bcriteria%2Ball%2Baccept%2BJSON%2Bstructure.%26theme%3Df0580ae664a0195833f0555d&w=1200&q=100"
image_type: "png"
image_size: 39600
image_height: 630
image_width: 1200
image_size_pretty: "39.6 kB"
word_count: 1571
reading_time: "6 min read"
---

[← Back to Index](../README.md)

## Last Pages

- [Choice - TypeSafe AI](./006-choice-typesafe-ai.md)
- [Score - TypeSafe AI](./007-score-typesafe-ai.md)
- [Noul - TypeSafe AI](./008-noul-typesafe-ai.md)

## Table of Contents

- [Where structure is allowed](#where-structure-is-allowed)
- [When to structure a question](#when-to-structure-a-question)
- [Structured instructions](#structured-instructions)
- [Structured Choice options](#structured-choice-options)
  - [JSON rubric for boundary clarification](#json-rubric-for-boundary-clarification)
  - [Walking a taxonomy](#walking-a-taxonomy)
- [Structured Score levels](#structured-score-levels)
- [Structured Noul criteria](#structured-noul-criteria)
- [On this page](#on-this-page)

---

Primitives (Questions)

Instructions, Choice options, Score levels, and Noul criteria all accept JSON structure.

System One models are trained to understand structure.

## Where structure is allowed

Every one of these fields is an [`EntryType`](https://docs.typesafe.ai/sdk/javascript/api/type-aliases/EntryType).

| Field                                   | Applies to          | Accepted shape                         |
| --------------------------------------- | ------------------- | -------------------------------------- |
| `instructions`                          | Choice, Score, Noul | `string`, `object`, `array`, or `null` |
| `criteria` values (option descriptions) | Choice              | `string`, `object`, `array`, or `null` |
| `criteria` entries (level descriptions) | Score               | `string`, `object`, `array`, or `null` |
| `criteria.true` and `criteria.false`    | Noul                | `string`, `object`, `array`, or `null` |

## When to structure a question

- **When it helps with clarity.** When a question has multiple parts, putting them in the form of JSON helps with clarity because the keys are labeled.
- **When question needs supporting data.** A schema, a taxonomy, or a database row is already JSON. Use the JSON entirely or pass in the relevant subfields instead of serializing them into a string template.

## Structured instructions

One `field` object describes the field being checked, and each question refers to it by key. The same shape drives a Noul that verifies a value, a Choice that picks one from candidates, and two Scores that place a value on a scale.

request

```json
{
  "state": {
    "source_text": "Invoice #4471 issued March 3, 2026 to Beaver Dam Logistics for $12,840.00, net 30."
  },
  "questions": {
    "invoice_number_is_correct": {
      "type": "noul",
      "instructions": {
        "field": {
          "name": "invoice_number",
          "type": "string",
          "description": "The identifier printed on the invoice."
        },
        "extracted_value": "4471",
        "question": "Does `extracted_value` match the `field` as it appears in `source_text`?"
      }
    },
    "customer_name": {
      "type": "choice",
      "instructions": {
        "field": {
          "name": "customer_name",
          "type": "string",
          "description": "The organization the invoice was issued to."
        },
        "question": "Which option is the value of `field` in `source_text`?"
      },
      "criteria": {
        "Beaver Logistics": null,
        "Dam Logistics": null,
        "Beaver Dam Logistics": null,
        "Beaver": null,
        "Dam": null
      }
    },
    "amount_due": {
      "type": "score",
      "instructions": {
        "field": {
          "name": "amount_due",
          "type": "number",
          "unit": "USD",
          "description": "The total the invoice asks to be paid."
        },
        "question": "How large is the `field` value in `source_text`?"
      },
      "criteria": [
        "Under $1,000",
        "$1,000 to $10,000",
        "$10,000 to $100,000",
        "$100,000 to $1,000,000",
        "Over $1,000,000"
      ]
    },
    "payment_terms": {
      "type": "score",
      "instructions": {
        "field": {
          "name": "payment_terms",
          "type": "integer",
          "unit": "days",
          "description": "Days allowed for payment, from terms such as \"net 30\"."
        },
        "question": "How many days does the `field` in `source_text` allow for payment?"
      },
      "criteria": [
        "Due on receipt",
        "Net 10",
        "Net 30",
        "Net 60",
        "Net 90"
      ]
    }
  }
}
```

[Try it in the Playground →](https://console.typesafe.ai/decode#share/N4IghgDglgagpgJwM5QPYDsQC4QDcCMIANCACaoDGArgLZzoAuAKnAB4PYjAA66ABH24gkqKggpwA+gzYMhWQSACS6XKigS+AYgAsOgOz4+UJEipxSfALJhxACz4BmInwBMABlcA2Pg1R8AITgwXEQ+ABEwGj4AGVQAcxMGDSQ+ADNUBD4AEnxXIgAOHXcAOnd3F3Q4BidSoV4AX2IQCARUGggGJBZ2Th5+RShVdQlJdFoAI0RJE0kKTIQ4CjlsPn6BASEGAE8IOHlFdFEAGyEiXg3B9CQGBCpltGuD9cvFNKg4Y9Jni9fNkHQUX2qyEQzUGik4xoUwQZ1+fy2u2BCiENwQQ3icIGCLIcCQFHRnUeByETDscGMpHoyXeYVaQxklgwvnJxmGEJK9WxGwa525-1kCDAywsklwYGO5hJID0hixOIAjuYbsSQSBwqg8XwAAaC4WMsUS8zavg0MAMCgOBis7W0r4msCpKA1SB7WxO-jakRiUYydjagD8XMuDV+vN+QmoN3a00BdB+3MRe2llpGwL5l1B11u92SGCQCZxdu+qxeOLjyMUUb8dAQYyB8r+ih2ybVaIxjZxVPxhLz6GlZIpmXiYHQUAAXubHiyKWC03wAO6O4ymcyWPyckDwnkZ15CJV4vvSgDqdg0DlQROZJhnfHFkqHaR1xZNQx13vEUj9DEDwZ328jdEZHRMBCz3EAghCMI4kSFUKALVZxmOY5d0zdUoliBIkhSA4kJQ7d-kg0IskiaIYOw+DcKoZDUI2IQiMQKiaIIxRSKY05uVDAZwwGIQolERhJFIKVSwAkAW0rVF5kWTsrjRXNHgQhQyzokBizA8sGzVfiqEE4T0xY-4JOlKEYVktDdOdaUAFUAGVwnM1TuwJKAr37NVB18VAGAlW85whPhHQAa1SPw+CmPgIDAKBSE3FieMVZUjzVAAJVAFz4Y5bHiWdQptF87yNWdPQ-X1ZF-LdONowDnUQKBQNWABtFihGs9AqSyXIiHKdxHKELqeq8nJ8AqHq+pAXJRvKIbJqm3riBaiaRrmmb8G68p1vm2j-gAeWI4bNs2v8BAAXTDXchCi7Y6EE4CaCUtYxOMttpIMxMQCGeSHnzDTVPU0T+VUitpSum6GGkRB7scoykWlBk4By2EFsB-5LJWFEyDAbYEO2py8RctzpUibHAuQ9KLHSTJIqxsGXDSNpoju1IzEtQLUm4DmAWqWoOaEOLAYS8CDxVDBpTSjKzXQbY+FILHUnILVrQpW0PntNl31ET8If9UnjnSymslB6kg0qkNqpAFzgPqg5msBoRwnMPhmUWCRXJWXGhAAOW5kbxu9mpHC2xb-b4Lwg7tkAQ4ATnm7czu4xpmiQT4lkZKxUCpY4kGwRqQAAKzgXAAFospkG4QBOhogA)

In code, you could loop over the potential records and build one of these questions per field, all sent in a single call. The [SDE cascade cookbook](https://docs.typesafe.ai/cookbooks/sde_cascade) does something similar to this.

Arrays work too. Use one when the instruction is a list of things to check or to compare:

```json
"instructions": {
  "question": "Does the claimed sender identity conflict with the sending domain?",
  "compare": ["ticket.sender.display_name", "ticket.sender.email"],
  "focus": "Compare the named organization with the email domain."
}
```

## Structured Choice options

A Choice option description can be a structured object as well.

### JSON rubric for boundary clarification

request

```json
{
  "state": "I ordered the standing desk two weeks ago and tracking still says label created. Was I even charged?",
  "questions": {
    "department": {
      "type": "choice",
      "instructions": {
        "question": "Which team should handle this message?",
        "focus": "Classify the customer's primary request, not every topic mentioned."
      },
      "criteria": {
        "billing": {
          "what": "Charges, invoices, refunds, or subscriptions",
          "not_for": "Order tracking or account access",
          "examples": [
            "I was charged twice",
            "Where is my refund?"
          ]
        },
        "orders": {
          "what": "Order status, delivery, cancellation, or returns",
          "not_for": "Charges or account access",
          "examples": [
            "Where is my package?",
            "Cancel my order"
          ]
        },
        "account": {
          "what": "Login, password, profile, or security",
          "not_for": "Charges or delivery",
          "examples": [
            "I can't log in",
            "Change my email"
          ]
        }
      }
    }
  }
}
```

[Try it in the Playground →](https://console.typesafe.ai/decode#share/N4IghgDglgagpgJwM5QPYDsQC4QDcCMIANCACaoDGArgLZzoAuAKnAB4PYgCSABKgqURxSPBgAs4PJAzDpSUdAHMegpAGtRAd1Q9NcOGqQ8winbJEMEYCmoXLpUADaOpYAJ5HHYAEZwXFBDgwBmEAOh4AdTAjXjhceh4KMTAERWEAfmIQCARUGggGJBZ2TmAAHXQeHjKyOAgUhjpGGqwecsqq6pAGNwg4Fq6k1CgKfuIKzq6FaQQqCgY0dCQB9smqmoBHKjgHDAGaiLERsVEgmikxVCpHEWS5R0lxKCM6JCQTOHSaogm1moAzShUZbYLoAYS8byg-zcogkiWBDDyiAA5EYclAaClYYEtjsGEQeOhUAweHFELCkdAKDwmgsMGEar8qgBfH4ddYgAJQEIIKBgFbMzo1bxORx2QUcv4gTTJBj7EBg5KpHaEhS4YajJCEwL-KhybV8BBSKjeJDcgqLEHstbCkDEhgAfUBCAVAHkBIhRFYbHYjcYKBQrowA1rrULJjU2GB8g8Qa0ANoR6W8TTRRLKtIWTQjMY2212w5CHjPWk4uB6uRfEDJqoAXWTbOTNX4gmQkoLXVlwXdnuN0mCwMJgnF8QQbkJFFko2cwUWhP4PECDCoCCW31rXQdzv4CqVKTSRkX1iD+tJJ524alkZA0djOwGSev0qLgRLL1h9RsH2r+c7NTBac-DLI02yZZ960bP87RPYN5VBVYCxqbt4NaGoABlUEUBRCXqN5tAEXDcn+Jw4AXfs4GoPkeg3CCtxJHdXVBADMx2f0RygMc3Fo-9b1YGMIDjR9N05Xgp3QFFSUcLCS3QHjO3BO40hAuAsSccDOwbZ8WSFHSOj0lksiQPxKJCUgAFlUBHJBsATEAACs4gAWi8EJpBAOsWSAA)

The example tells the model what each option does and does *not* cover. It sharpens the boundary between options.

### Walking a taxonomy

To classify into a deep taxonomy, ask one Choice per level and walk the tree in code. At each step the options are the children of the current node, and each option’s value is the child’s tree. Doing so lets the model see what lives under a branch before committing to it, which matters when the item belongs to a leaf whose name is not obvious from the branch name alone.

Here the state is a product listing and the first question picks a top-level department.

request

```json
{
  "state": "32oz plastic bottle with a flip straw lid. Fits most bike cages.",
  "questions": {
    "department": {
      "type": "choice",
      "instructions": "Which top-level department does this product belong to?",
      "criteria": {
        "Sporting Goods": {
          "Cycling": [
            "Bike Bottles & Cages",
            "Bike Lights",
            "Helmets"
          ],
          "Fitness": [
            "Yoga Mats",
            "Resistance Bands"
          ],
          "Outdoor": [
            "Tents",
            "Sleeping Bags",
            "Hydration Packs"
          ]
        },
        "Home & Kitchen": {
          "Drinkware": [
            "Water Bottles",
            "Travel Mugs",
            "Tumblers"
          ],
          "Cookware": [
            "Pots & Pans",
            "Bakeware"
          ]
        },
        "Baby & Toddler": [
          "Sippy Cups",
          "Bottle Warmers",
          "Bibs"
        ]
      }
    }
  }
}
```

[Try it in the Playground →](https://console.typesafe.ai/decode#share/N4IghgDglgagpgJwM5QPYDsQC4QDcCMIANCACaoDGArgLZzoAuAKnAB4PYgDMATKgF4ACCABswSBlAqCARqgYMRcQQHcoDABaCwggGYioEQRIRgVgg6QB0ggGLqkgmqgmyoAa2UUwAczhIrYhAIBFQaCAYkFnZOYAAddEFBOLI4CDAEBjpGFKxBeMSk5JAGAE8IOFziig1UKUriBKLiqHQTKgpJDCQqlIB1DSktBlQIAFolXDgRQVI0jKz6BlnUf0FNKEcQ1FIO5ZlpjB911AB+FKImopSKBHVEKDAqguaklIBlCFRM1uOAcVQOx62HyV1exQAwqUKAZ0D4qgBtMHg4oAIQ8ylR8kUawAZIIIb5-BdkeCUujPIIADJQHwaSIkwoo4oACWmdAZIFJRQAupcma8UvYGOh-MC8kiBWSQABNVA+HQAWTAnP5zLeIAASv5NgwwOgKJj9aRgdyknyzcUAPJUBjkb6Iy0aliMYFq9UfJRpX6CVG+N1O1mlUimLqJAAKYAo7lNUt53IAvu7mikWWFlPiANLqGr0Z6WlIAETu6HcKgyDQlgf6KsQvuxSgDcZTICYpimM0VVB8TfVxSYtBkSmQKUtFubkMBZYrjonGvD8kc+MjbUZffJYE85YQDTHieT1xAfpkpUE+KYO1Iw9nzI+hggp4hVAgvZR5Ibyj6GToI8aE-JUAyLG4I8siCZXOB6AJkESDTHAnRwKQio7NMSDYAiIAAFZwLgEy1hIIA8gmQA)

The bottle plausibly fits under two departments. Showing the subtrees lets the model see that both `Sporting Goods > Cycling > Bike Bottles & Cages` and `Home & Kitchen > Drinkware > Water Bottles` exist, and weigh the listing’s emphasis on bike cages against everyday drinkware. The `probabilities` on this answer tell you whether the split is close enough to explore both branches.

Once a department is chosen, ask the next Choice with that department’s children as the options and their subtrees as the values, and repeat until you reach a leaf. In code this could be a loop over a nested dict, where each question’s `criteria` is simply the current node. The [Hierarchical Classification cookbook](https://docs.typesafe.ai/cookbooks/hierarchical_classification) shows an example of a similar walk of the tree, including a beam search that keeps several candidate paths alive when the probabilities are close.

Subtrees can get large. If a branch is too large, trim the value to its direct children and a sample of leaves.

## Structured Score levels

Each entry in a Score `criteria` array can be an object.

request

```json
{
  "state": "Fixed the null check in the payment handler. Also refactored the retry loop while I was in there, and bumped the SDK version since the old one had that timeout bug.",
  "questions": {
    "pr_scope": {
      "type": "score",
      "instructions": {
        "question": "How focused is this pull request description on a single change?",
        "note": "Judge the number of independent changes, not the size of any one change."
      },
      "criteria": [
        {
          "summary": "One change, clearly stated",
          "signals": [
            "A single fix or feature",
            "Nothing described as \"also\" or \"while I was in there\""
          ]
        },
        {
          "summary": "One main change plus a small related tweak",
          "signals": [
            "A primary change and one minor adjacent edit",
            "The tweak supports the main change"
          ]
        },
        {
          "summary": "Several independent changes bundled together",
          "signals": [
            "Two or more unrelated fixes or features",
            "Changes that could each be their own PR"
          ]
        }
      ]
    }
  }
}
```

[Try it in the Playground →](https://console.typesafe.ai/decode#share/N4IghgDglgagpgJwM5QPYDsQC4QDcCMIANCACaoDGArgLZzoAuAKnAB4PYgBiUrcpAAgYALOAPRUANpIEVRFANYCo6IaIEQwATzqMBwsOlKTEAOgEBBSUlQCEcAGZgKDVPcEix9hgi0DJqKgQAgDuwlAmAgCSoWBIyqqe9kQChoIARrQQ-GpiAMoAIgDSAriIKBgCKOgUYp4CqJKCGGIGHgYMQlB0qFSdmQDmpsQgEAioNBAMSCzsnMAAOqoCC6MIAPpIFEFwq1gCi8sCKyAMWtl7J1tuu8RLx8erKkg+VC5o6EiXhw8PqwCOVDgLw+l1WAAlUCEBA5KFQkDkoPEREiNFIZPZAcDOqRgRQEFAph8GqowFUVANInJDAM4AB+VZEe6-E7oVAMW77VYAKSopFpuXEtHSiAaDgSuOyRnonWp6FpSBSbM69RQAC8xKhxYY-C1ZAZ5XBTKtmccAL5Mo4nfFQDkEsCXADapoePxZjxASFoNDAvjBIAA8ugxHLaSkKCZfZI-C8wBzSIyXb9VigBugwNYnUmWasLOT5ZEHLwGggYXA41R7Imre7VgA5dnheUCXFbAkiwRxFYLVYZmw91Yl7urMIRMQxEJdlS5Ks9kAmmsPAC62Yt2bdtc93t9Wn9QbEPunobEEEk8NSVR90jscEkcZyDBC5YU1fdHtT6cz2AEzsXyZAeZjN0O76jSYhpCSB4qG4qSkAAVs4MoCPwtqvm+HpMOoj7PlUVAQBAbjTIKh6qMeC7oSui5rouG45luNA+n636rHkcBlAgGYSnAUq4nox7xJkRgmB4qC0kkaGbh+fZZn+fwgEwIS2DBNA3AIVDoPYd7xjCvDAkODjlgwlbAhJb6rAAwgaCpqHGsi9E0yHOMIAgirkUCllCqgAAoAErkW+lHumaLqBQIwXoGaIwIiYLj8AAsqguLWNgjogHBbEALRadiIBLmaQA)

## Structured Noul criteria

Noul `criteria` is optional, and when the yes/no boundary is subtle, structured `true` and `false` descriptions let you pin it down with a definition and examples on each side.

request

```json
{
  "state": {
    "sender": {
      "display_name": "Beaver Dam Builders Ltd.",
      "email": "donotreply@payroll.example"
    },
    "message": "Your Q3 bonus is ready. Reply with your login password so we can verify your identity and release the funds."
  },
  "questions": {
    "requests_credentials": {
      "type": "noul",
      "instructions": {
        "question": "Does the `message` ask the recipient to disclose a sensitive credential?",
        "inspect": "message",
        "focus": "Look for a request to send the credential itself, not a request to change or reset it."
      },
      "criteria": {
        "true": {
          "what": "Asks the recipient to reply with, type, or send a password, PIN, one-time code, or other security sensitive answer",
          "examples": [
            "Reply with your password",
            "Send us the 6-digit code you just received"
          ]
        },
        "false": {
          "what": "No sensitive credential is requested",
          "examples": [
            "Reset your password from the settings page",
            "Your statement is ready"
          ]
        }
      }
    }
  }
}
```

[Try it in the Playground →](https://console.typesafe.ai/decode#share/N4IghgDglgagpgJwM5QPYDsQC4QDcCMIANCACaoDGArgLZzoAuAKnAB4PYjAA66ABH24gk9UoiFY+PfgMFkoSCABswATwD66MHQlyAQnDC5EfACLa+eqlCVjkfADINSAOiFFesuXBpgbuoXJ0VAYEOGVVAAEINQRUJSUXNm1lOCFPPgBfDxkhOiQkMABzNOw5AE1UKgQ+AEUAZj4AIwwqJD4FPjCwUlUXPgAlcKVVPgB3KAYACz5VKpqlVCKofhiCsdQEUj4kVHG4PgowfmMEKAAzUbnqjrFGSdHj7bClQxE+aYPzqnRSJDcQLxMsQQBA4jQIAwkCx2JxpAIhGEAI5UOBIKHqChhO4MKBgJRIXTw2RCBiqCClSRCYJUJTuDIIkArdEIKgUXEYQllYleIQotEc9ABECmVBoj5TA4AA3yhRKUr4YCQAGsJQcwhQoNB6AwPntSAoKIt3mAdvQULjjIdsTq8UoAPz0mS8pnoRRwdnC2XFUo5LyM86UNrChyoVCqwM1U3I1HovVm35q61wHF2jpQuBKc5EPjBXXRuD8uMMPYUKbHEp8TZdNFwXWTAEMrJ+kkgLGTRB4olNxmhVHd53+oRjcsMYUAQRV7U+Nc12sY8bCEXGkymObJFJz1ZEidNayQGy2OYACgBJAByW-QcAAtLi6IdUGItzUQpKaiJqGcyQmLVArccB7iMQPatskEKvFykgANqgS6QzLhM0yzPMfD7oepBOv6Q4gAAyqIfBtEmABsN4GssuoUE+BzXHwABWbS6hqcD-im6SDl4AC6oHZKBQjnPiIgDthjIjmAY5lEI557Duf5WliKa2viHTtDGApsSBHFgawKSQbosFafBta6tcNToZs2znOCSYiAwuLoEU7QxCUWEiYylQ3Oi4k+DqKk1j0qjsW53FaZkTZhTIEXAiQIivOyKYALLUQS2DQSAdFwLgN4qAwAogJxmRAA)

Was this page helpful?

[Noul](https://docs.typesafe.ai/primitives/noul)

[Previous](https://docs.typesafe.ai/primitives/noul) [AI primer Next](https://docs.typesafe.ai/introduction/machine-learning-primer)





## Next Page

- [AI primer - TypeSafe AI](./010-ai-primer-typesafe-ai.md)
- [Confidence - TypeSafe AI](./011-confidence-typesafe-ai.md)
- [How to build with TypeSafe - TypeSafe AI](./012-how-to-build-with-typesafe-typesafe-ai.md)




