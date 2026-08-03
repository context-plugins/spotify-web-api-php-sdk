
# Linked Track Object

*This model accepts additional fields of type array.*

## Structure

`LinkedTrackObject`

## Fields

| Name | Type | Tags | Description | Getter | Setter |
|  --- | --- | --- | --- | --- | --- |
| `externalUrls` | [`?ExternalUrlObject`](../../doc/models/external-url-object.md) | Optional | - | getExternalUrls(): ?ExternalUrlObject | setExternalUrls(?ExternalUrlObject externalUrls): void |
| `href` | `?string` | Optional | A link to the Web API endpoint providing full details of the track. | getHref(): ?string | setHref(?string href): void |
| `id` | `?string` | Optional | The [Spotify ID](https://developer.spotify.com/documentation/web-api/concepts/spotify-uris-ids) for the track. | getId(): ?string | setId(?string id): void |
| `type` | `?string` | Optional | The object type: "track". | getType(): ?string | setType(?string type): void |
| `uri` | `?string` | Optional | The [Spotify URI](https://developer.spotify.com/documentation/web-api/concepts/spotify-uris-ids) for the track. | getUri(): ?string | setUri(?string uri): void |
| `additionalProperties` | `array<string, array>` | Optional | - | findAdditionalProperty(string key): array | additionalProperty(string key, array value): void |

## Example

```php
use SpotifyWebApiLib\Models\Builders\LinkedTrackObjectBuilder;
use SpotifyWebApiLib\Models\Builders\ExternalUrlObjectBuilder;
use SpotifyWebApiLib\ApiHelper;

$linkedTrackObject = LinkedTrackObjectBuilder::init()
    ->externalUrls(
        ExternalUrlObjectBuilder::init()
            ->spotify('spotify6')
            ->additionalProperty('exampleAdditionalProperty', ApiHelper::deserialize('{"key1":"val1","key2":"val2"}'))
            ->build()
    )
    ->href('href0')
    ->id('id8')
    ->type('type2')
    ->uri('uri2')
    ->additionalProperty('exampleAdditionalProperty', ApiHelper::deserialize('{"key1":"val1","key2":"val2"}'))
    ->build();
```

