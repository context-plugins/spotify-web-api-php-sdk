# Search

```php
$searchApi = $client->getSearchApi();
```

## Class Name

`SearchApi`


# Search

Get Spotify catalog information about albums, artists, playlists, tracks, shows, episodes or audiobooks
that match a keyword string. Audiobooks are only available within the US, UK, Canada, Ireland, New Zealand and Australia markets.

```php
function search(
    string $q,
    array $type,
    ?string $market = null,
    ?int $limit = 20,
    ?int $offset = 0,
    ?string $includeExternal = null
): ApiResponse
```

## Authentication

This endpoint requires [oauth_2_0](../../doc/auth/oauth-2-authorization-code-grant.md)

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `q` | `string` | Query, Required | - |
| `type` | [`string(Itemtype)[]`](../../doc/models/itemtype.md) | Query, Required | - |
| `market` | `?string` | Query, Optional | - |
| `limit` | `?int` | Query, Optional | **Default**: `20`<br><br>**Constraints**: `>= 1`, `<= 50` |
| `offset` | `?int` | Query, Optional | **Default**: `0`<br><br>**Constraints**: `>= 0`, `<= 1000` |
| `includeExternal` | [`?string(IncludeExternal)`](../../doc/models/include-external.md) | Query, Optional | - |

## Response Type

**200**: Search response

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `getResult()` method on this instance returns the response data which is of type [`SearchItems`](../../doc/models/search-items.md).

## Example Usage

```php
$q = 'remaster%20track:Doxy%20artist:Miles%20Davis';

$type = [
    Itemtype::AUDIOBOOK,
    Itemtype::ALBUM,
    Itemtype::ARTIST
];

$market = 'ES';

$limit = 10;

$offset = 5;

$searchApi = $client->getSearchApi();
$apiResponse = $searchApi->search(
    $q,
    $type,
    $market,
    $limit,
    $offset
);

// Extracting response status code
var_dump($apiResponse->getStatusCode());
// Extracting response headers
var_dump($apiResponse->getHeaders());

if ($apiResponse->isSuccess()) {
    echo 'SearchItems:';
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

