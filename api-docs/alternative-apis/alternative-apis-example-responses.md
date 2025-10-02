# Alternative APIs - Example Responses

## Webhook Response Requirements

Your webhook endpoint should respond with appropriate HTTP status codes:

### Success Response

**Status**: 200 OK

```
(No specific response body required)
```

### Error Responses

See the [Error Codes and Throttling](../error-codes-and-throttling/error-codes-and-throttling-example-responses.md) documentation for standard error response formats that your webhook should return:

- **400 Bad Request** - ParseError, ValidationError
- **401 Unauthorized** - AuthenticationFailed, NotAuthenticated
- **403 Forbidden** - PermissionDenied
- **429 Too Many Requests** - Throttled

## SFTP APIs

For SFTP-based APIs (Flat File CSV, Invoice JSON, Order Events CSV), responses are file-based rather than HTTP responses. Refer to the specific documentation for each SFTP API for file format specifications.
