# Order Management (Suppliers) - Example Responses

## Common Response for Supplier Actions

Most supplier order management endpoints (acknowledge, backorder, cancel_acknowledge, dispatch, return_acknowledge) return the same success response:

**Status**: 200 OK or 201 Created

```
No response body
This request doesn't return any response body
```

This indicates the operation was successful.

## Error Responses

If the operation fails, you will receive an error response. See [Error Codes and Throttling](../error-codes-and-throttling/error-codes-and-throttling-example-responses.md) for standard error response formats.

Common error scenarios include:

- **400 Bad Request**: Invalid payload structure or missing required fields
- **401 Unauthorized**: Authentication failed or token expired
- **404 Not Found**: Order with specified ORDER_URI doesn't exist
- **500 Internal Server Error**: Service degradation or scheduled downtime
