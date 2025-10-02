# Order Management (Retailers) - Example Requests

## List Orders

```bash
curl --location 'https://api.sandbox.virtualstock.com/restapi/v3/orders/?format=json'
```

## View Order Details

```bash
curl --location --request GET 'https://api.sandbox.virtualstock.com/restapi/v4/orders/ORDER_URI/?format=json' \
--header 'Content-Type: application/json'
```

## List Carriers

```bash
curl --location --request GET 'https://api.sandbox.virtualstock.com/restapi/v4/order-tracking-carriers/?format=json'
```

## List Returns

```bash
curl --location 'https://api.sandbox.virtualstock.com/restapi/v4/returns/?format=json'
```

## List Returns with Filters

```bash
curl --location 'https://api.sandbox.virtualstock.com/restapi/v4/returns/?page=1&offset=0&limit=15&supplier_uuid=a8d85658-c168-4991-821d-38ccd9386521&return_status=RMA_REJ&from_date=2024-06-19&to_date=2024-06-19&format=json'
```
