# Supplier Management - Example Requests

## List Suppliers for Products

```bash
curl --location 'https://api.sandbox.virtualstock.com/api/v4/suppliers/?format=json' \
--data ''
```

## List Suppliers Filtered by Name

```bash
curl --location 'https://api.sandbox.virtualstock.com/api/v4/suppliers/?name=SupplierName&format=json' \
--data ''
```

## List Suppliers Filtered by Account ID

```bash
curl --location 'https://api.sandbox.virtualstock.com/api/v4/suppliers/?account_id=SBG001&format=json' \
--data ''
```

## Retrieve Channels

```bash
curl --location 'https://api.sandbox.virtualstock.com/api/v4/channels/?format=json' \
--data ''
```

## Retrieve a Supplier's Settings

```bash
curl --location 'https://api.sandbox.virtualstock.com/api/v4/suppliers/SUPPLIER_ID/settings/?format=json' \
--data ''
```
