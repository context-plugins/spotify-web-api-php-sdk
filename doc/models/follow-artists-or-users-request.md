
# Follow Artists or Users Request

*This model accepts additional fields of type array.*

## Structure

`FollowArtistsOrUsersRequest`

## Fields

| Name | Type | Tags | Description | Getter | Setter |
|  --- | --- | --- | --- | --- | --- |
| `ids` | `string[]` | Required | A JSON array of the artist or user [Spotify IDs](https://developer.spotify.com/documentation/web-api/concepts/spotify-uris-ids).<br>For example: `{ids:["74ASZWbe4lXaubB36ztrGX", "08td7MxkoHQkXnWAYD8d6Q"]}`. A maximum of 50 IDs can be sent in one request. _**Note**: if the `ids` parameter is present in the query string, any IDs listed here in the body will be ignored._ | getIds(): array | setIds(array ids): void |
| `additionalProperties` | `array<string, array>` | Optional | - | findAdditionalProperty(string key): array | additionalProperty(string key, array value): void |

## Example

```php
use SpotifyWebApiLib\Models\Builders\FollowArtistsOrUsersRequestBuilder;
use SpotifyWebApiLib\ApiHelper;

$followArtistsOrUsersRequest = FollowArtistsOrUsersRequestBuilder::init(
    [
        'ids1',
        'ids2'
    ]
)
    ->additionalProperty('exampleAdditionalProperty', ApiHelper::deserialize('{"key1":"val1","key2":"val2"}'))
    ->build();
```

