
# Playlists Request

*This model accepts additional fields of type array.*

## Structure

`PlaylistsRequest`

## Fields

| Name | Type | Tags | Description | Getter | Setter |
|  --- | --- | --- | --- | --- | --- |
| `name` | `?string` | Optional | The new name for the playlist, for example `"My New Playlist Title"` | getName(): ?string | setName(?string name): void |
| `public` | `?bool` | Optional | If `true` the playlist will be public, if `false` it will be private. | getPublic(): ?bool | setPublic(?bool public): void |
| `collaborative` | `?bool` | Optional | If `true`, the playlist will become collaborative and other users will be able to modify the playlist in their Spotify client. <br/><br>_**Note**: You can only set `collaborative` to `true` on non-public playlists._ | getCollaborative(): ?bool | setCollaborative(?bool collaborative): void |
| `description` | `?string` | Optional | Value for playlist description as displayed in Spotify Clients and in the Web API. | getDescription(): ?string | setDescription(?string description): void |
| `additionalProperties` | `array<string, array>` | Optional | - | findAdditionalProperty(string key): array | additionalProperty(string key, array value): void |

## Example

```php
use SpotifyWebApiLib\Models\Builders\PlaylistsRequestBuilder;
use SpotifyWebApiLib\ApiHelper;

$playlistsRequest = PlaylistsRequestBuilder::init()
    ->name('Updated Playlist Name')
    ->public(false)
    ->collaborative(false)
    ->description('Updated playlist description')
    ->additionalProperty('exampleAdditionalProperty', ApiHelper::deserialize('{"key1":"val1","key2":"val2"}'))
    ->build();
```

