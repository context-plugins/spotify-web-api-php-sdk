
# Playlist Snapshot Id

*This model accepts additional fields of type array.*

## Structure

`PlaylistSnapshotId`

## Fields

| Name | Type | Tags | Description | Getter | Setter |
|  --- | --- | --- | --- | --- | --- |
| `snapshotId` | `?string` | Optional | - | getSnapshotId(): ?string | setSnapshotId(?string snapshotId): void |
| `additionalProperties` | `array<string, array>` | Optional | - | findAdditionalProperty(string key): array | additionalProperty(string key, array value): void |

## Example

```php
use SpotifyWebApiLib\Models\Builders\PlaylistSnapshotIdBuilder;
use SpotifyWebApiLib\ApiHelper;

$playlistSnapshotId = PlaylistSnapshotIdBuilder::init()
    ->snapshotId('abc')
    ->additionalProperty('exampleAdditionalProperty', ApiHelper::deserialize('{"key1":"val1","key2":"val2"}'))
    ->build();
```

