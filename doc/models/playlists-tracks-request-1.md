
# Playlists Tracks Request 1

*This model accepts additional fields of type array.*

## Structure

`PlaylistsTracksRequest1`

## Fields

| Name | Type | Tags | Description | Getter | Setter |
|  --- | --- | --- | --- | --- | --- |
| `uris` | `?(string[])` | Optional | - | getUris(): ?array | setUris(?array uris): void |
| `rangeStart` | `?int` | Optional | The position of the first item to be reordered. | getRangeStart(): ?int | setRangeStart(?int rangeStart): void |
| `insertBefore` | `?int` | Optional | The position where the items should be inserted.<br/>To reorder the items to the end of the playlist, simply set _insert_before_ to the position after the last item.<br/>Examples:<br/>To reorder the first item to the last position in a playlist with 10 items, set _range_start_ to 0, and _insert_before_ to 10.<br/>To reorder the last item in a playlist with 10 items to the start of the playlist, set _range_start_ to 9, and _insert_before_ to 0. | getInsertBefore(): ?int | setInsertBefore(?int insertBefore): void |
| `rangeLength` | `?int` | Optional | The amount of items to be reordered. Defaults to 1 if not set.<br/>The range of items to be reordered begins from the _range_start_ position, and includes the _range_length_ subsequent items.<br/>Example:<br/>To move the items at index 9-10 to the start of the playlist, _range_start_ is set to 9, and _range_length_ is set to 2. | getRangeLength(): ?int | setRangeLength(?int rangeLength): void |
| `snapshotId` | `?string` | Optional | The playlist's snapshot ID against which you want to make the changes. | getSnapshotId(): ?string | setSnapshotId(?string snapshotId): void |
| `additionalProperties` | `array<string, array>` | Optional | - | findAdditionalProperty(string key): array | additionalProperty(string key, array value): void |

## Example

```php
use SpotifyWebApiLib\Models\Builders\PlaylistsTracksRequest1Builder;
use SpotifyWebApiLib\ApiHelper;

$playlistsTracksRequest1 = PlaylistsTracksRequest1Builder::init()
    ->uris(
        [
            'uris9'
        ]
    )
    ->rangeStart(1)
    ->insertBefore(3)
    ->rangeLength(2)
    ->snapshotId('snapshot_id4')
    ->additionalProperty('exampleAdditionalProperty', ApiHelper::deserialize('{"key1":"val1","key2":"val2"}'))
    ->build();
```

