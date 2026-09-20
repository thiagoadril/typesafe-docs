---
title: "Async client - TypeSafe AI"
date: "2026-09-18T09:14:15.481Z"
description: "Use AsyncTypeSafeClient to ask questions, list models, and configure asynchronous TypeSafe API requests."
url: "https://docs.typesafe.ai/sdk/python/api/clients/async"
publisher: "TypeSafe AI"
lang: "en"
logo_url: "https://docs.typesafe.ai/mintlify-assets/_mintlify/favicons/ts-docs/zg2v0DiYB7xPw0I2/_generated/favicon/android-chrome-192x192.png"
logo_type: "png"
logo_size: 8885
logo_height: 192
logo_width: 192
logo_size_pretty: "8.88 kB"
image_url: "https://ts-docs.mintlify.app/mintlify-assets/_next/image?url=%2F_mintlify%2Fapi%2Fog%3Fdivision%3DClients%26title%3DAsync%2Bclient%26description%3DUse%2BAsyncTypeSafeClient%2Bto%2Bask%2Bquestions%252C%2Blist%2Bmodels%252C%2Band%2Bconfigure%2Basynchronous%2BTypeSafe%2BAPI%2Brequests.%26theme%3Df0580ae664a0195833f0555d&w=1200&q=100"
image_type: "png"
image_size: 37897
image_height: 630
image_width: 1200
image_size_pretty: "37.9 kB"
word_count: 1305
reading_time: "5 min read"
---

[← Voltar ao índice](./README.md)


## Table of Contents

- [typesafe_sdk.AsyncTypeSafeClient](#typesafe_sdkasynctypesafeclient)
  - [models](#models)
  - [system_one](#system_one)
  - [aclose](#aclose)
- [Models resource](#models-resource)
  - [typesafe_sdk.AsyncModels](#typesafe_sdkasyncmodels)
    - [list](#list)
- [On this page](#on-this-page)

---

Clients

Use AsyncTypeSafeClient to ask questions, list models, and configure asynchronous TypeSafe API requests.

## typesafe_sdk.AsyncTypeSafeClient

```
AsyncTypeSafeClient(
    *,
    api_key: str | None = None,
    model: str | None = None,
    retry: RetryPolicy | None = None,
    timeout: float
    | httpx2.Timeout
    | None = None,
    headers: Mapping[str, str] | None = None,
    transport: httpx2.AsyncBaseTransport
    | None = None,
    http_client: httpx2.AsyncClient
    | None = None,
    base_url: str | None = None,
)
```

Create an asynchronous HTTP client for [TypeSafe AI API](https://typesafe.ai/).

Explicit options take precedence over environment variables; empty or whitespace-only environment values are ignored.

**Logging setup**

The SDK logs to the `typesafe_sdk` logger; configure it through standard logging, or set `TYPESAFE_LOG_LEVEL` (`debug`, `info`, …) for a quick default. Secret headers are redacted from log output; request and response bodies are not.

Parameters:

- **`api_key`** (`str | None`, default: `None` ) –

  Required API key; may be set via the `TYPESAFE_API_KEY` environment variable.

- **`model`** (`str | None`, default: `None` ) –

  Model name; may be set via the `TYPESAFE_DEFAULT_MODEL` environment variable.

- **`retry`** (`RetryPolicy | None`, default: `None` ) –

  A `RetryPolicy` controlling retry behavior; see `RetryPolicy` for the available options and their defaults. Pass `RetryPolicy(max_retries=0)` to disable retries.

- **`timeout`** (`float | httpx2.Timeout | None`, default: `None` ) –

  Timeout for HTTP operations. Inherits `http_client.timeout` when supplied, otherwise the SDK default.

- **`headers`** (`Mapping[str, str] | None`, default: `None` ) –

  Additional request headers to set.

- **`transport`** (`httpx2.AsyncBaseTransport | None`, default: `None` ) –

  Optional custom HTTP transport, closed when this SDK client closes.

- **`http_client`** (`httpx2.AsyncClient | None`, default: `None` ) –

  Optional `httpx2.AsyncClient`; mutually exclusive with `transport`. Closed when this SDK client closes.

- **`base_url`** (`str | None`, default: `None` ) –

  API root; may be set via the `TYPESAFE_BASE_URL` environment variable.

Raises:

- `TypeSafeError` –

  The API key is missing or the timeout is invalid.

- `ValueError` –

  Both `transport` and `http_client` are supplied.

Examples:

```python
import asyncio
from typesafe_sdk import AsyncTypeSafeClient, Choice, Noul
async def main() -> None:
    async with AsyncTypeSafeClient() as client:
        result = await client.system_one(
            state="I was charged twice. Please help.",
            questions={
                "billing": Noul(instructions="Is this about billing?"),
                "tone": Choice(
                    instructions="What is the tone?",
                    criteria={"calm": None, "angry": None},
                ),
            },
        )
        assert 0 <= result.nouls["billing"].noul <= 1
        assert result.choices["tone"].choice in {"calm", "angry"}
asyncio.run(main())
```

### models

`cached` `property`

```
models: AsyncModels
```

An accessor for the Models API resource.

Examples:

```python
async def main() -> None:
    async with AsyncTypeSafeClient() as client:
        models = await client.models.list()
```

### system_one

`async`

```
system_one(
    state: JSONContent,
    questions: Mapping[str, Question],
    *,
    model: str | None = None,
    retry: RetryPolicy | None = None,
    timeout: float
    | httpx2.Timeout
    | None = None,
    extra_headers: Mapping[str, str]
    | None = None,
    extra_body: Mapping[str, JSONValue | None]
    | None = None,
    response_model: type[ResponseT]
    | None = None,
) -> SystemOneResponse | ResponseT
```

```
system_one(
    state: JSONContent,
    questions: Mapping[str, Question],
    *,
    model: str | None = None,
    retry: RetryPolicy | None = None,
    timeout: float
    | httpx2.Timeout
    | None = None,
    extra_headers: Mapping[str, str]
    | None = None,
    extra_body: Mapping[str, JSONValue | None]
    | None = None,
    response_model: None = None,
) -> SystemOneResponse
```

```
system_one(
    state: JSONContent,
    questions: Mapping[str, Question],
    *,
    model: str | None = None,
    retry: RetryPolicy | None = None,
    timeout: float
    | httpx2.Timeout
    | None = None,
    extra_headers: Mapping[str, str]
    | None = None,
    extra_body: Mapping[str, JSONValue | None]
    | None = None,
    response_model: type[ResponseT],
) -> ResponseT
```

Answer named questions about text or structured state.

See [System One](https://docs.typesafe.ai/concepts/system-one) for details.

Parameters:

- **`state`** (`JSONContent`) –

  Text, a JSON object, or an array to evaluate. See [state](https://docs.typesafe.ai/concepts/state) for details.

- **`questions`** (`Mapping[str, Question]`) –

  Nonempty mapping of names to question objects or raw dictionaries.

- **`model`** (`str | None`, default: `None` ) –

  Model override; `None` inherits the client default.

- **`retry`** (`RetryPolicy | None`, default: `None` ) –

  An optional retry policy to override the client-level value for this call only.

- **`timeout`** (`float | httpx2.Timeout | None`, default: `None` ) –

  An optional timeout for http operations to override the client-level value for this call only, in seconds.

- **`extra_headers`** (`Mapping[str, str] | None`, default: `None` ) –

  Additional request headers to set.

- **`extra_body`** (`Mapping[str, JSONValue | None] | None`, default: `None` ) –

  Additional top-level request-body fields, shallow-merged over the body after `state`, `model`, and `questions` are set. Merging is last-write-wins: a key that collides with `state`, `model`, or `questions` overrides it, and object values are replaced rather than deep-merged.

- **`response_model`** (`type[ResponseT] | None`, default: `None` ) –

  Optional Pydantic `BaseModel` type describing the JSON response body, including any nested answer models.

Returns:

- `SystemOneResponse | ResponseT` –

  An instance of `response_model`, or `SystemOneResponse` with answers keyed by question

- `SystemOneResponse | ResponseT` –

  name and model and token usage details when no custom model is supplied.

Raises:

- `TypeSafeError` –

  Questions are empty or a score question’s criteria list is empty.

- `TypeSafeAPIError` –

  The server returns an unsuccessful HTTP response after any retries.

- `TypeSafeAPIConnectionError` –

  The request cannot connect or times out after any retries.

- `TypeSafeAPIResponseValidationError` –

  The response body does not match the response model.

Examples:

Create questions with named arguments:

```python
async def main() -> None:
    async with AsyncTypeSafeClient() as client:
        result = await client.system_one(
            state="I was charged twice. Please help.",
            questions={
                "billing": Noul(instructions="Is this about billing?"),
                "tone": Choice(
                    instructions="What is the tone?",
                    criteria={"calm": None, "angry": None},
                ),
            },
        )
        assert 0 <= result.nouls["billing"].noul <= 1
        assert result.choices["tone"].choice in {"calm", "angry"}
```

Pass questions as dictionaries:

```python
async def main() -> None:
    async with AsyncTypeSafeClient() as client:
        result = await client.system_one(
            state={"message": "I was charged twice. Please help."},
            questions={
                "billing": {"type": "noul", "instructions": "Is this about billing?"},
                "tone": {
                    "type": "choice",
                    "instructions": "What is the tone?",
                    "criteria": {"calm": None, "angry": None},
                },
            },
        )
        assert 0 <= result.nouls["billing"].noul <= 1
        assert result.choices["tone"].choice in {"calm", "angry"}
```

### aclose

`async`

```python
aclose() -> None
```

Release network resources and close the underlying HTTP client, including a supplied one.

## Models resource

Reached through [`AsyncTypeSafeClient.models`](https://docs.typesafe.ai/sdk/python/api/clients/async#typesafe_sdk.AsyncTypeSafeClient.models).

### typesafe_sdk.AsyncModels

Access to the models available to the account, reached through `AsyncTypeSafeClient.models`.

#### list

`async`

```
list(
    *,
    retry: RetryPolicy | None = None,
    timeout: float
    | httpx2.Timeout
    | None = None,
    extra_headers: Mapping[str, str]
    | None = None,
) -> ListModelsResponse
```

List the models available to the account.

Parameters:

- **`retry`** (`RetryPolicy | None`, default: `None` ) –

  An optional retry policy to override the client-level value for this call only.

- **`timeout`** (`float | httpx2.Timeout | None`, default: `None` ) –

  Per-operation timeout override; `None` inherits the client setting.

- **`extra_headers`** (`Mapping[str, str] | None`, default: `None` ) –

  Overrides for additional request headers; authentication, SDK identification, and `Accept` remain protected.

Returns:

- `ListModelsResponse` –

  A `ListModelsResponse` whose `models` holds each model’s name, description,

- `ListModelsResponse` –

  and release date.

Raises:

- `TypeSafeAPIError` –

  The server returns an unsuccessful HTTP response after any retries.

- `TypeSafeAPIConnectionError` –

  The request cannot connect or times out after any retries.

Examples:

```python
from typesafe_sdk import AsyncTypeSafeClient
async def main() -> None:
    async with AsyncTypeSafeClient() as client:
        models = await client.models.list()
```

Was this page helpful?

[API reference](https://docs.typesafe.ai/sdk/python/api)

[Previous](https://docs.typesafe.ai/sdk/python/api) [Sync client Next](https://docs.typesafe.ai/sdk/python/api/clients/sync)

[github](https://github.com/typesafe-ai) [discord](https://discord.gg/typesafe) [x](https://x.com/typesafeai)

[Powered byThis documentation is built and hosted on Mintlify, a developer documentation platform](https://www.mintlify.com/?utm_campaign=poweredBy&utm_medium=referral&utm_source=ts-docs)

## On this page

- [typesafe_sdk.AsyncTypeSafeClient](https://docs.typesafe.ai/sdk/python/api/clients/async#typesafe_sdk.AsyncTypeSafeClient)
  - [models](https://docs.typesafe.ai/sdk/python/api/clients/async#typesafe_sdk.AsyncTypeSafeClient.models)
  - [system_one](https://docs.typesafe.ai/sdk/python/api/clients/async#typesafe_sdk.AsyncTypeSafeClient.system_one)
  - [aclose](https://docs.typesafe.ai/sdk/python/api/clients/async#typesafe_sdk.AsyncTypeSafeClient.aclose)
- [Models resource](https://docs.typesafe.ai/sdk/python/api/clients/async#models-resource)
  - [typesafe_sdk.AsyncModels](https://docs.typesafe.ai/sdk/python/api/clients/async#typesafe_sdk.AsyncModels)
  - [list](https://docs.typesafe.ai/sdk/python/api/clients/async#typesafe_sdk.AsyncModels.list)

[github](https://github.com/typesafe-ai)[discord](https://discord.gg/typesafe)[x](https://x.com/typesafeai)

[Powered byThis documentation is built and hosted on Mintlify, a developer documentation platform](https://www.mintlify.com/?utm_campaign=poweredBy&utm_medium=referral&utm_source=ts-docs)