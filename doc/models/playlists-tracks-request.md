
# Playlists Tracks Request

*This model accepts additional fields of type array.*

## Structure

`PlaylistsTracksRequest`

## Fields

| Name | Type | Tags | Description | Getter | Setter |
|  --- | --- | --- | --- | --- | --- |
| `uris` | `?(string[])` | Optional | A JSON array of the [Spotify URIs](https://developer.spotify.com/documentation/web-api/concepts/spotify-uris-ids) to add. For example: `{"uris": ["spotify:track:4iV5W9uYEdYUVa79Axb7Rh","spotify:track:1301WleyT98MSxVHPZCA6M", "spotify:episode:512ojhOuo1ktJprKbVcKyQ"]}`<br/>A maximum of 100 items can be added in one request. _**Note**: if the `uris` parameter is present in the query string, any URIs listed here in the body will be ignored._ | getUris(): ?array | setUris(?array uris): void |
| `position` | `?int` | Optional | The position to insert the items, a zero-based index. For example, to insert the items in the first position: `position=0` ; to insert the items in the third position: `position=2`. If omitted, the items will be appended to the playlist. Items are added in the order they appear in the uris array. For example: `{"uris": ["spotify:track:4iV5W9uYEdYUVa79Axb7Rh","spotify:track:1301WleyT98MSxVHPZCA6M"], "position": 3}` | getPosition(): ?int | setPosition(?int position): void |
| `additionalProperties` | `array<string, array>` | Optional | - | findAdditionalProperty(string key): array | additionalProperty(string key, array value): void |

## Example

```php
use SpotifyWebApiLib\Models\Builders\PlaylistsTracksRequestBuilder;
use SpotifyWebApiLib\ApiHelper;

$playlistsTracksRequest = PlaylistsTracksRequestBuilder::init()
    ->uris(
        [
            'uris7'
        ]
    )
    ->position(168)
    ->additionalProperty('exampleAdditionalProperty', ApiHelper::deserialize('{"key1":"val1","key2":"val2"}'))
    ->build();
```

