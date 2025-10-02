# Product & Stock Management - Example Responses

## Update Stock Response

**Status**: 200 OK

```
No response body
This request doesn't return any response body
```

## Create Product Response

**Status**: 201 Created

```json
{
  "url": "https://api.sandbox.virtualstock.com/api/v4/products/12345/",
  "id": 12345,
  "part_number": "PROD001",
  "name": "Example Product",
  "description": "Product description",
  "supplier_free_stock": 100,
  "price": "29.99",
  "created_at": "2024-01-15T10:30:00Z",
  "updated_at": "2024-01-15T10:30:00Z"
}
```

## List Products Response

**Status**: 200 OK

```json
{
  "count": 50,
  "next": "https://api.sandbox.virtualstock.com/api/v4/products/?format=json&limit=10&offset=10",
  "previous": null,
  "results": [
    {
      "url": "https://api.sandbox.virtualstock.com/api/v4/products/12345/",
      "id": 12345,
      "part_number": "PROD001",
      "name": "Example Product",
      "supplier_free_stock": 100,
      "price": "29.99"
    },
    {
      "url": "https://api.sandbox.virtualstock.com/api/v4/products/12346/",
      "id": 12346,
      "part_number": "PROD002",
      "name": "Another Product",
      "supplier_free_stock": 50,
      "price": "19.99"
    }
  ]
}
```

## Retrieve Product Response

**Status**: 200 OK

```json
{
  "url": "https://api.sandbox.virtualstock.com/api/v4/products/12345/",
  "id": 12345,
  "part_number": "PROD001",
  "name": "Example Product",
  "description": "Product description",
  "supplier_free_stock": 100,
  "price": "29.99",
  "cost_price": "15.00",
  "category": "Electronics",
  "brand": "Example Brand",
  "weight": "0.5",
  "dimensions": "10x10x5",
  "barcode": "1234567890123",
  "created_at": "2024-01-15T10:30:00Z",
  "updated_at": "2024-01-15T10:30:00Z"
}
```

## Update Product Response

**Status**: 200 OK

```json
{
  "url": "https://api.sandbox.virtualstock.com/api/v4/products/12345/",
  "id": 12345,
  "part_number": "PROD001",
  "name": "Updated Product Name",
  "description": "Product description",
  "supplier_free_stock": 100,
  "price": "34.99",
  "updated_at": "2024-01-16T14:20:00Z"
}
```

## Delete Product Response

**Status**: 204 No Content

```
No response body
This request doesn't return any response body
```

## List Product Categories Response

**Status**: 200 OK

```json
{
  "count": 10,
  "next": null,
  "previous": null,
  "results": [
    {
      "id": 1,
      "name": "Electronics",
      "description": "Electronic products",
      "parent_category": null
    },
    {
      "id": 2,
      "name": "Furniture",
      "description": "Furniture and home items",
      "parent_category": null
    },
    {
      "id": 3,
      "name": "Clothing",
      "description": "Apparel and accessories",
      "parent_category": null
    }
  ]
}
```
