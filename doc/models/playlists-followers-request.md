
# Playlists Followers Request

*This model accepts additional fields of type array.*

## Structure

`PlaylistsFollowersRequest`

## Fields

| Name | Type | Tags | Description | Getter | Setter |
|  --- | --- | --- | --- | --- | --- |
| `public` | `?bool` | Optional | Defaults to `true`. If `true` the playlist will be included in user's public playlists, if `false` it will remain private. | getPublic(): ?bool | setPublic(?bool public): void |
| `additionalProperties` | `array<string, array>` | Optional | - | findAdditionalProperty(string key): array | additionalProperty(string key, array value): void |

## Example

```php
use SpotifyWebApiLib\Models\Builders\PlaylistsFollowersRequestBuilder;
use SpotifyWebApiLib\ApiHelper;

$playlistsFollowersRequest = PlaylistsFollowersRequestBuilder::init()
    ->public(false)
    ->additionalProperty('exampleAdditionalProperty', ApiHelper::deserialize('{"key1":"val1","key2":"val2"}'))
    ->build();
```

