# Order Creation - Example Requests

## Create an Order

```bash
curl --location 'https://oms.the-edge.io/restapi/v3.1/orders/?format=json' \
--header 'Content-Type: application/json' \
--data-raw '{
"supplier": "https://oms.the-edge.io/restapi/v3/suppliers/SUPPLIER_RESTFUL_ID/",
"order_number": "608490239",
"order_date": "2019-10-07T15:32:05",
"invoice_title": "Mr",
"invoice_full_name": "Inv Full Name",
"invoice_address_1": "Inv Address 1",
"invoice_address_2": "Inv Address 2",
"invoice_address_3": "Inv Address 3",
"invoice_postcode": "Inv Postcode",
"invoice_country": "Inv Country",
"invoice_phone": "Inv Phone",
"invoice_email": "InvEmail@email.com",
"shipments": [
 {
 "shipping_title": "Mr",
 "shipping_full_name": "Ship Full Name",
 "shipping_address_1": "Ship Address 1",
 "shipping_address_2": "Ship Address 2",
 "shipping_address_3": "Ship Address 3",
 "shipping_postcode": "Ship Postcode",
 "shipping_country": "Ship Country",
 "shipping_phone": "Ship Phone",
 "shipping_email": "ShipPhone@email.com",
 "shipping": "10.00",
 "total_price": "50.00",
 "expected_delivery_date": "2019-10-20T00:00:00",
 "items": [
     {
     "part_number": "5397007210323",
     "line_ref": "00001",
     "quantity": 1,
     "name": "C&L AFFINI BACK TO WALL TOILE",
     "description": "Toilet",
     "retailer_ref": "Retailer Ref 1",
     "supplier_ref": "Supplier Ref 1",
     "additional_ref": "Additional Ref 1",
     "cost": "5.00",
     "shipping": "1.00",
     "sub_total": "6.00",
     "tax": "0.50",
     "total": "6.50",
     "promised_date": "2019-10-20T00:00:00"
     }
 ]
 }
]
}
'
```
