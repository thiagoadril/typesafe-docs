---
title: "TypeSafe Python SDK - TypeSafe AI"
date: "2026-09-18T09:52:54.757Z"
description: "Install the TypeSafe Python SDK and get started with asynchronous or synchronous API calls."
url: "https://docs.typesafe.ai/sdk/python"
publisher: "TypeSafe AI"
lang: "en"
logo_url: "https://docs.typesafe.ai/mintlify-assets/_mintlify/favicons/ts-docs/zg2v0DiYB7xPw0I2/_generated/favicon/android-chrome-192x192.png"
logo_type: "png"
logo_size: 8885
logo_height: 192
logo_width: 192
logo_size_pretty: "8.88 kB"
image_url: "https://ts-docs.mintlify.app/mintlify-assets/_next/image?url=%2F_mintlify%2Fapi%2Fog%3Fdivision%3DPython%2BSDK%26title%3DTypeSafe%2BPython%2BSDK%26description%3DInstall%2Bthe%2BTypeSafe%2BPython%2BSDK%2Band%2Bget%2Bstarted%2Bwith%2Basynchronous%2Bor%2Bsynchronous%2BAPI%2Bcalls.%26theme%3Df0580ae664a0195833f0555d&w=1200&q=100"
image_type: "png"
image_size: 40082
image_height: 630
image_width: 1200
image_size_pretty: "40.1 kB"
word_count: 340
reading_time: "2 min read"
---

[← Voltar ao índice](./README.md)


## Table of Contents

- [Quickstart](#quickstart)
- [Usage](#usage)
- [On this page](#on-this-page)

---

Python SDK

Install the TypeSafe Python SDK and get started with asynchronous or synchronous API calls.

Browse the [Python SDK source on GitHub](https://github.com/typesafe-ai/typesafe-sdk-python).

Asynchronous and synchronous Python clients for the [TypeSafe](https://typesafe.ai/) API. Learn how to use TypeSafe [here](https://docs.typesafe.ai/).

## Quickstart

1.  Install the SDK:

    ```shellscript
    uv add typesafe-sdk
    ```

    ```shellscript
    pip install typesafe-sdk
    ```

2.  Set `TYPESAFE_API_KEY` in your environment (create it [here](https://console.typesafe.ai/))

3.  Call the System One API:

    With [AsyncTypeSafeClient](https://docs.typesafe.ai/sdk/python/api/clients/async):

    ```python
    from typesafe_sdk import AsyncTypeSafeClient, Choice, Noul, Score
    async def main() -> None:
        async with AsyncTypeSafeClient() as client:
            response = await client.system_one(
                state={"document": "I was charged twice. Please fix this ASAP."},
                questions={
                    "billing": Noul(instructions="Is this ticket about billing?"),
                    "tone": Choice(
                        instructions="What is the customer's tone?",
                        criteria={"calm": None, "frustrated": None, "angry": None},
                    ),
                    "urgency": Score(
                        instructions="How urgent is this ticket?",
                        criteria=["can wait", "this week", "today"],
                    ),
                },
            )
        print(response.nouls["billing"].noul)
        print(response.choices["tone"].choice)
        print(response.scores["urgency"].score)
    ```

    With [TypeSafeClient](https://docs.typesafe.ai/sdk/python/api/clients/sync):

    ```python
    from typesafe_sdk import Choice, Noul, Score, TypeSafeClient
    with TypeSafeClient() as client:
        response = client.system_one(
            state={"document": "I was charged twice. Please fix this ASAP."},
            questions={
                "billing": Noul(instructions="Is this ticket about billing?"),
                "tone": Choice(
                    instructions="What is the customer's tone?",
                    criteria={"calm": None, "frustrated": None, "angry": None},
                ),
                "urgency": Score(
                    instructions="How urgent is this ticket?",
                    criteria=["can wait", "this week", "today"],
                ),
            },
        )
    print(response.nouls["billing"].noul)
    print(response.choices["tone"].choice)
    print(response.scores["urgency"].score)
    ```

## Usage

Learn more in the [Usage guide](https://docs.typesafe.ai/sdk/python/usage).

Was this page helpful?

[Client SDKs](https://docs.typesafe.ai/sdk)

[Previous](https://docs.typesafe.ai/sdk) [Usage Next](https://docs.typesafe.ai/sdk/python/usage)

[github](https://github.com/typesafe-ai) [discord](https://discord.gg/typesafe) [x](https://x.com/typesafeai)

[Powered byThis documentation is built and hosted on Mintlify, a developer documentation platform](https://www.mintlify.com/?utm_campaign=poweredBy&utm_medium=referral&utm_source=ts-docs)

## On this page

- [Quickstart](https://docs.typesafe.ai/sdk/python#quickstart)
- [Usage](https://docs.typesafe.ai/sdk/python#usage)

[github](https://github.com/typesafe-ai)[discord](https://discord.gg/typesafe)[x](https://x.com/typesafeai)

[Powered byThis documentation is built and hosted on Mintlify, a developer documentation platform](https://www.mintlify.com/?utm_campaign=poweredBy&utm_medium=referral&utm_source=ts-docs)