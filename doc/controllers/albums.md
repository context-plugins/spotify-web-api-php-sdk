# Albums

```php
$albumsApi = $client->getAlbumsApi();
```

## Class Name

`AlbumsApi`

## Methods

* [Get-an-Album](../../doc/controllers/albums.md#get-an-album)
* [Get-Multiple-Albums](../../doc/controllers/albums.md#get-multiple-albums)
* [Get-an-Albums-Tracks](../../doc/controllers/albums.md#get-an-albums-tracks)
* [Get-Users-Saved-Albums](../../doc/controllers/albums.md#get-users-saved-albums)
* [Save-Albums-User](../../doc/controllers/albums.md#save-albums-user)
* [Remove-Albums-User](../../doc/controllers/albums.md#remove-albums-user)
* [Check-Users-Saved-Albums](../../doc/controllers/albums.md#check-users-saved-albums)
* [Get-New-Releases](../../doc/controllers/albums.md#get-new-releases)


# Get-an-Album

Get Spotify catalog information for a single album.

```php
function getAnAlbum(string $id, ?string $market = null): ApiResponse
```

## Authentication

This endpoint requires [oauth_2_0](../../doc/auth/oauth-2-authorization-code-grant.md)

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `id` | `string` | Template, Required | - |
| `market` | `?string` | Query, Optional | - |

## Response Type

**200**: An album

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `getResult()` method on this instance returns the response data which is of type [`AlbumObject`](../../doc/models/album-object.md).

## Example Usage

```php
$id = '4aawyAB9vmqN3uQ7FjRGTy';

$market = 'ES';

$albumsApi = $client->getAlbumsApi();
$apiResponse = $albumsApi->getAnAlbum(
    $id,
    $market
);

// Extracting response status code
var_dump($apiResponse->getStatusCode());
// Extracting response headers
var_dump($apiResponse->getHeaders());

if ($apiResponse->isSuccess()) {
    echo 'AlbumObject:';
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


# Get-Multiple-Albums

Get Spotify catalog information for multiple albums identified by their Spotify IDs.

```php
function getMultipleAlbums(string $ids, ?string $market = null): ApiResponse
```

## Authentication

This endpoint requires [oauth_2_0](../../doc/auth/oauth-2-authorization-code-grant.md)

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `ids` | `string` | Query, Required | - |
| `market` | `?string` | Query, Optional | - |

## Response Type

**200**: A set of albums

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `getResult()` method on this instance returns the response data which is of type [`ManyAlbums`](../../doc/models/many-albums.md).

## Example Usage

```php
$ids = '382ObEPsp2rxGrnsizN5TX,1A2GTWGtFfWp7KSQTwWOyo,2noRn2Aes5aoNVsU6iWThc';

$market = 'ES';

$albumsApi = $client->getAlbumsApi();
$apiResponse = $albumsApi->getMultipleAlbums(
    $ids,
    $market
);

// Extracting response status code
var_dump($apiResponse->getStatusCode());
// Extracting response headers
var_dump($apiResponse->getHeaders());

if ($apiResponse->isSuccess()) {
    echo 'ManyAlbums:';
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


# Get-an-Albums-Tracks

Get Spotify catalog information about an album’s tracks.
Optional parameters can be used to limit the number of tracks returned.

```php
function getAnAlbumsTracks(string $id, ?string $market = null, ?int $limit = 20, ?int $offset = 0): ApiResponse
```

## Authentication

This endpoint requires [oauth_2_0](../../doc/auth/oauth-2-authorization-code-grant.md)

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `id` | `string` | Template, Required | - |
| `market` | `?string` | Query, Optional | - |
| `limit` | `?int` | Query, Optional | **Default**: `20`<br><br>**Constraints**: `>= 1`, `<= 50` |
| `offset` | `?int` | Query, Optional | **Default**: `0` |

## Response Type

**200**: Pages of tracks

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `getResult()` method on this instance returns the response data which is of type [`PagingSimplifiedTrackObject`](../../doc/models/paging-simplified-track-object.md).

## Example Usage

```php
$id = '4aawyAB9vmqN3uQ7FjRGTy';

$market = 'ES';

$limit = 10;

$offset = 5;

$albumsApi = $client->getAlbumsApi();
$apiResponse = $albumsApi->getAnAlbumsTracks(
    $id,
    $market,
    $limit,
    $offset
);

// Extracting response status code
var_dump($apiResponse->getStatusCode());
// Extracting response headers
var_dump($apiResponse->getHeaders());

if ($apiResponse->isSuccess()) {
    echo 'PagingSimplifiedTrackObject:';
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


# Get-Users-Saved-Albums

Get a list of the albums saved in the current Spotify user's 'Your Music' library.

```php
function getUsersSavedAlbums(?int $limit = 20, ?int $offset = 0, ?string $market = null): ApiResponse
```

## Authentication

This endpoint requires [oauth_2_0](../../doc/auth/oauth-2-authorization-code-grant.md)

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `limit` | `?int` | Query, Optional | **Default**: `20`<br><br>**Constraints**: `>= 1`, `<= 50` |
| `offset` | `?int` | Query, Optional | **Default**: `0` |
| `market` | `?string` | Query, Optional | - |

## Requires scope

### oauth_2_0

`user-library-read`

## Response Type

**200**: Pages of albums

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `getResult()` method on this instance returns the response data which is of type [`PagingSavedAlbumObject`](../../doc/models/paging-saved-album-object.md).

## Example Usage

```php
$limit = 10;

$offset = 5;

$market = 'ES';

$albumsApi = $client->getAlbumsApi();
$apiResponse = $albumsApi->getUsersSavedAlbums(
    $limit,
    $offset,
    $market
);

// Extracting response status code
var_dump($apiResponse->getStatusCode());
// Extracting response headers
var_dump($apiResponse->getHeaders());

if ($apiResponse->isSuccess()) {
    echo 'PagingSavedAlbumObject:';
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


# Save-Albums-User

Save one or more albums to the current user's 'Your Music' library.

```php
function saveAlbumsUser(string $ids, ?SaveAlbumsRequest $body = null): ApiResponse
```

## Authentication

This endpoint requires [oauth_2_0](../../doc/auth/oauth-2-authorization-code-grant.md)

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `ids` | `string` | Query, Required | - |
| `body` | [`?SaveAlbumsRequest`](../../doc/models/save-albums-request.md) | Body, Optional | - |

## Requires scope

### oauth_2_0

`user-library-modify`

## Response Type

**200**: The album is saved

This method returns an [`ApiResponse`](../../doc/api-response.md) instance.

## Example Usage

```php
$ids = '382ObEPsp2rxGrnsizN5TX,1A2GTWGtFfWp7KSQTwWOyo,2noRn2Aes5aoNVsU6iWThc';

$albumsApi = $client->getAlbumsApi();
$apiResponse = $albumsApi->saveAlbumsUser($ids);

// Extracting response status code
var_dump($apiResponse->getStatusCode());
// Extracting response headers
var_dump($apiResponse->getHeaders());

if ($apiResponse->isSuccess()) {
    echo 'void:';
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


# Remove-Albums-User

Remove one or more albums from the current user's 'Your Music' library.

```php
function removeAlbumsUser(string $ids, ?RemoveAlbumsRequest $body = null): ApiResponse
```

## Authentication

This endpoint requires [oauth_2_0](../../doc/auth/oauth-2-authorization-code-grant.md)

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `ids` | `string` | Query, Required | - |
| `body` | [`?RemoveAlbumsRequest`](../../doc/models/remove-albums-request.md) | Body, Optional | - |

## Requires scope

### oauth_2_0

`user-library-modify`

## Response Type

**200**: Album(s) have been removed from the library

This method returns an [`ApiResponse`](../../doc/api-response.md) instance.

## Example Usage

```php
$ids = '382ObEPsp2rxGrnsizN5TX,1A2GTWGtFfWp7KSQTwWOyo,2noRn2Aes5aoNVsU6iWThc';

$albumsApi = $client->getAlbumsApi();
$apiResponse = $albumsApi->removeAlbumsUser($ids);

// Extracting response status code
var_dump($apiResponse->getStatusCode());
// Extracting response headers
var_dump($apiResponse->getHeaders());

if ($apiResponse->isSuccess()) {
    echo 'void:';
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


# Check-Users-Saved-Albums

Check if one or more albums is already saved in the current Spotify user's 'Your Music' library.

```php
function checkUsersSavedAlbums(string $ids): ApiResponse
```

## Authentication

This endpoint requires [oauth_2_0](../../doc/auth/oauth-2-authorization-code-grant.md)

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `ids` | `string` | Query, Required | - |

## Requires scope

### oauth_2_0

`user-library-read`

## Response Type

**200**: Array of booleans

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `getResult()` method on this instance returns the response data which is of type `bool[]`.

## Example Usage

```php
$ids = '382ObEPsp2rxGrnsizN5TX,1A2GTWGtFfWp7KSQTwWOyo,2noRn2Aes5aoNVsU6iWThc';

$albumsApi = $client->getAlbumsApi();
$apiResponse = $albumsApi->checkUsersSavedAlbums($ids);

// Extracting response status code
var_dump($apiResponse->getStatusCode());
// Extracting response headers
var_dump($apiResponse->getHeaders());

if ($apiResponse->isSuccess()) {
    echo 'bool[]:';
    var_dump($apiResponse->getResult());
} else {
    $error = $apiResponse->getResult();
    var_dump($error);
}
```

## Example Response

```
[
  false,
  true
]
```

## Errors

| HTTP Status Code | Error Description | Exception Class |
|  --- | --- | --- |
| 401 | Bad or expired token. This can happen if the user revoked a token or<br>the access token has expired. You should re-authenticate the user. | [`Unauthorized1Exception`](../../doc/models/unauthorized-1-exception.md) |
| 403 | Bad OAuth request (wrong consumer key, bad nonce, expired<br>timestamp...). Unfortunately, re-authenticating the user won't help here. | [`Forbidden1Exception`](../../doc/models/forbidden-1-exception.md) |
| 429 | The app has exceeded its rate limits. | [`TooManyRequests1Exception`](../../doc/models/too-many-requests-1-exception.md) |


# Get-New-Releases

Get a list of new album releases featured in Spotify (shown, for example, on a Spotify player’s “Browse” tab).

```php
function getNewReleases(?int $limit = 20, ?int $offset = 0): ApiResponse
```

## Authentication

This endpoint requires [oauth_2_0](../../doc/auth/oauth-2-authorization-code-grant.md)

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `limit` | `?int` | Query, Optional | **Default**: `20`<br><br>**Constraints**: `>= 1`, `<= 50` |
| `offset` | `?int` | Query, Optional | **Default**: `0` |

## Response Type

**200**: A paged set of albums

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `getResult()` method on this instance returns the response data which is of type [`PagedAlbums`](../../doc/models/paged-albums.md).

## Example Usage

```php
$limit = 10;

$offset = 5;

$albumsApi = $client->getAlbumsApi();
$apiResponse = $albumsApi->getNewReleases(
    $limit,
    $offset
);

// Extracting response status code
var_dump($apiResponse->getStatusCode());
// Extracting response headers
var_dump($apiResponse->getHeaders());

if ($apiResponse->isSuccess()) {
    echo 'PagedAlbums:';
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

