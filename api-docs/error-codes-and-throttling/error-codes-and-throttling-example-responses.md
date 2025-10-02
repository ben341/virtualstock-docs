# Error Codes and Throttling - Example Responses

## Throttling Response

**Status**: 429 Too Many Requests

```
Request was throttled. Request was throttled. Expected available in XX.0 seconds.
```

## Error Response Pattern

**Status**: 400 Bad Request, 401 Unauthorized, 404 Not Found, etc.

```json
{
  "error": "Error description",
  "detail": "Detailed error message",
  "code": "ERROR_CODE"
}
```

## Example 400 Bad Request

```json
{
  "error": "Validation failed",
  "detail": "The field 'part_number' is required",
  "code": "VALIDATION_ERROR"
}
```

## Example 401 Unauthorized

```json
{
  "error": "Authentication credentials were not provided",
  "detail": "No valid token found in request headers",
  "code": "AUTHENTICATION_FAILED"
}
```

## Example 404 Not Found

```json
{
  "error": "Not found",
  "detail": "Order with ID 99999 does not exist",
  "code": "NOT_FOUND"
}
```

## Example 500 Internal Server Error

```json
{
  "error": "Internal server error",
  "detail": "An unexpected error occurred. Please contact support if the problem persists.",
  "code": "INTERNAL_ERROR"
}
```
