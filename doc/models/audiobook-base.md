
# Audiobook Base

*This model accepts additional fields of type array.*

## Structure

`AudiobookBase`

## Fields

| Name | Type | Tags | Description | Getter | Setter |
|  --- | --- | --- | --- | --- | --- |
| `authors` | [`AuthorObject[]`](../../doc/models/author-object.md) | Required | The author(s) for the audiobook. | getAuthors(): array | setAuthors(array authors): void |
| `availableMarkets` | `string[]` | Required | A list of the countries in which the audiobook can be played, identified by their [ISO 3166-1 alpha-2](http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2) code. | getAvailableMarkets(): array | setAvailableMarkets(array availableMarkets): void |
| `copyrights` | [`CopyrightObject[]`](../../doc/models/copyright-object.md) | Required | The copyright statements of the audiobook. | getCopyrights(): array | setCopyrights(array copyrights): void |
| `description` | `string` | Required | A description of the audiobook. HTML tags are stripped away from this field, use `html_description` field in case HTML tags are needed. | getDescription(): string | setDescription(string description): void |
| `htmlDescription` | `string` | Required | A description of the audiobook. This field may contain HTML tags. | getHtmlDescription(): string | setHtmlDescription(string htmlDescription): void |
| `edition` | `?string` | Optional | The edition of the audiobook. | getEdition(): ?string | setEdition(?string edition): void |
| `explicit` | `bool` | Required | Whether or not the audiobook has explicit content (true = yes it does; false = no it does not OR unknown). | getExplicit(): bool | setExplicit(bool explicit): void |
| `externalUrls` | [`ExternalUrlObject`](../../doc/models/external-url-object.md) | Required | - | getExternalUrls(): ExternalUrlObject | setExternalUrls(ExternalUrlObject externalUrls): void |
| `href` | `string` | Required | A link to the Web API endpoint providing full details of the audiobook. | getHref(): string | setHref(string href): void |
| `id` | `string` | Required | The [Spotify ID](https://developer.spotify.com/documentation/web-api/concepts/spotify-uris-ids) for the audiobook. | getId(): string | setId(string id): void |
| `images` | [`ImageObject[]`](../../doc/models/image-object.md) | Required | The cover art for the audiobook in various sizes, widest first. | getImages(): array | setImages(array images): void |
| `languages` | `string[]` | Required | A list of the languages used in the audiobook, identified by their [ISO 639](https://en.wikipedia.org/wiki/ISO_639) code. | getLanguages(): array | setLanguages(array languages): void |
| `mediaType` | `string` | Required | The media type of the audiobook. | getMediaType(): string | setMediaType(string mediaType): void |
| `name` | `string` | Required | The name of the audiobook. | getName(): string | setName(string name): void |
| `narrators` | [`NarratorObject[]`](../../doc/models/narrator-object.md) | Required | The narrator(s) for the audiobook. | getNarrators(): array | setNarrators(array narrators): void |
| `publisher` | `string` | Required | The publisher of the audiobook. | getPublisher(): string | setPublisher(string publisher): void |
| `type` | [`string(Type9)`](../../doc/models/type-9.md) | Required | - | getType(): string | setType(string type): void |
| `uri` | `string` | Required | The [Spotify URI](https://developer.spotify.com/documentation/web-api/concepts/spotify-uris-ids) for the audiobook. | getUri(): string | setUri(string uri): void |
| `totalChapters` | `int` | Required | The number of chapters in this audiobook. | getTotalChapters(): int | setTotalChapters(int totalChapters): void |
| `additionalProperties` | `array<string, array>` | Optional | - | findAdditionalProperty(string key): array | additionalProperty(string key, array value): void |

## Example

```php
use SpotifyWebApiLib\Models\Builders\AudiobookBaseBuilder;
use SpotifyWebApiLib\Models\Builders\AuthorObjectBuilder;
use SpotifyWebApiLib\ApiHelper;
use SpotifyWebApiLib\Models\Builders\CopyrightObjectBuilder;
use SpotifyWebApiLib\Models\Builders\ExternalUrlObjectBuilder;
use SpotifyWebApiLib\Models\Builders\ImageObjectBuilder;
use SpotifyWebApiLib\Models\Builders\NarratorObjectBuilder;
use SpotifyWebApiLib\Models\Type9;

$audiobookBase = AudiobookBaseBuilder::init(
    [
        AuthorObjectBuilder::init()
            ->name('name0')
            ->additionalProperty('exampleAdditionalProperty', ApiHelper::deserialize('{"key1":"val1","key2":"val2"}'))
            ->build()
    ],
    [
        'available_markets4',
        'available_markets5',
        'available_markets6'
    ],
    [
        CopyrightObjectBuilder::init()
            ->text('text2')
            ->type('type2')
            ->additionalProperty('exampleAdditionalProperty', ApiHelper::deserialize('{"key1":"val1","key2":"val2"}'))
            ->build()
    ],
    'description0',
    'html_description0',
    false,
    ExternalUrlObjectBuilder::init()
        ->spotify('spotify6')
        ->additionalProperty('exampleAdditionalProperty', ApiHelper::deserialize('{"key1":"val1","key2":"val2"}'))
        ->build(),
    'href2',
    'id0',
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
    [
        'languages7',
        'languages8',
        'languages9'
    ],
    'media_type2',
    'name0',
    [
        NarratorObjectBuilder::init()
            ->name('name0')
            ->additionalProperty('exampleAdditionalProperty', ApiHelper::deserialize('{"key1":"val1","key2":"val2"}'))
            ->build()
    ],
    'publisher2',
    Type9::AUDIOBOOK,
    'uri4',
    120
)
    ->edition('Unabridged')
    ->additionalProperty('exampleAdditionalProperty', ApiHelper::deserialize('{"key1":"val1","key2":"val2"}'))
    ->build();
```

