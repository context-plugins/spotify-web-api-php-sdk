
# Playlist Tracks Ref Object

*This model accepts additional fields of type array.*

## Structure

`PlaylistTracksRefObject`

## Fields

| Name | Type | Tags | Description | Getter | Setter |
|  --- | --- | --- | --- | --- | --- |
| `href` | `?string` | Optional | A link to the Web API endpoint where full details of the playlist's tracks can be retrieved. | getHref(): ?string | setHref(?string href): void |
| `total` | `?int` | Optional | Number of tracks in the playlist. | getTotal(): ?int | setTotal(?int total): void |
| `additionalProperties` | `array<string, array>` | Optional | - | findAdditionalProperty(string key): array | additionalProperty(string key, array value): void |

## Example

```php
use SpotifyWebApiLib\Models\Builders\PlaylistTracksRefObjectBuilder;
use SpotifyWebApiLib\ApiHelper;

$playlistTracksRefObject = PlaylistTracksRefObjectBuilder::init()
    ->href('href6')
    ->total(80)
    ->additionalProperty('exampleAdditionalProperty', ApiHelper::deserialize('{"key1":"val1","key2":"val2"}'))
    ->build();
```

