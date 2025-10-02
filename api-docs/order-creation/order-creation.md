# Virtualstock API - Order Creation

## Create an Order

### POST `/restapi/v3.1/orders/?format=json`

With this call, you can generate a brand new order, and associate it to your supplier. The example request contains every possible field you could use in the sample request.

**NOTE**: This endpoint has version 3.1. If you wish to use the attribute `item.additional_ref` that maps this additional field to the suppliers SFTP API integration.

**Authorization**: Basic Auth

**Headers**:
- `Content-Type: application/json`

**Query Parameters**:
- `format=json`

## Attribute Summary

### Order-Level Fields

| Field | Required | Field type | Limit | Description | Sample content |
|-------|----------|------------|-------|-------------|----------------|
| supplier | Y | Text | 100 | Supplier ID (link) | https://domain/restapi/v2/suppliers/nnn/ where nnn is unique Supplier REST ID |
| order_number | Y | Text | 100 | Unique identifier for the order | TEST-180711145243 |
| order_date | Y | Date | 20 | The date of the order | 2018-07-11T14:52:43 |
| customer_ref | N | Text | 100 | End customers reference number, supplied by the retailer | ENDUSER-180711145343 |
| retailer_ref | N | Text | 100 | An additional reference that the retailer may wish to provide | CHANNEL-180711145343 |
| supplier_ref | N | Text | 100 | Supplier unique reference for the order | SUPPLIER-180711145343 |
| comments | N | Text | 255 | Free text field - text visible in Comments & Order History | Comment to the order |
| test_flag | N | Boolean | N/A | Flag to indicate this as a test order | True - for a test order |

### Invoice Address Fields

| Field | Required | Field type | Limit | Description | Sample content |
|-------|----------|------------|-------|-------------|----------------|
| invoice_title | N | Text | 100 | The title of the ordering customer | Mr, Miss, Mrs |
| invoice_full_name | N | Text | 100 | The full name of the ordering customer | Sarah Smith |
| invoice_address_1 | N | Text | 255 | First line of the address of the ordering customer | Penny Royal Road |
| invoice_address_2 | N | Text | 100 | Second line of the address of the ordering customer | Danbury |
| invoice_address_3 | N | Text | 100 | Third line of the address of the ordering customer | Chelmsford |
| invoice_postcode | N | Text | 100 | Postcode of the ordering customer | SK12 |
| invoice_country | N | Text | 100 | Country of the ordering customer | GB |
| invoice_phone | N | Text | 100 | Phone number of the ordering customer | 1793707666 |
| invoice_email | N | Text | 75 | Email address of the ordering customer | john@orderingcustomer.com |

### Shipping Address Fields

| Field | Required | Field type | Limit | Description | Sample content |
|-------|----------|------------|-------|-------------|----------------|
| shipping_title | N | Text | 100 | The title of the destination customer | Mr, Miss, Mrs |
| shipping_full_name | Y | Text | 100 | The full name of the destination customer | Peter Radshore |
| shipping_address_1 | Y | Text | 255 | First line of the address of the destination customer | Penny Royal Road |
| shipping_address_2 | N | Text | 100 | Second line of the address of the destination customer | Danbury |
| shipping_address_3 | N | Text | 100 | Third line of the address of the destination customer | Chelmsford |
| shipping_postcode | Y | Text | 100 | Postcode of the destination customer | LS28 |
| shipping_country | Y | Text | 100 | Country of the destination customer | GB |
| shipping_phone | N | Text | 100 | Phone number of the destination customer | 1793707686 |
| shipping_email | N | Text | 75 | Email address of the destination customer | peter@testing.com |

### Shipment Fields

| Field | Required | Field type | Limit | Description | Sample content |
|-------|----------|------------|-------|-------------|----------------|
| carrier_name | N | Text | 100 | Carrier slug value | dpd |
| carrier_service | N | Text | 100 | Carrier service name (10 characters for Order item split) | Next day |
| shipping | N | Decimal | 14 Digits 2 Decimals | Shipping cost charged to the end customer by the retailer | 5 |
| total_price | N | Decimal | 14 Digits 2 Decimals | Total price | 150 |
| expected_delivery_date | N | Date | 10 | Date of the expected delivery | 2018-07-12T08:00:00 |

### Order Item Fields

| Field | Required | Field type | Limit | Description | Sample content |
|-------|----------|------------|-------|-------------|----------------|
| items | node | node | Node | node | No data required |
| part_number | Y | Text | 255 | EAN, GTIN or other Product SKU identifier | 1004613 |
| line_ref | Y | Text | 100 | Retailers unique identifier for the line within an order | 100013292 |
| quantity | Y | Numeric | None | The ordered quantity | 1 |
| name | Y | Text | 255 | Name of the order item | The test widget 3892 |
| description | N | Text | 255 | Description of the order item | Test widget |
| retailer_ref | N | Text | 100 | An additional retailer reference that the retailer may wish to provide | RET1004613 |
| additional_ref | N | Text | 100 | An additional item reference that the retailer may wish to provide. NOTE this one maps to the supplier SFTP API integration. retailer_ref does not | ADD1004613 |
| cost | N | Decimal | 14 Digits 2 Decimals | The cost price of the item | 69 |
| shipping | N | Decimal | 14 Digits 2 Decimals | Shipping cost charged to the end customer by the retailer | 5 |
| sub_total | N | Decimal | 14 Digits 2 Decimals | Subtotal of the order line | 150 |
| tax | N | Decimal | 14 Digits 2 Decimals | VAT of the order line | 28 |
| total | N | Decimal | 14 Digits 2 Decimals | Total order line price (sub_total + tax) | 178 |
| promised_date | N | Date | 20 | Promise date of the order line. Should be populated in order to track supplier compliance. | 2018-07-14T08:00:00 |

## End-to-End Field Mapping

Mapping between the REST API, User interface and the Supplier SFTP API:

| REST API field | The UI on Virtualstock | Supplier SFTP API on Virtualstock V6 | Example data |
|----------------|------------------------|--------------------------------------|--------------|
| order_number | Supplier Order Number: | order_number | Y100009263 |
| order_date | Purchase Date: | order_date | Apr 16, 2021 9:01:33 |
| customer_ref | End User PO Number: | po_enduser | 254155338 |
| retailer_ref | Channel Order Reference: | retailer_ref | 20210416100202486721080 |
| shipping_title | To: | shipping_title | Mr |
| shipping_full_name | To: | shipping_full_name | Andrew Williams |
| shipping_address_1 | Address 1: | shipping_address_1 | Number 1 |
| shipping_address_2 | Address 2: | shipping_address_2 | Victoria Street |
| shipping_address_3 | Address 3: | shipping_address_3 | London |
| shipping_postcode | Postcode: | shipping_postcode | SW1E DFR |
| shipping_country | Country: | shipping_country | GB |
| shipping_phone | Mobile Phone No.: | shipping_phone | 98098098 |
| shipping_email | Email: | shipping_email | test@gmail.com |
| expected_delivery_date | Expected Delivery Date: | expected_delivery_date | April 21, 2021 |
| items | -- | -- | -- |
| part_number | Item SKU | part_number | 58000128 |
| additional_ref | ...more Additional Reference | additional_ref | ADD00128 |
| line_ref | ...more Line Ref | line_ref | 1 |
| quantity | Qty | quantity | 1 |
| name | description | description | Jo Malone London Myrrh & Tonka Cologne Intense, 100ml |
| promised_date | Promise Date | promised_date | 2021-04-21T09:23:00 |

## Request Body Example

```json
{
    "supplier": "https://api.sandbox.virtualstock.com/restapi/v3/suppliers/SUPPLIER_RESTFUL_ID/",
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
```
