---
title: "Class: APIPromise<T> - TypeSafe AI"
date: "2026-09-18T09:14:15.556Z"
url: "https://docs.typesafe.ai/sdk/javascript/api/classes/APIPromise"
publisher: "TypeSafe AI"
lang: "en"
description: "A promise for the parsed result with access to the HTTP response.
Non-2xx responses reject with an APIError, including through asResponse()."
logo_url: "https://docs.typesafe.ai/mintlify-assets/_mintlify/favicons/ts-docs/zg2v0DiYB7xPw0I2/_generated/favicon/android-chrome-192x192.png"
logo_type: "png"
logo_size: 8885
logo_height: 192
logo_width: 192
logo_size_pretty: "8.88 kB"
image_url: "https://ts-docs.mintlify.app/mintlify-assets/_next/image?url=%2F_mintlify%2Fapi%2Fog%3Fdivision%3DClasses%26title%3DClass%253A%2BAPIPromise%253CT%253E%26theme%3Df0580ae664a0195833f0555d&w=1200&q=100"
image_type: "png"
image_size: 27494
image_height: 630
image_width: 1200
image_size_pretty: "27.5 kB"
word_count: 580
reading_time: "3 min read"
---

[← Voltar ao índice](./README.md)


## Table of Contents

- [Extends](#extends)
- [Type Parameters](#type-parameters)
  - [T](#t)
- [Constructors](#constructors)
  - [Constructor](#constructor)
    - [Parameters](#parameters)
      - [responsePromise](#responsepromise)
      - [parseResponse](#parseresponse)
    - [Returns](#returns)
    - [Overrides](#overrides)
- [Methods](#methods)
  - [asResponse()](#asresponse)
    - [Returns](#returns-1)
  - [catch()](#catch)
    - [Type Parameters](#type-parameters-1)
      - [TResult](#tresult)
    - [Parameters](#parameters-1)
      - [onrejected?](#onrejected)
    - [Returns](#returns-2)
    - [Overrides](#overrides-1)
  - [finally()](#finally)
    - [Parameters](#parameters-2)
      - [onfinally?](#onfinally)
    - [Returns](#returns-3)
    - [Overrides](#overrides-2)
  - [map()](#map)
    - [Type Parameters](#type-parameters-2)
      - [U](#u)
    - [Parameters](#parameters-3)
      - [fn](#fn)
    - [Returns](#returns-4)
  - [then()](#then)
    - [Type Parameters](#type-parameters-3)
      - [TResult1](#tresult1)
      - [TResult2](#tresult2)
    - [Parameters](#parameters-4)
      - [onfulfilled?](#onfulfilled)
      - [onrejected?](#onrejected-1)
    - [Returns](#returns-5)
    - [Overrides](#overrides-3)
  - [withResponse()](#withresponse)
    - [Returns](#returns-6)
- [On this page](#on-this-page)

---

Classes

A promise for the parsed result with access to the HTTP response.

Non-2xx responses reject with an `APIError`, including through `asResponse()`.

## Extends

- `Promise`\<`T`\>

## Type Parameters

### T

`T`

## Constructors

### Constructor

```typescript
new APIPromise<T>(responsePromise, parseResponse): APIPromise<T>;
```

#### Parameters

##### responsePromise

`Promise`\<`Response`\>

##### parseResponse

(`response`) =\> `Promise`\<`T`\>

#### Returns

`APIPromise`\<`T`\>

#### Overrides

```typescript
Promise<T>.constructor
```

## Methods

### asResponse()

```typescript
asResponse(): Promise<Response>;
```

Resolves to the raw `Response` without parsing the body. SDK requests buffer the full body under the request timeout before handoff; reading it afterwards is caller-owned. The caller owns the body; don’t also `await` the parsed result on the same promise.

#### Returns

`Promise`\<`Response`\>

------------------------------------------------------------------------

### catch()

```typescript
catch<TResult>(onrejected?): Promise<T | TResult>;
```

Attaches a callback for only the rejection of the Promise.

#### Type Parameters

##### TResult

`TResult` = `never`

#### Parameters

##### onrejected?

((`reason`) =\> `TResult` \| `PromiseLike`\<`TResult`\>) \| `null`

The callback to execute when the Promise is rejected.

#### Returns

`Promise`\<`T` \| `TResult`\>

A Promise for the completion of the callback.

#### Overrides

```typescript
Promise.catch
```

------------------------------------------------------------------------

### finally()

```typescript
finally(onfinally?): Promise<T>;
```

Attaches a callback that is invoked when the Promise is settled (fulfilled or rejected). The resolved value cannot be modified from the callback.

#### Parameters

##### onfinally?

(() =\> `void`) \| `null`

The callback to execute when the Promise is settled (fulfilled or rejected).

#### Returns

`Promise`\<`T`\>

A Promise for the completion of the callback.

#### Overrides

```typescript
Promise.finally
```

------------------------------------------------------------------------

### map()

```typescript
map<U>(fn): APIPromise<U>;
```

Transform the parsed result, sharing the HTTP response and a single body parse.

#### Type Parameters

##### U

`U`

#### Parameters

##### fn

(`data`) =\> `U`

#### Returns

`APIPromise`\<`U`\>

------------------------------------------------------------------------

### then()

```typescript
then<TResult1, TResult2>(onfulfilled?, onrejected?): Promise<TResult1 | TResult2>;
```

Attaches callbacks for the resolution and/or rejection of the Promise.

#### Type Parameters

##### TResult1

`TResult1` = `T`

##### TResult2

`TResult2` = `never`

#### Parameters

##### onfulfilled?

((`value`) =\> `TResult1` \| `PromiseLike`\<`TResult1`\>) \| `null`

The callback to execute when the Promise is resolved.

##### onrejected?

((`reason`) =\> `TResult2` \| `PromiseLike`\<`TResult2`\>) \| `null`

The callback to execute when the Promise is rejected.

#### Returns

`Promise`\<`TResult1` \| `TResult2`\>

A Promise for the completion of which ever callback is executed.

#### Overrides

```typescript
Promise.then
```

------------------------------------------------------------------------

### withResponse()

```typescript
withResponse(): Promise<WithResponse<T>>;
```

Return the parsed result, HTTP response, and request ID.

#### Returns

`Promise`\< [`WithResponse`](https://docs.typesafe.ai/sdk/javascript/api/interfaces/WithResponse) \<`T`\>\>

Was this page helpful?

[Class: APIError](https://docs.typesafe.ai/sdk/javascript/api/classes/APIError)

[Previous](https://docs.typesafe.ai/sdk/javascript/api/classes/APIError) [Class: APITimeoutError Next](https://docs.typesafe.ai/sdk/javascript/api/classes/APITimeoutError)

[github](https://github.com/typesafe-ai) [discord](https://discord.gg/typesafe) [x](https://x.com/typesafeai)

[Powered byThis documentation is built and hosted on Mintlify, a developer documentation platform](https://www.mintlify.com/?utm_campaign=poweredBy&utm_medium=referral&utm_source=ts-docs)

## On this page

- [Extends](https://docs.typesafe.ai/sdk/javascript/api/classes/APIPromise#extends)
- [Type Parameters](https://docs.typesafe.ai/sdk/javascript/api/classes/APIPromise#type-parameters)
  - [T](https://docs.typesafe.ai/sdk/javascript/api/classes/APIPromise#t)
- [Constructors](https://docs.typesafe.ai/sdk/javascript/api/classes/APIPromise#constructors)
  - [Constructor](https://docs.typesafe.ai/sdk/javascript/api/classes/APIPromise#constructor)
  - [Parameters](https://docs.typesafe.ai/sdk/javascript/api/classes/APIPromise#parameters)
  - [Returns](https://docs.typesafe.ai/sdk/javascript/api/classes/APIPromise#returns)
  - [Overrides](https://docs.typesafe.ai/sdk/javascript/api/classes/APIPromise#overrides)
- [Methods](https://docs.typesafe.ai/sdk/javascript/api/classes/APIPromise#methods)
  - [asResponse()](https://docs.typesafe.ai/sdk/javascript/api/classes/APIPromise#asresponse)
  - [Returns](https://docs.typesafe.ai/sdk/javascript/api/classes/APIPromise#returns-2)
  - [catch()](https://docs.typesafe.ai/sdk/javascript/api/classes/APIPromise#catch)
  - [Type Parameters](https://docs.typesafe.ai/sdk/javascript/api/classes/APIPromise#type-parameters-2)
  - [Parameters](https://docs.typesafe.ai/sdk/javascript/api/classes/APIPromise#parameters-2)
  - [Returns](https://docs.typesafe.ai/sdk/javascript/api/classes/APIPromise#returns-3)
  - [Overrides](https://docs.typesafe.ai/sdk/javascript/api/classes/APIPromise#overrides-2)
  - [finally()](https://docs.typesafe.ai/sdk/javascript/api/classes/APIPromise#finally)
  - [Parameters](https://docs.typesafe.ai/sdk/javascript/api/classes/APIPromise#parameters-3)
  - [Returns](https://docs.typesafe.ai/sdk/javascript/api/classes/APIPromise#returns-4)
  - [Overrides](https://docs.typesafe.ai/sdk/javascript/api/classes/APIPromise#overrides-3)
  - [map()](https://docs.typesafe.ai/sdk/javascript/api/classes/APIPromise#map)
  - [Type Parameters](https://docs.typesafe.ai/sdk/javascript/api/classes/APIPromise#type-parameters-3)
  - [Parameters](https://docs.typesafe.ai/sdk/javascript/api/classes/APIPromise#parameters-4)
  - [Returns](https://docs.typesafe.ai/sdk/javascript/api/classes/APIPromise#returns-5)
  - [then()](https://docs.typesafe.ai/sdk/javascript/api/classes/APIPromise#then)
  - [Type Parameters](https://docs.typesafe.ai/sdk/javascript/api/classes/APIPromise#type-parameters-4)
  - [Parameters](https://docs.typesafe.ai/sdk/javascript/api/classes/APIPromise#parameters-5)
  - [Returns](https://docs.typesafe.ai/sdk/javascript/api/classes/APIPromise#returns-6)
  - [Overrides](https://docs.typesafe.ai/sdk/javascript/api/classes/APIPromise#overrides-4)
  - [withResponse()](https://docs.typesafe.ai/sdk/javascript/api/classes/APIPromise#withresponse)
  - [Returns](https://docs.typesafe.ai/sdk/javascript/api/classes/APIPromise#returns-7)

[github](https://github.com/typesafe-ai)[discord](https://discord.gg/typesafe)[x](https://x.com/typesafeai)

[Powered byThis documentation is built and hosted on Mintlify, a developer documentation platform](https://www.mintlify.com/?utm_campaign=poweredBy&utm_medium=referral&utm_source=ts-docs)