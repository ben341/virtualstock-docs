# Virtualstock API - Product & Stock Management

## Create a Product

### POST `/api/v4/products/?format=json`

Create a new product in the Virtualstock platform.

**Authorization**: Basic Auth

**Headers**:
- `Content-Type: application/json`

**Query Parameters**:
- `format=json`

*Note: Contact Virtualstock support for detailed product schema and required fields specific to your retailer integration*

---

## List Products

### GET `/api/v4/products/?format=json`

Retrieve a list of products.

**Authorization**: Basic Auth

**Query Parameters**:
- `format=json`
- Additional filtering parameters available (contact support for details)

---

## Retrieve a Product

### GET `/api/v4/products/{PRODUCT_REST_ID}/?format=json`

Retrieve details for a specific product by its REST ID.

**Authorization**: Basic Auth

**Path Parameters**:
- `PRODUCT_REST_ID`: The unique REST ID for the product

**Query Parameters**:
- `format=json`

---

## Retrieve a Product by Part Number

### GET `/api/v4/products/by-part-number/{PART_NUMBER}/?format=json`

Retrieve details for a specific product by its part number (SKU/EAN/GTIN).

**Authorization**: Basic Auth

**Path Parameters**:
- `PART_NUMBER`: The product's part number (SKU, EAN, or GTIN)

**Query Parameters**:
- `format=json`

---

## Update a Product

### PATCH `/api/v4/products/{PRODUCT_REST_ID}/?format=json`

Update an existing product's details.

**Authorization**: Basic Auth

**Headers**:
- `Content-Type: application/json`

**Path Parameters**:
- `PRODUCT_REST_ID`: The unique REST ID for the product

**Query Parameters**:
- `format=json`

**Important Notes**:
- Use PATCH for partial updates
- Only include fields you want to update
- For stock-only updates, use the dedicated stock endpoint (see below) for better performance

---

## Update Stock Availability

### PATCH `/api/v4/products/{PRODUCT_REST_ID}/stock`

Provide a stock availability update. This endpoint is optimized for stock-only updates and consequently performs a lot faster than the PATCH Update a product endpoint.

**Authorization**: Basic Auth

**Headers**:
- `Content-Type: application/json`

**Path Parameters**:
- `PRODUCT_REST_ID`: The unique REST ID for the product

### Request Body

```json
{
    "supplier_free_stock": 2
}
```

### Important Notes

- **Only use this endpoint for updates to only the stock value of a product**
- If your retailer would like you to provide more fields on the product such as back in stock dates or lead times as well as stock, then please use the "Update product" endpoint
- In the full product update endpoint, some retailers have only `free_stock` on their product data model instead of `supplier_free_stock` and you need to specify the correct field per retailer
- For this stock-only field endpoint, please provide `supplier_free_stock` always and the endpoint will work out the correct field to populate for any retailer

---

## Delete a Product

### DELETE `/api/v4/products/{PRODUCT_REST_ID}`

Delete a product from the system.

**Authorization**: Basic Auth

**Path Parameters**:
- `PRODUCT_REST_ID`: The unique REST ID for the product

**Important**: This action may be irreversible depending on your retailer's configuration. Contact support if you need to archive products instead of deleting them.

---

## List Product Categories

### GET `/api/v4/product-categories/?format=json`

Retrieve a list of available product categories.

**Authorization**: Basic Auth

**Query Parameters**:
- `format=json`

### Product Categories

Product categories are used to:
- Organize products in the retailer's catalog
- Apply category-specific validation rules
- Enable category-based reporting and analytics
- Support rich product induction workflows

---

## Rich Product Induction

Virtualstock can be used for rich product induction - where the supplier's product data is validated against the retailer's data model, before it is published to the retailer's systems.

This process ensures:
- Data quality and consistency
- Compliance with retailer's product standards
- Proper categorization and attributes
- Validated images and documentation
