
# Artist Discography Album Object

*This model accepts additional fields of type array.*

## Structure

`ArtistDiscographyAlbumObject`

## Fields

| Name | Type | Tags | Description | Getter | Setter |
|  --- | --- | --- | --- | --- | --- |
| `albumType` | [`string(AlbumType)`](../../doc/models/album-type.md) | Required | - | getAlbumType(): string | setAlbumType(string albumType): void |
| `totalTracks` | `int` | Required | The number of tracks in the album. | getTotalTracks(): int | setTotalTracks(int totalTracks): void |
| `availableMarkets` | `string[]` | Required | The markets in which the album is available: [ISO 3166-1 alpha-2 country codes](http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2). _**NOTE**: an album is considered available in a market when at least 1 of its tracks is available in that market._ | getAvailableMarkets(): array | setAvailableMarkets(array availableMarkets): void |
| `externalUrls` | [`ExternalUrlObject`](../../doc/models/external-url-object.md) | Required | - | getExternalUrls(): ExternalUrlObject | setExternalUrls(ExternalUrlObject externalUrls): void |
| `href` | `string` | Required | A link to the Web API endpoint providing full details of the album. | getHref(): string | setHref(string href): void |
| `id` | `string` | Required | The [Spotify ID](https://developer.spotify.com/documentation/web-api/concepts/spotify-uris-ids) for the album. | getId(): string | setId(string id): void |
| `images` | [`ImageObject[]`](../../doc/models/image-object.md) | Required | The cover art for the album in various sizes, widest first. | getImages(): array | setImages(array images): void |
| `name` | `string` | Required | The name of the album. In case of an album takedown, the value may be an empty string. | getName(): string | setName(string name): void |
| `releaseDate` | `string` | Required | The date the album was first released. | getReleaseDate(): string | setReleaseDate(string releaseDate): void |
| `releaseDatePrecision` | [`string(ReleaseDatePrecision)`](../../doc/models/release-date-precision.md) | Required | - | getReleaseDatePrecision(): string | setReleaseDatePrecision(string releaseDatePrecision): void |
| `restrictions` | [`?AlbumRestrictionObject`](../../doc/models/album-restriction-object.md) | Optional | - | getRestrictions(): ?AlbumRestrictionObject | setRestrictions(?AlbumRestrictionObject restrictions): void |
| `type` | [`string(Type2)`](../../doc/models/type-2.md) | Required | - | getType(): string | setType(string type): void |
| `uri` | `string` | Required | The [Spotify URI](https://developer.spotify.com/documentation/web-api/concepts/spotify-uris-ids) for the album. | getUri(): string | setUri(string uri): void |
| `artists` | [`SimplifiedArtistObject[]`](../../doc/models/simplified-artist-object.md) | Required | The artists of the album. Each artist object includes a link in `href` to more detailed information about the artist. | getArtists(): array | setArtists(array artists): void |
| `albumGroup` | [`string(AlbumGroup)`](../../doc/models/album-group.md) | Required | - | getAlbumGroup(): string | setAlbumGroup(string albumGroup): void |
| `additionalProperties` | `array<string, array>` | Optional | - | findAdditionalProperty(string key): array | additionalProperty(string key, array value): void |

## Example

```php
use SpotifyWebApiLib\Models\Builders\ArtistDiscographyAlbumObjectBuilder;
use SpotifyWebApiLib\Models\AlbumType;
use SpotifyWebApiLib\Models\Builders\ExternalUrlObjectBuilder;
use SpotifyWebApiLib\ApiHelper;
use SpotifyWebApiLib\Models\Builders\ImageObjectBuilder;
use SpotifyWebApiLib\Models\ReleaseDatePrecision;
use SpotifyWebApiLib\Models\Type2;
use SpotifyWebApiLib\Models\Builders\SimplifiedArtistObjectBuilder;
use SpotifyWebApiLib\Models\Type;
use SpotifyWebApiLib\Models\AlbumGroup;
use SpotifyWebApiLib\Models\Builders\AlbumRestrictionObjectBuilder;
use SpotifyWebApiLib\Models\Reason;

$artistDiscographyAlbumObject = ArtistDiscographyAlbumObjectBuilder::init(
    AlbumType::COMPILATION,
    9,
    [
        'CA',
        'BR',
        'IT'
    ],
    ExternalUrlObjectBuilder::init()
        ->spotify('spotify6')
        ->additionalProperty('exampleAdditionalProperty', ApiHelper::deserialize('{"key1":"val1","key2":"val2"}'))
        ->build(),
    'href6',
    '2up3OPMp9Tb4dAKM2erWXQ',
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
    'name4',
    '1981-12',
    ReleaseDatePrecision::YEAR,
    Type2::ALBUM,
    'spotify:album:2up3OPMp9Tb4dAKM2erWXQ',
    [
        SimplifiedArtistObjectBuilder::init()
            ->externalUrls(
                ExternalUrlObjectBuilder::init()
                    ->spotify('spotify6')
                    ->additionalProperty('exampleAdditionalProperty', ApiHelper::deserialize('{"key1":"val1","key2":"val2"}'))
                    ->build()
            )
            ->href('href2')
            ->id('id0')
            ->name('name0')
            ->type(Type::ARTIST)
            ->additionalProperty('exampleAdditionalProperty', ApiHelper::deserialize('{"key1":"val1","key2":"val2"}'))
            ->build()
    ],
    AlbumGroup::COMPILATION
)
    ->restrictions(
        AlbumRestrictionObjectBuilder::init()
            ->reason(Reason::EXPLICIT)
            ->additionalProperty('exampleAdditionalProperty', ApiHelper::deserialize('{"key1":"val1","key2":"val2"}'))
            ->build()
    )
    ->additionalProperty('exampleAdditionalProperty', ApiHelper::deserialize('{"key1":"val1","key2":"val2"}'))
    ->build();
```

