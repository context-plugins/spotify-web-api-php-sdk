# Users

```php
$usersApi = $client->getUsersApi();
```

## Class Name

`UsersApi`

## Methods

* [Get-Current-Users-Profile](../../doc/controllers/users.md#get-current-users-profile)
* [Get-Users-Profile](../../doc/controllers/users.md#get-users-profile)
* [Follow-Playlist](../../doc/controllers/users.md#follow-playlist)
* [Unfollow-Playlist](../../doc/controllers/users.md#unfollow-playlist)
* [Get-Followed](../../doc/controllers/users.md#get-followed)
* [Follow-Artists-Users](../../doc/controllers/users.md#follow-artists-users)
* [Unfollow-Artists-Users](../../doc/controllers/users.md#unfollow-artists-users)
* [Check-Current-User-Follows](../../doc/controllers/users.md#check-current-user-follows)
* [Check-if-User-Follows-Playlist](../../doc/controllers/users.md#check-if-user-follows-playlist)
* [Get-Users-Top-Artists](../../doc/controllers/users.md#get-users-top-artists)
* [Get-Users-Top-Tracks](../../doc/controllers/users.md#get-users-top-tracks)


# Get-Current-Users-Profile

Get detailed profile information about the current user (including the
current user's username).

```php
function getCurrentUsersProfile(): ApiResponse
```

## Authentication

This endpoint requires [oauth_2_0](../../doc/auth/oauth-2-authorization-code-grant.md)

## Requires scope

### oauth_2_0

`user-read-email`, `user-read-private`

## Response Type

**200**: A user

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `getResult()` method on this instance returns the response data which is of type [`PrivateUserObject`](../../doc/models/private-user-object.md).

## Example Usage

```php
$usersApi = $client->getUsersApi();
$apiResponse = $usersApi->getCurrentUsersProfile();

// Extracting response status code
var_dump($apiResponse->getStatusCode());
// Extracting response headers
var_dump($apiResponse->getHeaders());

if ($apiResponse->isSuccess()) {
    echo 'PrivateUserObject:';
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


# Get-Users-Profile

Get public profile information about a Spotify user.

```php
function getUsersProfile(string $userId): ApiResponse
```

## Authentication

This endpoint requires [oauth_2_0](../../doc/auth/oauth-2-authorization-code-grant.md)

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `userId` | `string` | Template, Required | - |

## Response Type

**200**: A user

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `getResult()` method on this instance returns the response data which is of type [`PublicUserObject`](../../doc/models/public-user-object.md).

## Example Usage

```php
$userId = 'smedjan';

$usersApi = $client->getUsersApi();
$apiResponse = $usersApi->getUsersProfile($userId);

// Extracting response status code
var_dump($apiResponse->getStatusCode());
// Extracting response headers
var_dump($apiResponse->getHeaders());

if ($apiResponse->isSuccess()) {
    echo 'PublicUserObject:';
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


# Follow-Playlist

Add the current user as a follower of a playlist.

```php
function followPlaylist(string $playlistId, ?PlaylistsFollowersRequest $body = null): ApiResponse
```

## Authentication

This endpoint requires [oauth_2_0](../../doc/auth/oauth-2-authorization-code-grant.md)

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `playlistId` | `string` | Template, Required | - |
| `body` | [`?PlaylistsFollowersRequest`](../../doc/models/playlists-followers-request.md) | Body, Optional | - |

## Requires scope

### oauth_2_0

`playlist-modify-private`, `playlist-modify-public`

## Response Type

**200**: Playlist followed

This method returns an [`ApiResponse`](../../doc/api-response.md) instance.

## Example Usage

```php
$playlistId = '3cEYpjA9oz9GiPac4AsH4n';

$body = PlaylistsFollowersRequestBuilder::init()
    ->public(false)
    ->build();

$usersApi = $client->getUsersApi();
$apiResponse = $usersApi->followPlaylist(
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


# Unfollow-Playlist

Remove the current user as a follower of a playlist.

```php
function unfollowPlaylist(string $playlistId): ApiResponse
```

## Authentication

This endpoint requires [oauth_2_0](../../doc/auth/oauth-2-authorization-code-grant.md)

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `playlistId` | `string` | Template, Required | - |

## Requires scope

### oauth_2_0

`playlist-modify-private`, `playlist-modify-public`

## Response Type

**200**: Playlist unfollowed

This method returns an [`ApiResponse`](../../doc/api-response.md) instance.

## Example Usage

```php
$playlistId = '3cEYpjA9oz9GiPac4AsH4n';

$usersApi = $client->getUsersApi();
$apiResponse = $usersApi->unfollowPlaylist($playlistId);

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


# Get-Followed

Get the current user's followed artists.

```php
function getFollowed(string $type, ?string $after = null, ?int $limit = 20): ApiResponse
```

## Authentication

This endpoint requires [oauth_2_0](../../doc/auth/oauth-2-authorization-code-grant.md)

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `type` | [`string(ItemType1)`](../../doc/models/item-type-1.md) | Query, Required | - |
| `after` | `?string` | Query, Optional | - |
| `limit` | `?int` | Query, Optional | **Default**: `20`<br><br>**Constraints**: `>= 1`, `<= 50` |

## Requires scope

### oauth_2_0

`user-follow-read`

## Response Type

**200**: A paged set of artists

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `getResult()` method on this instance returns the response data which is of type [`CursorPagedArtists`](../../doc/models/cursor-paged-artists.md).

## Example Usage

```php
$type = ItemType1::ARTIST;

$after = '0I2XqVXqHScXjHhk6AYYRe';

$limit = 10;

$usersApi = $client->getUsersApi();
$apiResponse = $usersApi->getFollowed(
    $type,
    $after,
    $limit
);

// Extracting response status code
var_dump($apiResponse->getStatusCode());
// Extracting response headers
var_dump($apiResponse->getHeaders());

if ($apiResponse->isSuccess()) {
    echo 'CursorPagedArtists:';
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


# Follow-Artists-Users

Add the current user as a follower of one or more artists or other Spotify users.

```php
function followArtistsUsers(string $type, string $ids, ?FollowArtistsOrUsersRequest $body = null): ApiResponse
```

## Authentication

This endpoint requires [oauth_2_0](../../doc/auth/oauth-2-authorization-code-grant.md)

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `type` | [`string(ItemType2)`](../../doc/models/item-type-2.md) | Query, Required | - |
| `ids` | `string` | Query, Required | - |
| `body` | [`?FollowArtistsOrUsersRequest`](../../doc/models/follow-artists-or-users-request.md) | Body, Optional | - |

## Requires scope

### oauth_2_0

`user-follow-modify`

## Response Type

**204**: Artist or user followed

This method returns an [`ApiResponse`](../../doc/api-response.md) instance.

## Example Usage

```php
$type = ItemType2::ARTIST;

$ids = '2CIMQHirSU0MQqyYHq0eOx,57dN52uHvrHOxijzpIgu3E,1vCWHaC5f2uS3yhpwWbIA6';

$usersApi = $client->getUsersApi();
$apiResponse = $usersApi->followArtistsUsers(
    $type,
    $ids
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


# Unfollow-Artists-Users

Remove the current user as a follower of one or more artists or other Spotify users.

```php
function unfollowArtistsUsers(
    string $type,
    string $ids,
    ?UnfollowArtistsOrUsersRequest $body = null
): ApiResponse
```

## Authentication

This endpoint requires [oauth_2_0](../../doc/auth/oauth-2-authorization-code-grant.md)

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `type` | [`string(ItemType3)`](../../doc/models/item-type-3.md) | Query, Required | - |
| `ids` | `string` | Query, Required | - |
| `body` | [`?UnfollowArtistsOrUsersRequest`](../../doc/models/unfollow-artists-or-users-request.md) | Body, Optional | - |

## Requires scope

### oauth_2_0

`user-follow-modify`

## Response Type

**200**: Artist or user unfollowed

This method returns an [`ApiResponse`](../../doc/api-response.md) instance.

## Example Usage

```php
$type = ItemType3::ARTIST;

$ids = '2CIMQHirSU0MQqyYHq0eOx,57dN52uHvrHOxijzpIgu3E,1vCWHaC5f2uS3yhpwWbIA6';

$usersApi = $client->getUsersApi();
$apiResponse = $usersApi->unfollowArtistsUsers(
    $type,
    $ids
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


# Check-Current-User-Follows

Check to see if the current user is following one or more artists or other Spotify users.

```php
function checkCurrentUserFollows(string $type, string $ids): ApiResponse
```

## Authentication

This endpoint requires [oauth_2_0](../../doc/auth/oauth-2-authorization-code-grant.md)

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `type` | [`string(ItemType3)`](../../doc/models/item-type-3.md) | Query, Required | - |
| `ids` | `string` | Query, Required | - |

## Requires scope

### oauth_2_0

`user-follow-read`

## Response Type

**200**: Array of booleans

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `getResult()` method on this instance returns the response data which is of type `bool[]`.

## Example Usage

```php
$type = ItemType3::ARTIST;

$ids = '2CIMQHirSU0MQqyYHq0eOx,57dN52uHvrHOxijzpIgu3E,1vCWHaC5f2uS3yhpwWbIA6';

$usersApi = $client->getUsersApi();
$apiResponse = $usersApi->checkCurrentUserFollows(
    $type,
    $ids
);

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


# Check-if-User-Follows-Playlist

Check to see if one or more Spotify users are following a specified playlist.

```php
function checkIfUserFollowsPlaylist(string $playlistId, string $ids): ApiResponse
```

## Authentication

This endpoint requires [oauth_2_0](../../doc/auth/oauth-2-authorization-code-grant.md)

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `playlistId` | `string` | Template, Required | - |
| `ids` | `string` | Query, Required | - |

## Response Type

**200**: Array of booleans

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `getResult()` method on this instance returns the response data which is of type `bool[]`.

## Example Usage

```php
$playlistId = '3cEYpjA9oz9GiPac4AsH4n';

$ids = 'jmperezperez,thelinmichael,wizzler';

$usersApi = $client->getUsersApi();
$apiResponse = $usersApi->checkIfUserFollowsPlaylist(
    $playlistId,
    $ids
);

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


# Get-Users-Top-Artists

Get the current user's top artists based on calculated affinity.

```php
function getUsersTopArtists(?string $timeRange = 'medium_term', ?int $limit = 20, ?int $offset = 0): ApiResponse
```

## Authentication

This endpoint requires [oauth_2_0](../../doc/auth/oauth-2-authorization-code-grant.md)

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `timeRange` | `?string` | Query, Optional | **Default**: `'medium_term'` |
| `limit` | `?int` | Query, Optional | **Default**: `20`<br><br>**Constraints**: `>= 1`, `<= 50` |
| `offset` | `?int` | Query, Optional | **Default**: `0` |

## Requires scope

### oauth_2_0

`user-top-read`

## Response Type

**200**: Pages of artists

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `getResult()` method on this instance returns the response data which is of type [`PagingArtistObject`](../../doc/models/paging-artist-object.md).

## Example Usage

```php
$timeRange = 'medium_term';

$limit = 10;

$offset = 5;

$usersApi = $client->getUsersApi();
$apiResponse = $usersApi->getUsersTopArtists(
    $timeRange,
    $limit,
    $offset
);

// Extracting response status code
var_dump($apiResponse->getStatusCode());
// Extracting response headers
var_dump($apiResponse->getHeaders());

if ($apiResponse->isSuccess()) {
    echo 'PagingArtistObject:';
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


# Get-Users-Top-Tracks

Get the current user's top tracks based on calculated affinity.

```php
function getUsersTopTracks(?string $timeRange = 'medium_term', ?int $limit = 20, ?int $offset = 0): ApiResponse
```

## Authentication

This endpoint requires [oauth_2_0](../../doc/auth/oauth-2-authorization-code-grant.md)

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `timeRange` | `?string` | Query, Optional | **Default**: `'medium_term'` |
| `limit` | `?int` | Query, Optional | **Default**: `20`<br><br>**Constraints**: `>= 1`, `<= 50` |
| `offset` | `?int` | Query, Optional | **Default**: `0` |

## Requires scope

### oauth_2_0

`user-top-read`

## Response Type

**200**: Pages of tracks

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `getResult()` method on this instance returns the response data which is of type [`PagingTrackObject`](../../doc/models/paging-track-object.md).

## Example Usage

```php
$timeRange = 'medium_term';

$limit = 10;

$offset = 5;

$usersApi = $client->getUsersApi();
$apiResponse = $usersApi->getUsersTopTracks(
    $timeRange,
    $limit,
    $offset
);

// Extracting response status code
var_dump($apiResponse->getStatusCode());
// Extracting response headers
var_dump($apiResponse->getHeaders());

if ($apiResponse->isSuccess()) {
    echo 'PagingTrackObject:';
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

