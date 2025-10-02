# Virtualstock API - Authentication

## Security

Virtualstock REST API is secured by HTTPS protocol, which is always enabled. HTTPS protocol uses HTTPS-within-TLS, so TLS v1.2 provides both confidentiality as well as integrity.

## Authentication Methods

Virtualstock API supports two authentication methods:

1. **JWT Token Authentication** (Recommended)
2. **Basic Authentication** (Will eventually be deprecated)

## JWT Token Authentication

Our application uses JWT token based authentication. Learn more about JWT at [jwt.io](https://jwt.io).

### JWT Token Workflow

1. **Obtain an initial JWT token**: Authenticate with the API server by providing your credentials. Upon successful authentication, you will receive an initial JWT token.

2. **Store the JWT token securely**: Store the received JWT token securely, either in memory or in a persistent storage like a database or file.

3. **Include the JWT token in API requests**: For each subsequent API request, include the JWT token in the request headers as an authorization bearer token.

4. **Handle token expiration**: JWT tokens have an expiration time set by the server. Monitor the expiration time and handle token refresh before it expires.

5. **Refresh the JWT token**: Before the token expiration, make a separate API call to refresh the token. This call typically requires providing the expired token along with the refresh token.

6. **Receive and update the new JWT token**: After the refresh API call, you will receive a new JWT token. Update the stored token with the new one and continue using it for subsequent API requests.

### Token Validity

- **Access Token**: Valid for 5 minutes
- **Refresh Token**: Valid for 4 hours

### Request Token Endpoint

**POST** `/restapi/v4/token`

**Request Body:**
```json
{
    "username": "your-username",
    "password": "your-password"
}
```

**Response:**
```json
{
  "refresh": "your-refresh-token",
  "access": "your-access-token"
}
```

### Refresh Token Endpoint

**POST** `/restapi/v4/token/refresh`

**Request Body:**
```json
{
    "refresh": "your-refresh-token"
}
```

**Response:**
```json
{
  "access": "your-new-access-token"
}
```

## Python Example

```python
import requests

# Obtain an initial JWT token (authentication step)
initial_token = "your_initial_token_here"

# Include the JWT token in the request headers
headers = {"Authorization": f"Bearer {initial_token}"}

# Make a request to the API
response = requests.get("https://api.sandbox.virtualstock.com/restapi/v4/orders/?format=json", headers=headers)

# Handle token expiration
if response.status_code == 401:  # Unauthorized error
    # Refresh the JWT token (refresh step)
    refresh_token = "your_refresh_token_here"
    refresh_payload = {"refresh_token": refresh_token}
    refresh_response = requests.post("https://api.sandbox.virtualstock.com/restapi/v4/token/refresh", json=refresh_payload)

    if refresh_response.status_code == 200:  # Successful refresh
        # Update the stored token with the new one
        new_token = refresh_response.json()["access_token"]
        headers["Authorization"] = f"Bearer {new_token}"

        # Retry the original request with the new token
        response = requests.get("https://api.sandbox.virtualstock.com/restapi/v4/orders/?format=json", headers=headers)
```

## PHP Example

```php
// Initial JWT token (authentication step)
$initial_token = "your_initial_token_here";

// Set the headers with the JWT token
$headers = [
    "Authorization: Bearer $initial_token",
    "Content-Type: application/json"
];

// Function to make GET requests using cURL
function make_request($url, $headers) {
    $ch = curl_init($url);
    curl_setopt($ch, CURLOPT_RETURNTRANSFER, true);
    curl_setopt($ch, CURLOPT_HTTPHEADER, $headers);
    $response = curl_exec($ch);
    $http_code = curl_getinfo($ch, CURLINFO_HTTP_CODE);
    curl_close($ch);
    return ['response' => $response, 'http_code' => $http_code];
}

// Make an API request to get the orders
$response_data = make_request("https://api.sandbox.virtualstock.com/restapi/v4/orders/?format=json", $headers);
$response = json_decode($response_data['response'], true);
$http_code = $response_data['http_code'];

// Handle token expiration (401 Unauthorized)
if ($http_code == 401) {
    // Refresh token logic
    $refresh_token = "your_refresh_token_here";
    $refresh_payload = json_encode(['refresh_token' => $refresh_token]);

    // Prepare refresh token cURL request
    $ch = curl_init("https://api.sandbox.virtualstock.com/restapi/v4/token/refresh");
    curl_setopt($ch, CURLOPT_POST, true);
    curl_setopt($ch, CURLOPT_POSTFIELDS, $refresh_payload);
    curl_setopt($ch, CURLOPT_RETURNTRANSFER, true);
    curl_setopt($ch, CURLOPT_HTTPHEADER, ['Content-Type: application/json']);
    $refresh_response = curl_exec($ch);
    $refresh_http_code = curl_getinfo($ch, CURLINFO_HTTP_CODE);
    curl_close($ch);

    // Check if refresh was successful
    if ($refresh_http_code == 200) {
        $refresh_response_data = json_decode($refresh_response, true);
        $new_token = $refresh_response_data["access_token"];

        // Update the authorization header with the new token
        $headers = [
            "Authorization: Bearer $new_token",
            "Content-Type: application/json"
        ];

        // Retry the original request with the new token
        $response_data = make_request("https://api.sandbox.virtualstock.com/restapi/v4/orders/?format=json", $headers);
        $response = json_decode($response_data['response'], true);
    } else {
        // Handle token refresh failure
        echo "Failed to refresh the token. HTTP Code: $refresh_http_code";
    }
}

// Output the API response
echo "<pre>";
print_r($response);
echo "</pre>";
```

## Basic Authentication

Our REST API does still support Basic Authentication with just your username and password, but JWT is advised as Basic Auth will eventually be deprecated.

## SFTP API Authentication

If you're using the SFTP API you simply use the username and password provided by our support team.

You can either request an SFTP server to be set up for you, or use your own. In either case you will be authenticating using the username and password for the SFTP account.
