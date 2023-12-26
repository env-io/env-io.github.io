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

| Type       | Address                            |
| ---------- | ---------------------------------- |
| Sandbox    | https://api.gescargo.co.id/sandbox |
| Production | https://api.gescargo.co.id/v1      |

# Authentication

Envio uses API Keys to allow access to the API. You can get your API KEY in our client portal or request to envio sales person.

Envio expects for the API Key to be included in all API request to the server
in a header that looks like the following:

`Authorization: Bearer API_KEY`

or in url query parameters

`https://api.gescargo.co.id/sandbox?token=API_KEY`

<aside class="notice">
You must replace <code>API_KEY</code> with your personal API key.
</aside>

# Stock

## HTTP Request

`POST http://API_SERVER/stock`

<aside class="notice">
You must replace <code>API_SERVER</code> with our production or sandbox server that mentioned above.
</aside>

## Request

> Example Body Request:

```json
{
  "warehouse_code": "ID_SO20230726000340",
  "item_name": "Beras 5Kg",
  "tonage": 5000,
  "quantity": 1000
}
```

| Fields         | Required (Y/N) | Type    | Description                   |
| -------------- | -------------- | ------- | ----------------------------- |
| warehouse_code | Y              | String  | Refference code for warehouse |
| item_name      | Y              | String  | Item name                     |
| tonage         | Y              | Float   | Tonage of the item, in gramm  |
| quantity       | Y              | Integer | Number of quantity            |

## Response

> Example Body Response:

```json
{
  "message": "success",
  "data": {
    "id": "522fe017-4207-481e-b290-ffc2bb5d801c"
  }
}
```

# Rencana Salur

## Call Back Request

> Example Body Request:

```json
{
  "warehouse_code": "ID_SO20230726000340",
  "doc_code": "DO8734072200",
  "dispatched_plan_at": "2023-12-27T00:00:00Z",
  "total_pbp": 307,
  "total_quantum": 3070,
  "area": {
    "id": "b64b3436-35bf-434e-a461-99318c654409",
    "village_id": "ef2fd678-2e7b-498d-ad00-8b2f72e4adf0",
    "village": {
      "id": "ef2fd678-2e7b-498d-ad00-8b2f72e4adf0",
      "name": "KALILUNJAR",
      "latitude": 0,
      "longitude": 0,
      "district": {
        "id": "4b8e9ce6-d484-11ed-afa1-0242ac120002",
        "name": "BANJARMANGU",
        "regency": {
          "id": "d304f69e-d483-11ed-afa1-0242ac120002",
          "name": "KAB. BANJARNEGARA",
          "sorting_dusun": false,
          "kanwil": {
            "id": "5b827df8-d483-11ed-afa1-0242ac120002",
            "name": "DI YOGYAKARTA / JATENG"
          }
        }
      }
    }
  }
}
```

## Response

> Example Body Response:

```json
{
  "message": "success",
  "data": [
    {
      "doc_out_code": "522fe017-4207-481e-b290-ffc2bb5d801c"
    }
  ]
}
```

# Proof Of Delivered

## Call Back Request

```json
{
  "bapang_periode": "202401",
  "doc_code": "DO8734072200",
  "bast_code": "DO8734072200",
  "delivered_at": "2023-12-27T08:00:00Z",
  "nama_pbp": "SUMINAH",
  "status": "delivered",
  "area": {
    "id": "b64b3436-35bf-434e-a461-99318c654409",
    "village_id": "ef2fd678-2e7b-498d-ad00-8b2f72e4adf0",
    "village": {
      "id": "ef2fd678-2e7b-498d-ad00-8b2f72e4adf0",
      "name": "KALILUNJAR",
      "latitude": 0,
      "longitude": 0,
      "district": {
        "id": "4b8e9ce6-d484-11ed-afa1-0242ac120002",
        "name": "BANJARMANGU",
        "regency": {
          "id": "d304f69e-d483-11ed-afa1-0242ac120002",
          "name": "KAB. BANJARNEGARA",
          "sorting_dusun": false,
          "kanwil": {
            "id": "5b827df8-d483-11ed-afa1-0242ac120002",
            "name": "DI YOGYAKARTA / JATENG"
          }
        }
      }
    }
  },
  "pod_image": "https://pod.gescargo.co.id/12388103921283123.jpg"
}
```

## Pergantian PBP

## Call Back Request

```json
{
  "bapang_periode": "202401",
  "doc_code": "DO8734072200",
  "bast_code": "DO87340722001234",
  "delivered_at": "2023-12-27T08:00:00Z",
  "nama_pbp": "SUMINAH",
  "status": "changed",
  "reason": "pindah rumah",
  "area": {
    "id": "b64b3436-35bf-434e-a461-99318c654409",
    "village_id": "ef2fd678-2e7b-498d-ad00-8b2f72e4adf0",
    "village": {
      "id": "ef2fd678-2e7b-498d-ad00-8b2f72e4adf0",
      "name": "KALILUNJAR",
      "latitude": 0,
      "longitude": 0,
      "district": {
        "id": "4b8e9ce6-d484-11ed-afa1-0242ac120002",
        "name": "BANJARMANGU",
        "regency": {
          "id": "d304f69e-d483-11ed-afa1-0242ac120002",
          "name": "KAB. BANJARNEGARA",
          "sorting_dusun": false,
          "kanwil": {
            "id": "5b827df8-d483-11ed-afa1-0242ac120002",
            "name": "DI YOGYAKARTA / JATENG"
          }
        }
      }
    }
  },
  "pod_image": "https://pod.gescargo.co.id/12388103921283123.jpg"
}
```
