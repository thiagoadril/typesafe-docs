---
title: "Class: APIError - TypeSafe AI"
date: "2026-09-18T09:14:15.585Z"
url: "https://docs.typesafe.ai/sdk/javascript/api/classes/APIError"
publisher: "TypeSafe AI"
lang: "en"
description: "An unsuccessful HTTP response from the API."
logo_url: "https://docs.typesafe.ai/mintlify-assets/_mintlify/favicons/ts-docs/zg2v0DiYB7xPw0I2/_generated/favicon/android-chrome-192x192.png"
logo_type: "png"
logo_size: 8885
logo_height: 192
logo_width: 192
logo_size_pretty: "8.88 kB"
image_url: "https://ts-docs.mintlify.app/mintlify-assets/_next/image?url=%2F_mintlify%2Fapi%2Fog%3Fdivision%3DClasses%26title%3DClass%253A%2BAPIError%26theme%3Df0580ae664a0195833f0555d&w=1200&q=100"
image_type: "png"
image_size: 26084
image_height: 630
image_width: 1200
image_size_pretty: "26.1 kB"
word_count: 246
reading_time: "1 min read"
---

[← Voltar ao índice](./README.md)


## Table of Contents

- [Extends](#extends)
- [Extended by](#extended-by)
- [Constructors](#constructors)
  - [Constructor](#constructor)
    - [Parameters](#parameters)
      - [status](#status)
      - [body](#body)
      - [headers](#headers)
      - [message?](#message)
    - [Returns](#returns)
    - [Overrides](#overrides)
- [Properties](#properties)
  - [body](#body-1)
  - [headers](#headers-1)
  - [requestId](#requestid)
  - [status](#status-1)
- [Methods](#methods)
  - [fromResponse()](#fromresponse)
    - [Parameters](#parameters-1)
      - [status](#status-2)
      - [body](#body-2)
      - [headers](#headers-2)
    - [Returns](#returns-1)
- [On this page](#on-this-page)

---

Classes

An unsuccessful HTTP response from the API.

## Extends

- [`TypeSafeError`](https://docs.typesafe.ai/sdk/javascript/api/classes/TypeSafeError)

## Extended by

- [`AuthenticationError`](https://docs.typesafe.ai/sdk/javascript/api/classes/AuthenticationError)
- [`BadRequestError`](https://docs.typesafe.ai/sdk/javascript/api/classes/BadRequestError)
- [`InternalServerError`](https://docs.typesafe.ai/sdk/javascript/api/classes/InternalServerError)
- [`NotFoundError`](https://docs.typesafe.ai/sdk/javascript/api/classes/NotFoundError)
- [`PermissionDeniedError`](https://docs.typesafe.ai/sdk/javascript/api/classes/PermissionDeniedError)
- [`RateLimitError`](https://docs.typesafe.ai/sdk/javascript/api/classes/RateLimitError)
- [`UnprocessableEntityError`](https://docs.typesafe.ai/sdk/javascript/api/classes/UnprocessableEntityError)

## Constructors

### Constructor

```typescript
new APIError(
   status,
   body,
   headers,
   message?
): APIError;
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

`APIError`

#### Overrides

[`TypeSafeError`](https://docs.typesafe.ai/sdk/javascript/api/classes/TypeSafeError).[`constructor`](https://docs.typesafe.ai/sdk/javascript/api/classes/TypeSafeError#sdk-constructor)

## Properties

### body

```typescript
readonly body: unknown;
```

Parsed JSON, response text, or `undefined` for an empty body.

------------------------------------------------------------------------

### headers

```typescript
readonly headers: Headers;
```

HTTP response headers.

------------------------------------------------------------------------

### requestId

```typescript
readonly requestId: string | undefined;
```

Request ID from `x-typesafe-request-id`, or `undefined` when absent.

------------------------------------------------------------------------

### status

```typescript
readonly status: number;
```

HTTP response status code.

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

`APIError`

Was this page helpful?

[Class: APIConnectionError](https://docs.typesafe.ai/sdk/javascript/api/classes/APIConnectionError)

[Previous](https://docs.typesafe.ai/sdk/javascript/api/classes/APIConnectionError) [Class: APIPromise\<T\> Next](https://docs.typesafe.ai/sdk/javascript/api/classes/APIPromise)

[github](https://github.com/typesafe-ai) [discord](https://discord.gg/typesafe) [x](https://x.com/typesafeai)

[Powered byThis documentation is built and hosted on Mintlify, a developer documentation platform](https://www.mintlify.com/?utm_campaign=poweredBy&utm_medium=referral&utm_source=ts-docs)

## On this page

- [Extends](https://docs.typesafe.ai/sdk/javascript/api/classes/APIError#extends)
- [Extended by](https://docs.typesafe.ai/sdk/javascript/api/classes/APIError#extended-by)
- [Constructors](https://docs.typesafe.ai/sdk/javascript/api/classes/APIError#constructors)
  - [Constructor](https://docs.typesafe.ai/sdk/javascript/api/classes/APIError#constructor)
  - [Parameters](https://docs.typesafe.ai/sdk/javascript/api/classes/APIError#parameters)
  - [Returns](https://docs.typesafe.ai/sdk/javascript/api/classes/APIError#returns)
  - [Overrides](https://docs.typesafe.ai/sdk/javascript/api/classes/APIError#overrides)
- [Properties](https://docs.typesafe.ai/sdk/javascript/api/classes/APIError#properties)
  - [body](https://docs.typesafe.ai/sdk/javascript/api/classes/APIError#body)
  - [headers](https://docs.typesafe.ai/sdk/javascript/api/classes/APIError#headers)
  - [requestId](https://docs.typesafe.ai/sdk/javascript/api/classes/APIError#requestid)
  - [status](https://docs.typesafe.ai/sdk/javascript/api/classes/APIError#status)
- [Methods](https://docs.typesafe.ai/sdk/javascript/api/classes/APIError#methods)
  - [fromResponse()](https://docs.typesafe.ai/sdk/javascript/api/classes/APIError#fromresponse)
  - [Parameters](https://docs.typesafe.ai/sdk/javascript/api/classes/APIError#parameters-2)
  - [Returns](https://docs.typesafe.ai/sdk/javascript/api/classes/APIError#returns-2)

[github](https://github.com/typesafe-ai)[discord](https://discord.gg/typesafe)[x](https://x.com/typesafeai)

[Powered byThis documentation is built and hosted on Mintlify, a developer documentation platform](https://www.mintlify.com/?utm_campaign=poweredBy&utm_medium=referral&utm_source=ts-docs)