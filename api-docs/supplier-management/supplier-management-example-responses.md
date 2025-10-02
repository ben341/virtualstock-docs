# Supplier Management - Example Responses

## List Suppliers Response

**Status**: 200 OK

```json
{
  "count": 2,
  "next": null,
  "previous": null,
  "results": [
    {
      "url": "https://api.sandbox.virtualstock.com/api/v4/suppliers/2540/",
      "uuid": "a8d85658-c168-4991-821d-38ccd9386521",
      "name": "Supplier Name 1",
      "account_id": "SBG001",
      "email": "supplier1@example.com",
      "phone": "01234567890"
    },
    {
      "url": "https://api.sandbox.virtualstock.com/api/v4/suppliers/2541/",
      "uuid": "b9e96769-d279-5aa2-932e-49dde0497632",
      "name": "Supplier Name 2",
      "account_id": "SBG002",
      "email": "supplier2@example.com",
      "phone": "09876543210"
    }
  ]
}
```

## Retrieve Channels Response

**Status**: 200 OK

```json
{
  "count": 3,
  "next": null,
  "previous": null,
  "results": [
    {
      "id": 1,
      "name": "CHANNEL1",
      "description": "UK Main Channel"
    },
    {
      "id": 2,
      "name": "CHANNEL2",
      "description": "EU Channel"
    },
    {
      "id": 3,
      "name": "CHANNEL3",
      "description": "US Channel"
    }
  ]
}
```

## Retrieve Supplier Settings Response

**Status**: 200 OK

```json
{
  "supplier_id": "2540",
  "auto_acknowledge": true,
  "allowed_carriers": ["dpd", "royal-mail", "fedex"],
  "default_lead_time_days": 3,
  "fulfillment_routes": ["Direct to customer", "Via warehouse"],
  "notification_email": "operations@supplier.com",
  "integration_type": "REST_API"
}
```
