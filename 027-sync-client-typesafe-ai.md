---
title: "Sync client - TypeSafe AI"
date: "2026-09-18T09:14:15.483Z"
description: "Use TypeSafeClient to ask questions, list models, and configure synchronous TypeSafe API requests."
url: "https://docs.typesafe.ai/sdk/python/api/clients/sync"
publisher: "TypeSafe AI"
lang: "en"
logo_url: "https://docs.typesafe.ai/mintlify-assets/_mintlify/favicons/ts-docs/zg2v0DiYB7xPw0I2/_generated/favicon/android-chrome-192x192.png"
logo_type: "png"
logo_size: 8885
logo_height: 192
logo_width: 192
logo_size_pretty: "8.88 kB"
image_url: "https://ts-docs.mintlify.app/mintlify-assets/_next/image?url=%2F_mintlify%2Fapi%2Fog%3Fdivision%3DClients%26title%3DSync%2Bclient%26description%3DUse%2BTypeSafeClient%2Bto%2Bask%2Bquestions%252C%2Blist%2Bmodels%252C%2Band%2Bconfigure%2Bsynchronous%2BTypeSafe%2BAPI%2Brequests.%26theme%3Df0580ae664a0195833f0555d&w=1200&q=100"
image_type: "png"
image_size: 37607
image_height: 630
image_width: 1200
image_size_pretty: "37.6 kB"
word_count: 1266
reading_time: "5 min read"
---

[← Voltar ao índice](./README.md)


## Table of Contents

- [typesafe_sdk.TypeSafeClient](#typesafe_sdktypesafeclient)
  - [models](#models)
  - [system_one](#system_one)
  - [close](#close)
- [Models resource](#models-resource)
  - [typesafe_sdk.Models](#typesafe_sdkmodels)
    - [list](#list)
- [On this page](#on-this-page)

---

Clients

Use TypeSafeClient to ask questions, list models, and configure synchronous TypeSafe API requests.

## typesafe_sdk.TypeSafeClient

```
TypeSafeClient(
    *,
    api_key: str | None = None,
    model: str | None = None,
    retry: RetryPolicy | None = None,
    timeout: float
    | httpx2.Timeout
    | None = None,
    headers: Mapping[str, str] | None = None,
    transport: httpx2.BaseTransport
    | None = None,
    http_client: httpx2.Client | None = None,
    base_url: str | None = None,
)
```

Create an HTTP client for [TypeSafe AI API](https://typesafe.ai/).

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

- **`transport`** (`httpx2.BaseTransport | None`, default: `None` ) –

  Optional custom HTTP transport, closed when this SDK client closes.

- **`http_client`** (`httpx2.Client | None`, default: `None` ) –

  Optional `httpx2.Client`; mutually exclusive with `transport`. Closed when this SDK client closes.

- **`base_url`** (`str | None`, default: `None` ) –

  API root; may be set via the `TYPESAFE_BASE_URL` environment variable.

Raises:

- `TypeSafeError` –

  The API key is missing or the timeout is invalid.

- `ValueError` –

  Both `transport` and `http_client` are supplied.

Examples:

```python
from typesafe_sdk import Choice, Noul, TypeSafeClient
with TypeSafeClient() as client:
    result = client.system_one(
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

### models

`cached` `property`

```
models: Models
```

An accessor for the Models API resource.

Examples:

```python
with TypeSafeClient() as client:
    models = client.models.list()
```

### system_one

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
with TypeSafeClient() as client:
    result = client.system_one(
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
with TypeSafeClient() as client:
    result = client.system_one(
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

### close

```python
close() -> None
```

Release network resources and close the underlying HTTP client, including a supplied one.

## Models resource

Reached through [`TypeSafeClient.models`](https://docs.typesafe.ai/sdk/python/api/clients/sync#typesafe_sdk.TypeSafeClient.models).

### typesafe_sdk.Models

Access to the models available to the account, reached through `TypeSafeClient.models`.

#### list

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
from typesafe_sdk import TypeSafeClient
with TypeSafeClient() as client:
    models = client.models.list()
```

Was this page helpful?

[Async client](https://docs.typesafe.ai/sdk/python/api/clients/async)

[Previous](https://docs.typesafe.ai/sdk/python/api/clients/async) [Questions Next](https://docs.typesafe.ai/sdk/python/api/types/questions)

[github](https://github.com/typesafe-ai) [discord](https://discord.gg/typesafe) [x](https://x.com/typesafeai)

[Powered byThis documentation is built and hosted on Mintlify, a developer documentation platform](https://www.mintlify.com/?utm_campaign=poweredBy&utm_medium=referral&utm_source=ts-docs)

## On this page

- [typesafe_sdk.TypeSafeClient](https://docs.typesafe.ai/sdk/python/api/clients/sync#typesafe_sdk.TypeSafeClient)
  - [models](https://docs.typesafe.ai/sdk/python/api/clients/sync#typesafe_sdk.TypeSafeClient.models)
  - [system_one](https://docs.typesafe.ai/sdk/python/api/clients/sync#typesafe_sdk.TypeSafeClient.system_one)
  - [close](https://docs.typesafe.ai/sdk/python/api/clients/sync#typesafe_sdk.TypeSafeClient.close)
- [Models resource](https://docs.typesafe.ai/sdk/python/api/clients/sync#models-resource)
  - [typesafe_sdk.Models](https://docs.typesafe.ai/sdk/python/api/clients/sync#typesafe_sdk.Models)
  - [list](https://docs.typesafe.ai/sdk/python/api/clients/sync#typesafe_sdk.Models.list)

[github](https://github.com/typesafe-ai)[discord](https://discord.gg/typesafe)[x](https://x.com/typesafeai)

[Powered byThis documentation is built and hosted on Mintlify, a developer documentation platform](https://www.mintlify.com/?utm_campaign=poweredBy&utm_medium=referral&utm_source=ts-docs)