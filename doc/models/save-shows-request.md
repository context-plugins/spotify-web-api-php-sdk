
# Save Shows Request

*This model accepts additional fields of type array.*

## Structure

`SaveShowsRequest`

## Fields

| Name | Type | Tags | Description | Getter | Setter |
|  --- | --- | --- | --- | --- | --- |
| `ids` | `?(string[])` | Optional | A JSON array of the [Spotify IDs](https://developer.spotify.comhttps://developer.spotify.com/documentation/web-api/#spotify-uris-and-ids).  <br>A maximum of 50 items can be specified in one request. *Note: if the `ids` parameter is present in the query string, any IDs listed here in the body will be ignored.* | getIds(): ?array | setIds(?array ids): void |
| `additionalProperties` | `array<string, array>` | Optional | - | findAdditionalProperty(string key): array | additionalProperty(string key, array value): void |

## Example

```php
use SpotifyWebApiLib\Models\Builders\SaveShowsRequestBuilder;
use SpotifyWebApiLib\ApiHelper;

$saveShowsRequest = SaveShowsRequestBuilder::init()
    ->ids(
        [
            'ids5',
            'ids6',
            'ids7'
        ]
    )
    ->additionalProperty('exampleAdditionalProperty', ApiHelper::deserialize('{"key1":"val1","key2":"val2"}'))
    ->build();
```

