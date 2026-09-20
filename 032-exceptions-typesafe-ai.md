---
title: "Exceptions - TypeSafe AI"
date: "2026-09-15T18:15:54.313Z"
description: "Handle TypeSafe API errors, rate limits, connection failures, and timeouts."
url: "https://docs.typesafe.ai/sdk/python/api/exceptions"
publisher: "TypeSafe AI"
lang: "en"
logo_url: "https://docs.typesafe.ai/mintlify-assets/_mintlify/favicons/ts-docs/zg2v0DiYB7xPw0I2/_generated/favicon/android-chrome-192x192.png"
logo_type: "png"
logo_size: 8885
logo_height: 192
logo_width: 192
logo_size_pretty: "8.88 kB"
image_url: "https://ts-docs.mintlify.app/mintlify-assets/_next/image?url=%2F_mintlify%2Fapi%2Fog%3Fdivision%3DAPI%2Breference%26title%3DExceptions%26description%3DHandle%2BTypeSafe%2BAPI%2Berrors%252C%2Brate%2Blimits%252C%2Bconnection%2Bfailures%252C%2Band%2Btimeouts.%26theme%3Df0580ae664a0195833f0555d&w=1200&q=100"
image_type: "png"
image_size: 34288
image_height: 630
image_width: 1200
image_size_pretty: "34.3 kB"
word_count: 603
reading_time: "3 min read"
---

[← Voltar ao índice](./README.md)


## Table of Contents

- [Base exception](#base-exception)
- [typesafe_sdk.TypeSafeError](#typesafe_sdktypesafeerror)
- [HTTP errors](#http-errors)
- [typesafe_sdk.TypeSafeAPIError](#typesafe_sdktypesafeapierror)
  - [status](#status)
  - [body](#body)
  - [headers](#headers)
  - [endpoint](#endpoint)
  - [request_id](#request_id)
- [typesafe_sdk.TypeSafeBadRequestError](#typesafe_sdktypesafebadrequesterror)
- [typesafe_sdk.TypeSafeAuthenticationError](#typesafe_sdktypesafeauthenticationerror)
- [typesafe_sdk.TypeSafePermissionDeniedError](#typesafe_sdktypesafepermissiondeniederror)
- [typesafe_sdk.TypeSafeNotFoundError](#typesafe_sdktypesafenotfounderror)
- [typesafe_sdk.TypeSafeUnprocessableEntityError](#typesafe_sdktypesafeunprocessableentityerror)
- [typesafe_sdk.TypeSafeRateLimitError](#typesafe_sdktypesaferatelimiterror)
  - [retry_after_ms](#retry_after_ms)
- [typesafe_sdk.TypeSafeInternalServerError](#typesafe_sdktypesafeinternalservererror)
- [Connection errors](#connection-errors)
- [typesafe_sdk.TypeSafeAPIConnectionError](#typesafe_sdktypesafeapiconnectionerror)
- [typesafe_sdk.TypeSafeAPITimeoutError](#typesafe_sdktypesafeapitimeouterror)
  - [timeout](#timeout)
- [Response validation](#response-validation)
- [typesafe_sdk.TypeSafeAPIResponseValidationError](#typesafe_sdktypesafeapiresponsevalidationerror)
  - [field_path](#field_path)
  - [args](#args)
- [On this page](#on-this-page)

---

API reference

Handle TypeSafe API errors, rate limits, connection failures, and timeouts.

## Base exception

## typesafe_sdk.TypeSafeError

Bases: `Exception`

Base exception for SDK failures.

## HTTP errors

## typesafe_sdk.TypeSafeAPIError

Bases: `TypeSafeError`

An unsuccessful HTTP response with its body and request metadata.

### status

`instance-attribute`

```python
status = status
```

HTTP response status code.

### body

`instance-attribute`

```python
body = body
```

The server’s JSON error body, plain response text, or `None` for an empty body.

### headers

`instance-attribute`

```python
headers = headers
```

HTTP response headers.

### endpoint

`instance-attribute`

```python
endpoint = endpoint
```

The request method and URL, without credentials, query parameters, or fragment, when available.

### request_id

`property`

```
request_id: str | None
```

The `x-typesafe-request-id` response header, or `None` if absent.

## typesafe_sdk.TypeSafeBadRequestError

Bases: `TypeSafeAPIError`

The request was invalid (400).

## typesafe_sdk.TypeSafeAuthenticationError

Bases: `TypeSafeAPIError`

Authentication failed (401).

## typesafe_sdk.TypeSafePermissionDeniedError

Bases: `TypeSafeAPIError`

Access was denied (403).

## typesafe_sdk.TypeSafeNotFoundError

Bases: `TypeSafeAPIError`

The resource was not found (404).

## typesafe_sdk.TypeSafeUnprocessableEntityError

Bases: `TypeSafeAPIError`

The request failed server validation (422).

## typesafe_sdk.TypeSafeRateLimitError

Bases: `TypeSafeAPIError`

The rate limit was exceeded (429).

### retry_after_ms

`instance-attribute`

```python
retry_after_ms = parse_retry_after(headers)
```

The server’s requested wait in milliseconds, or `None` if unavailable.

## typesafe_sdk.TypeSafeInternalServerError

Bases: `TypeSafeAPIError`

The server failed to process the request (5xx).

## Connection errors

## typesafe_sdk.TypeSafeAPIConnectionError

Bases: `TypeSafeError`, `ConnectionError`

A request failed without an HTTP response.

## typesafe_sdk.TypeSafeAPITimeoutError

Bases: `TypeSafeAPIConnectionError`, `TimeoutError`

A request exceeded its configured timeout.

### timeout

`instance-attribute`

```python
timeout = timeout
```

The timeout setting used for the request, in seconds or as an `httpx2.Timeout`.

## Response validation

## typesafe_sdk.TypeSafeAPIResponseValidationError

Bases: `TypeSafeAPIError`

A successful HTTP response whose body was missing or structurally invalid required data.

### field_path

`instance-attribute`

```python
field_path = field_path
```

Dotted path to the offending field, such as `answers.tone.confidence`.

### args

`instance-attribute`

```python
args = (
    status,
    body,
    headers,
    field_path,
    endpoint,
)
```

Was this page helpful?

[Common types](https://docs.typesafe.ai/sdk/python/api/types/common)

[Previous](https://docs.typesafe.ai/sdk/python/api/types/common) [Constants Next](https://docs.typesafe.ai/sdk/python/api/constants)

[github](https://github.com/typesafe-ai) [discord](https://discord.gg/typesafe) [x](https://x.com/typesafeai)

[Powered byThis documentation is built and hosted on Mintlify, a developer documentation platform](https://www.mintlify.com/?utm_campaign=poweredBy&utm_medium=referral&utm_source=ts-docs)

## On this page

- [Base exception](https://docs.typesafe.ai/sdk/python/api/exceptions#base-exception)
- [typesafe_sdk.TypeSafeError](https://docs.typesafe.ai/sdk/python/api/exceptions#typesafe_sdk.TypeSafeError)
- [HTTP errors](https://docs.typesafe.ai/sdk/python/api/exceptions#http-errors)
- [typesafe_sdk.TypeSafeAPIError](https://docs.typesafe.ai/sdk/python/api/exceptions#typesafe_sdk.TypeSafeAPIError)
  - [status](https://docs.typesafe.ai/sdk/python/api/exceptions#typesafe_sdk.TypeSafeAPIError.status)
  - [body](https://docs.typesafe.ai/sdk/python/api/exceptions#typesafe_sdk.TypeSafeAPIError.body)
  - [headers](https://docs.typesafe.ai/sdk/python/api/exceptions#typesafe_sdk.TypeSafeAPIError.headers)
  - [endpoint](https://docs.typesafe.ai/sdk/python/api/exceptions#typesafe_sdk.TypeSafeAPIError.endpoint)
  - [request_id](https://docs.typesafe.ai/sdk/python/api/exceptions#typesafe_sdk.TypeSafeAPIError.request_id)
- [typesafe_sdk.TypeSafeBadRequestError](https://docs.typesafe.ai/sdk/python/api/exceptions#typesafe_sdk.TypeSafeBadRequestError)
- [typesafe_sdk.TypeSafeAuthenticationError](https://docs.typesafe.ai/sdk/python/api/exceptions#typesafe_sdk.TypeSafeAuthenticationError)
- [typesafe_sdk.TypeSafePermissionDeniedError](https://docs.typesafe.ai/sdk/python/api/exceptions#typesafe_sdk.TypeSafePermissionDeniedError)
- [typesafe_sdk.TypeSafeNotFoundError](https://docs.typesafe.ai/sdk/python/api/exceptions#typesafe_sdk.TypeSafeNotFoundError)
- [typesafe_sdk.TypeSafeUnprocessableEntityError](https://docs.typesafe.ai/sdk/python/api/exceptions#typesafe_sdk.TypeSafeUnprocessableEntityError)
- [typesafe_sdk.TypeSafeRateLimitError](https://docs.typesafe.ai/sdk/python/api/exceptions#typesafe_sdk.TypeSafeRateLimitError)
  - [retry_after_ms](https://docs.typesafe.ai/sdk/python/api/exceptions#typesafe_sdk.TypeSafeRateLimitError.retry_after_ms)
- [typesafe_sdk.TypeSafeInternalServerError](https://docs.typesafe.ai/sdk/python/api/exceptions#typesafe_sdk.TypeSafeInternalServerError)
- [Connection errors](https://docs.typesafe.ai/sdk/python/api/exceptions#connection-errors)
- [typesafe_sdk.TypeSafeAPIConnectionError](https://docs.typesafe.ai/sdk/python/api/exceptions#typesafe_sdk.TypeSafeAPIConnectionError)
- [typesafe_sdk.TypeSafeAPITimeoutError](https://docs.typesafe.ai/sdk/python/api/exceptions#typesafe_sdk.TypeSafeAPITimeoutError)
  - [timeout](https://docs.typesafe.ai/sdk/python/api/exceptions#typesafe_sdk.TypeSafeAPITimeoutError.timeout)
- [Response validation](https://docs.typesafe.ai/sdk/python/api/exceptions#response-validation)
- [typesafe_sdk.TypeSafeAPIResponseValidationError](https://docs.typesafe.ai/sdk/python/api/exceptions#typesafe_sdk.TypeSafeAPIResponseValidationError)
  - [field_path](https://docs.typesafe.ai/sdk/python/api/exceptions#typesafe_sdk.TypeSafeAPIResponseValidationError.field_path)
  - [args](https://docs.typesafe.ai/sdk/python/api/exceptions#typesafe_sdk.TypeSafeAPIResponseValidationError.args)

[github](https://github.com/typesafe-ai)[discord](https://discord.gg/typesafe)[x](https://x.com/typesafeai)

[Powered byThis documentation is built and hosted on Mintlify, a developer documentation platform](https://www.mintlify.com/?utm_campaign=poweredBy&utm_medium=referral&utm_source=ts-docs)