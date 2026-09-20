---
title: "Class: TypeSafeClient - TypeSafe AI"
date: "2026-09-18T09:14:15.588Z"
url: "https://docs.typesafe.ai/sdk/javascript/api/classes/TypeSafeClient"
publisher: "TypeSafe AI"
lang: "en"
description: "Client for the TypeSafe AI API."
logo_url: "https://docs.typesafe.ai/mintlify-assets/_mintlify/favicons/ts-docs/zg2v0DiYB7xPw0I2/_generated/favicon/android-chrome-192x192.png"
logo_type: "png"
logo_size: 8885
logo_height: 192
logo_width: 192
logo_size_pretty: "8.88 kB"
image_url: "https://ts-docs.mintlify.app/mintlify-assets/_next/image?url=%2F_mintlify%2Fapi%2Fog%3Fdivision%3DClasses%26title%3DClass%253A%2BTypeSafeClient%26theme%3Df0580ae664a0195833f0555d&w=1200&q=100"
image_type: "png"
image_size: 29286
image_height: 630
image_width: 1200
image_size_pretty: "29.3 kB"
word_count: 456
reading_time: "2 min read"
---

[← Voltar ao índice](./README.md)


## Table of Contents

- [Constructors](#constructors)
  - [Constructor](#constructor)
    - [Parameters](#parameters)
      - [config?](#config)
    - [Returns](#returns)
    - [Throws](#throws)
- [Properties](#properties)
  - [baseURL](#baseurl)
  - [defaultHeaders](#defaultheaders)
  - [defaultModel](#defaultmodel)
  - [fetch](#fetch)
  - [logger](#logger)
  - [logLevel](#loglevel)
  - [models](#models)
  - [retry](#retry)
  - [timeout](#timeout)
- [Methods](#methods)
  - [systemOne()](#systemone)
    - [Type Parameters](#type-parameters)
      - [Q](#q)
    - [Parameters](#parameters-1)
      - [request](#request)
      - [options?](#options)
    - [Returns](#returns-1)
    - [Throws](#throws-1)
    - [Throws](#throws-2)
    - [Throws](#throws-3)
    - [Throws](#throws-4)
    - [Example](#example)
- [On this page](#on-this-page)

---

Classes

Client for the TypeSafe AI API.

## Constructors

### Constructor

```typescript
new TypeSafeClient(config?): TypeSafeClient;
```

Create a client for the TypeSafe AI API.

Explicit options take precedence over environment variables, then SDK defaults. Empty or whitespace-only environment values are ignored.

#### Parameters

##### config?

[`TypeSafeClientConfig`](https://docs.typesafe.ai/sdk/javascript/api/interfaces/TypeSafeClientConfig) = `{}`

#### Returns

`TypeSafeClient`

#### Throws

The API key is missing, configuration is invalid, or the runtime is unsupported.

## Properties

### baseURL

```typescript
readonly baseURL: string;
```

API root with trailing slashes removed.

------------------------------------------------------------------------

### defaultHeaders

```typescript
readonly defaultHeaders: Readonly<Record<string, string>>;
```

Additional headers sent with each request.

------------------------------------------------------------------------

### defaultModel

```typescript
readonly defaultModel: string;
```

Model used when a request omits `model`.

------------------------------------------------------------------------

### fetch

```typescript
readonly fetch: Fetch;
```

HTTP fetch implementation.

------------------------------------------------------------------------

### logger

```typescript
readonly logger: Logger;
```

The configured logger, filtered to `logLevel`.

------------------------------------------------------------------------

### logLevel

```typescript
readonly logLevel: LogLevel;
```

Configured log verbosity.

------------------------------------------------------------------------

### models

```typescript
readonly models: Models;
```

The models available to the account.

------------------------------------------------------------------------

### retry

```typescript
readonly retry: RetryPolicy;
```

Retry settings with constructor overrides applied.

------------------------------------------------------------------------

### timeout

```typescript
readonly timeout: number;
```

Timeout per attempt in milliseconds.

## Methods

### systemOne()

```typescript
systemOne<Q>(request, options?): APIPromise<SystemOneResult<Q>>;
```

Answer named questions about text or structured state.

#### Type Parameters

##### Q

`Q` *extends* [`Questions`](https://docs.typesafe.ai/sdk/javascript/api/interfaces/Questions)

#### Parameters

##### request

[`SystemOneRequest`](https://docs.typesafe.ai/sdk/javascript/api/interfaces/SystemOneRequest) \<`Q`\>

State, questions, and an optional model override.

##### options?

[`RequestOptions`](https://docs.typesafe.ai/sdk/javascript/api/interfaces/RequestOptions) = `{}`

Per-call timeout, retry, headers, and cancellation settings.

#### Returns

[`APIPromise`](https://docs.typesafe.ai/sdk/javascript/api/classes/APIPromise) \< [`SystemOneResult`](https://docs.typesafe.ai/sdk/javascript/api/interfaces/SystemOneResult) \<`Q`\>\>

Answers typed by question name and criteria, with model and token usage.

#### Throws

Questions are empty, or score criteria are not a list of at least two entries.

#### Throws

The server returns a non-2xx response after retries.

#### Throws

The request cannot connect or times out after retries.

#### Throws

The caller aborts the request.

#### Example

```typescript
const { answers } = await client.systemOne({
  state: "I was charged twice. Please help.",
  questions: { billing: noul("Is this about billing?") },
});
console.log(answers.billing.noul);
```

Was this page helpful?

[Class: RateLimitError](https://docs.typesafe.ai/sdk/javascript/api/classes/RateLimitError)

[Previous](https://docs.typesafe.ai/sdk/javascript/api/classes/RateLimitError) [Class: TypeSafeError Next](https://docs.typesafe.ai/sdk/javascript/api/classes/TypeSafeError)

[github](https://github.com/typesafe-ai) [discord](https://discord.gg/typesafe) [x](https://x.com/typesafeai)

[Powered byThis documentation is built and hosted on Mintlify, a developer documentation platform](https://www.mintlify.com/?utm_campaign=poweredBy&utm_medium=referral&utm_source=ts-docs)

## On this page

- [Constructors](https://docs.typesafe.ai/sdk/javascript/api/classes/TypeSafeClient#constructors)
  - [Constructor](https://docs.typesafe.ai/sdk/javascript/api/classes/TypeSafeClient#constructor)
  - [Parameters](https://docs.typesafe.ai/sdk/javascript/api/classes/TypeSafeClient#parameters)
  - [Returns](https://docs.typesafe.ai/sdk/javascript/api/classes/TypeSafeClient#returns)
  - [Throws](https://docs.typesafe.ai/sdk/javascript/api/classes/TypeSafeClient#throws)
- [Properties](https://docs.typesafe.ai/sdk/javascript/api/classes/TypeSafeClient#properties)
  - [baseURL](https://docs.typesafe.ai/sdk/javascript/api/classes/TypeSafeClient#baseurl)
  - [defaultHeaders](https://docs.typesafe.ai/sdk/javascript/api/classes/TypeSafeClient#defaultheaders)
  - [defaultModel](https://docs.typesafe.ai/sdk/javascript/api/classes/TypeSafeClient#defaultmodel)
  - [fetch](https://docs.typesafe.ai/sdk/javascript/api/classes/TypeSafeClient#fetch)
  - [logger](https://docs.typesafe.ai/sdk/javascript/api/classes/TypeSafeClient#logger)
  - [logLevel](https://docs.typesafe.ai/sdk/javascript/api/classes/TypeSafeClient#loglevel)
  - [models](https://docs.typesafe.ai/sdk/javascript/api/classes/TypeSafeClient#models)
  - [retry](https://docs.typesafe.ai/sdk/javascript/api/classes/TypeSafeClient#retry)
  - [timeout](https://docs.typesafe.ai/sdk/javascript/api/classes/TypeSafeClient#timeout)
- [Methods](https://docs.typesafe.ai/sdk/javascript/api/classes/TypeSafeClient#methods)
  - [systemOne()](https://docs.typesafe.ai/sdk/javascript/api/classes/TypeSafeClient#systemone)
  - [Type Parameters](https://docs.typesafe.ai/sdk/javascript/api/classes/TypeSafeClient#type-parameters)
  - [Parameters](https://docs.typesafe.ai/sdk/javascript/api/classes/TypeSafeClient#parameters-2)
  - [Returns](https://docs.typesafe.ai/sdk/javascript/api/classes/TypeSafeClient#returns-2)
  - [Throws](https://docs.typesafe.ai/sdk/javascript/api/classes/TypeSafeClient#throws-2)
  - [Throws](https://docs.typesafe.ai/sdk/javascript/api/classes/TypeSafeClient#throws-3)
  - [Throws](https://docs.typesafe.ai/sdk/javascript/api/classes/TypeSafeClient#throws-4)
  - [Throws](https://docs.typesafe.ai/sdk/javascript/api/classes/TypeSafeClient#throws-5)
  - [Example](https://docs.typesafe.ai/sdk/javascript/api/classes/TypeSafeClient#example)

[github](https://github.com/typesafe-ai)[discord](https://discord.gg/typesafe)[x](https://x.com/typesafeai)

[Powered byThis documentation is built and hosted on Mintlify, a developer documentation platform](https://www.mintlify.com/?utm_campaign=poweredBy&utm_medium=referral&utm_source=ts-docs)