# Virtualstock API - Error Codes and Throttling

## REST API Error Codes

| Code | Description |
|------|-------------|
| 200 OK | The request you made returned successfully |
| 201 Created | Your POST was successful and the entity you submitted has been created on our platform |
| 400 Bad Request | Your payload contains an invalid value or a missing value or is not structured correctly. There will be a secondary error code and a message indicating which type of error occurred. |
| 401 Unauthorised | Your authentication credentials are incorrect |
| 404 Not found | Your URL / Endpoint is not correct or contains an invalid REST ID |
| 429 Request was throttled | See the details on throttling below |
| 500 Internal Server Error | Our service is in a degraded state or is in scheduled downtime for a release |

## Error Response Best Practices

**Important**: We do not recommend parsing error messages to perform business logic. Instead, you should only rely on HTTP response codes and error codes.

## Throttling Limit

All API requests are limited to **250 requests per minute**.

### How Throttling Works

- You will be given an error message informing you when you are next able to make another API call if you exceed this limit
- For example, you can call the API 250 times in the first few seconds of the minute, but have to then wait until the next minute to call again
- The API will return a status code of **429** and a message in the response: `Request was throttled. Expected available in XX.0 seconds.`

### Example Throttling Response

**Status Code**: 429 Too Many Requests

**Response Message**:
```
Request was throttled. Request was throttled. Expected available in XX.0 seconds.
```

## Webhook API Exception Handling

When building Webhook APIs to receive data from Virtualstock, your API should respond with the following error codes:

### ParseError
- **Status Code**: 400 Bad Request
- **Description**: Raised if the request contains malformed data when accessing request.data

### AuthenticationFailed
- **Status Code**: 401 Unauthenticated (or 403 Forbidden depending on authentication scheme)
- **Description**: Raised when an incoming request includes incorrect authentication

### NotAuthenticated
- **Status Code**: 401 Unauthenticated (or 403 Forbidden depending on authentication scheme)
- **Description**: Raised when an unauthenticated request fails the permission checks
- **Note**: See the authentication documentation for more details

### PermissionDenied
- **Status Code**: 403 Forbidden
- **Description**: Raised when an authenticated request fails the permission checks

### Throttled
- **Status Code**: 429 Too Many Requests
- **Description**: Raised when an incoming request fails the throttling checks
- **Note**: Virtualstock are reviewing the API performance metrics and as such are not able to share the throttling limits that will apply

### ValidationError
- **Status Code**: 400 Bad Request
- **Description**: Raised when request validation fails

### Retry Behavior

For any of these errors, if Virtualstock fails to deliver the update, it will attempt to replay failed messages several times over the course of 24 hours. Virtualstock will log the failure and an alert will be monitored by our Service Desk team, who will be in touch to help resolve connectivity.
