# Order Management (Retailers) - Example Responses

## List Carriers Response

**Status**: 200 OK

```json
[
  {
    "id": 144,
    "slug": "2go",
    "name": "2GO"
  },
  {
    "id": 30,
    "slug": "4px",
    "name": "4PX"
  }
]
```

## List Returns Response

**Status**: 200 OK

```json
{
  "count": 1,
  "next": null,
  "previous": null,
  "results": [
    {
      "id": "6dc60007-8f4b-458a-8802-6f1d21a8fbc7",
      "quantity": 1,
      "order": {
        "url": "https://www.sandbox.the-edge.io/restapi/v4/orders/234419/",
        "retailer": "https://www.sandbox.the-edge.io/restapi/v4/customers/224/",
        "order_reference": "200300-2021-01-02",
        "order_date": "2021-02-01T00:00:00",
        "status": "RMA_REC",
        "purchase_order_reference": null,
        "end_user_purchase_order_reference": "47190100",
        "additional_order_reference": "0038",
        "comment": null,
        "test_flag": false,
        "supplier": "https://www.sandbox.the-edge.io/restapi/v4/suppliers/210/",
        "items": [
          {
            "url": "https://www.sandbox.the-edge.io/restapi/v4/items/247427/",
            "part_number": "66682708",
            "retailer_sku_reference": "6254354307031",
            "supplier_sku_reference": null,
            "line_reference": "1",
            "quantity": 2,
            "name": null,
            "description": "JL LUX TE BASE BK LIFT 210",
            "status": "RMA_REC",
            "unit_cost_price": null,
            "subtotal": null,
            "tax": null,
            "tax_rate": null,
            "total": null,
            "promised_date": "2021-02-05T00:00:00",
            "retailer_additional_reference": null
          }
        ],
        "currency_code": "GBP",
        "subtotal": null,
        "tax": null,
        "total": null,
        "shipping_address": {
          "country": "United Kingdom",
          "line_1": "Order placed Branch",
          "line_2": "",
          "city": null,
          "postal_code": "",
          "state": null,
          "phone": null,
          "full_name": "Order placed Branch",
          "email": null
        },
        "retailer_data": {
          "uuid": "213b5935-cfc6-4055-b1e1-a88807322355",
          "name": "Retailer name",
          "email": "",
          "phone": "",
          "tax_code": "",
          "address": {
            "line_1": "",
            "line_2": "",
            "city": "",
            "state": "",
            "country": "GB",
            "postal_code": ""
          }
        },
        "delivery_service_code": null
      },
      "order_item": {
        "url": "https://www.sandbox.the-edge.io/restapi/v4/items/247427/",
        "part_number": "66682708",
        "retailer_sku_reference": "6254354307031",
        "supplier_sku_reference": null,
        "line_reference": "1",
        "quantity": 2,
        "name": null,
        "description": "JL LUX TE BASE BK LIFT 210",
        "status": "RMA_REC",
        "unit_cost_price": null,
        "subtotal": null,
        "tax": null,
        "tax_rate": null,
        "total": null,
        "promised_date": null,
        "retailer_additional_reference": null
      },
      "return_reason": {
        "id": "2d755932-6feb-40bd-ae6b-e974be981980",
        "code": "250",
        "description": "Missing items",
        "is_enabled": true,
        "created_at": "2022-06-13T09:35:52.701216"
      },
      "return_reason_code": "250",
      "status": {
        "code": "RMA_REC",
        "description": "Return Approved"
      },
      "return_date": "2021-02-01 13:47:40",
      "requested_at": null,
      "requested_message": null,
      "authorised_at": null,
      "authorised_message": null,
      "declined_at": null,
      "declined_message": null,
      "rejected_at": null,
      "rejected_message": null,
      "approved_at": "2021-02-01 13:47:40",
      "created_at": "2022-06-13 09:42:27",
      "supplier": {
        "name": "Supplier Name"
      },
      "retailer": {
        "name": "Retailer name"
      },
      "return_approved": {
        "code": "300",
        "description": "Agreed return",
        "created_at": "2022-06-13T09:36:04.923484"
      },
      "return_rejected": null,
      "return_approved_amount": null,
      "return_approved_amount_status": null,
      "return_authorised_collection_date": null
    }
  ]
}
```

## List Orders Response (Pagination Example)

**Status**: 200 OK

```json
{
  "count": 100,
  "next": "https://api.sandbox.virtualstock.com/restapi/v3/orders/?limit=10&offset=10",
  "previous": null,
  "results": [
    {
      "url": "https://api.sandbox.virtualstock.com/restapi/v3/orders/12345/",
      "order_reference": "ORDER-001",
      "order_date": "2024-01-15T10:30:00",
      "status": "new"
    }
  ]
}
```
