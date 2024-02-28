---
title: API Reference

language_tabs:
  - json

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

| Type       | Address                         |
| ---------- | ------------------------------- |
| Sandbox    | https://api.envio.co.id/sandbox |
| Production | https://api.envio.co.id/v1      |

# Authentication

Envio uses API Keys to allow access to the API. You can get your API KEY in our client portal or request to envio sales person.

Envio expects for the API Key to be included in all API request to the server
in a header that looks like the following:

`Authorization: API_KEY`

or in url query parameters

`https://api.envio.co.id/sandbox?token=API_KEY`

<aside class="notice">
You must replace <code>API_KEY</code> with your personal API key.
</aside>

# Shipment Creating

## HTTP Request

`POST http://API_SERVER/distribution`

<aside class="notice">
You must replace <code>API_SERVER</code> with our production or sandbox server that mentioned above.
</aside>

## Request

> Example Body Request:

```json
{
  "ref_code": "ID_SO20230726000340",
  "cod_value": 23000,
  "pickup_address": {
    "name": "PERGUDANGAN KOSAMBI PERMAI",
    "contact_person": "PERGUDANGAN KOSAMBI PERMAI",
    "phone_number": "628767438745",
    "address": "JL. RAYA PERANCIS NO.17, BELIMBING, KEC. KOSAMBI, KABUPATEN TANGERANG, BANTEN 15212",
    "province": "Banten",
    "regency": "kabupaten tangerang",
    "district": "kosambi",
    "village": "belimbing",
    "latitude": 38.8951,
    "longitude": -77.0364
  },
  "recipient": {
    "contact_person": "SAPTA APRIYANA",
    "phone_number": "6285156701828",
    "address": "JL.PENGADEGAN UTARA NO.1, KEL.CIKOKO, KEC.PANCORAN,KOTA JAKARTA SELATAN, DKI JAKARTA",
    "province": "DKI Jakarta",
    "regency": "Jakarta Selatan",
    "district": "Pancoran",
    "village": "cikoko",
    "latitude": 38.8951,
    "longitude": -77.0364
  },
  "items": [
    {
      "item_code": "2192x127y",
      "item_name": "Air Mineral 300 ML",
      "quantity": 1,
      "weight": 10,
      "long": 10,
      "high": 20,
      "wide": 30,
      "unit_price": 12500
    }
  ],
  "eta_at": "2023-07-27T15:40:20+07:00",
  "etd_at": "2023-07-27T15:40:20+07:00"
}
```

| Fields                                  | Required (Y/N) | Type                        | Description                                                                                                                |
| --------------------------------------- | -------------- | --------------------------- | -------------------------------------------------------------------------------------------------------------------------- |
| ref_code                                | Y              | String                      | Your refference code, can be your order number or any refference code in your application                                  |
| cod_value                               | N              | Decimal                     | If your shipment need us to collect the money on delivery, fill 0 if you dont need it                                      |
| pickup_address                          | Y              | Object                      | -                                                                                                                          |
| <div align="right">name</div>           | Y              | String                      | custom name for this address, ex: "DC Jakarta"                                                                             |
| <div align="right">contact_person</div> | Y              | String                      | Contact person for pickup in your warehouse                                                                                |
| <div align="right">phone_number</div>   | Y              | String                      | Phone number of contact person                                                                                             |
| <div align="right">address</div>        | Y              | String                      | Detailed address for pick-up                                                                                               |
| <div align="right">province</div>       | N              | String                      | Name of pickup address province                                                                                            |
| <div align="right">regency</div>        | N              | String                      | Name of pickup address regency                                                                                             |
| <div align="right">district</div>       | N              | String                      | Name of pickup address district                                                                                            |
| <div align="right">village</div>        | N              | String                      | Name of pickup address village                                                                                             |
| <div align="right">latitude</div>       | N              | Float                       | Latitude coordinate                                                                                                        |
| <div align="right">longitude</div>      | N              | Float                       | Longitude coordinate                                                                                                       |
| recipient                               | Y              | Object                      | -                                                                                                                          |
| <div align="right">contact_person</div> | Y              | String                      | Recipient full name                                                                                                        |
| <div align="right">phone_number</div>   | Y              | String                      | Phone number of recipient                                                                                                  |
| <div align="right">address</div>        | Y              | String                      | Detailed address recipient                                                                                                 |
| <div align="right">province</div>       | N              | String                      | Name of recipient province                                                                                                 |
| <div align="right">regency</div>        | N              | String                      | Name of recipient regency                                                                                                  |
| <div align="right">district</div>       | N              | String                      | Name of recipient district                                                                                                 |
| <div align="right">village</div>        | N              | String                      | Name of recipient village                                                                                                  |
| <div align="right">latitude</div>       | N              | Float                       | Latitude coordinate                                                                                                        |
| <div align="right">longitude</div>      | N              | Float                       | Longitude coordinate                                                                                                       |
| items                                   | N              | Array Object                | -                                                                                                                          |
| <div align="right">item_code</div>      | N              | String                      | can be used for unique items                                                                                               |
| <div align="right">item_name</div>      | Y              | String                      | Name of items                                                                                                              |
| <div align="right">quantity</div>       | Y              | Float                       | quantity of items                                                                                                          |
| <div align="right">weight</div>         | N              | Float                       | weight of items                                                                                                            |
| <div align="right">long</div>           | N              | Float                       | long of items                                                                                                              |
| <div align="right">high</div>           | N              | Float                       | high of items                                                                                                              |
| <div align="right">wide</div>           | N              | Float                       | wide of items                                                                                                              |
| <div align="right">unit_price</div>     | N              | Float                       | unit price of items                                                                                                        |
| eta_at                                  | Y              | Date time format (ISO 8601) | Estimated time arrival, if any your shipment has window receiving time, using format: 2023-07-28T07:20:24+07:00 (ISO 8601) |
| etd_at                                  | Y              | Date time format (ISO 8601) | Estimated time departure, scheduled pick-up time, using format: 2023-07-28T07:20:24+07:00 (ISO 8601)                       |
|                                         |

## Response

> Example Body Response:

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

| Parameter      | Description                                |
| -------------- | ------------------------------------------ |
| id             | Envio shipment ids                         |
| code           | Envio unique shipment code (resi number)   |
| ref_code       | Your refference code that you input before |
| eprint_receipt | link to print receipt                      |

# Shipment Updating

## HTTP Request

`PUT http://API_SERVER/distribution`

<aside class="notice">
You must replace <code>API_SERVER</code> with our production or sandbox server that mentioned above.
</aside>

## Request

> Example Body Request:

```json
{
  "ref_code": "ID_SO20230726000340",
  "cod_value": 23000
}
```

| Fields    | Required (Y/N) | Type    | Description                                                                               |
| --------- | -------------- | ------- | ----------------------------------------------------------------------------------------- |
| ref_code  | Y              | String  | Your refference code, can be your order number or any refference code in your application |
| cod_value | N              | Decimal | If your shipment need us to collect the money on delivery, fill 0 if you dont need it     |

## Response

> Example Body Response:

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

| Parameter      | Description                                |
| -------------- | ------------------------------------------ |
| id             | Envio shipment ids                         |
| code           | Envio unique shipment code (resi number)   |
| ref_code       | Your refference code that you input before |
| eprint_receipt | link to print receipt                      |

# Shipment Tracking

## HTTP Request

`GET http://API_SERVER/tracking/distribution`

<aside class="notice">
You must replace <code>API_SERVER</code> with our production or sandbox server that mentioned above.
</aside>

## Request

| Query Parameter | Required(Y/N) | Description                                                   |
| --------------- | ------------- | ------------------------------------------------------------- |
| code            | Y             | You can fill with your refference code or envio shipment code |

`GET http://API_SERVER/tracking/distribution?code=ID_SO20230726000340`

## Response

> Example Body Response:

```json
{
  "message": "success",
  "data": {
    "id": "53ab0a61-508d-4094-aa61-b4dbce0bd2d2",
    "code": "S4563844412",
    "ref_code": "ID_SO20230726000386",
    "eta_at": "2023-06-09T23:00:00Z",
    "ata_at": "2023-06-09T13:46:00Z",
    "etd_at": "2023-06-08T23:00:00Z",
    "atd_at": "2023-06-08T19:00:00Z",
    "received_by": "Robert",
    "status": "delivered",
    "cod_value": 23000,
    "cod_status": "collected",
    "logs": [
      {
        "message": "Pengiriman telah selesai, diterima oleh (Robert)",
        "recorded_at": "2023-06-09T01:46:00Z",
        "latitude": -6.2999841,
        "longitude": 107.1501828
      },
      {
        "message": "Pengiriman dalam perjalanan menuju lokasi anda",
        "recorded_at": "2023-06-09T01:46:00Z",
        "latitude": -6.2996329,
        "longitude": 107.1503314
      },
      {
        "message": "Pengiriman telah dijadwalkan untuk menuju lokasi penerima",
        "recorded_at": "2023-06-08T16:43:00Z",
        "latitude": -6.2996329,
        "longitude": 107.1503314
      },
      {
        "message": "Pengiriman anda berhasil dipickup, barang diterima di (BKI 01 - Chekpoint Bekasi)",
        "recorded_at": "2023-06-08T16:40:00Z",
        "latitude": -6.2996329,
        "longitude": 107.1503314
      },
      {
        "message": "Paket telah dijadwalkan untuk dipickup",
        "recorded_at": "2023-06-08T16:37:00Z",
        "latitude": 0,
        "longitude": 0
      },
      {
        "message": "Satrio membuat order pengiriman",
        "recorded_at": "2023-06-08T16:24:00Z",
        "latitude": 0,
        "longitude": 0
      }
    ]
  }
}
```

| Parameter   | Description                                                                                                      |
| ----------- | ---------------------------------------------------------------------------------------------------------------- |
| id          | Envio shipment ids                                                                                               |
| code        | Envio unique shipment code                                                                                       |
| ref_code    | Your refference code, can be your order number or any refference code in your application                        |
| eta_at      | estimated time arrival -- estimated time for delivery, Date time format (ISO 8601)                               |
| ata_at      | actual time arrival -- actual delivered time, will appear when delivered - Date time format (ISO 8601)           |
| etd_at      | estimated time departure -- estimated time for pickup, Date time format (ISO 8601)                               |
| atd_at      | actual time departure -- actual pickup time, will appear when pick-up already done - Date time format (ISO 8601) |
| received_by | name of who received the packages                                                                                |
| status      | - new (shipment was created)                                                                                     |
|             | - on_pickup (packages is in pickup process)                                                                      |
|             | - on_delivery (packages is on the way to the recipient's location)                                               |
|             | - on_transit (packages is on the way to envio hubs)                                                              |
|             | - Console (packages is in envio hubs)                                                                            |
|             | - delivered (packages delivered)                                                                                 |
|             | - disputed (failed to reach recipient, will back to envio hubs)                                                  |
| cod_value   | the amount that envio should collecting in delivery                                                              |
| cod_status  | - '' (no cod or not collected by envio)                                                                          |
|             | - collected (collected by envio)                                                                                 |
| logs        | shipment process logs                                                                                            |

# Shipment Cancelling

## HTTP Request

`DELETE http://API_SERVER/distribution`

<aside class="notice">
You must replace <code>API_SERVER</code> with our production or sandbox server that mentioned above.
</aside>

## Request

> Example Body Request:

```json
{
  "code": "S4563844412",
  "ref_code": "ID_SO20230726000386"
}
```

| Fields   | Required (Y/N) | Type   | Description                                |
| -------- | -------------- | ------ | ------------------------------------------ |
| code     | Y              | String | Envio shipment code (Resi Number)          |
| ref_code | Y              | String | Your refference code that you input before |

## Response

> Example Body Response:

```json
{
  "message": "success"
}
```

# Callback Shipment (Webhook)

A callback is an webhook that notify your own system at various stages of shipment (e.g. at the start or end of an shipment, before or after a pick-up, etc). We will send an POST Http Request with JSON body.

You can set your webhook URL in client area.

## Update PerItem/SKU

Event when shipment is update item/sku

```json
{
  "code": "S4563844412",
  "ref_code": "ID_SO20230726000386",
  "item": {
    "item_code": "2192x127y",
    "item_name": "Air Mineral 300 ML",
    "quantity": 2,
    "weight": 10,
    "long": 10,
    "high": 20,
    "wide": 30
  }
}
```

## Assign Driver

Event when shipment is assign driver

```json
{
  "code": "M0000000001",
  "shipment": {
    "code": "S4563844412",
    "ref_code": "ID_SO20230726000386"
  },
  "driver_name": "Usep",
  "driver_phone": "6281897381723",
  "vehicle_number": "B 8219 K"
}
```

## Manifested

Event when shipment is scheduled

```json
{
  "code": "M0000000001",
  "shipment": {
    "code": "S4563844412",
    "ref_code": "ID_SO20230726000386"
  },
  "status": "manifested"
}
```

## Pick-up Succeed

Event when shipment is picked-up

```json
{
  "code": "M0000000001",
  "shipment": {
    "code": "S4563844412",
    "ref_code": "ID_SO20230726000386"
  },
  "status": "picked_up",
  "ata_at": "2023-06-09T23:00:00Z"
}
```

## Pick-up Failed

Event when shipment is failed to pick-up

```json
{
  "code": "M0000000001",
  "shipment": {
    "code": "S4563844412",
    "ref_code": "ID_SO20230726000386"
  },
  "status": "picked_up_failed",
  "message": "Barang belum ready di pickup"
}
```

## Delivered

Event when shipment is delivered

```json
{
  "code": "M0000000001",
  "shipment": {
    "code": "S4563844412",
    "ref_code": "ID_SO20230726000386"
  },
  "status": "delivered",
  "received_by": "Robert",
  "cod_value": 23000,
  "cod_status": "collected",
  "ata_at": "2023-06-09T23:00:00Z",
  "images": [
    "https://xxxx.png"
    "https://yyyy.png"
  ]
}
```

## Delivery Failed

Event when shipment is failed to be delivered with any reasons

```json
{
  "code": "M0000000001",
  "shipment": {
    "code": "S4563844412",
    "ref_code": "ID_SO20230726000386"
  },
  "status": "delivery_failed",
  "ata_at": "2023-06-09T23:00:00Z",
  "message": "failed delivery reason here"
}
```

## Delivery Resend

Event when shipment is failed to be delivered with any reasons

```json
{
  "code": "M0000000001",
  "shipment": {
    "code": "S4563844412",
    "ref_code": "ID_SO20230726000386"
  },
  "status": "resend",
  "ata_at": "2023-06-09T23:00:00Z",
  "eta_at": "2023-06-10T23:00:00Z",
  "message": "failed delivery reason here"
}
```

## Cancelled

Event when shipment goods was returned

```json
{
  "code": "M0000000001",
  "shipment": {
    "code": "S4563844412",
    "ref_code": "ID_SO20230726000386"
  },
  "status": "cancelled",
  "received_by": "Robert",
  "ata_at": "2023-06-09T23:00:00Z"
}
```

## Returned

Event when shipment goods was returned

```json
{
  "code": "M0000000001",
  "shipment": {
    "code": "S4563844412",
    "ref_code": "ID_SO20230726000386"
  },
  "status": "returned",
  "received_by": "Robert",
  "ata_at": "2023-06-09T23:00:00Z"
}
```
