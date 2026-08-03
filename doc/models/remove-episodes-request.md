
# Remove Episodes Request

*This model accepts additional fields of type array.*

## Structure

`RemoveEpisodesRequest`

## Fields

| Name | Type | Tags | Description | Getter | Setter |
|  --- | --- | --- | --- | --- | --- |
| `ids` | `?(string[])` | Optional | A JSON array of the [Spotify IDs](https://developer.spotify.com/documentation/web-api/concepts/spotify-uris-ids). <br/>A maximum of 50 items can be specified in one request. _**Note**: if the `ids` parameter is present in the query string, any IDs listed here in the body will be ignored._ | getIds(): ?array | setIds(?array ids): void |
| `additionalProperties` | `array<string, array>` | Optional | - | findAdditionalProperty(string key): array | additionalProperty(string key, array value): void |

## Example

```php
use SpotifyWebApiLib\Models\Builders\RemoveEpisodesRequestBuilder;
use SpotifyWebApiLib\ApiHelper;

$removeEpisodesRequest = RemoveEpisodesRequestBuilder::init()
    ->ids(
        [
            'ids9'
        ]
    )
    ->additionalProperty('exampleAdditionalProperty', ApiHelper::deserialize('{"key1":"val1","key2":"val2"}'))
    ->build();
```

