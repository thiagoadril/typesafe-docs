---
title: "Changelog - TypeSafe AI"
date: "2026-09-18T09:14:15.475Z"
description: "Python clients for the TypeSafe AI API"
url: "https://docs.typesafe.ai/sdk/python/changelog"
publisher: "TypeSafe AI"
lang: "en"
logo_url: "https://docs.typesafe.ai/mintlify-assets/_mintlify/favicons/ts-docs/zg2v0DiYB7xPw0I2/_generated/favicon/android-chrome-192x192.png"
logo_type: "png"
logo_size: 8885
logo_height: 192
logo_width: 192
logo_size_pretty: "8.88 kB"
image_url: "https://ts-docs.mintlify.app/mintlify-assets/_next/image?url=%2F_mintlify%2Fapi%2Fog%3Fdivision%3DPython%2BSDK%26title%3DChangelog%26description%3DPython%2Bclients%2Bfor%2Bthe%2BTypeSafe%2BAI%2BAPI%26theme%3Df0580ae664a0195833f0555d&w=1200&q=100"
image_type: "png"
image_size: 30620
image_height: 630
image_width: 1200
image_size_pretty: "30.6 kB"
word_count: 330
reading_time: "2 min read"
---

[← Voltar ao índice](./README.md)


## Table of Contents

- [v0.7.0 (2026-09-18)](#v070-2026-09-18)
  - [Breaking Changes](#breaking-changes)
  - [Bug fixes](#bug-fixes)
  - [Features](#features)
- [v0.6.0 (2026-09-15)](#v060-2026-09-15)
  - [Breaking Changes](#breaking-changes-1)
  - [Features](#features-1)
  - [Bug fixes](#bug-fixes-1)
  - [Documentation](#documentation)
- [v0.5.7 (2026-09-14)](#v057-2026-09-14)
- [On this page](#on-this-page)

---

Python SDK

Python clients for the TypeSafe AI API

## v0.7.0 (2026-09-18)

### Breaking Changes

- ser/de library has been changed from `msgspec` to `pydantic`

### Bug fixes

- `str` subclasses are now correctly serialized as strings instead of lists of characters

### Features

- the `system_one` method now accepts a new `response_model` argument that can be set to a desired `pydantic` model for additional *type-safety*

## v0.6.0 (2026-09-15)

### Breaking Changes

- accept `Score.criteria` as an ordered sequence instead of a dictionary keyed by integers

### Features

- improve type annotations on SDK inputs to accept abstract types like `Mapping` and `Sequence`
- improve error messages to include http details and metadata

### Bug fixes

- handle invalid values in `RetryPolicy`
- make exceptions and responses picklable

### Documentation

- link more concepts from main [docs](https://docs.typesafe.ai/)

## v0.5.7 (2026-09-14)

This is the initial public release of TypeSafe Python SDK. Learn more in the [documentation](https://docs.typesafe.ai/sdk/python).

Was this page helpful?

[Usage](https://docs.typesafe.ai/sdk/python/usage)

[Previous](https://docs.typesafe.ai/sdk/python/usage) [API reference Next](https://docs.typesafe.ai/sdk/python/api)

[github](https://github.com/typesafe-ai) [discord](https://discord.gg/typesafe) [x](https://x.com/typesafeai)

[Powered byThis documentation is built and hosted on Mintlify, a developer documentation platform](https://www.mintlify.com/?utm_campaign=poweredBy&utm_medium=referral&utm_source=ts-docs)

## On this page

- [v0.7.0 (2026-09-18)](https://docs.typesafe.ai/sdk/python/changelog#v070-2026-09-18)
  - [Breaking Changes](https://docs.typesafe.ai/sdk/python/changelog#breaking-changes)
  - [Bug fixes](https://docs.typesafe.ai/sdk/python/changelog#bug-fixes)
  - [Features](https://docs.typesafe.ai/sdk/python/changelog#features)
- [v0.6.0 (2026-09-15)](https://docs.typesafe.ai/sdk/python/changelog#v060-2026-09-15)
  - [Breaking Changes](https://docs.typesafe.ai/sdk/python/changelog#breaking-changes_1)
  - [Features](https://docs.typesafe.ai/sdk/python/changelog#features_1)
  - [Bug fixes](https://docs.typesafe.ai/sdk/python/changelog#bug-fixes_1)
  - [Documentation](https://docs.typesafe.ai/sdk/python/changelog#documentation)
- [v0.5.7 (2026-09-14)](https://docs.typesafe.ai/sdk/python/changelog#v057-2026-09-14)

[github](https://github.com/typesafe-ai)[discord](https://discord.gg/typesafe)[x](https://x.com/typesafeai)

[Powered byThis documentation is built and hosted on Mintlify, a developer documentation platform](https://www.mintlify.com/?utm_campaign=poweredBy&utm_medium=referral&utm_source=ts-docs)