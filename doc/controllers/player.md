# Player

```php
$playerApi = $client->getPlayerApi();
```

## Class Name

`PlayerApi`

## Methods

* [Get-Information-about-the-Users-Current-Playback](../../doc/controllers/player.md#get-information-about-the-users-current-playback)
* [Transfer-a-Users-Playback](../../doc/controllers/player.md#transfer-a-users-playback)
* [Get-a-Users-Available-Devices](../../doc/controllers/player.md#get-a-users-available-devices)
* [Get-the-Users-Currently-Playing-Track](../../doc/controllers/player.md#get-the-users-currently-playing-track)
* [Start-a-Users-Playback](../../doc/controllers/player.md#start-a-users-playback)
* [Pause-a-Users-Playback](../../doc/controllers/player.md#pause-a-users-playback)
* [Skip-Users-Playback-to-Next-Track](../../doc/controllers/player.md#skip-users-playback-to-next-track)
* [Skip-Users-Playback-to-Previous-Track](../../doc/controllers/player.md#skip-users-playback-to-previous-track)
* [Seek-to-Position-in-Currently-Playing-Track](../../doc/controllers/player.md#seek-to-position-in-currently-playing-track)
* [Set-Repeat-Mode-on-Users-Playback](../../doc/controllers/player.md#set-repeat-mode-on-users-playback)
* [Set-Volume-for-Users-Playback](../../doc/controllers/player.md#set-volume-for-users-playback)
* [Toggle-Shuffle-for-Users-Playback](../../doc/controllers/player.md#toggle-shuffle-for-users-playback)
* [Get-Recently-Played](../../doc/controllers/player.md#get-recently-played)
* [Get-Queue](../../doc/controllers/player.md#get-queue)
* [Add-to-Queue](../../doc/controllers/player.md#add-to-queue)


# Get-Information-about-the-Users-Current-Playback

Get information about the user’s current playback state, including track or episode, progress, and active device.

```php
function getInformationAboutTheUsersCurrentPlayback(
    ?string $market = null,
    ?string $additionalTypes = null
): ApiResponse
```

## Authentication

This endpoint requires [oauth_2_0](../../doc/auth/oauth-2-authorization-code-grant.md)

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `market` | `?string` | Query, Optional | - |
| `additionalTypes` | `?string` | Query, Optional | - |

## Requires scope

### oauth_2_0

`user-read-playback-state`

## Response Type

**200**: Information about playback

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `getResult()` method on this instance returns the response data which is of type [`CurrentlyPlayingContextObject`](../../doc/models/currently-playing-context-object.md).

## Example Usage

```php
$market = 'ES';

$playerApi = $client->getPlayerApi();
$apiResponse = $playerApi->getInformationAboutTheUsersCurrentPlayback($market);

// Extracting response status code
var_dump($apiResponse->getStatusCode());
// Extracting response headers
var_dump($apiResponse->getHeaders());

if ($apiResponse->isSuccess()) {
    echo 'CurrentlyPlayingContextObject:';
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


# Transfer-a-Users-Playback

Transfer playback to a new device and optionally begin playback. This API only works for users who have Spotify Premium. The order of execution is not guaranteed when you use this API with other Player API endpoints.

```php
function transferAUsersPlayback(?MePlayerRequest $body = null): ApiResponse
```

## Authentication

This endpoint requires [oauth_2_0](../../doc/auth/oauth-2-authorization-code-grant.md)

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `body` | [`?MePlayerRequest`](../../doc/models/me-player-request.md) | Body, Optional | - |

## Requires scope

### oauth_2_0

`user-modify-playback-state`

## Response Type

**204**: Playback transferred

This method returns an [`ApiResponse`](../../doc/api-response.md) instance.

## Example Usage

```php
$body = MePlayerRequestBuilder::init(
    [
        '74ASZWbe4lXaubB36ztrGX'
    ]
)->build();

$playerApi = $client->getPlayerApi();
$apiResponse = $playerApi->transferAUsersPlayback($body);

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


# Get-a-Users-Available-Devices

Get information about a user’s available Spotify Connect devices. Some device models are not supported and will not be listed in the API response.

```php
function getAUsersAvailableDevices(): ApiResponse
```

## Authentication

This endpoint requires [oauth_2_0](../../doc/auth/oauth-2-authorization-code-grant.md)

## Requires scope

### oauth_2_0

`user-read-playback-state`

## Response Type

**200**: A set of devices

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `getResult()` method on this instance returns the response data which is of type [`ManyDevices`](../../doc/models/many-devices.md).

## Example Usage

```php
$playerApi = $client->getPlayerApi();
$apiResponse = $playerApi->getAUsersAvailableDevices();

// Extracting response status code
var_dump($apiResponse->getStatusCode());
// Extracting response headers
var_dump($apiResponse->getHeaders());

if ($apiResponse->isSuccess()) {
    echo 'ManyDevices:';
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


# Get-the-Users-Currently-Playing-Track

Get the object currently being played on the user's Spotify account.

```php
function getTheUsersCurrentlyPlayingTrack(?string $market = null, ?string $additionalTypes = null): ApiResponse
```

## Authentication

This endpoint requires [oauth_2_0](../../doc/auth/oauth-2-authorization-code-grant.md)

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `market` | `?string` | Query, Optional | - |
| `additionalTypes` | `?string` | Query, Optional | - |

## Requires scope

### oauth_2_0

`user-read-currently-playing`

## Response Type

**200**: Information about the currently playing track

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `getResult()` method on this instance returns the response data which is of type [`CurrentlyPlayingObject`](../../doc/models/currently-playing-object.md).

## Example Usage

```php
$market = 'ES';

$playerApi = $client->getPlayerApi();
$apiResponse = $playerApi->getTheUsersCurrentlyPlayingTrack($market);

// Extracting response status code
var_dump($apiResponse->getStatusCode());
// Extracting response headers
var_dump($apiResponse->getHeaders());

if ($apiResponse->isSuccess()) {
    echo 'CurrentlyPlayingObject:';
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


# Start-a-Users-Playback

Start a new context or resume current playback on the user's active device. This API only works for users who have Spotify Premium. The order of execution is not guaranteed when you use this API with other Player API endpoints.

```php
function startAUsersPlayback(?string $deviceId = null, ?StartOrResumePlaybackRequest $body = null): ApiResponse
```

## Authentication

This endpoint requires [oauth_2_0](../../doc/auth/oauth-2-authorization-code-grant.md)

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `deviceId` | `?string` | Query, Optional | - |
| `body` | [`?StartOrResumePlaybackRequest`](../../doc/models/start-or-resume-playback-request.md) | Body, Optional | - |

## Requires scope

### oauth_2_0

`user-modify-playback-state`

## Response Type

**204**: Playback started

This method returns an [`ApiResponse`](../../doc/api-response.md) instance.

## Example Usage

```php
$deviceId = '0d1841b0976bae2a3a310dd74c0f3df354899bc8';

$body = StartOrResumePlaybackRequestBuilder::init()
    ->contextUri('spotify:album:5ht7ItJgpBH7W6vJ5BqpPr')
    ->offset(ApiHelper::deserialize('{"position":5}'))
    ->positionMs(0)
    ->build();

$playerApi = $client->getPlayerApi();
$apiResponse = $playerApi->startAUsersPlayback(
    $deviceId,
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


# Pause-a-Users-Playback

Pause playback on the user's account. This API only works for users who have Spotify Premium. The order of execution is not guaranteed when you use this API with other Player API endpoints.

```php
function pauseAUsersPlayback(?string $deviceId = null): ApiResponse
```

## Authentication

This endpoint requires [oauth_2_0](../../doc/auth/oauth-2-authorization-code-grant.md)

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `deviceId` | `?string` | Query, Optional | - |

## Requires scope

### oauth_2_0

`user-modify-playback-state`

## Response Type

**204**: Playback paused

This method returns an [`ApiResponse`](../../doc/api-response.md) instance.

## Example Usage

```php
$deviceId = '0d1841b0976bae2a3a310dd74c0f3df354899bc8';

$playerApi = $client->getPlayerApi();
$apiResponse = $playerApi->pauseAUsersPlayback($deviceId);

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


# Skip-Users-Playback-to-Next-Track

Skips to next track in the user’s queue. This API only works for users who have Spotify Premium. The order of execution is not guaranteed when you use this API with other Player API endpoints.

```php
function skipUsersPlaybackToNextTrack(?string $deviceId = null): ApiResponse
```

## Authentication

This endpoint requires [oauth_2_0](../../doc/auth/oauth-2-authorization-code-grant.md)

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `deviceId` | `?string` | Query, Optional | - |

## Requires scope

### oauth_2_0

`user-modify-playback-state`

## Response Type

**204**: Command sent

This method returns an [`ApiResponse`](../../doc/api-response.md) instance.

## Example Usage

```php
$deviceId = '0d1841b0976bae2a3a310dd74c0f3df354899bc8';

$playerApi = $client->getPlayerApi();
$apiResponse = $playerApi->skipUsersPlaybackToNextTrack($deviceId);

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


# Skip-Users-Playback-to-Previous-Track

Skips to previous track in the user’s queue. This API only works for users who have Spotify Premium. The order of execution is not guaranteed when you use this API with other Player API endpoints.

```php
function skipUsersPlaybackToPreviousTrack(?string $deviceId = null): ApiResponse
```

## Authentication

This endpoint requires [oauth_2_0](../../doc/auth/oauth-2-authorization-code-grant.md)

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `deviceId` | `?string` | Query, Optional | - |

## Requires scope

### oauth_2_0

`user-modify-playback-state`

## Response Type

**204**: Command sent

This method returns an [`ApiResponse`](../../doc/api-response.md) instance.

## Example Usage

```php
$deviceId = '0d1841b0976bae2a3a310dd74c0f3df354899bc8';

$playerApi = $client->getPlayerApi();
$apiResponse = $playerApi->skipUsersPlaybackToPreviousTrack($deviceId);

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


# Seek-to-Position-in-Currently-Playing-Track

Seeks to the given position in the user’s currently playing track. This API only works for users who have Spotify Premium. The order of execution is not guaranteed when you use this API with other Player API endpoints.

```php
function seekToPositionInCurrentlyPlayingTrack(int $positionMs, ?string $deviceId = null): ApiResponse
```

## Authentication

This endpoint requires [oauth_2_0](../../doc/auth/oauth-2-authorization-code-grant.md)

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `positionMs` | `int` | Query, Required | - |
| `deviceId` | `?string` | Query, Optional | - |

## Requires scope

### oauth_2_0

`user-modify-playback-state`

## Response Type

**204**: Command sent

This method returns an [`ApiResponse`](../../doc/api-response.md) instance.

## Example Usage

```php
$positionMs = 25000;

$deviceId = '0d1841b0976bae2a3a310dd74c0f3df354899bc8';

$playerApi = $client->getPlayerApi();
$apiResponse = $playerApi->seekToPositionInCurrentlyPlayingTrack(
    $positionMs,
    $deviceId
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


# Set-Repeat-Mode-on-Users-Playback

Set the repeat mode for the user's playback. This API only works for users who have Spotify Premium. The order of execution is not guaranteed when you use this API with other Player API endpoints.

```php
function setRepeatModeOnUsersPlayback(string $state, ?string $deviceId = null): ApiResponse
```

## Authentication

This endpoint requires [oauth_2_0](../../doc/auth/oauth-2-authorization-code-grant.md)

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `state` | `string` | Query, Required | - |
| `deviceId` | `?string` | Query, Optional | - |

## Requires scope

### oauth_2_0

`user-modify-playback-state`

## Response Type

**204**: Command sent

This method returns an [`ApiResponse`](../../doc/api-response.md) instance.

## Example Usage

```php
$state = 'context';

$deviceId = '0d1841b0976bae2a3a310dd74c0f3df354899bc8';

$playerApi = $client->getPlayerApi();
$apiResponse = $playerApi->setRepeatModeOnUsersPlayback(
    $state,
    $deviceId
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


# Set-Volume-for-Users-Playback

Set the volume for the user’s current playback device. This API only works for users who have Spotify Premium. The order of execution is not guaranteed when you use this API with other Player API endpoints.

```php
function setVolumeForUsersPlayback(int $volumePercent, ?string $deviceId = null): ApiResponse
```

## Authentication

This endpoint requires [oauth_2_0](../../doc/auth/oauth-2-authorization-code-grant.md)

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `volumePercent` | `int` | Query, Required | - |
| `deviceId` | `?string` | Query, Optional | - |

## Requires scope

### oauth_2_0

`user-modify-playback-state`

## Response Type

**204**: Command sent

This method returns an [`ApiResponse`](../../doc/api-response.md) instance.

## Example Usage

```php
$volumePercent = 50;

$deviceId = '0d1841b0976bae2a3a310dd74c0f3df354899bc8';

$playerApi = $client->getPlayerApi();
$apiResponse = $playerApi->setVolumeForUsersPlayback(
    $volumePercent,
    $deviceId
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


# Toggle-Shuffle-for-Users-Playback

Toggle shuffle on or off for user’s playback. This API only works for users who have Spotify Premium. The order of execution is not guaranteed when you use this API with other Player API endpoints.

```php
function toggleShuffleForUsersPlayback(bool $state, ?string $deviceId = null): ApiResponse
```

## Authentication

This endpoint requires [oauth_2_0](../../doc/auth/oauth-2-authorization-code-grant.md)

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `state` | `bool` | Query, Required | - |
| `deviceId` | `?string` | Query, Optional | - |

## Requires scope

### oauth_2_0

`user-modify-playback-state`

## Response Type

**204**: Command sent

This method returns an [`ApiResponse`](../../doc/api-response.md) instance.

## Example Usage

```php
$state = true;

$deviceId = '0d1841b0976bae2a3a310dd74c0f3df354899bc8';

$playerApi = $client->getPlayerApi();
$apiResponse = $playerApi->toggleShuffleForUsersPlayback(
    $state,
    $deviceId
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


# Get-Recently-Played

Get tracks from the current user's recently played tracks.
_**Note**: Currently doesn't support podcast episodes._

```php
function getRecentlyPlayed(?int $limit = 20, ?int $after = null, ?int $before = null): ApiResponse
```

## Authentication

This endpoint requires [oauth_2_0](../../doc/auth/oauth-2-authorization-code-grant.md)

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `limit` | `?int` | Query, Optional | **Default**: `20`<br><br>**Constraints**: `>= 1`, `<= 50` |
| `after` | `?int` | Query, Optional | - |
| `before` | `?int` | Query, Optional | - |

## Requires scope

### oauth_2_0

`user-read-recently-played`

## Response Type

**200**: A paged set of tracks

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `getResult()` method on this instance returns the response data which is of type [`CursorPagingPlayHistoryObject`](../../doc/models/cursor-paging-play-history-object.md).

## Example Usage

```php
$limit = 10;

$after = 1484811043508;

$playerApi = $client->getPlayerApi();
$apiResponse = $playerApi->getRecentlyPlayed(
    $limit,
    $after
);

// Extracting response status code
var_dump($apiResponse->getStatusCode());
// Extracting response headers
var_dump($apiResponse->getHeaders());

if ($apiResponse->isSuccess()) {
    echo 'CursorPagingPlayHistoryObject:';
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


# Get-Queue

Get the list of objects that make up the user's queue.

```php
function getQueue(): ApiResponse
```

## Authentication

This endpoint requires [oauth_2_0](../../doc/auth/oauth-2-authorization-code-grant.md)

## Requires scope

### oauth_2_0

`user-read-currently-playing`, `user-read-playback-state`

## Response Type

**200**: Information about the queue

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `getResult()` method on this instance returns the response data which is of type [`QueueObject`](../../doc/models/queue-object.md).

## Example Usage

```php
$playerApi = $client->getPlayerApi();
$apiResponse = $playerApi->getQueue();

// Extracting response status code
var_dump($apiResponse->getStatusCode());
// Extracting response headers
var_dump($apiResponse->getHeaders());

if ($apiResponse->isSuccess()) {
    echo 'QueueObject:';
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


# Add-to-Queue

Add an item to the end of the user's current playback queue. This API only works for users who have Spotify Premium. The order of execution is not guaranteed when you use this API with other Player API endpoints.

```php
function addToQueue(string $uri, ?string $deviceId = null): ApiResponse
```

## Authentication

This endpoint requires [oauth_2_0](../../doc/auth/oauth-2-authorization-code-grant.md)

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `uri` | `string` | Query, Required | - |
| `deviceId` | `?string` | Query, Optional | - |

## Requires scope

### oauth_2_0

`user-modify-playback-state`

## Response Type

**204**: Command received

This method returns an [`ApiResponse`](../../doc/api-response.md) instance.

## Example Usage

```php
$uri = 'spotify:track:4iV5W9uYEdYUVa79Axb7Rh';

$deviceId = '0d1841b0976bae2a3a310dd74c0f3df354899bc8';

$playerApi = $client->getPlayerApi();
$apiResponse = $playerApi->addToQueue(
    $uri,
    $deviceId
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

