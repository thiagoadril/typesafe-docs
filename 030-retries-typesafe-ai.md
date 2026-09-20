---
title: "Retries - TypeSafe AI"
date: "2026-09-15T18:15:54.317Z"
description: "Configure retries with RetryPolicy — attempt count, retryable statuses, backoff, and retry headers handling."
url: "https://docs.typesafe.ai/sdk/python/api/retries"
publisher: "TypeSafe AI"
lang: "en"
logo_url: "https://docs.typesafe.ai/mintlify-assets/_mintlify/favicons/ts-docs/zg2v0DiYB7xPw0I2/_generated/favicon/android-chrome-192x192.png"
logo_type: "png"
logo_size: 8885
logo_height: 192
logo_width: 192
logo_size_pretty: "8.88 kB"
image_url: "https://ts-docs.mintlify.app/mintlify-assets/_next/image?url=%2F_mintlify%2Fapi%2Fog%3Fdivision%3DTypes%26title%3DRetries%26description%3DConfigure%2Bretries%2Bwith%2BRetryPolicy%2B%25E2%2580%2594%2Battempt%2Bcount%252C%2Bretryable%2Bstatuses%252C%2Bbackoff%252C%2Band%2Bretry%2Bheaders%2Bhandling.%26theme%3Df0580ae664a0195833f0555d&w=1200&q=100"
image_type: "png"
image_size: 36053
image_height: 630
image_width: 1200
image_size_pretty: "36.1 kB"
word_count: 609
reading_time: "3 min read"
---

[← Voltar ao índice](./README.md)


## Table of Contents

- [typesafe_sdk.RetryPolicy](#typesafe_sdkretrypolicy)
  - [max_retries](#max_retries)
  - [backoff_initial](#backoff_initial)
  - [backoff_max](#backoff_max)
  - [backoff_jitter](#backoff_jitter)
  - [http_statuses](#http_statuses)
  - [respect_retry_after](#respect_retry_after)
  - [api_connection_error](#api_connection_error)
  - [api_timeout_error](#api_timeout_error)
  - [exceptions](#exceptions)
  - [predicate](#predicate)
  - [timeout](#timeout)
- [On this page](#on-this-page)

---

Types

Configure retries with RetryPolicy — attempt count, retryable statuses, backoff, and retry headers handling.

## typesafe_sdk.RetryPolicy

`dataclass`

```
RetryPolicy(
    max_retries: int = 2,
    backoff_initial: float = 0.5,
    backoff_max: float = 5.0,
    backoff_jitter: float = 0.25,
    http_statuses: set[int] = (
        lambda: {408, 429, *range(500, 600)}
    )(),
    respect_retry_after: bool = True,
    api_connection_error: bool = True,
    api_timeout_error: bool = True,
    exceptions: set[
        type[BaseException]
    ] = set(),
    predicate: Callable[[BaseException], bool]
    | None = None,
    timeout: float | None = 30.0,
)
```

Configuration for SDK retry behavior.

Examples:

```python
from typesafe_sdk import RetryPolicy, TypeSafeClient
client = TypeSafeClient(
    retry=RetryPolicy(
        max_retries=3, timeout=10.0, http_statuses={429, 500, 502, 503, 504}
    )
)
```

### max_retries

`class-attribute` `instance-attribute`

```
max_retries: int = 2
```

Maximum retries after the initial attempt; `0` disables retries.

### backoff_initial

`class-attribute` `instance-attribute`

```
backoff_initial: float = 0.5
```

First backoff delay in seconds, doubled each attempt up to `backoff_max`; zero disables backoff.

### backoff_max

`class-attribute` `instance-attribute`

```
backoff_max: float = 5.0
```

Maximum backoff delay in seconds; zero disables backoff.

### backoff_jitter

`class-attribute` `instance-attribute`

```
backoff_jitter: float = 0.25
```

Fraction of each backoff delay randomly subtracted, between 0 and 1.

### http_statuses

`class-attribute` `instance-attribute`

```
http_statuses: set[int] = field(
    default_factory=lambda: {
        408,
        429,
        *range(500, 600),
    }
)
```

HTTP status codes that are retried.

### respect_retry_after

`class-attribute` `instance-attribute`

```
respect_retry_after: bool = True
```

Whether to honor `Retry-After` and `retry-after-ms` response headers.

### api_connection_error

`class-attribute` `instance-attribute`

```
api_connection_error: bool = True
```

Whether to retry `TypeSafeAPIConnectionError`, raised when the request cannot reach or read from the server.

### api_timeout_error

`class-attribute` `instance-attribute`

```
api_timeout_error: bool = True
```

Whether to retry `TypeSafeAPITimeoutError`, raised when the request exceeds its timeout.

### exceptions

`class-attribute` `instance-attribute`

```
exceptions: set[type[BaseException]] = field(
    default_factory=set
)
```

Additional exception types that trigger a retry, on top of the built-in rules.

### predicate

`class-attribute` `instance-attribute`

```
predicate: (
    Callable[[BaseException], bool] | None
) = None
```

An optional predicate called with the raised exception; returning `True` triggers a retry in addition to the other rules.

### timeout

`class-attribute` `instance-attribute`

```
timeout: float | None = 30.0
```

Total retry budget in seconds per SDK call, including the initial attempt and delays; `None` disables the limit.

Stops before a retry whose delay would reach or exceed the budget, re-raising the last error.

Was this page helpful?

[Answers and responses](https://docs.typesafe.ai/sdk/python/api/types/responses)

[Previous](https://docs.typesafe.ai/sdk/python/api/types/responses) [Common types Next](https://docs.typesafe.ai/sdk/python/api/types/common)

[github](https://github.com/typesafe-ai) [discord](https://discord.gg/typesafe) [x](https://x.com/typesafeai)

[Powered byThis documentation is built and hosted on Mintlify, a developer documentation platform](https://www.mintlify.com/?utm_campaign=poweredBy&utm_medium=referral&utm_source=ts-docs)

## On this page

- [typesafe_sdk.RetryPolicy](https://docs.typesafe.ai/sdk/python/api/retries#typesafe_sdk.RetryPolicy)
  - [max_retries](https://docs.typesafe.ai/sdk/python/api/retries#typesafe_sdk.RetryPolicy.max_retries)
  - [backoff_initial](https://docs.typesafe.ai/sdk/python/api/retries#typesafe_sdk.RetryPolicy.backoff_initial)
  - [backoff_max](https://docs.typesafe.ai/sdk/python/api/retries#typesafe_sdk.RetryPolicy.backoff_max)
  - [backoff_jitter](https://docs.typesafe.ai/sdk/python/api/retries#typesafe_sdk.RetryPolicy.backoff_jitter)
  - [http_statuses](https://docs.typesafe.ai/sdk/python/api/retries#typesafe_sdk.RetryPolicy.http_statuses)
  - [respect_retry_after](https://docs.typesafe.ai/sdk/python/api/retries#typesafe_sdk.RetryPolicy.respect_retry_after)
  - [api_connection_error](https://docs.typesafe.ai/sdk/python/api/retries#typesafe_sdk.RetryPolicy.api_connection_error)
  - [api_timeout_error](https://docs.typesafe.ai/sdk/python/api/retries#typesafe_sdk.RetryPolicy.api_timeout_error)
  - [exceptions](https://docs.typesafe.ai/sdk/python/api/retries#typesafe_sdk.RetryPolicy.exceptions)
  - [predicate](https://docs.typesafe.ai/sdk/python/api/retries#typesafe_sdk.RetryPolicy.predicate)
  - [timeout](https://docs.typesafe.ai/sdk/python/api/retries#typesafe_sdk.RetryPolicy.timeout)

[github](https://github.com/typesafe-ai)[discord](https://discord.gg/typesafe)[x](https://x.com/typesafeai)

[Powered byThis documentation is built and hosted on Mintlify, a developer documentation platform](https://www.mintlify.com/?utm_campaign=poweredBy&utm_medium=referral&utm_source=ts-docs)