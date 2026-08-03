# Artists

```php
$artistsApi = $client->getArtistsApi();
```

## Class Name

`ArtistsApi`

## Methods

* [Get-an-Artist](../../doc/controllers/artists.md#get-an-artist)
* [Get-Multiple-Artists](../../doc/controllers/artists.md#get-multiple-artists)
* [Get-an-Artists-Albums](../../doc/controllers/artists.md#get-an-artists-albums)
* [Get-an-Artists-Top-Tracks](../../doc/controllers/artists.md#get-an-artists-top-tracks)
* [Get-an-Artists-Related-Artists](../../doc/controllers/artists.md#get-an-artists-related-artists)


# Get-an-Artist

Get Spotify catalog information for a single artist identified by their unique Spotify ID.

```php
function getAnArtist(string $id): ApiResponse
```

## Authentication

This endpoint requires [oauth_2_0](../../doc/auth/oauth-2-authorization-code-grant.md)

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `id` | `string` | Template, Required | - |

## Response Type

**200**: An artist

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `getResult()` method on this instance returns the response data which is of type [`ArtistObject`](../../doc/models/artist-object.md).

## Example Usage

```php
$id = '0TnOYISbd1XYRBk9myaseg';

$artistsApi = $client->getArtistsApi();
$apiResponse = $artistsApi->getAnArtist($id);

// Extracting response status code
var_dump($apiResponse->getStatusCode());
// Extracting response headers
var_dump($apiResponse->getHeaders());

if ($apiResponse->isSuccess()) {
    echo 'ArtistObject:';
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


# Get-Multiple-Artists

Get Spotify catalog information for several artists based on their Spotify IDs.

```php
function getMultipleArtists(string $ids): ApiResponse
```

## Authentication

This endpoint requires [oauth_2_0](../../doc/auth/oauth-2-authorization-code-grant.md)

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `ids` | `string` | Query, Required | - |

## Response Type

**200**: A set of artists

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `getResult()` method on this instance returns the response data which is of type [`ManyArtists`](../../doc/models/many-artists.md).

## Example Usage

```php
$ids = '2CIMQHirSU0MQqyYHq0eOx,57dN52uHvrHOxijzpIgu3E,1vCWHaC5f2uS3yhpwWbIA6';

$artistsApi = $client->getArtistsApi();
$apiResponse = $artistsApi->getMultipleArtists($ids);

// Extracting response status code
var_dump($apiResponse->getStatusCode());
// Extracting response headers
var_dump($apiResponse->getHeaders());

if ($apiResponse->isSuccess()) {
    echo 'ManyArtists:';
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


# Get-an-Artists-Albums

Get Spotify catalog information about an artist's albums.

```php
function getAnArtistsAlbums(
    string $id,
    ?string $includeGroups = null,
    ?string $market = null,
    ?int $limit = 20,
    ?int $offset = 0
): ApiResponse
```

## Authentication

This endpoint requires [oauth_2_0](../../doc/auth/oauth-2-authorization-code-grant.md)

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `id` | `string` | Template, Required | - |
| `includeGroups` | `?string` | Query, Optional | - |
| `market` | `?string` | Query, Optional | - |
| `limit` | `?int` | Query, Optional | **Default**: `20`<br><br>**Constraints**: `>= 1`, `<= 50` |
| `offset` | `?int` | Query, Optional | **Default**: `0` |

## Response Type

**200**: Pages of albums

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `getResult()` method on this instance returns the response data which is of type [`PagingArtistDiscographyAlbumObject`](../../doc/models/paging-artist-discography-album-object.md).

## Example Usage

```php
$id = '0TnOYISbd1XYRBk9myaseg';

$includeGroups = 'single,appears_on';

$market = 'ES';

$limit = 10;

$offset = 5;

$artistsApi = $client->getArtistsApi();
$apiResponse = $artistsApi->getAnArtistsAlbums(
    $id,
    $includeGroups,
    $market,
    $limit,
    $offset
);

// Extracting response status code
var_dump($apiResponse->getStatusCode());
// Extracting response headers
var_dump($apiResponse->getHeaders());

if ($apiResponse->isSuccess()) {
    echo 'PagingArtistDiscographyAlbumObject:';
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


# Get-an-Artists-Top-Tracks

Get Spotify catalog information about an artist's top tracks by country.

```php
function getAnArtistsTopTracks(string $id, ?string $market = null): ApiResponse
```

## Authentication

This endpoint requires [oauth_2_0](../../doc/auth/oauth-2-authorization-code-grant.md)

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `id` | `string` | Template, Required | - |
| `market` | `?string` | Query, Optional | - |

## Response Type

**200**: A set of tracks

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `getResult()` method on this instance returns the response data which is of type [`ManyTracks`](../../doc/models/many-tracks.md).

## Example Usage

```php
$id = '0TnOYISbd1XYRBk9myaseg';

$market = 'ES';

$artistsApi = $client->getArtistsApi();
$apiResponse = $artistsApi->getAnArtistsTopTracks(
    $id,
    $market
);

// Extracting response status code
var_dump($apiResponse->getStatusCode());
// Extracting response headers
var_dump($apiResponse->getHeaders());

if ($apiResponse->isSuccess()) {
    echo 'ManyTracks:';
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


# Get-an-Artists-Related-Artists

Get Spotify catalog information about artists similar to a given artist. Similarity is based on analysis of the Spotify community's listening history.

```php
function getAnArtistsRelatedArtists(string $id): ApiResponse
```

## Authentication

This endpoint requires [oauth_2_0](../../doc/auth/oauth-2-authorization-code-grant.md)

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `id` | `string` | Template, Required | - |

## Response Type

**200**: A set of artists

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `getResult()` method on this instance returns the response data which is of type [`ManyArtists`](../../doc/models/many-artists.md).

## Example Usage

```php
$id = '0TnOYISbd1XYRBk9myaseg';

$artistsApi = $client->getArtistsApi();
$apiResponse = $artistsApi->getAnArtistsRelatedArtists($id);

// Extracting response status code
var_dump($apiResponse->getStatusCode());
// Extracting response headers
var_dump($apiResponse->getHeaders());

if ($apiResponse->isSuccess()) {
    echo 'ManyArtists:';
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

