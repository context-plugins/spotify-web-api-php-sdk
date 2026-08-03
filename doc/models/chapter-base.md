
# Chapter Base

*This model accepts additional fields of type array.*

## Structure

`ChapterBase`

## Fields

| Name | Type | Tags | Description | Getter | Setter |
|  --- | --- | --- | --- | --- | --- |
| `audioPreviewUrl` | `?string` | Required | A URL to a 30 second preview (MP3 format) of the chapter. `null` if not available. | getAudioPreviewUrl(): ?string | setAudioPreviewUrl(?string audioPreviewUrl): void |
| `availableMarkets` | `?(string[])` | Optional | A list of the countries in which the chapter can be played, identified by their [ISO 3166-1 alpha-2](http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2) code. | getAvailableMarkets(): ?array | setAvailableMarkets(?array availableMarkets): void |
| `chapterNumber` | `int` | Required | The number of the chapter | getChapterNumber(): int | setChapterNumber(int chapterNumber): void |
| `description` | `string` | Required | A description of the chapter. HTML tags are stripped away from this field, use `html_description` field in case HTML tags are needed. | getDescription(): string | setDescription(string description): void |
| `htmlDescription` | `string` | Required | A description of the chapter. This field may contain HTML tags. | getHtmlDescription(): string | setHtmlDescription(string htmlDescription): void |
| `durationMs` | `int` | Required | The chapter length in milliseconds. | getDurationMs(): int | setDurationMs(int durationMs): void |
| `explicit` | `bool` | Required | Whether or not the chapter has explicit content (true = yes it does; false = no it does not OR unknown). | getExplicit(): bool | setExplicit(bool explicit): void |
| `externalUrls` | [`ExternalUrlObject`](../../doc/models/external-url-object.md) | Required | - | getExternalUrls(): ExternalUrlObject | setExternalUrls(ExternalUrlObject externalUrls): void |
| `href` | `string` | Required | A link to the Web API endpoint providing full details of the chapter. | getHref(): string | setHref(string href): void |
| `id` | `string` | Required | The [Spotify ID](https://developer.spotify.com/documentation/web-api/concepts/spotify-uris-ids) for the chapter. | getId(): string | setId(string id): void |
| `images` | [`ImageObject[]`](../../doc/models/image-object.md) | Required | The cover art for the chapter in various sizes, widest first. | getImages(): array | setImages(array images): void |
| `isPlayable` | `bool` | Required | True if the chapter is playable in the given market. Otherwise false. | getIsPlayable(): bool | setIsPlayable(bool isPlayable): void |
| `languages` | `string[]` | Required | A list of the languages used in the chapter, identified by their [ISO 639-1](https://en.wikipedia.org/wiki/ISO_639) code. | getLanguages(): array | setLanguages(array languages): void |
| `name` | `string` | Required | The name of the chapter. | getName(): string | setName(string name): void |
| `releaseDate` | `string` | Required | The date the chapter was first released, for example `"1981-12-15"`. Depending on the precision, it might be shown as `"1981"` or `"1981-12"`. | getReleaseDate(): string | setReleaseDate(string releaseDate): void |
| `releaseDatePrecision` | [`string(ReleaseDatePrecision)`](../../doc/models/release-date-precision.md) | Required | - | getReleaseDatePrecision(): string | setReleaseDatePrecision(string releaseDatePrecision): void |
| `resumePoint` | [`?ResumePointObject`](../../doc/models/resume-point-object.md) | Optional | - | getResumePoint(): ?ResumePointObject | setResumePoint(?ResumePointObject resumePoint): void |
| `type` | [`string(Type5)`](../../doc/models/type-5.md) | Required | - | getType(): string | setType(string type): void |
| `uri` | `string` | Required | The [Spotify URI](https://developer.spotify.com/documentation/web-api/concepts/spotify-uris-ids) for the chapter. | getUri(): string | setUri(string uri): void |
| `restrictions` | [`?ChapterRestrictionObject`](../../doc/models/chapter-restriction-object.md) | Optional | - | getRestrictions(): ?ChapterRestrictionObject | setRestrictions(?ChapterRestrictionObject restrictions): void |
| `additionalProperties` | `array<string, array>` | Optional | - | findAdditionalProperty(string key): array | additionalProperty(string key, array value): void |

## Example

```php
use SpotifyWebApiLib\Models\Builders\ChapterBaseBuilder;
use SpotifyWebApiLib\Models\Builders\ExternalUrlObjectBuilder;
use SpotifyWebApiLib\ApiHelper;
use SpotifyWebApiLib\Models\Builders\ImageObjectBuilder;
use SpotifyWebApiLib\Models\ReleaseDatePrecision;
use SpotifyWebApiLib\Models\Type5;
use SpotifyWebApiLib\Models\Builders\ResumePointObjectBuilder;
use SpotifyWebApiLib\Models\Builders\ChapterRestrictionObjectBuilder;

$chapterBase = ChapterBaseBuilder::init(
    1,
    'We kept on ascending, with occasional periods of quick descent, but in the main always ascending. Suddenly, I became conscious of the fact that the driver was in the act of pulling up the horses in the courtyard of a vast ruined castle, from whose tall black windows came no ray of light, and whose broken battlements showed a jagged line against the moonlit sky.
',
    '<p>We kept on ascending, with occasional periods of quick descent, but in the main always ascending. Suddenly, I became conscious of the fact that the driver was in the act of pulling up the horses in the courtyard of a vast ruined castle, from whose tall black windows came no ray of light, and whose broken battlements showed a jagged line against the moonlit sky.</p>
',
    1686230,
    false,
    ExternalUrlObjectBuilder::init()
        ->spotify('spotify6')
        ->additionalProperty('exampleAdditionalProperty', ApiHelper::deserialize('{"key1":"val1","key2":"val2"}'))
        ->build(),
    'https://api.spotify.com/v1/episodes/5Xt5DXGzch68nYYamXrNxZ',
    '5Xt5DXGzch68nYYamXrNxZ',
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
        'fr',
        'en'
    ],
    'Starting Your Own Podcast: Tips, Tricks, and Advice From Anchor Creators
',
    '1981-12-15',
    ReleaseDatePrecision::YEAR,
    Type5::EPISODE,
    'spotify:episode:0zLhl3WsOCQHbe1BPTiHgr'
)
    ->audioPreviewUrl('https://p.scdn.co/mp3-preview/2f37da1d4221f40b9d1a98cd191f4d6f1646ad17')
    ->availableMarkets(
        [
            'available_markets0',
            'available_markets1',
            'available_markets2'
        ]
    )
    ->resumePoint(
        ResumePointObjectBuilder::init()
            ->fullyPlayed(false)
            ->resumePositionMs(254)
            ->additionalProperty('exampleAdditionalProperty', ApiHelper::deserialize('{"key1":"val1","key2":"val2"}'))
            ->build()
    )
    ->restrictions(
        ChapterRestrictionObjectBuilder::init()
            ->reason('reason0')
            ->additionalProperty('exampleAdditionalProperty', ApiHelper::deserialize('{"key1":"val1","key2":"val2"}'))
            ->build()
    )
    ->additionalProperty('exampleAdditionalProperty', ApiHelper::deserialize('{"key1":"val1","key2":"val2"}'))
    ->build();
```

