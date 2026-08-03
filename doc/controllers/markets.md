# Markets

```php
$marketsApi = $client->getMarketsApi();
```

## Class Name

`MarketsApi`


# Get-Available-Markets

Get the list of markets where Spotify is available.

```php
function getAvailableMarkets(): ApiResponse
```

## Authentication

This endpoint requires [oauth_2_0](../../doc/auth/oauth-2-authorization-code-grant.md)

## Response Type

**200**: A markets object with an array of country codes

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `getResult()` method on this instance returns the response data which is of type [`Markets`](../../doc/models/markets.md).

## Example Usage

```php
$marketsApi = $client->getMarketsApi();
$apiResponse = $marketsApi->getAvailableMarkets();

// Extracting response status code
var_dump($apiResponse->getStatusCode());
// Extracting response headers
var_dump($apiResponse->getHeaders());

if ($apiResponse->isSuccess()) {
    echo 'Markets:';
    var_dump($apiResponse->getResult());
} else {
    $error = $apiResponse->getResult();
    var_dump($error);
}
```

## Errors

| HTTP Status Code | Error Description | Exception Class |
|  --- | --- | --- |
| 401 | Bad or expired token. This can happen if the user revoked a token or<br>the access token has expired. You should re-authenticate the user. | [`Unauthorized1Exception`](../../doc/models/unauthorized-1-exception.md) |
| 403 | Bad OAuth request (wrong consumer key, bad nonce, expired<br>timestamp...). Unfortunately, re-authenticating the user won't help here. | [`Forbidden1Exception`](../../doc/models/forbidden-1-exception.md) |
| 429 | The app has exceeded its rate limits. | [`TooManyRequests1Exception`](../../doc/models/too-many-requests-1-exception.md) |

