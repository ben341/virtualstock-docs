# Virtualstock API - Supplier Management

## List Suppliers for Products

### GET `/api/v4/suppliers/?format=json`

Retrieve a list of suppliers configured in the system.

**Authorization**: Basic Auth

**Query Parameters**:
- `format=json`

### Filter by Supplier Name

You can filter this endpoint by supplier name. Add the name parameter to the url:

```
https://www.sandbox.the-edge.io/api/v4/suppliers/?name={SupplierName}&format=json
```

### Filter by Account ID

You can also filter this endpoint by supplier account ID. Add the account_id parameter to the url. Account IDs are set on suppliers as part of onboarding and are typically the retailers system identifiers.

```
https://www.sandbox.the-edge.io/api/v4/suppliers/?account_id={AccountID}&format=json
```

**Example**:
```
GET /api/v4/suppliers/?account_id=SBG001&format=json
```

---

## Retrieve Channels

### GET `/api/v4/channels/?format=json`

Retrieve available channels for order routing. Channels are used to separate orders by Region, or Buying groups within one organisation.

**Authorization**: Basic Auth

**Query Parameters**:
- `format=json`

---

## Retrieve a Supplier's Settings

### GET `/api/v4/suppliers/{SUPPLIER_ID}/settings/?format=json`

Retrieve configuration settings for a specific supplier.

**Authorization**: Basic Auth

**Path Parameters**:
- `SUPPLIER_ID`: The unique REST ID for the supplier

**Query Parameters**:
- `format=json`

### Settings Response

This endpoint returns supplier-specific configuration including:
- Order processing preferences
- Carrier restrictions
- Communication settings
- Integration-specific parameters
- Fulfillment route configurations

---

## Supplier Context

Suppliers in Virtualstock can be:
- Manufacturers
- Distributors
- Vendors
- The retailer's own warehouses
- Store network locations

In most cases, these suppliers are fulfilling dropship or marketplace orders for their client retailers.
