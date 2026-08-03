# Playlists

```php
$playlistsApi = $client->getPlaylistsApi();
```

## Class Name

`PlaylistsApi`

## Methods

* [Get-Playlist](../../doc/controllers/playlists.md#get-playlist)
* [Change-Playlist-Details](../../doc/controllers/playlists.md#change-playlist-details)
* [Get-Playlists-Tracks](../../doc/controllers/playlists.md#get-playlists-tracks)
* [Add-Tracks-to-Playlist](../../doc/controllers/playlists.md#add-tracks-to-playlist)
* [Reorder-or-Replace-Playlists-Tracks](../../doc/controllers/playlists.md#reorder-or-replace-playlists-tracks)
* [Remove-Tracks-Playlist](../../doc/controllers/playlists.md#remove-tracks-playlist)
* [Get-a-List-of-Current-Users-Playlists](../../doc/controllers/playlists.md#get-a-list-of-current-users-playlists)
* [Get-List-Users-Playlists](../../doc/controllers/playlists.md#get-list-users-playlists)
* [Create-Playlist](../../doc/controllers/playlists.md#create-playlist)
* [Get-Featured-Playlists](../../doc/controllers/playlists.md#get-featured-playlists)
* [Get-a-Categories-Playlists](../../doc/controllers/playlists.md#get-a-categories-playlists)
* [Get-Playlist-Cover](../../doc/controllers/playlists.md#get-playlist-cover)
* [Upload-Custom-Playlist-Cover](../../doc/controllers/playlists.md#upload-custom-playlist-cover)


# Get-Playlist

Get a playlist owned by a Spotify user.

```php
function getPlaylist(
    string $playlistId,
    ?string $market = null,
    ?string $fields = null,
    ?string $additionalTypes = null
): ApiResponse
```

## Authentication

This endpoint requires [oauth_2_0](../../doc/auth/oauth-2-authorization-code-grant.md)

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `playlistId` | `string` | Template, Required | - |
| `market` | `?string` | Query, Optional | - |
| `fields` | `?string` | Query, Optional | - |
| `additionalTypes` | `?string` | Query, Optional | - |

## Response Type

**200**: A playlist

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `getResult()` method on this instance returns the response data which is of type [`PlaylistObject`](../../doc/models/playlist-object.md).

## Example Usage

```php
$playlistId = '3cEYpjA9oz9GiPac4AsH4n';

$market = 'ES';

$fields = 'items(added_by.id,track(name,href,album(name,href)))';

$playlistsApi = $client->getPlaylistsApi();
$apiResponse = $playlistsApi->getPlaylist(
    $playlistId,
    $market,
    $fields
);

// Extracting response status code
var_dump($apiResponse->getStatusCode());
// Extracting response headers
var_dump($apiResponse->getHeaders());

if ($apiResponse->isSuccess()) {
    echo 'PlaylistObject:';
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


# Change-Playlist-Details

Change a playlist's name and public/private state. (The user must, of
course, own the playlist.)

```php
function changePlaylistDetails(string $playlistId, ?PlaylistsRequest $body = null): ApiResponse
```

## Authentication

This endpoint requires [oauth_2_0](../../doc/auth/oauth-2-authorization-code-grant.md)

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `playlistId` | `string` | Template, Required | - |
| `body` | [`?PlaylistsRequest`](../../doc/models/playlists-request.md) | Body, Optional | - |

## Requires scope

### oauth_2_0

`playlist-modify-private`, `playlist-modify-public`

## Response Type

**200**: Playlist updated

This method returns an [`ApiResponse`](../../doc/api-response.md) instance.

## Example Usage

```php
$playlistId = '3cEYpjA9oz9GiPac4AsH4n';

$body = PlaylistsRequestBuilder::init()
    ->name('Updated Playlist Name')
    ->public(false)
    ->description('Updated playlist description')
    ->build();

$playlistsApi = $client->getPlaylistsApi();
$apiResponse = $playlistsApi->changePlaylistDetails(
    $playlistId,
    $body
);

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


# Get-Playlists-Tracks

Get full details of the items of a playlist owned by a Spotify user.

```php
function getPlaylistsTracks(
    string $playlistId,
    ?string $market = null,
    ?string $fields = null,
    ?int $limit = 20,
    ?int $offset = 0,
    ?string $additionalTypes = null
): ApiResponse
```

## Authentication

This endpoint requires [oauth_2_0](../../doc/auth/oauth-2-authorization-code-grant.md)

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `playlistId` | `string` | Template, Required | - |
| `market` | `?string` | Query, Optional | - |
| `fields` | `?string` | Query, Optional | - |
| `limit` | `?int` | Query, Optional | **Default**: `20`<br><br>**Constraints**: `>= 1`, `<= 100` |
| `offset` | `?int` | Query, Optional | **Default**: `0` |
| `additionalTypes` | `?string` | Query, Optional | - |

## Requires scope

### oauth_2_0

`playlist-read-private`

## Response Type

**200**: Pages of tracks

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `getResult()` method on this instance returns the response data which is of type [`PagingPlaylistTrackObject`](../../doc/models/paging-playlist-track-object.md).

## Example Usage

```php
$playlistId = '3cEYpjA9oz9GiPac4AsH4n';

$market = 'ES';

$fields = 'items(added_by.id,track(name,href,album(name,href)))';

$limit = 10;

$offset = 5;

$playlistsApi = $client->getPlaylistsApi();
$apiResponse = $playlistsApi->getPlaylistsTracks(
    $playlistId,
    $market,
    $fields,
    $limit,
    $offset
);

// Extracting response status code
var_dump($apiResponse->getStatusCode());
// Extracting response headers
var_dump($apiResponse->getHeaders());

if ($apiResponse->isSuccess()) {
    echo 'PagingPlaylistTrackObject:';
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


# Add-Tracks-to-Playlist

Add one or more items to a user's playlist.

```php
function addTracksToPlaylist(
    string $playlistId,
    ?int $position = null,
    ?string $uris = null,
    ?PlaylistsTracksRequest $body = null
): ApiResponse
```

## Authentication

This endpoint requires [oauth_2_0](../../doc/auth/oauth-2-authorization-code-grant.md)

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `playlistId` | `string` | Template, Required | - |
| `position` | `?int` | Query, Optional | - |
| `uris` | `?string` | Query, Optional | - |
| `body` | [`?PlaylistsTracksRequest`](../../doc/models/playlists-tracks-request.md) | Body, Optional | - |

## Requires scope

### oauth_2_0

`playlist-modify-private`, `playlist-modify-public`

## Response Type

**201**: A snapshot ID for the playlist

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `getResult()` method on this instance returns the response data which is of type [`PlaylistSnapshotId`](../../doc/models/playlist-snapshot-id.md).

## Example Usage

```php
$playlistId = '3cEYpjA9oz9GiPac4AsH4n';

$position = 0;

$uris = 'spotify:track:4iV5W9uYEdYUVa79Axb7Rh,spotify:track:1301WleyT98MSxVHPZCA6M';

$playlistsApi = $client->getPlaylistsApi();
$apiResponse = $playlistsApi->addTracksToPlaylist(
    $playlistId,
    $position,
    $uris
);

// Extracting response status code
var_dump($apiResponse->getStatusCode());
// Extracting response headers
var_dump($apiResponse->getHeaders());

if ($apiResponse->isSuccess()) {
    echo 'PlaylistSnapshotId:';
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


# Reorder-or-Replace-Playlists-Tracks

Either reorder or replace items in a playlist depending on the request's parameters.
To reorder items, include `range_start`, `insert_before`, `range_length` and `snapshot_id` in the request's body.
To replace items, include `uris` as either a query parameter or in the request's body.
Replacing items in a playlist will overwrite its existing items. This operation can be used for replacing or clearing items in a playlist.
<br/>
**Note**: Replace and reorder are mutually exclusive operations which share the same endpoint, but have different parameters.
These operations can't be applied together in a single request.

```php
function reorderOrReplacePlaylistsTracks(
    string $playlistId,
    ?string $uris = null,
    ?PlaylistsTracksRequest1 $body = null
): ApiResponse
```

## Authentication

This endpoint requires [oauth_2_0](../../doc/auth/oauth-2-authorization-code-grant.md)

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `playlistId` | `string` | Template, Required | - |
| `uris` | `?string` | Query, Optional | - |
| `body` | [`?PlaylistsTracksRequest1`](../../doc/models/playlists-tracks-request-1.md) | Body, Optional | - |

## Requires scope

### oauth_2_0

`playlist-modify-private`, `playlist-modify-public`

## Response Type

**200**: A snapshot ID for the playlist

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `getResult()` method on this instance returns the response data which is of type [`PlaylistSnapshotId`](../../doc/models/playlist-snapshot-id.md).

## Example Usage

```php
$playlistId = '3cEYpjA9oz9GiPac4AsH4n';

$body = PlaylistsTracksRequest1Builder::init()
    ->rangeStart(1)
    ->insertBefore(3)
    ->rangeLength(2)
    ->build();

$playlistsApi = $client->getPlaylistsApi();
$apiResponse = $playlistsApi->reorderOrReplacePlaylistsTracks(
    $playlistId,
    null,
    $body
);

// Extracting response status code
var_dump($apiResponse->getStatusCode());
// Extracting response headers
var_dump($apiResponse->getHeaders());

if ($apiResponse->isSuccess()) {
    echo 'PlaylistSnapshotId:';
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


# Remove-Tracks-Playlist

Remove one or more items from a user's playlist.

```php
function removeTracksPlaylist(string $playlistId, ?PlaylistsTracksRequest2 $body = null): ApiResponse
```

## Authentication

This endpoint requires [oauth_2_0](../../doc/auth/oauth-2-authorization-code-grant.md)

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `playlistId` | `string` | Template, Required | - |
| `body` | [`?PlaylistsTracksRequest2`](../../doc/models/playlists-tracks-request-2.md) | Body, Optional | - |

## Requires scope

### oauth_2_0

`playlist-modify-private`, `playlist-modify-public`

## Response Type

**200**: A snapshot ID for the playlist

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `getResult()` method on this instance returns the response data which is of type [`PlaylistSnapshotId`](../../doc/models/playlist-snapshot-id.md).

## Example Usage

```php
$playlistId = '3cEYpjA9oz9GiPac4AsH4n';

$body = PlaylistsTracksRequest2Builder::init(
    [
        Track1Builder::init()->build()
    ]
)->build();

$playlistsApi = $client->getPlaylistsApi();
$apiResponse = $playlistsApi->removeTracksPlaylist(
    $playlistId,
    $body
);

// Extracting response status code
var_dump($apiResponse->getStatusCode());
// Extracting response headers
var_dump($apiResponse->getHeaders());

if ($apiResponse->isSuccess()) {
    echo 'PlaylistSnapshotId:';
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


# Get-a-List-of-Current-Users-Playlists

Get a list of the playlists owned or followed by the current Spotify
user.

```php
function getAListOfCurrentUsersPlaylists(?int $limit = 20, ?int $offset = 0): ApiResponse
```

## Authentication

This endpoint requires [oauth_2_0](../../doc/auth/oauth-2-authorization-code-grant.md)

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `limit` | `?int` | Query, Optional | **Default**: `20`<br><br>**Constraints**: `>= 1`, `<= 50` |
| `offset` | `?int` | Query, Optional | **Default**: `0` |

## Requires scope

### oauth_2_0

`playlist-read-private`

## Response Type

**200**: A paged set of playlists

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `getResult()` method on this instance returns the response data which is of type [`PagingPlaylistObject`](../../doc/models/paging-playlist-object.md).

## Example Usage

```php
$limit = 10;

$offset = 5;

$playlistsApi = $client->getPlaylistsApi();
$apiResponse = $playlistsApi->getAListOfCurrentUsersPlaylists(
    $limit,
    $offset
);

// Extracting response status code
var_dump($apiResponse->getStatusCode());
// Extracting response headers
var_dump($apiResponse->getHeaders());

if ($apiResponse->isSuccess()) {
    echo 'PagingPlaylistObject:';
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


# Get-List-Users-Playlists

Get a list of the playlists owned or followed by a Spotify user.

```php
function getListUsersPlaylists(string $userId, ?int $limit = 20, ?int $offset = 0): ApiResponse
```

## Authentication

This endpoint requires [oauth_2_0](../../doc/auth/oauth-2-authorization-code-grant.md)

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `userId` | `string` | Template, Required | - |
| `limit` | `?int` | Query, Optional | **Default**: `20`<br><br>**Constraints**: `>= 1`, `<= 50` |
| `offset` | `?int` | Query, Optional | **Default**: `0` |

## Requires scope

### oauth_2_0

`playlist-read-collaborative`, `playlist-read-private`

## Response Type

**200**: A paged set of playlists

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `getResult()` method on this instance returns the response data which is of type [`PagingPlaylistObject`](../../doc/models/paging-playlist-object.md).

## Example Usage

```php
$userId = 'smedjan';

$limit = 10;

$offset = 5;

$playlistsApi = $client->getPlaylistsApi();
$apiResponse = $playlistsApi->getListUsersPlaylists(
    $userId,
    $limit,
    $offset
);

// Extracting response status code
var_dump($apiResponse->getStatusCode());
// Extracting response headers
var_dump($apiResponse->getHeaders());

if ($apiResponse->isSuccess()) {
    echo 'PagingPlaylistObject:';
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


# Create-Playlist

Create a playlist for a Spotify user. (The playlist will be empty until
you [add tracks](https://developer.spotify.com/documentation/web-api/reference/add-tracks-to-playlist).)
Each user is generally limited to a maximum of 11000 playlists.

```php
function createPlaylist(string $userId, ?UsersPlaylistsRequest $body = null): ApiResponse
```

## Authentication

This endpoint requires [oauth_2_0](../../doc/auth/oauth-2-authorization-code-grant.md)

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `userId` | `string` | Template, Required | - |
| `body` | [`?UsersPlaylistsRequest`](../../doc/models/users-playlists-request.md) | Body, Optional | - |

## Requires scope

### oauth_2_0

`playlist-modify-private`, `playlist-modify-public`

## Response Type

**201**: A playlist

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `getResult()` method on this instance returns the response data which is of type [`PlaylistObject`](../../doc/models/playlist-object.md).

## Example Usage

```php
$userId = 'smedjan';

$body = UsersPlaylistsRequestBuilder::init(
    'New Playlist'
)
    ->public(false)
    ->description('New playlist description')
    ->build();

$playlistsApi = $client->getPlaylistsApi();
$apiResponse = $playlistsApi->createPlaylist(
    $userId,
    $body
);

// Extracting response status code
var_dump($apiResponse->getStatusCode());
// Extracting response headers
var_dump($apiResponse->getHeaders());

if ($apiResponse->isSuccess()) {
    echo 'PlaylistObject:';
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


# Get-Featured-Playlists

Get a list of Spotify featured playlists (shown, for example, on a Spotify player's 'Browse' tab).

```php
function getFeaturedPlaylists(?string $locale = null, ?int $limit = 20, ?int $offset = 0): ApiResponse
```

## Authentication

This endpoint requires [oauth_2_0](../../doc/auth/oauth-2-authorization-code-grant.md)

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `locale` | `?string` | Query, Optional | - |
| `limit` | `?int` | Query, Optional | **Default**: `20`<br><br>**Constraints**: `>= 1`, `<= 50` |
| `offset` | `?int` | Query, Optional | **Default**: `0` |

## Response Type

**200**: A paged set of playlists

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `getResult()` method on this instance returns the response data which is of type [`PagingFeaturedPlaylistObject`](../../doc/models/paging-featured-playlist-object.md).

## Example Usage

```php
$locale = 'sv_SE';

$limit = 10;

$offset = 5;

$playlistsApi = $client->getPlaylistsApi();
$apiResponse = $playlistsApi->getFeaturedPlaylists(
    $locale,
    $limit,
    $offset
);

// Extracting response status code
var_dump($apiResponse->getStatusCode());
// Extracting response headers
var_dump($apiResponse->getHeaders());

if ($apiResponse->isSuccess()) {
    echo 'PagingFeaturedPlaylistObject:';
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


# Get-a-Categories-Playlists

Get a list of Spotify playlists tagged with a particular category.

```php
function getACategoriesPlaylists(string $categoryId, ?int $limit = 20, ?int $offset = 0): ApiResponse
```

## Authentication

This endpoint requires [oauth_2_0](../../doc/auth/oauth-2-authorization-code-grant.md)

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `categoryId` | `string` | Template, Required | - |
| `limit` | `?int` | Query, Optional | **Default**: `20`<br><br>**Constraints**: `>= 1`, `<= 50` |
| `offset` | `?int` | Query, Optional | **Default**: `0` |

## Response Type

**200**: A paged set of playlists

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `getResult()` method on this instance returns the response data which is of type [`PagingFeaturedPlaylistObject`](../../doc/models/paging-featured-playlist-object.md).

## Example Usage

```php
$categoryId = 'dinner';

$limit = 10;

$offset = 5;

$playlistsApi = $client->getPlaylistsApi();
$apiResponse = $playlistsApi->getACategoriesPlaylists(
    $categoryId,
    $limit,
    $offset
);

// Extracting response status code
var_dump($apiResponse->getStatusCode());
// Extracting response headers
var_dump($apiResponse->getHeaders());

if ($apiResponse->isSuccess()) {
    echo 'PagingFeaturedPlaylistObject:';
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


# Get-Playlist-Cover

Get the current image associated with a specific playlist.

```php
function getPlaylistCover(string $playlistId): ApiResponse
```

## Authentication

This endpoint requires [oauth_2_0](../../doc/auth/oauth-2-authorization-code-grant.md)

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `playlistId` | `string` | Template, Required | - |

## Response Type

**200**: A set of images

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `getResult()` method on this instance returns the response data which is of type [`ImageObject[]`](../../doc/models/image-object.md).

## Example Usage

```php
$playlistId = '3cEYpjA9oz9GiPac4AsH4n';

$playlistsApi = $client->getPlaylistsApi();
$apiResponse = $playlistsApi->getPlaylistCover($playlistId);

// Extracting response status code
var_dump($apiResponse->getStatusCode());
// Extracting response headers
var_dump($apiResponse->getHeaders());

if ($apiResponse->isSuccess()) {
    echo 'ImageObject[]:';
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


# Upload-Custom-Playlist-Cover

Replace the image used to represent a specific playlist.

```php
function uploadCustomPlaylistCover(string $playlistId, array $body): ApiResponse
```

## Authentication

This endpoint requires [oauth_2_0](../../doc/auth/oauth-2-authorization-code-grant.md)

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `playlistId` | `string` | Template, Required | - |
| `body` | `array` | Body, Required | - |

## Requires scope

### oauth_2_0

`playlist-modify-private`, `playlist-modify-public`, `ugc-image-upload`

## Response Type

**202**: Image uploaded

This method returns an [`ApiResponse`](../../doc/api-response.md) instance.

## Example Usage

```php
$playlistId = '3cEYpjA9oz9GiPac4AsH4n';

$body = ApiHelper::deserialize('{"key1":"val1","key2":"val2"}');

$playlistsApi = $client->getPlaylistsApi();
$apiResponse = $playlistsApi->uploadCustomPlaylistCover(
    $playlistId,
    $body
);

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

