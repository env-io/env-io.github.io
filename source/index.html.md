---
title: API Reference

language_tabs: # must be one of https://github.com/rouge-ruby/rouge/wiki/List-of-supported-languages-and-lexers
  - http

includes:
  - errors

search: true

code_clipboard: true

meta:
  - name: description
    content: Documentation for Envio Logistics Distribution Service API
---

# Overview

This API is used for Envio Logistics client that use our distribution service
to create, cancel and track the shipment.

API server address:
| Type | Address |
| ------------ | -------------------------------------------------------------------------------- |
| Sandbox | https://api.envio.co.id/sandbox |
| Production | https://api.envio.co.id/v1 |

# Authentication

Envio uses API Keys to allow access to the API. You can get your API KEY in our client portal or request to envio sales person.

Envio expects for the API Key to be included in all API request to the server
in a header or in url query parameters that looks like the following:

`Authorization: Bearer API_KEY`

or

`https://api.envio.co.id/sandbox?token=API_KEY`

<aside class="notice">
You must replace <code>API_KEY</code> with your personal API key.
</aside>

# Shipment Creating

## Http Request

`POST http://API_SERVER/tms/delivery/shipment/customer`

<aside class="notice">
You must replace <code>API_SERVER</code> with our production or sandbox server that mentioned above.
</aside>

## Request

| Fields         | Required (Y/N) | Type                            | Description                                                                                                                |
| -------------- | -------------- | ------------------------------- | -------------------------------------------------------------------------------------------------------------------------- |
| ref_code       | N              | String                          | Your refference code, can be your order number or any refference code in your application                                  |
| cod_value      | N              | Decimal                         | If your shipment need us to collect the money on delivery, fill 0 if you dont need it                                      |
| pickup_address | Y              | Object                          | -                                                                                                                          |
| name           | Y              | String                          | -                                                                                                                          |
| contact_person | Y              | String                          | -                                                                                                                          |
| recipient      | Y              | Object                          | -                                                                                                                          |
| eta_at         | Y              | Date and time format (ISO 8601) | Estimated time arrival, if any your shipment has window receiving time, using format: 2023-07-28T07:20:24+07:00 (ISO 8601) |
| etd_at         | Y              | Date and time format (ISO 8601) | Estimated time departure, scheduled pick-up time, using format: 2023-07-28T07:20:24+07:00 (ISO 8601)                       |

## Response

# Shipment Tracking

## Request

## Response

# Shipment Cancelling

## Request

## Response

## Get All Kittens

```ruby
require 'kittn'

api = Kittn::APIClient.authorize!('meowmeowmeow')
api.kittens.get
```

```python
import kittn

api = kittn.authorize('meowmeowmeow')
api.kittens.get()
```

```shell
curl "http://example.com/api/kittens" \
  -H "Authorization: meowmeowmeow"
```

```javascript
const kittn = require("kittn");

let api = kittn.authorize("meowmeowmeow");
let kittens = api.kittens.get();
```

> The above command returns JSON structured like this:

```json
[
  {
    "id": 1,
    "name": "Fluffums",
    "breed": "calico",
    "fluffiness": 6,
    "cuteness": 7
  },
  {
    "id": 2,
    "name": "Max",
    "breed": "unknown",
    "fluffiness": 5,
    "cuteness": 10
  }
]
```

This endpoint retrieves all kittens.

### HTTP Request

`GET http://example.com/api/kittens`

### Query Parameters

| Parameter    | Default | Description                                                                      |
| ------------ | ------- | -------------------------------------------------------------------------------- |
| include_cats | false   | If set to true, the result will also include cats.                               |
| available    | true    | If set to false, the result will include kittens that have already been adopted. |

<aside class="success">
Remember — a happy kitten is an authenticated kitten!
</aside>

## Get a Specific Kitten

```ruby
require 'kittn'

api = Kittn::APIClient.authorize!('meowmeowmeow')
api.kittens.get(2)
```

```python
import kittn

api = kittn.authorize('meowmeowmeow')
api.kittens.get(2)
```

```shell
curl "http://example.com/api/kittens/2" \
  -H "Authorization: meowmeowmeow"
```

```javascript
const kittn = require("kittn");

let api = kittn.authorize("meowmeowmeow");
let max = api.kittens.get(2);
```

> The above command returns JSON structured like this:

```json
{
  "id": 2,
  "name": "Max",
  "breed": "unknown",
  "fluffiness": 5,
  "cuteness": 10
}
```

This endpoint retrieves a specific kitten.

<aside class="warning">Inside HTML code blocks like this one, you can't use Markdown, so use <code>&lt;code&gt;</code> blocks to denote code.</aside>

### HTTP Request

`GET http://example.com/kittens/<ID>`

### URL Parameters

| Parameter | Description                      |
| --------- | -------------------------------- |
| ID        | The ID of the kitten to retrieve |

## Delete a Specific Kitten

```ruby
require 'kittn'

api = Kittn::APIClient.authorize!('meowmeowmeow')
api.kittens.delete(2)
```

```python
import kittn

api = kittn.authorize('meowmeowmeow')
api.kittens.delete(2)
```

```shell
curl "http://example.com/api/kittens/2" \
  -X DELETE \
  -H "Authorization: meowmeowmeow"
```

```javascript
const kittn = require("kittn");

let api = kittn.authorize("meowmeowmeow");
let max = api.kittens.delete(2);
```

> The above command returns JSON structured like this:

```json
{
  "id": 2,
  "deleted": ":("
}
```

This endpoint deletes a specific kitten.

### HTTP Request

`DELETE http://example.com/kittens/<ID>`

### URL Parameters

| Parameter | Description                    |
| --------- | ------------------------------ |
| ID        | The ID of the kitten to delete |
