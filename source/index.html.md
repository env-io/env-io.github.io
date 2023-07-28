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

| Fields         | Required (Y/N) | Type                            | Description                                                                                                                                           |
| -------------- | -------------- | ------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------- |
| ref_code       | Y              | String                          | Your refference code, can be your order number or any refference code in your application                                                             |
| cod_value      | N              | Decimal                         | If your shipment need us to collect the money on delivery, fill 0 if you dont need it                                                                 |
| pickup_address | Y              | Object                          | This pickup address is for the pickup address for the goods to be sent                                                                                |
| name           | Y              | String                          | Pickup Address name                                                                                                                                   |
| contact_person | Y              | String                          | Pickup Address contatct person                                                                                                                        |
| address        | Y              | String                          | You can fill in the detailed address of Jl, village, district, regency, province here or you fill in the request village, district, regency, province |
| province       | N              | String                          | Province of the pickup address                                                                                                                        |
| regency        | N              | String                          | Regency of the pickup address                                                                                                                         |
| district       | N              | String                          | District of the pickup address                                                                                                                        |
| village        | N              | String                          | Village of the pickup address                                                                                                                         |
| recipient      | Y              | Object                          | This recipient is for the destination address of the goods to be sent                                                                                 |
| contact_person | Y              | String                          | Recipeint Contact person                                                                                                                              |
| address        | Y              | String                          | You can fill in the detailed address of Jl, village, district, regency, province here or you fill in the request village, district, regency, province |
| province       | N              | String                          | Province of the recipient                                                                                                                             |
| regency        | N              | String                          | Regency of the recipient                                                                                                                              |
| district       | N              | String                          | District of the recipient                                                                                                                             |
| village        | N              | String                          | Village of the recipient                                                                                                                              |
| eta_at         | Y              | Date and time format (ISO 8601) | Estimated time arrival, if any your shipment has window receiving time, using format: 2023-07-28T07:20:24+07:00 (ISO 8601)                            |
| etd_at         | Y              | Date and time format (ISO 8601) | Estimated time departure, scheduled pick-up time, using format: 2023-07-28T07:20:24+07:00 (ISO 8601)                                                  |
| items          | N              | Array                           | -                                                                                                                                                     |
| item_name      | Y              | string                          | Items to be shipped                                                                                                                                   |
| quantity       | Y              | decimal                         | The quantity to be sent by default contains 1                                                                                                         |
| weight         | N              | decimal                         | Weight contains the unit of the item                                                                                                                  |

## Response

```json
{
  "message": "success",
  "data": {
    "id": "522fe017-4207-481e-b290-ffc2bb5d801c",
    "code": "S0503380732",
    "ref_code": "ID_SO20230726000340",
    "eprint_receipt": "https://sandbox.envio.co.id/print/resi/522fe017-4207-481e-b290-ffc2bb5d801c"
  }
}
```

# Shipment Tracking

## HTTP Request

`GET http://API_SERVER/tracking/customer`

<aside class="notice">
You must replace <code>API_SERVER</code> with our production or sandbox server that mentioned above.
</aside>

### Query Parameters

| Parameter | Required(Y/N) | Description                                          |
| --------- | ------------- | ---------------------------------------------------- |
| code      | Y             | You can fill in the Refference Code or Shipment Code |

## Response

```json
{
  "message": "success",
  "data": {
    "id": "53ab0a61-508d-4094-aa61-b4dbce0bd2d2",
    "code": "S4563844412",
    "ref_code": "ID_SO20230726000386",
    "tracking_code": "",
    "eta_at": "2023-07-27T08:40:00Z",
    "ata_at": "0001-01-01T00:00:00Z",
    "received_by": "",
    "status": "new",
    "cod_value": 23000,
    "cod_status": "",
    "logs": [
      {
        "message": "Envio Admin membuat order pengiriman",
        "recorded_at": "2023-07-28T03:28:00Z",
        "latitude": 0,
        "longitude": 0
      },
      {
        "action": "draft_shipment",
        "message": "Pengiriman anda terbuat",
        "recorded_at": "0001-01-01T00:00:00Z",
        "latitude": 0,
        "longitude": 0
      }
    ]
  }
}
```

# Shipment Cancelling

## HTTP Request

`DELETE http://API_SERVER/tms/delivery/shipment/customer`

<aside class="notice">
You must replace <code>API_SERVER</code> with our production or sandbox server that mentioned above.
</aside>

## Request

| Fields   | Required (Y/N) | Type   | Description                                                                               |
| -------- | -------------- | ------ | ----------------------------------------------------------------------------------------- |
| ref_code | Y              | String | Your refference code, can be your order number or any refference code in your application |

## Response

```json
{
  "message": "success"
}
```