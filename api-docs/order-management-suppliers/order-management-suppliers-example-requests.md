# Order Management (Suppliers) - Example Requests

## Acknowledge an Order

```bash
curl --location 'https://api.sandbox.virtualstock.com/api/v3/orders/ORDER_URI/acknowledge/?format=json' \
--header 'Content-Type: application/json' \
--data '{
"items":
    [
    {
    "part_number": "PartNumber_02",
    "line_ref": "100002",
    "quantity": 5,
    "sub_status": "Pending",
    "supplier_dispatch_date": "2019-10-10T12:00:00",
    "supplier_delivery_date":"2019-10-10T12:00:00",
    "comment": "Line acknowledged"
    },
    {
    "part_number": "PartNumber_01",
    "line_ref": "100001",
    "quantity": 40,
    "sub_status": "ASN Received",
    "supplier_dispatch_date": "2019-10-10T12:00:00",
    "supplier_delivery_date":"2019-10-10T12:00:00",
    "comment": "ASN received for line"
    }
    ]
}
'
```

## Backorder an Order

```bash
curl --location 'https://api.sandbox.virtualstock.com/restapi/v4/orders/ORDER_URI/backorder/?format=json' \
--header 'Content-Type: application/json' \
--data '{
"items":
    [
    {
    "part_number": "PartNumber_02",
    "line_ref": "100002",
    "quantity": 10,
    "sub_status": "Pending",
    "supplier_dispatch_date": "2019-10-20T12:00:00",
    "supplier_delivery_date": "2019-10-23T12:00:00",
    "comment": "Line set to backorder"
    },
    {
    "part_number": "PartNumber_01",
    "line_ref": "100001",
    "quantity": 40,
    "sub_status": "Pending",
    "supplier_dispatch_date": "2019-10-10T12:00:00",
    "supplier_delivery_date":"2019-10-10T12:00:00",
    "comment": "Line set to backorder"
    }
    ]
}
'
```

## Acknowledge a Cancellation

```bash
curl --location 'https://api.sandbox.virtualstock.com/restapi/v4/orders/ORDER_URI/cancel_acknowledge/?format=json' \
--header 'Content-Type: application/json' \
--data '{
    "items":
    [
        {
            "part_number": "PartNumber_02",
            "line_ref": "100002",
            "quantity": 10,
            "comment": "I accept"
        },
        {
            "part_number": "PartNumber_01",
            "line_ref": "100001",
            "quantity": 5,
            "comment": "I accept but i'\''m not happy about it"
        }
    ]
}'
```

## Dispatch an Order

```bash
curl --location 'https://api.sandbox.virtualstock.com/restapi/v4/orders/ORDER_URI/dispatch/?format=json' \
--header 'Content-Type: application/json' \
--data '{
    "items":
    [
        {
            "part_number": "PartNumber_02",
            "line_ref": "100002",
            "quantity": 10,
            "supplier_dispatch_date": "2019-10-10",
            "supplier_delivery_date": "2019-10-12",
            "tracking_number": 1123581321,
            "carrier": "Fedex"
        },
        {
            "part_number": "PartNumber_01",
            "line_ref": "100001",
            "quantity": 5,
            "supplier_dispatch_date": "2019-10-10",
            "supplier_delivery_date": "2019-10-12",
            "tracking_number": 22481220,
            "carrier": "Royal Mail"
        }
    ]
}'
```

## Acknowledge a Return

```bash
curl --location 'https://api.sandbox.virtualstock.com/restapi/v4/orders/ORDER_URI/return_acknowledge/?format=json' \
--header 'Content-Type: application/json' \
--data '{
    "items": [
                {
                    "part_number": "PartNumber_01",
                    "line_ref": "10001",
                    "quantity": "2"
                }
            ]
}'
```
