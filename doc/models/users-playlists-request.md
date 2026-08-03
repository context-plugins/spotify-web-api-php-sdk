
# Users Playlists Request

*This model accepts additional fields of type array.*

## Structure

`UsersPlaylistsRequest`

## Fields

| Name | Type | Tags | Description | Getter | Setter |
|  --- | --- | --- | --- | --- | --- |
| `name` | `string` | Required | The name for the new playlist, for example `"Your Coolest Playlist"`. This name does not need to be unique; a user may have several playlists with the same name. | getName(): string | setName(string name): void |
| `public` | `?bool` | Optional | Defaults to `true`. If `true` the playlist will be public, if `false` it will be private. To be able to create private playlists, the user must have granted the `playlist-modify-private` [scope](https://developer.spotify.com/documentation/web-api/concepts/scopes/#list-of-scopes) | getPublic(): ?bool | setPublic(?bool public): void |
| `collaborative` | `?bool` | Optional | Defaults to `false`. If `true` the playlist will be collaborative. _**Note**: to create a collaborative playlist you must also set `public` to `false`. To create collaborative playlists you must have granted `playlist-modify-private` and `playlist-modify-public` [scopes](https://developer.spotify.com/documentation/web-api/concepts/scopes/#list-of-scopes)._ | getCollaborative(): ?bool | setCollaborative(?bool collaborative): void |
| `description` | `?string` | Optional | value for playlist description as displayed in Spotify Clients and in the Web API. | getDescription(): ?string | setDescription(?string description): void |
| `additionalProperties` | `array<string, array>` | Optional | - | findAdditionalProperty(string key): array | additionalProperty(string key, array value): void |

## Example

```php
use SpotifyWebApiLib\Models\Builders\UsersPlaylistsRequestBuilder;
use SpotifyWebApiLib\ApiHelper;

$usersPlaylistsRequest = UsersPlaylistsRequestBuilder::init(
    'New Playlist'
)
    ->public(false)
    ->collaborative(false)
    ->description('New playlist description')
    ->additionalProperty('exampleAdditionalProperty', ApiHelper::deserialize('{"key1":"val1","key2":"val2"}'))
    ->build();
```

