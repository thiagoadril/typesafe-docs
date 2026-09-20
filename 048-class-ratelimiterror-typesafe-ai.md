---
title: "Class: RateLimitError - TypeSafe AI"
date: "2026-09-18T09:14:15.587Z"
url: "https://docs.typesafe.ai/sdk/javascript/api/classes/RateLimitError"
publisher: "TypeSafe AI"
lang: "en"
description: "Classes"
logo_url: "https://docs.typesafe.ai/mintlify-assets/_mintlify/favicons/ts-docs/zg2v0DiYB7xPw0I2/_generated/favicon/android-chrome-192x192.png"
logo_type: "png"
logo_size: 8885
logo_height: 192
logo_width: 192
logo_size_pretty: "8.88 kB"
image_url: "https://ts-docs.mintlify.app/mintlify-assets/_next/image?url=%2F_mintlify%2Fapi%2Fog%3Fdivision%3DClasses%26title%3DClass%253A%2BRateLimitError%26theme%3Df0580ae664a0195833f0555d&w=1200&q=100"
image_type: "png"
image_size: 27877
image_height: 630
image_width: 1200
image_size_pretty: "27.9 kB"
word_count: 355
reading_time: "2 min read"
---

[← Voltar ao índice](./README.md)


## Table of Contents

- [Extends](#extends)
- [Constructors](#constructors)
  - [Constructor](#constructor)
    - [Parameters](#parameters)
      - [status](#status)
      - [body](#body)
      - [headers](#headers)
      - [message?](#message)
    - [Returns](#returns)
    - [Inherited from](#inherited-from)
- [Properties](#properties)
  - [body](#body-1)
    - [Inherited from](#inherited-from-1)
  - [headers](#headers-1)
    - [Inherited from](#inherited-from-2)
  - [requestId](#requestid)
    - [Inherited from](#inherited-from-3)
  - [retryAfterMs](#retryafterms)
  - [status](#status-1)
    - [Inherited from](#inherited-from-4)
- [Methods](#methods)
  - [fromResponse()](#fromresponse)
    - [Parameters](#parameters-1)
      - [status](#status-2)
      - [body](#body-2)
      - [headers](#headers-2)
    - [Returns](#returns-1)
    - [Inherited from](#inherited-from-5)
- [On this page](#on-this-page)

---

Classes

HTTP 429: the rate limit was exceeded.

## Extends

- [`APIError`](https://docs.typesafe.ai/sdk/javascript/api/classes/APIError)

## Constructors

### Constructor

```typescript
new RateLimitError(
   status,
   body,
   headers,
   message?
): RateLimitError;
```

#### Parameters

##### status

`number`

##### body

`unknown`

##### headers

`Headers`

##### message?

`string`

#### Returns

`RateLimitError`

#### Inherited from

[`APIError`](https://docs.typesafe.ai/sdk/javascript/api/classes/APIError).[`constructor`](https://docs.typesafe.ai/sdk/javascript/api/classes/APIError#sdk-constructor)

## Properties

### body

```typescript
readonly body: unknown;
```

Parsed JSON, response text, or `undefined` for an empty body.

#### Inherited from

[`APIError`](https://docs.typesafe.ai/sdk/javascript/api/classes/APIError).[`body`](https://docs.typesafe.ai/sdk/javascript/api/classes/APIError#sdk-body)

------------------------------------------------------------------------

### headers

```typescript
readonly headers: Headers;
```

HTTP response headers.

#### Inherited from

[`APIError`](https://docs.typesafe.ai/sdk/javascript/api/classes/APIError).[`headers`](https://docs.typesafe.ai/sdk/javascript/api/classes/APIError#sdk-headers)

------------------------------------------------------------------------

### requestId

```typescript
readonly requestId: string | undefined;
```

Request ID from `x-typesafe-request-id`, or `undefined` when absent.

#### Inherited from

[`APIError`](https://docs.typesafe.ai/sdk/javascript/api/classes/APIError).[`requestId`](https://docs.typesafe.ai/sdk/javascript/api/classes/APIError#sdk-requestid)

------------------------------------------------------------------------

### retryAfterMs

```typescript
readonly retryAfterMs: number | undefined;
```

Server retry delay in milliseconds, or `undefined` when absent or invalid.

------------------------------------------------------------------------

### status

```typescript
readonly status: number;
```

HTTP response status code.

#### Inherited from

[`APIError`](https://docs.typesafe.ai/sdk/javascript/api/classes/APIError).[`status`](https://docs.typesafe.ai/sdk/javascript/api/classes/APIError#sdk-status)

## Methods

### fromResponse()

```typescript
static fromResponse(
   status,
   body,
   headers
): APIError;
```

Create the error subclass for an HTTP status code.

#### Parameters

##### status

`number`

##### body

`unknown`

##### headers

`Headers`

#### Returns

[`APIError`](https://docs.typesafe.ai/sdk/javascript/api/classes/APIError)

#### Inherited from

[`APIError`](https://docs.typesafe.ai/sdk/javascript/api/classes/APIError).[`fromResponse`](https://docs.typesafe.ai/sdk/javascript/api/classes/APIError#sdk-fromresponse)

Was this page helpful?

[Class: PermissionDeniedError](https://docs.typesafe.ai/sdk/javascript/api/classes/PermissionDeniedError)

[Previous](https://docs.typesafe.ai/sdk/javascript/api/classes/PermissionDeniedError) [Class: TypeSafeClient Next](https://docs.typesafe.ai/sdk/javascript/api/classes/TypeSafeClient)

[github](https://github.com/typesafe-ai) [discord](https://discord.gg/typesafe) [x](https://x.com/typesafeai)

[Powered byThis documentation is built and hosted on Mintlify, a developer documentation platform](https://www.mintlify.com/?utm_campaign=poweredBy&utm_medium=referral&utm_source=ts-docs)

## On this page

- [Extends](https://docs.typesafe.ai/sdk/javascript/api/classes/RateLimitError#extends)
- [Constructors](https://docs.typesafe.ai/sdk/javascript/api/classes/RateLimitError#constructors)
  - [Constructor](https://docs.typesafe.ai/sdk/javascript/api/classes/RateLimitError#constructor)
  - [Parameters](https://docs.typesafe.ai/sdk/javascript/api/classes/RateLimitError#parameters)
  - [Returns](https://docs.typesafe.ai/sdk/javascript/api/classes/RateLimitError#returns)
  - [Inherited from](https://docs.typesafe.ai/sdk/javascript/api/classes/RateLimitError#inherited-from)
- [Properties](https://docs.typesafe.ai/sdk/javascript/api/classes/RateLimitError#properties)
  - [body](https://docs.typesafe.ai/sdk/javascript/api/classes/RateLimitError#body)
  - [Inherited from](https://docs.typesafe.ai/sdk/javascript/api/classes/RateLimitError#inherited-from-2)
  - [headers](https://docs.typesafe.ai/sdk/javascript/api/classes/RateLimitError#headers)
  - [Inherited from](https://docs.typesafe.ai/sdk/javascript/api/classes/RateLimitError#inherited-from-3)
  - [requestId](https://docs.typesafe.ai/sdk/javascript/api/classes/RateLimitError#requestid)
  - [Inherited from](https://docs.typesafe.ai/sdk/javascript/api/classes/RateLimitError#inherited-from-4)
  - [retryAfterMs](https://docs.typesafe.ai/sdk/javascript/api/classes/RateLimitError#retryafterms)
  - [status](https://docs.typesafe.ai/sdk/javascript/api/classes/RateLimitError#status)
  - [Inherited from](https://docs.typesafe.ai/sdk/javascript/api/classes/RateLimitError#inherited-from-5)
- [Methods](https://docs.typesafe.ai/sdk/javascript/api/classes/RateLimitError#methods)
  - [fromResponse()](https://docs.typesafe.ai/sdk/javascript/api/classes/RateLimitError#fromresponse)
  - [Parameters](https://docs.typesafe.ai/sdk/javascript/api/classes/RateLimitError#parameters-2)
  - [Returns](https://docs.typesafe.ai/sdk/javascript/api/classes/RateLimitError#returns-2)
  - [Inherited from](https://docs.typesafe.ai/sdk/javascript/api/classes/RateLimitError#inherited-from-6)

[github](https://github.com/typesafe-ai)[discord](https://discord.gg/typesafe)[x](https://x.com/typesafeai)

[Powered byThis documentation is built and hosted on Mintlify, a developer documentation platform](https://www.mintlify.com/?utm_campaign=poweredBy&utm_medium=referral&utm_source=ts-docs)