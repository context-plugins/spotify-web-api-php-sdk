
# Artist Object

*This model accepts additional fields of type array.*

## Structure

`ArtistObject`

## Fields

| Name | Type | Tags | Description | Getter | Setter |
|  --- | --- | --- | --- | --- | --- |
| `externalUrls` | [`?ExternalUrlObject`](../../doc/models/external-url-object.md) | Optional | - | getExternalUrls(): ?ExternalUrlObject | setExternalUrls(?ExternalUrlObject externalUrls): void |
| `followers` | [`?FollowersObject`](../../doc/models/followers-object.md) | Optional | - | getFollowers(): ?FollowersObject | setFollowers(?FollowersObject followers): void |
| `genres` | `?(string[])` | Optional | A list of the genres the artist is associated with. If not yet classified, the array is empty. | getGenres(): ?array | setGenres(?array genres): void |
| `href` | `?string` | Optional | A link to the Web API endpoint providing full details of the artist. | getHref(): ?string | setHref(?string href): void |
| `id` | `?string` | Optional | The [Spotify ID](https://developer.spotify.com/documentation/web-api/concepts/spotify-uris-ids) for the artist. | getId(): ?string | setId(?string id): void |
| `images` | [`?(ImageObject[])`](../../doc/models/image-object.md) | Optional | Images of the artist in various sizes, widest first. | getImages(): ?array | setImages(?array images): void |
| `name` | `?string` | Optional | The name of the artist. | getName(): ?string | setName(?string name): void |
| `popularity` | `?int` | Optional | The popularity of the artist. The value will be between 0 and 100, with 100 being the most popular. The artist's popularity is calculated from the popularity of all the artist's tracks. | getPopularity(): ?int | setPopularity(?int popularity): void |
| `type` | [`?string(Type)`](../../doc/models/type.md) | Optional | - | getType(): ?string | setType(?string type): void |
| `uri` | `?string` | Optional | The [Spotify URI](https://developer.spotify.com/documentation/web-api/concepts/spotify-uris-ids) for the artist. | getUri(): ?string | setUri(?string uri): void |
| `additionalProperties` | `array<string, array>` | Optional | - | findAdditionalProperty(string key): array | additionalProperty(string key, array value): void |

## Example

```php
use SpotifyWebApiLib\Models\Builders\ArtistObjectBuilder;
use SpotifyWebApiLib\Models\Builders\ExternalUrlObjectBuilder;
use SpotifyWebApiLib\ApiHelper;
use SpotifyWebApiLib\Models\Builders\FollowersObjectBuilder;

$artistObject = ArtistObjectBuilder::init()
    ->externalUrls(
        ExternalUrlObjectBuilder::init()
            ->spotify('spotify6')
            ->additionalProperty('exampleAdditionalProperty', ApiHelper::deserialize('{"key1":"val1","key2":"val2"}'))
            ->build()
    )
    ->followers(
        FollowersObjectBuilder::init()
            ->href('href0')
            ->total(82)
            ->additionalProperty('exampleAdditionalProperty', ApiHelper::deserialize('{"key1":"val1","key2":"val2"}'))
            ->build()
    )
    ->genres(
        [
            'Prog rock',
            'Grunge'
        ]
    )
    ->href('href8')
    ->id('id6')
    ->additionalProperty('exampleAdditionalProperty', ApiHelper::deserialize('{"key1":"val1","key2":"val2"}'))
    ->build();
```

