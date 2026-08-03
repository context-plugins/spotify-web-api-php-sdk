# Tracks

```php
$tracksApi = $client->getTracksApi();
```

## Class Name

`TracksApi`

## Methods

* [Get-Track](../../doc/controllers/tracks.md#get-track)
* [Get-Several-Tracks](../../doc/controllers/tracks.md#get-several-tracks)
* [Get-Users-Saved-Tracks](../../doc/controllers/tracks.md#get-users-saved-tracks)
* [Save-Tracks-User](../../doc/controllers/tracks.md#save-tracks-user)
* [Remove-Tracks-User](../../doc/controllers/tracks.md#remove-tracks-user)
* [Check-Users-Saved-Tracks](../../doc/controllers/tracks.md#check-users-saved-tracks)
* [Get-Several-Audio-Features](../../doc/controllers/tracks.md#get-several-audio-features)
* [Get-Audio-Features](../../doc/controllers/tracks.md#get-audio-features)
* [Get-Audio-Analysis](../../doc/controllers/tracks.md#get-audio-analysis)
* [Get-Recommendations](../../doc/controllers/tracks.md#get-recommendations)


# Get-Track

Get Spotify catalog information for a single track identified by its
unique Spotify ID.

```php
function getTrack(string $id, ?string $market = null): ApiResponse
```

## Authentication

This endpoint requires [oauth_2_0](../../doc/auth/oauth-2-authorization-code-grant.md)

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `id` | `string` | Template, Required | - |
| `market` | `?string` | Query, Optional | - |

## Response Type

**200**: A track

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `getResult()` method on this instance returns the response data which is of type [`TrackObject`](../../doc/models/track-object.md).

## Example Usage

```php
$id = '11dFghVXANMlKmJXsNCbNl';

$market = 'ES';

$tracksApi = $client->getTracksApi();
$apiResponse = $tracksApi->getTrack(
    $id,
    $market
);

// Extracting response status code
var_dump($apiResponse->getStatusCode());
// Extracting response headers
var_dump($apiResponse->getHeaders());

if ($apiResponse->isSuccess()) {
    echo 'TrackObject:';
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


# Get-Several-Tracks

Get Spotify catalog information for multiple tracks based on their Spotify IDs.

```php
function getSeveralTracks(string $ids, ?string $market = null): ApiResponse
```

## Authentication

This endpoint requires [oauth_2_0](../../doc/auth/oauth-2-authorization-code-grant.md)

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `ids` | `string` | Query, Required | - |
| `market` | `?string` | Query, Optional | - |

## Response Type

**200**: A set of tracks

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `getResult()` method on this instance returns the response data which is of type [`ManyTracks`](../../doc/models/many-tracks.md).

## Example Usage

```php
$ids = '7ouMYWpwJ422jRcDASZB7P,4VqPOruhp5EdPBeR92t6lQ,2takcwOaAZWiXQijPHIx7B';

$market = 'ES';

$tracksApi = $client->getTracksApi();
$apiResponse = $tracksApi->getSeveralTracks(
    $ids,
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


# Get-Users-Saved-Tracks

Get a list of the songs saved in the current Spotify user's 'Your Music' library.

```php
function getUsersSavedTracks(?string $market = null, ?int $limit = 20, ?int $offset = 0): ApiResponse
```

## Authentication

This endpoint requires [oauth_2_0](../../doc/auth/oauth-2-authorization-code-grant.md)

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `market` | `?string` | Query, Optional | - |
| `limit` | `?int` | Query, Optional | **Default**: `20`<br><br>**Constraints**: `>= 1`, `<= 50` |
| `offset` | `?int` | Query, Optional | **Default**: `0` |

## Requires scope

### oauth_2_0

`user-library-read`

## Response Type

**200**: Pages of tracks

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `getResult()` method on this instance returns the response data which is of type [`PagingSavedTrackObject`](../../doc/models/paging-saved-track-object.md).

## Example Usage

```php
$market = 'ES';

$limit = 10;

$offset = 5;

$tracksApi = $client->getTracksApi();
$apiResponse = $tracksApi->getUsersSavedTracks(
    $market,
    $limit,
    $offset
);

// Extracting response status code
var_dump($apiResponse->getStatusCode());
// Extracting response headers
var_dump($apiResponse->getHeaders());

if ($apiResponse->isSuccess()) {
    echo 'PagingSavedTrackObject:';
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


# Save-Tracks-User

Save one or more tracks to the current user's 'Your Music' library.

```php
function saveTracksUser(string $ids, ?SaveTracksRequest $body = null): ApiResponse
```

## Authentication

This endpoint requires [oauth_2_0](../../doc/auth/oauth-2-authorization-code-grant.md)

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `ids` | `string` | Query, Required | - |
| `body` | [`?SaveTracksRequest`](../../doc/models/save-tracks-request.md) | Body, Optional | - |

## Requires scope

### oauth_2_0

`user-library-modify`

## Response Type

**200**: Track saved

This method returns an [`ApiResponse`](../../doc/api-response.md) instance.

## Example Usage

```php
$ids = '7ouMYWpwJ422jRcDASZB7P,4VqPOruhp5EdPBeR92t6lQ,2takcwOaAZWiXQijPHIx7B';

$tracksApi = $client->getTracksApi();
$apiResponse = $tracksApi->saveTracksUser($ids);

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


# Remove-Tracks-User

Remove one or more tracks from the current user's 'Your Music' library.

```php
function removeTracksUser(string $ids, ?RemoveTracksRequest $body = null): ApiResponse
```

## Authentication

This endpoint requires [oauth_2_0](../../doc/auth/oauth-2-authorization-code-grant.md)

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `ids` | `string` | Query, Required | - |
| `body` | [`?RemoveTracksRequest`](../../doc/models/remove-tracks-request.md) | Body, Optional | - |

## Requires scope

### oauth_2_0

`user-library-modify`

## Response Type

**200**: Track removed

This method returns an [`ApiResponse`](../../doc/api-response.md) instance.

## Example Usage

```php
$ids = '7ouMYWpwJ422jRcDASZB7P,4VqPOruhp5EdPBeR92t6lQ,2takcwOaAZWiXQijPHIx7B';

$tracksApi = $client->getTracksApi();
$apiResponse = $tracksApi->removeTracksUser($ids);

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


# Check-Users-Saved-Tracks

Check if one or more tracks is already saved in the current Spotify user's 'Your Music' library.

```php
function checkUsersSavedTracks(string $ids): ApiResponse
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
$ids = '7ouMYWpwJ422jRcDASZB7P,4VqPOruhp5EdPBeR92t6lQ,2takcwOaAZWiXQijPHIx7B';

$tracksApi = $client->getTracksApi();
$apiResponse = $tracksApi->checkUsersSavedTracks($ids);

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


# Get-Several-Audio-Features

Get audio features for multiple tracks based on their Spotify IDs.

```php
function getSeveralAudioFeatures(string $ids): ApiResponse
```

## Authentication

This endpoint requires [oauth_2_0](../../doc/auth/oauth-2-authorization-code-grant.md)

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `ids` | `string` | Query, Required | - |

## Response Type

**200**: A set of audio features

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `getResult()` method on this instance returns the response data which is of type [`ManyAudioFeatures`](../../doc/models/many-audio-features.md).

## Example Usage

```php
$ids = '7ouMYWpwJ422jRcDASZB7P,4VqPOruhp5EdPBeR92t6lQ,2takcwOaAZWiXQijPHIx7B';

$tracksApi = $client->getTracksApi();
$apiResponse = $tracksApi->getSeveralAudioFeatures($ids);

// Extracting response status code
var_dump($apiResponse->getStatusCode());
// Extracting response headers
var_dump($apiResponse->getHeaders());

if ($apiResponse->isSuccess()) {
    echo 'ManyAudioFeatures:';
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


# Get-Audio-Features

Get audio feature information for a single track identified by its unique
Spotify ID.

```php
function getAudioFeatures(string $id): ApiResponse
```

## Authentication

This endpoint requires [oauth_2_0](../../doc/auth/oauth-2-authorization-code-grant.md)

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `id` | `string` | Template, Required | - |

## Response Type

**200**: Audio features for one track

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `getResult()` method on this instance returns the response data which is of type [`AudioFeaturesObject`](../../doc/models/audio-features-object.md).

## Example Usage

```php
$id = '11dFghVXANMlKmJXsNCbNl';

$tracksApi = $client->getTracksApi();
$apiResponse = $tracksApi->getAudioFeatures($id);

// Extracting response status code
var_dump($apiResponse->getStatusCode());
// Extracting response headers
var_dump($apiResponse->getHeaders());

if ($apiResponse->isSuccess()) {
    echo 'AudioFeaturesObject:';
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


# Get-Audio-Analysis

Get a low-level audio analysis for a track in the Spotify catalog. The audio analysis describes the track’s structure and musical content, including rhythm, pitch, and timbre.

```php
function getAudioAnalysis(string $id): ApiResponse
```

## Authentication

This endpoint requires [oauth_2_0](../../doc/auth/oauth-2-authorization-code-grant.md)

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `id` | `string` | Template, Required | - |

## Response Type

**200**: Audio analysis for one track

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `getResult()` method on this instance returns the response data which is of type [`AudioAnalysisObject`](../../doc/models/audio-analysis-object.md).

## Example Usage

```php
$id = '11dFghVXANMlKmJXsNCbNl';

$tracksApi = $client->getTracksApi();
$apiResponse = $tracksApi->getAudioAnalysis($id);

// Extracting response status code
var_dump($apiResponse->getStatusCode());
// Extracting response headers
var_dump($apiResponse->getHeaders());

if ($apiResponse->isSuccess()) {
    echo 'AudioAnalysisObject:';
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


# Get-Recommendations

Recommendations are generated based on the available information for a given seed entity and matched against similar artists and tracks. If there is sufficient information about the provided seeds, a list of tracks will be returned together with pool size details.

For artists and tracks that are very new or obscure there might not be enough data to generate a list of tracks.

```php
function getRecommendations(
    ?int $limit = 20,
    ?string $market = null,
    ?string $seedArtists = null,
    ?string $seedGenres = null,
    ?string $seedTracks = null,
    ?float $minAcousticness = null,
    ?float $maxAcousticness = null,
    ?float $targetAcousticness = null,
    ?float $minDanceability = null,
    ?float $maxDanceability = null,
    ?float $targetDanceability = null,
    ?int $minDurationMs = null,
    ?int $maxDurationMs = null,
    ?int $targetDurationMs = null,
    ?float $minEnergy = null,
    ?float $maxEnergy = null,
    ?float $targetEnergy = null,
    ?float $minInstrumentalness = null,
    ?float $maxInstrumentalness = null,
    ?float $targetInstrumentalness = null,
    ?int $minKey = null,
    ?int $maxKey = null,
    ?int $targetKey = null,
    ?float $minLiveness = null,
    ?float $maxLiveness = null,
    ?float $targetLiveness = null,
    ?float $minLoudness = null,
    ?float $maxLoudness = null,
    ?float $targetLoudness = null,
    ?int $minMode = null,
    ?int $maxMode = null,
    ?int $targetMode = null,
    ?int $minPopularity = null,
    ?int $maxPopularity = null,
    ?int $targetPopularity = null,
    ?float $minSpeechiness = null,
    ?float $maxSpeechiness = null,
    ?float $targetSpeechiness = null,
    ?float $minTempo = null,
    ?float $maxTempo = null,
    ?float $targetTempo = null,
    ?int $minTimeSignature = null,
    ?int $maxTimeSignature = null,
    ?int $targetTimeSignature = null,
    ?float $minValence = null,
    ?float $maxValence = null,
    ?float $targetValence = null
): ApiResponse
```

## Authentication

This endpoint requires [oauth_2_0](../../doc/auth/oauth-2-authorization-code-grant.md)

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `limit` | `?int` | Query, Optional | **Default**: `20`<br><br>**Constraints**: `>= 1`, `<= 100` |
| `market` | `?string` | Query, Optional | - |
| `seedArtists` | `?string` | Query, Optional | - |
| `seedGenres` | `?string` | Query, Optional | - |
| `seedTracks` | `?string` | Query, Optional | - |
| `minAcousticness` | `?float` | Query, Optional | **Constraints**: `>= 0`, `<= 1` |
| `maxAcousticness` | `?float` | Query, Optional | **Constraints**: `>= 0`, `<= 1` |
| `targetAcousticness` | `?float` | Query, Optional | **Constraints**: `>= 0`, `<= 1` |
| `minDanceability` | `?float` | Query, Optional | **Constraints**: `>= 0`, `<= 1` |
| `maxDanceability` | `?float` | Query, Optional | **Constraints**: `>= 0`, `<= 1` |
| `targetDanceability` | `?float` | Query, Optional | **Constraints**: `>= 0`, `<= 1` |
| `minDurationMs` | `?int` | Query, Optional | - |
| `maxDurationMs` | `?int` | Query, Optional | - |
| `targetDurationMs` | `?int` | Query, Optional | - |
| `minEnergy` | `?float` | Query, Optional | **Constraints**: `>= 0`, `<= 1` |
| `maxEnergy` | `?float` | Query, Optional | **Constraints**: `>= 0`, `<= 1` |
| `targetEnergy` | `?float` | Query, Optional | **Constraints**: `>= 0`, `<= 1` |
| `minInstrumentalness` | `?float` | Query, Optional | **Constraints**: `>= 0`, `<= 1` |
| `maxInstrumentalness` | `?float` | Query, Optional | **Constraints**: `>= 0`, `<= 1` |
| `targetInstrumentalness` | `?float` | Query, Optional | **Constraints**: `>= 0`, `<= 1` |
| `minKey` | `?int` | Query, Optional | **Constraints**: `>= 0`, `<= 11` |
| `maxKey` | `?int` | Query, Optional | **Constraints**: `>= 0`, `<= 11` |
| `targetKey` | `?int` | Query, Optional | **Constraints**: `>= 0`, `<= 11` |
| `minLiveness` | `?float` | Query, Optional | **Constraints**: `>= 0`, `<= 1` |
| `maxLiveness` | `?float` | Query, Optional | **Constraints**: `>= 0`, `<= 1` |
| `targetLiveness` | `?float` | Query, Optional | **Constraints**: `>= 0`, `<= 1` |
| `minLoudness` | `?float` | Query, Optional | - |
| `maxLoudness` | `?float` | Query, Optional | - |
| `targetLoudness` | `?float` | Query, Optional | - |
| `minMode` | `?int` | Query, Optional | **Constraints**: `>= 0`, `<= 1` |
| `maxMode` | `?int` | Query, Optional | **Constraints**: `>= 0`, `<= 1` |
| `targetMode` | `?int` | Query, Optional | **Constraints**: `>= 0`, `<= 1` |
| `minPopularity` | `?int` | Query, Optional | **Constraints**: `>= 0`, `<= 100` |
| `maxPopularity` | `?int` | Query, Optional | **Constraints**: `>= 0`, `<= 100` |
| `targetPopularity` | `?int` | Query, Optional | **Constraints**: `>= 0`, `<= 100` |
| `minSpeechiness` | `?float` | Query, Optional | **Constraints**: `>= 0`, `<= 1` |
| `maxSpeechiness` | `?float` | Query, Optional | **Constraints**: `>= 0`, `<= 1` |
| `targetSpeechiness` | `?float` | Query, Optional | **Constraints**: `>= 0`, `<= 1` |
| `minTempo` | `?float` | Query, Optional | - |
| `maxTempo` | `?float` | Query, Optional | - |
| `targetTempo` | `?float` | Query, Optional | - |
| `minTimeSignature` | `?int` | Query, Optional | **Constraints**: `<= 11` |
| `maxTimeSignature` | `?int` | Query, Optional | - |
| `targetTimeSignature` | `?int` | Query, Optional | - |
| `minValence` | `?float` | Query, Optional | **Constraints**: `>= 0`, `<= 1` |
| `maxValence` | `?float` | Query, Optional | **Constraints**: `>= 0`, `<= 1` |
| `targetValence` | `?float` | Query, Optional | **Constraints**: `>= 0`, `<= 1` |

## Response Type

**200**: A set of recommendations

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `getResult()` method on this instance returns the response data which is of type [`RecommendationsObject`](../../doc/models/recommendations-object.md).

## Example Usage

```php
$limit = 10;

$market = 'ES';

$seedArtists = '4NHQUGzhtTLFvgF5SZesLK';

$seedGenres = 'classical,country';

$seedTracks = '0c6xIDDpzE81m2q797ordA';

$tracksApi = $client->getTracksApi();
$apiResponse = $tracksApi->getRecommendations(
    $limit,
    $market,
    $seedArtists,
    $seedGenres,
    $seedTracks
);

// Extracting response status code
var_dump($apiResponse->getStatusCode());
// Extracting response headers
var_dump($apiResponse->getHeaders());

if ($apiResponse->isSuccess()) {
    echo 'RecommendationsObject:';
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

