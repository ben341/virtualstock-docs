# Virtualstock API - Order Management for Retailers

## List Retailers

### GET `/restapi/v4/customers/`

List all your retailers.

**Authorization**: Basic Auth

**Parameters**:
- `format=json`

---

## List Orders (V3)

### GET `/restapi/v3/orders/?format=json`

To fetch orders, use the limit and offset parameters to scroll through pages of results.

**Authorization**: Basic Auth

**Pagination**:
- `"next": "https://oms.sandbox.the-edge.io/restapi/v3/orders?limit=10&offset=10"`
- `"previous": "https://oms.sandbox.the-edge.io/restapi/v3/orders?limit=10"`

### Query Parameters

Acquire a full list of orders for the retailer, which have been generated over the past 3 days.

In order to use these, you simply add the modifier after "/orders/?". If you wish to change these, you can use "&" between each modifier.

**NOTE**: For performance reasons, we do not return more than 3 days of results. `ord_days` should only be used if you are testing your integration and need to fetch new orders that are more than 3 days old. In production, you do NOT need to use `ord_days` but instead, fetch and process new orders every hour.

#### Date Filtering

- If `ord_days` is not set it will default to 2 days
- If `ord_days` and `chg_days` are both set, only `chg_days` is used

**If `ord_days` is set**:
- Orders will be filtered by order creation date
- The "from date" will be the current time minus number of specified ord_days
- The "to date" will be 73 hours greater than "from date"
- i.e., you can only list a maximum of 73 hours of orders, but you can iterate through incrementing ord_days

**If `chg_days` is set**:
- Orders will be filtered by order modified date
- The "from date" will be the current time minus number of specified chg_days
- The "to date" will be 73 hours greater than "from date"
- i.e., you can only list a maximum of 73 hours of orders, but you can iterate through incrementing chg_days

#### Status Filtering

`status`: Allows you to filter your results by a particular order status. For example: `"status=new"` for newly created orders.

| Status | Description |
|--------|-------------|
| new | Orders in a status of New |
| order_ack | Orders in a status of Processing |
| cancel | Orders in a status of Cancellation Requested |
| cancel_ack | Orders in a status of Cancellation Acknowledged |
| return | Orders in a status of Return Requested |
| return_ack | Orders in a status of Return Acknowledged |

---

## View Order Details

### GET `/restapi/v4/orders/{ORDER_URI}/?format=json`

This call allows you to retrieve information for a specific order, once you already know the Restful ID. This restful ID can be acquired via the "List Orders" call, or cached whenever you call the "Create an order" endpoint for generating any new order.

**Authorization**: Basic Auth

**Path Parameters**:
- `ORDER_URI`: The unique REST ID for the order (replace in the URL)

**Query Parameters**:
- `format=json`

### Order Response Structure

The response includes:
- Order metadata (order_reference, order_date, status, etc.)
- Retailer information
- Supplier information
- Items array with line-level details
- Shipping address
- Retailer data
- Currency and pricing information

---

## List Carriers

### GET `/restapi/v4/order-tracking-carriers/?format=json`

This endpoint will return all available carriers on our platform. Please note, as a supplier you may have been restricted to the carriers you use most. This is simply a list of all of them which helps you provide the correct information to us when calling our APIs.

**Authorization**: Basic Auth

**Query Parameters**:
- `format=json`

### Carrier Response Structure

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

---

## List Returns

### GET `/restapi/v4/returns/?format=json`

Retrieve a list of returns with various filtering options.

**Authorization**: Basic Auth

### Available Query Parameters

```
?page=1&offset=0&limit=15
&supplier_uuid=a8d85658-c168-4991-821d-38ccd9386521
&return_approve_reason=351
&return_reject_reason=321
&return_reason=335
&return_status=RMA_REJ
&sla_violation=return_time_to_authorise
&item_reference=sdsfsd
&order_reference=897987987987
&return_amount=partially
&from_date=2024-06-19
&to_date=2024-06-19
&from_date_complete=2024-06-19
&to_date_complete=2024-06-19
```

### Return Response Structure

The response includes:
- Return ID and quantity
- Order information with full order details
- Order item details
- Return reason with code and description
- Status information
- Date tracking (return_date, requested_at, authorised_at, declined_at, etc.)
- Supplier and retailer information
- Return approval/rejection details
