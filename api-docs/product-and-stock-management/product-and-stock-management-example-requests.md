# Product & Stock Management - Example Requests

## Update Stock Successfully

```bash
curl --location -g --request PATCH 'https://api.sandbox.virtualstock.com/api/v4/products/{PRODUCT_REST_ID}/stock' \
--header 'Content-Type: application/json' \
--data '{
    "supplier_free_stock": 2
}
'
```

## Create a Product

```bash
curl --location 'https://api.sandbox.virtualstock.com/api/v4/products/?format=json' \
--header 'Content-Type: application/json' \
--data '{
    "part_number": "PROD001",
    "name": "Example Product",
    "description": "Product description",
    "supplier_free_stock": 100,
    "price": 29.99
}
'
```

## List Products

```bash
curl --location 'https://api.sandbox.virtualstock.com/api/v4/products/?format=json'
```

## Retrieve a Product by REST ID

```bash
curl --location 'https://api.sandbox.virtualstock.com/api/v4/products/PRODUCT_REST_ID/?format=json'
```

## Retrieve a Product by Part Number

```bash
curl --location 'https://api.sandbox.virtualstock.com/api/v4/products/by-part-number/PROD001/?format=json'
```

## Update a Product

```bash
curl --location -g --request PATCH 'https://api.sandbox.virtualstock.com/api/v4/products/{PRODUCT_REST_ID}/?format=json' \
--header 'Content-Type: application/json' \
--data '{
    "name": "Updated Product Name",
    "price": 34.99
}
'
```

## Delete a Product

```bash
curl --location -g --request DELETE 'https://api.sandbox.virtualstock.com/api/v4/products/{PRODUCT_REST_ID}' \
--data ''
```

## List Product Categories

```bash
curl --location 'https://api.sandbox.virtualstock.com/api/v4/product-categories/?format=json'
```
