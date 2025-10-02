# Virtualstock API - Order Management for Suppliers

## Acknowledge an Order

### POST `/restapi/v3/orders/{ORDER_URI}/acknowledge/?format=json`

This call allows you to acknowledge an order. The purpose of this is to allow suppliers to acknowledge orders in an automated fashion, however it can be used by retail users, should they wish to acknowledge on behalf of their suppliers (with prior consent), or if they are fulfilling their own orders (e.g., sending orders to their own warehouse).

**Authorization**: Basic Auth

**Headers**:
- `Content-Type: application/json`

**Path Parameters**:
- `ORDER_URI`: The unique REST ID for the order

**Query Parameters**:
- `format=json`

### Request Body Structure

```json
{
    "items": [
        {
            "part_number": "PartNumber_02",
            "line_ref": "100002",
            "quantity": 5,
            "sub_status": "Pending",
            "supplier_dispatch_date": "2019-10-10T12:00:00",
            "supplier_delivery_date": "2019-10-10T12:00:00",
            "comment": "Line acknowledged"
        }
    ]
}
```

### Field Definitions

| Field | Required | Field type | Limit | Description | Sample content |
|-------|----------|------------|-------|-------------|----------------|
| part_number | Y | Text | 255 | EAN, GTIN or other Product SKU identifier | 1004613 |
| line_ref | Y | Text | 100 | Retailers unique identifier for the line within an order | 100013292 |
| quantity | Y | Numeric | None | The ordered quantity | 1 |
| sub_status | N | Text | 100 | Sub-Statuses are based on the clients requirements, they will be a static list | Pending |
| supplier_dispatch_date | N | DateTime | 19 | Date of the expected Supplier Dispatch Date | 2018-07-12T08:00:00 |
| supplier_delivery_date | N | DateTime | 19 | Date of the expected Supplier Delivery Date | 2018-07-12T08:00:00 |
| comment | N | Text | 255 | Additional information that you wish to share with the client | Item may require fitting |

---

## Backorder an Order

### POST `/restapi/v4/orders/{ORDER_URI}/backorder/?format=json`

This call allows you to back-order an order. The purpose of this is to allow suppliers to acknowledge orders in an automated fashion, however it can be used by retail users, should they wish to acknowledge on behalf of their suppliers (with prior consent), or if they are fulfilling their own orders.

**Authorization**: Basic Auth

**Headers**:
- `Content-Type: application/json`

**Path Parameters**:
- `ORDER_URI`: The unique REST ID for the order

**Query Parameters**:
- `format=json`

### Request Body Structure

```json
{
    "items": [
        {
            "part_number": "PartNumber_02",
            "line_ref": "100002",
            "quantity": 10,
            "sub_status": "Pending",
            "supplier_dispatch_date": "2019-10-20T12:00:00",
            "supplier_delivery_date": "2019-10-23T12:00:00",
            "fulfillment_route": "Direct to customer",
            "comment": "Line set to backorder"
        }
    ]
}
```

### Field Definitions

| Field | Required | Field type | Limit | Description | Sample content |
|-------|----------|------------|-------|-------------|----------------|
| part_number | Y | Text | 255 | EAN, GTIN or other Product SKU identifier | 1004613 |
| line_ref | Y | Text | 100 | Retailers unique identifier for the line within an order | 100013292 |
| quantity | Y | Numeric | None | The ordered quantity | 1 |
| sub_status | Y | Text | 100 | Sub-Statuses are based on the clients requirements, they will be a static list | Pending |
| supplier_dispatch_date | Y | DateTime | 19 | Date of the expected Supplier Dispatch Date | 2018-07-12T08:00:00 |
| supplier_delivery_date | Y/N | DateTime | 19 | Mandatory for some retailers, The Date of the expected Supplier Delivery Date | 2018-07-12T08:00:00 |
| fulfillment_route | N/Y | Text | 255 | Note: not all retailers require this field, remove it from the payload if they do not. If they do you'll need to contact our support desk for a list of values to provide for each retailer | Direct to customer |
| comment | N | Text | 255 | Additional information that you wish to share with the client. Note some retailers do not support comments | Item may require fitting |

---

## Acknowledge a Cancellation

### POST `/restapi/v4/orders/{ORDER_URI}/cancel_acknowledge/?format=json`

This call allows you to acknowledge a cancellation for an order. The purpose of this is to allow suppliers to acknowledge cancellations in an automated fashion, however it can be used by retail users, should they wish to acknowledge on behalf of their suppliers (with prior consent), or if they are fulfilling their own orders.

**Authorization**: Basic Auth

**Headers**:
- `Content-Type: application/json`

**Path Parameters**:
- `ORDER_URI`: The unique REST ID for the order

**Query Parameters**:
- `format=json`

### Request Body Structure

```json
{
    "items": [
        {
            "part_number": "PartNumber_02",
            "line_ref": "100002",
            "quantity": 10,
            "comment": "I accept"
        }
    ]
}
```

### Field Definitions

| Field | Required | Field type | Limit | Description | Sample content |
|-------|----------|------------|-------|-------------|----------------|
| part_number | Y | Text | 255 | EAN, GTIN or other Product SKU identifier | 1004613 |
| line_ref | Y | Text | 100 | Retailers unique identifier for the line within an order | 100013292 |
| quantity | Y | Numeric | None | The ordered quantity | 1 |
| comment | N | Text | 255 | Additional information that you wish to share with the client | Item may require fitting |

---

## Dispatch an Order

### POST `/restapi/v4/orders/{ORDER_URI}/dispatch/?format=json`

This call allows you to Dispatch an order. The purpose of this is to allow suppliers to dispatch orders in an automated fashion, however it can be used by retail users, should they wish to dispatch on behalf of their suppliers (with prior consent), or if they are fulfilling their own orders.

**Authorization**: Basic Auth

**Headers**:
- `Content-Type: application/json`

**Path Parameters**:
- `ORDER_URI`: The unique REST ID for the order

**Query Parameters**:
- `format=json`

### Request Body Structure

```json
{
    "items": [
        {
            "part_number": "PartNumber_02",
            "line_ref": "100002",
            "quantity": 10,
            "supplier_dispatch_date": "2019-10-10",
            "supplier_delivery_date": "2019-10-12",
            "tracking_number": 1123581321,
            "carrier": "Fedex"
        }
    ]
}
```

### Field Definitions

| Field | Required | Field type | Limit | Description | Sample content |
|-------|----------|------------|-------|-------------|----------------|
| part_number | Y | Text | 255 | EAN, GTIN or other Product SKU identifier | 1004613 |
| line_ref | Y | Text | 100 | Retailers unique identifier for the line within an order | 100013292 |
| quantity | Y | Numeric | None | The ordered quantity | 1 |
| carrier | Y | Text | 255 | The carrier "slug" as listed on Virtualstock. e.g if the Carrier is DPD then the "slug" is "dpd" (ask your support team for the list of "slug" values for your carriers) | dpd |
| supplier_dispatch_date | Y | Date | 10 | Date of the expected Supplier Dispatch Date | 2019-10-10 |
| tracking_number | Y | Text | 100 | Tracking Number for the carrier selected | 34098675738421 |
| tracking_url | N | Text | 255 | Tracking URL associated to the carrier selected | https://track.dhlparcel.co.uk/ |

---

## Acknowledge a Return

### POST `/restapi/v4/orders/{ORDER_URI}/return_acknowledge/?format=json`

This call allows you to acknowledge a return request.

**Authorization**: Basic Auth

**Headers**:
- `Content-Type: application/json`

**Path Parameters**:
- `ORDER_URI`: The unique REST ID for the order

**Query Parameters**:
- `format=json`

### Request Body Structure

```json
{
    "items": [
        {
            "part_number": "PartNumber_01",
            "line_ref": "10001",
            "quantity": "2"
        }
    ]
}
```

---

## Create an Invoice

### POST `/restapi/v4/orders/{ORDER_URI}/invoice/?format=json`

Create an invoice for a dispatched order.

**Authorization**: Basic Auth

**Headers**:
- `Content-Type: application/json`

**Path Parameters**:
- `ORDER_URI`: The unique REST ID for the order

**Query Parameters**:
- `format=json`

*Note: Specific payload details should be obtained from Virtualstock support team*
