
# Start or Resume Playback Request

*This model accepts additional fields of type array.*

## Structure

`StartOrResumePlaybackRequest`

## Fields

| Name | Type | Tags | Description | Getter | Setter |
|  --- | --- | --- | --- | --- | --- |
| `contextUri` | `?string` | Optional | Optional. Spotify URI of the context to play.<br>Valid contexts are albums, artists & playlists.<br>`{context_uri:"spotify:album:1Je1IMUlBXcx1Fz0WE7oPT"}` | getContextUri(): ?string | setContextUri(?string contextUri): void |
| `uris` | `?(string[])` | Optional | Optional. A JSON array of the Spotify track URIs to play.<br>For example: `{"uris": ["spotify:track:4iV5W9uYEdYUVa79Axb7Rh", "spotify:track:1301WleyT98MSxVHPZCA6M"]}` | getUris(): ?array | setUris(?array uris): void |
| `offset` | `?array` | Optional | Optional. Indicates from where in the context playback should start. Only available when context_uri corresponds to an album or playlist object<br>"position" is zero based and can’t be negative. Example: `"offset": {"position": 5}`<br>"uri" is a string representing the uri of the item to start at. Example: `"offset": {"uri": "spotify:track:1301WleyT98MSxVHPZCA6M"}` | getOffset(): ?array | setOffset(?array offset): void |
| `positionMs` | `?int` | Optional | Indicates from what position to start playback. Must be a positive number. Passing in a position that is greater than the length of the track will cause the player to start playing the next song. | getPositionMs(): ?int | setPositionMs(?int positionMs): void |
| `additionalProperties` | `array<string, array>` | Optional | - | findAdditionalProperty(string key): array | additionalProperty(string key, array value): void |

## Example

```php
use SpotifyWebApiLib\Models\Builders\StartOrResumePlaybackRequestBuilder;
use SpotifyWebApiLib\ApiHelper;

$startOrResumePlaybackRequest = StartOrResumePlaybackRequestBuilder::init()
    ->contextUri('spotify:album:5ht7ItJgpBH7W6vJ5BqpPr')
    ->uris(
        [
            'uris5'
        ]
    )
    ->offset(ApiHelper::deserialize('{"position":5}'))
    ->positionMs(0)
    ->additionalProperty('exampleAdditionalProperty', ApiHelper::deserialize('{"key1":"val1","key2":"val2"}'))
    ->build();
```

