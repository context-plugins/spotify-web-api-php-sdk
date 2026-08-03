
# Playlists Tracks Request 2

*This model accepts additional fields of type array.*

## Structure

`PlaylistsTracksRequest2`

## Fields

| Name | Type | Tags | Description | Getter | Setter |
|  --- | --- | --- | --- | --- | --- |
| `tracks` | [`Track1[]`](../../doc/models/track-1.md) | Required | An array of objects containing [Spotify URIs](https://developer.spotify.com/documentation/web-api/concepts/spotify-uris-ids) of the tracks or episodes to remove.<br>For example: `{ "tracks": [{ "uri": "spotify:track:4iV5W9uYEdYUVa79Axb7Rh" },{ "uri": "spotify:track:1301WleyT98MSxVHPZCA6M" }] }`. A maximum of 100 objects can be sent at once. | getTracks(): array | setTracks(array tracks): void |
| `snapshotId` | `?string` | Optional | The playlist's snapshot ID against which you want to make the changes.<br>The API will validate that the specified items exist and in the specified positions and make the changes,<br>even if more recent changes have been made to the playlist. | getSnapshotId(): ?string | setSnapshotId(?string snapshotId): void |
| `additionalProperties` | `array<string, array>` | Optional | - | findAdditionalProperty(string key): array | additionalProperty(string key, array value): void |

## Example

```php
use SpotifyWebApiLib\Models\Builders\PlaylistsTracksRequest2Builder;
use SpotifyWebApiLib\Models\Builders\Track1Builder;
use SpotifyWebApiLib\ApiHelper;

$playlistsTracksRequest2 = PlaylistsTracksRequest2Builder::init(
    [
        Track1Builder::init()
            ->uri('uri8')
            ->additionalProperty('exampleAdditionalProperty', ApiHelper::deserialize('{"key1":"val1","key2":"val2"}'))
            ->build()
    ]
)
    ->snapshotId('snapshot_id8')
    ->additionalProperty('exampleAdditionalProperty', ApiHelper::deserialize('{"key1":"val1","key2":"val2"}'))
    ->build();
```

