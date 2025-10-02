# Order Creation - Example Responses

## Create an Order Response

**Status**: 200 OK

```json
{
  "url": "https://oms.sandbox.the-edge.io/restapi/v3/orders/189785/",
  "retailer": "https://oms.sandbox.the-edge.io/restapi/v3/customers/203/",
  "retailer_name": "MyCompanyName",
  "supplier": "https://oms.sandbox.the-edge.io/restapi/v3/suppliers/2540/",
  "supplier_name": "Supplier Name",
  "order_number": "222555000_100000600003",
  "order_date": "2020-09-02T13:30:02",
  "customer_ref": "123453/1",
  "retailer_ref": null,
  "supplier_ref": null,
  "invoice_title": "Mr",
  "invoice_full_name": null,
  "invoice_address_1": null,
  "invoice_address_2": null,
  "invoice_address_3": null,
  "invoice_postcode": null,
  "invoice_country": null,
  "invoice_phone": null,
  "invoice_email": null,
  "test_flag": false,
  "current_status": "New Order",
  "shipments": [
    {
      "url": "https://oms.sandbox.the-edge.io/restapi/v3/orders/9999999/shipments/1/",
      "shipment_id": null,
      "shipping_title": "Mr",
      "shipping_full_name": "B Jones",
      "shipping_address_1": "123 The Road",
      "shipping_address_2": "The Town",
      "shipping_address_3": "Reading",
      "shipping_postcode": "RG1 1AR",
      "shipping_country": "UK",
      "shipping_phone": "0123456789",
      "shipping_email": "test@gmail.com",
      "carrier_name": null,
      "carrier_service": null,
      "shipping": null,
      "total_price": null,
      "giftwrap": false,
      "signature": false,
      "expected_delivery_date": null,
      "dispatch_date": null,
      "tracking_number": null,
      "tracking_url": null,
      "current_status": "New Order",
      "items": [
        {
          "url": "https://oms.sandbox.the-edge.io/restapi/v3/items/9999999/",
          "part_number": "1234567",
          "line_ref": "1",
          "quantity": 1,
          "name": null,
          "description": "Widget1",
          "retailer_ref": null,
          "additional_ref": null,
          "supplier_ref": null,
          "cost": null,
          "shipping": null,
          "sub_total": null,
          "tax": null,
          "total": null,
          "current_status": "New Order",
          "dispatch_status": null,
          "dispatch_date": null,
          "delivery_date": null,
          "tracking_number": "",
          "tracking_url": "",
          "cancel_date": null,
          "cancel_reason": null,
          "cancel_quantity": null,
          "return_date": null,
          "return_code": null,
          "return_reason": null,
          "return_quantity": null,
          "promised_date": "2020-09-07T13:30:02"
        }
      ],
      "shipping_address_type": ""
    }
  ],
  "account_id": "SBG001",
  "order_channel": null
}
```
