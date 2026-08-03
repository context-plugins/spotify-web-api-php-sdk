
# Show Base

*This model accepts additional fields of type array.*

## Structure

`ShowBase`

## Fields

| Name | Type | Tags | Description | Getter | Setter |
|  --- | --- | --- | --- | --- | --- |
| `availableMarkets` | `string[]` | Required | A list of the countries in which the show can be played, identified by their [ISO 3166-1 alpha-2](http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2) code. | getAvailableMarkets(): array | setAvailableMarkets(array availableMarkets): void |
| `copyrights` | [`CopyrightObject[]`](../../doc/models/copyright-object.md) | Required | The copyright statements of the show. | getCopyrights(): array | setCopyrights(array copyrights): void |
| `description` | `string` | Required | A description of the show. HTML tags are stripped away from this field, use `html_description` field in case HTML tags are needed. | getDescription(): string | setDescription(string description): void |
| `htmlDescription` | `string` | Required | A description of the show. This field may contain HTML tags. | getHtmlDescription(): string | setHtmlDescription(string htmlDescription): void |
| `explicit` | `bool` | Required | Whether or not the show has explicit content (true = yes it does; false = no it does not OR unknown). | getExplicit(): bool | setExplicit(bool explicit): void |
| `externalUrls` | [`ExternalUrlObject`](../../doc/models/external-url-object.md) | Required | - | getExternalUrls(): ExternalUrlObject | setExternalUrls(ExternalUrlObject externalUrls): void |
| `href` | `string` | Required | A link to the Web API endpoint providing full details of the show. | getHref(): string | setHref(string href): void |
| `id` | `string` | Required | The [Spotify ID](https://developer.spotify.com/documentation/web-api/concepts/spotify-uris-ids) for the show. | getId(): string | setId(string id): void |
| `images` | [`ImageObject[]`](../../doc/models/image-object.md) | Required | The cover art for the show in various sizes, widest first. | getImages(): array | setImages(array images): void |
| `isExternallyHosted` | `bool` | Required | True if all of the shows episodes are hosted outside of Spotify's CDN. This field might be `null` in some cases. | getIsExternallyHosted(): bool | setIsExternallyHosted(bool isExternallyHosted): void |
| `languages` | `string[]` | Required | A list of the languages used in the show, identified by their [ISO 639](https://en.wikipedia.org/wiki/ISO_639) code. | getLanguages(): array | setLanguages(array languages): void |
| `mediaType` | `string` | Required | The media type of the show. | getMediaType(): string | setMediaType(string mediaType): void |
| `name` | `string` | Required | The name of the episode. | getName(): string | setName(string name): void |
| `publisher` | `string` | Required | The publisher of the show. | getPublisher(): string | setPublisher(string publisher): void |
| `type` | [`string(Type6)`](../../doc/models/type-6.md) | Required | - | getType(): string | setType(string type): void |
| `uri` | `string` | Required | The [Spotify URI](https://developer.spotify.com/documentation/web-api/concepts/spotify-uris-ids) for the show. | getUri(): string | setUri(string uri): void |
| `totalEpisodes` | `int` | Required | The total number of episodes in the show. | getTotalEpisodes(): int | setTotalEpisodes(int totalEpisodes): void |
| `additionalProperties` | `array<string, array>` | Optional | - | findAdditionalProperty(string key): array | additionalProperty(string key, array value): void |

## Example

```php
use SpotifyWebApiLib\Models\Builders\ShowBaseBuilder;
use SpotifyWebApiLib\Models\Builders\CopyrightObjectBuilder;
use SpotifyWebApiLib\ApiHelper;
use SpotifyWebApiLib\Models\Builders\ExternalUrlObjectBuilder;
use SpotifyWebApiLib\Models\Builders\ImageObjectBuilder;
use SpotifyWebApiLib\Models\Type6;

$showBase = ShowBaseBuilder::init(
    [
        'available_markets2',
        'available_markets3'
    ],
    [
        CopyrightObjectBuilder::init()
            ->text('text2')
            ->type('type2')
            ->additionalProperty('exampleAdditionalProperty', ApiHelper::deserialize('{"key1":"val1","key2":"val2"}'))
            ->build()
    ],
    'description2',
    'html_description2',
    false,
    ExternalUrlObjectBuilder::init()
        ->spotify('spotify6')
        ->additionalProperty('exampleAdditionalProperty', ApiHelper::deserialize('{"key1":"val1","key2":"val2"}'))
        ->build(),
    'href0',
    'id8',
    [
        ImageObjectBuilder::init(
            'https://i.scdn.co/image/ab67616d00001e02ff9ca10b55ce82ae553c8228
'
        )
            ->height(300)
            ->width(300)
            ->additionalProperty('exampleAdditionalProperty', ApiHelper::deserialize('{"key1":"val1","key2":"val2"}'))
            ->build()
    ],
    false,
    [
        'languages3',
        'languages4',
        'languages5'
    ],
    'media_type4',
    'name8',
    'publisher4',
    Type6::SHOW,
    'uri2',
    144
)
    ->additionalProperty('exampleAdditionalProperty', ApiHelper::deserialize('{"key1":"val1","key2":"val2"}'))
    ->build();
```

