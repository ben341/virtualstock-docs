# Virtualstock API Documentation - Master Navigation Guide

## 📋 Table of Contents

- [Quick Start](#quick-start)
- [Document Structure](#document-structure)
- [API Categories](#api-categories)
- [Finding Specific Tasks](#finding-specific-tasks)
- [Examples Location](#examples-location)
- [Postman Collection](#postman-collection)
- [Quick Reference Matrix](#quick-reference-matrix)

---

## Quick Start

### New to Virtualstock API?
Start here: [`api-docs/overview/overview-and-introduction.md`](api-docs/overview/overview-and-introduction.md)

### Need to authenticate?
Go here: [`api-docs/authentication/authentication.md`](api-docs/authentication/authentication.md)

### Want to create your first order?
Jump to: [`api-docs/order-creation/order-creation.md`](api-docs/order-creation/order-creation.md)

---

## Document Structure

Each API topic follows a consistent 3-file structure:

```
api-docs/
├── {topic-name}/
│   ├── {topic-name}.md                      # Main documentation with endpoints, schemas, and field definitions
│   ├── {topic-name}-example-requests.md     # Sample request payloads
│   └── {topic-name}-example-responses.md    # Sample response payloads
```

### Documentation Categories

1. **[overview](api-docs/overview/)** - Introduction, getting started, breaking change policy, environments
2. **[authentication](api-docs/authentication/)** - JWT tokens, basic auth, SFTP credentials
3. **[order-creation](api-docs/order-creation/)** - Create new orders
4. **[order-management-retailers](api-docs/order-management-retailers/)** - Retailer-side order operations
5. **[order-management-suppliers](api-docs/order-management-suppliers/)** - Supplier-side order operations (acknowledge, dispatch, cancel, etc.)
6. **[product-and-stock-management](api-docs/product-and-stock-management/)** - Product CRUD operations and stock updates
7. **[supplier-management](api-docs/supplier-management/)** - Supplier configuration and management
8. **[error-codes-and-throttling](api-docs/error-codes-and-throttling/)** - HTTP status codes, error handling, rate limits
9. **[alternative-apis](api-docs/alternative-apis/)** - SFTP, webhook, and other integration methods

---

## API Categories

### 🔐 Authentication & Security
**Location**: `api-docs/authentication/`

- **JWT Token Authentication** (Recommended)
  - Request Token: `POST /restapi/v4/token`
  - Refresh Token: `POST /restapi/v4/token/refresh`
  - Token Validity: Access (5 min), Refresh (4 hours)
- **Basic Authentication** (Legacy - will be deprecated)
- **SFTP Authentication**

**Examples**: `api-docs/authentication/authentication-example-requests.md`

---

### 📦 Order Management

#### Creating Orders (Retailers)
**Location**: `api-docs/order-creation/`

- **Create Order**: `POST /restapi/v3.1/orders/?format=json`
  - Complete field reference with order-level, invoice, shipping, and item fields
  - End-to-end field mapping (REST API ↔ UI ↔ SFTP)

**Examples**: `api-docs/order-creation/order-creation-example-requests.md`

#### Managing Orders (Suppliers)
**Location**: `api-docs/order-management-suppliers/`

Suppliers can perform the following actions:
- **Acknowledge Order**: `POST /restapi/v3/orders/{ORDER_URI}/acknowledge/`
- **Backorder Order**: `POST /restapi/v4/orders/{ORDER_URI}/backorder/`
- **Dispatch Order**: `POST /restapi/v4/orders/{ORDER_URI}/dispatch/`
- **Acknowledge Cancellation**: `POST /restapi/v4/orders/{ORDER_URI}/cancel_acknowledge/`
- **Acknowledge Return**: `POST /restapi/v4/orders/{ORDER_URI}/return_acknowledge/`
- **Create Invoice**: `POST /restapi/v4/orders/{ORDER_URI}/invoice/`

**Examples**: `api-docs/order-management-suppliers/order-management-suppliers-example-requests.md`

#### Managing Orders (Retailers)
**Location**: `api-docs/order-management-retailers/`

Retailer-specific order operations and queries.

**Examples**: `api-docs/order-management-retailers/order-management-retailers-example-requests.md`

---

### 🛍️ Product & Stock Management
**Location**: `api-docs/product-and-stock-management/`

- **Create Product**: `POST /api/v4/products/`
- **List Products**: `GET /api/v4/products/`
- **Get Product by REST ID**: `GET /api/v4/products/{PRODUCT_REST_ID}/`
- **Get Product by Part Number**: `GET /api/v4/products/by-part-number/{PART_NUMBER}/`
- **Update Product**: `PATCH /api/v4/products/{PRODUCT_REST_ID}/`
- **Update Stock Only** (Optimized): `PATCH /api/v4/products/{PRODUCT_REST_ID}/stock`
- **Delete Product**: `DELETE /api/v4/products/{PRODUCT_REST_ID}`
- **List Product Categories**: `GET /api/v4/product-categories/`

**Important Notes**:
- Use the dedicated `/stock` endpoint for stock-only updates (faster performance)
- Always use `supplier_free_stock` field in stock-only endpoint
- Contact support for retailer-specific product schemas

**Examples**: `api-docs/product-and-stock-management/product-and-stock-management-example-requests.md`

---

### 🏢 Supplier Management
**Location**: `api-docs/supplier-management/`

Configure and manage supplier settings, integrations, and preferences.

**Examples**: `api-docs/supplier-management/supplier-management-example-requests.md`

---

### ⚠️ Error Handling & Throttling
**Location**: `api-docs/error-codes-and-throttling/`

#### HTTP Status Codes
- `200 OK` - Success
- `201 Created` - Resource created
- `400 Bad Request` - Invalid payload or missing required fields
- `401 Unauthorized` - Authentication failed
- `404 Not Found` - Invalid endpoint or REST ID
- `429 Throttled` - Rate limit exceeded (250 requests/minute)
- `500 Internal Server Error` - Service degraded or in maintenance

#### Rate Limiting
- **Limit**: 250 requests per minute
- **Throttle Response**: `429` status with retry-after time in seconds

#### Best Practices
- Do NOT parse error messages for business logic
- Rely on HTTP status codes and error codes only
- Handle 429 errors with exponential backoff

**Examples**: `api-docs/error-codes-and-throttling/error-codes-and-throttling-example-responses.md`

---

### 🔌 Alternative Integration Methods
**Location**: `api-docs/alternative-apis/`

- SFTP API integration
- Webhook integrations
- Pre-built connectors (e.g., Linnworks)

**Examples**: `api-docs/alternative-apis/alternative-apis-example-requests.md`

---

## Finding Specific Tasks

### "I want to..."

#### ...authenticate with the API
→ `api-docs/authentication/authentication.md`
- JWT workflow explained at lines 18-31
- Python example at lines 75-103
- PHP example at lines 105-173

#### ...create a new order
→ `api-docs/order-creation/order-creation.md`
- Endpoint documentation at lines 1-10
- Complete field reference at lines 19-89
- Field mapping table at lines 91-117
- Full example payload at lines 119-170

#### ...acknowledge an order (as a supplier)
→ `api-docs/order-management-suppliers/order-management-suppliers.md:1-49`
- Request structure at lines 20-36
- Field definitions at lines 38-48

#### ...dispatch an order
→ `api-docs/order-management-suppliers/order-management-suppliers.md:146-192`
- Dispatch endpoint and payload structure
- Required tracking and carrier information

#### ...update product stock
→ `api-docs/product-and-stock-management/product-and-stock-management.md:90-119`
- Optimized stock-only endpoint
- Performance notes and field requirements

#### ...handle rate limiting
→ `api-docs/error-codes-and-throttling/error-codes-and-throttling.md:19-36`
- Throttling limits and behavior
- Retry strategies

#### ...understand breaking vs non-breaking changes
→ `api-docs/overview/overview-and-introduction.md:31-63`
- Breaking change definitions
- Non-breaking change examples
- Future-proofing your integration

---

## Examples Location

### Request Examples
Every topic has a dedicated `-example-requests.md` file:

```
api-docs/authentication/authentication-example-requests.md
api-docs/order-creation/order-creation-example-requests.md
api-docs/order-management-suppliers/order-management-suppliers-example-requests.md
api-docs/order-management-retailers/order-management-retailers-example-requests.md
api-docs/product-and-stock-management/product-and-stock-management-example-requests.md
api-docs/supplier-management/supplier-management-example-requests.md
api-docs/error-codes-and-throttling/error-codes-and-throttling-example-requests.md
api-docs/alternative-apis/alternative-apis-example-requests.md
```

### Response Examples
Every topic has a dedicated `-example-responses.md` file:

```
api-docs/authentication/authentication-example-responses.md
api-docs/order-creation/order-creation-example-responses.md
api-docs/order-management-suppliers/order-management-suppliers-example-responses.md
api-docs/order-management-retailers/order-management-retailers-example-responses.md
api-docs/product-and-stock-management/product-and-stock-management-example-responses.md
api-docs/supplier-management/supplier-management-example-responses.md
api-docs/error-codes-and-throttling/error-codes-and-throttling-example-responses.md
api-docs/alternative-apis/alternative-apis-example-responses.md
```

### Code Examples
Python and PHP authentication examples are included directly in:
- `api-docs/authentication/authentication.md` (lines 75-173)

---

## Postman Collection

**Location**: `Virtualstock API integration documentation.postman_collection.json`

This Postman collection includes:
- Pre-configured requests for all endpoints
- Environment variables for sandbox and production
- Example payloads for all operations
- Authentication helpers

**Import Instructions**:
1. Open Postman
2. Click "Import" button
3. Select the JSON file from the root directory
4. Configure environment variables (base URL, username, password)

---

## Quick Reference Matrix

| Task | Endpoint | Method | Documentation | Examples |
|------|----------|--------|---------------|----------|
| Get JWT Token | `/restapi/v4/token` | POST | [authentication.md](api-docs/authentication/authentication.md) | [requests](api-docs/authentication/authentication-example-requests.md) |
| Refresh Token | `/restapi/v4/token/refresh` | POST | [authentication.md](api-docs/authentication/authentication.md) | [requests](api-docs/authentication/authentication-example-requests.md) |
| Create Order | `/restapi/v3.1/orders/` | POST | [order-creation.md](api-docs/order-creation/order-creation.md) | [requests](api-docs/order-creation/order-creation-example-requests.md) |
| Acknowledge Order | `/restapi/v3/orders/{ID}/acknowledge/` | POST | [order-mgmt-suppliers.md](api-docs/order-management-suppliers/order-management-suppliers.md) | [requests](api-docs/order-management-suppliers/order-management-suppliers-example-requests.md) |
| Backorder | `/restapi/v4/orders/{ID}/backorder/` | POST | [order-mgmt-suppliers.md](api-docs/order-management-suppliers/order-management-suppliers.md) | [requests](api-docs/order-management-suppliers/order-management-suppliers-example-requests.md) |
| Dispatch Order | `/restapi/v4/orders/{ID}/dispatch/` | POST | [order-mgmt-suppliers.md](api-docs/order-management-suppliers/order-management-suppliers.md) | [requests](api-docs/order-management-suppliers/order-management-suppliers-example-requests.md) |
| Cancel Ack | `/restapi/v4/orders/{ID}/cancel_acknowledge/` | POST | [order-mgmt-suppliers.md](api-docs/order-management-suppliers/order-management-suppliers.md) | [requests](api-docs/order-management-suppliers/order-management-suppliers-example-requests.md) |
| Return Ack | `/restapi/v4/orders/{ID}/return_acknowledge/` | POST | [order-mgmt-suppliers.md](api-docs/order-management-suppliers/order-management-suppliers.md) | [requests](api-docs/order-management-suppliers/order-management-suppliers-example-requests.md) |
| Create Invoice | `/restapi/v4/orders/{ID}/invoice/` | POST | [order-mgmt-suppliers.md](api-docs/order-management-suppliers/order-management-suppliers.md) | [requests](api-docs/order-management-suppliers/order-management-suppliers-example-requests.md) |
| Create Product | `/api/v4/products/` | POST | [product-stock-mgmt.md](api-docs/product-and-stock-management/product-and-stock-management.md) | [requests](api-docs/product-and-stock-management/product-and-stock-management-example-requests.md) |
| List Products | `/api/v4/products/` | GET | [product-stock-mgmt.md](api-docs/product-and-stock-management/product-and-stock-management.md) | [requests](api-docs/product-and-stock-management/product-and-stock-management-example-requests.md) |
| Get Product | `/api/v4/products/{ID}/` | GET | [product-stock-mgmt.md](api-docs/product-and-stock-management/product-and-stock-management.md) | [requests](api-docs/product-and-stock-management/product-and-stock-management-example-requests.md) |
| Get by Part# | `/api/v4/products/by-part-number/{PN}/` | GET | [product-stock-mgmt.md](api-docs/product-and-stock-management/product-and-stock-management.md) | [requests](api-docs/product-and-stock-management/product-and-stock-management-example-requests.md) |
| Update Product | `/api/v4/products/{ID}/` | PATCH | [product-stock-mgmt.md](api-docs/product-and-stock-management/product-and-stock-management.md) | [requests](api-docs/product-and-stock-management/product-and-stock-management-example-requests.md) |
| Update Stock | `/api/v4/products/{ID}/stock` | PATCH | [product-stock-mgmt.md](api-docs/product-and-stock-management/product-and-stock-management.md) | [requests](api-docs/product-and-stock-management/product-and-stock-management-example-requests.md) |
| Delete Product | `/api/v4/products/{ID}` | DELETE | [product-stock-mgmt.md](api-docs/product-and-stock-management/product-and-stock-management.md) | [requests](api-docs/product-and-stock-management/product-and-stock-management-example-requests.md) |
| List Categories | `/api/v4/product-categories/` | GET | [product-stock-mgmt.md](api-docs/product-and-stock-management/product-and-stock-management.md) | [requests](api-docs/product-and-stock-management/product-and-stock-management-example-requests.md) |

---

## Environment URLs

- **Sandbox**: `https://api.sandbox.virtualstock.com`
- **Production**: `https://api.virtualstock.com`

---

## Additional Resources

### Support Contacts
- Contact Virtualstock support for:
  - Retailer-specific product schemas
  - Custom field requirements
  - Carrier slug values
  - Webhook configuration
  - SFTP server setup

### Pre-built Integrations
- **Linnworks Connector**: https://www.linnworks.com/connect/lw-virtualstock-emea

---

## Document Version Information

- **Total Documentation Files**: 27 markdown files
- **Total Lines**: ~2,278 lines
- **Last Updated**: 2025-10-02
- **API Versions**: v3, v3.1, v4

---

## Tips for Navigating This Documentation

1. **Start with the overview** if you're new to Virtualstock
2. **Use the Quick Reference Matrix** for fast endpoint lookup
3. **Check example files** for working payloads before implementing
4. **Reference error-codes documentation** when debugging
5. **Use the Postman collection** for testing before coding
6. **Note API version numbers** in endpoints (v3, v3.1, v4)
7. **Contact support** for retailer-specific customizations

---

**Happy integrating! 🚀**
