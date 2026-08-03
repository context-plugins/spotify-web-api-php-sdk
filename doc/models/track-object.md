
# Track Object

*This model accepts additional fields of type array.*

## Structure

`TrackObject`

## Fields

| Name | Type | Tags | Description | Getter | Setter |
|  --- | --- | --- | --- | --- | --- |
| `album` | [`?SimplifiedAlbumObject`](../../doc/models/simplified-album-object.md) | Optional | - | getAlbum(): ?SimplifiedAlbumObject | setAlbum(?SimplifiedAlbumObject album): void |
| `artists` | [`?(ArtistObject[])`](../../doc/models/artist-object.md) | Optional | The artists who performed the track. Each artist object includes a link in `href` to more detailed information about the artist. | getArtists(): ?array | setArtists(?array artists): void |
| `availableMarkets` | `?(string[])` | Optional | A list of the countries in which the track can be played, identified by their [ISO 3166-1 alpha-2](http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2) code. | getAvailableMarkets(): ?array | setAvailableMarkets(?array availableMarkets): void |
| `discNumber` | `?int` | Optional | The disc number (usually `1` unless the album consists of more than one disc). | getDiscNumber(): ?int | setDiscNumber(?int discNumber): void |
| `durationMs` | `?int` | Optional | The track length in milliseconds. | getDurationMs(): ?int | setDurationMs(?int durationMs): void |
| `explicit` | `?bool` | Optional | Whether or not the track has explicit lyrics ( `true` = yes it does; `false` = no it does not OR unknown). | getExplicit(): ?bool | setExplicit(?bool explicit): void |
| `externalIds` | [`?ExternalIdObject`](../../doc/models/external-id-object.md) | Optional | - | getExternalIds(): ?ExternalIdObject | setExternalIds(?ExternalIdObject externalIds): void |
| `externalUrls` | [`?ExternalUrlObject`](../../doc/models/external-url-object.md) | Optional | - | getExternalUrls(): ?ExternalUrlObject | setExternalUrls(?ExternalUrlObject externalUrls): void |
| `href` | `?string` | Optional | A link to the Web API endpoint providing full details of the track. | getHref(): ?string | setHref(?string href): void |
| `id` | `?string` | Optional | The [Spotify ID](https://developer.spotify.com/documentation/web-api/concepts/spotify-uris-ids) for the track. | getId(): ?string | setId(?string id): void |
| `isPlayable` | `?bool` | Optional | Part of the response when [Track Relinking](https://developer.spotify.com/documentation/web-api/concepts/track-relinking) is applied. If `true`, the track is playable in the given market. Otherwise `false`. | getIsPlayable(): ?bool | setIsPlayable(?bool isPlayable): void |
| `linkedFrom` | [`?LinkedTrackObject`](../../doc/models/linked-track-object.md) | Optional | - | getLinkedFrom(): ?LinkedTrackObject | setLinkedFrom(?LinkedTrackObject linkedFrom): void |
| `restrictions` | [`?TrackRestrictionObject`](../../doc/models/track-restriction-object.md) | Optional | - | getRestrictions(): ?TrackRestrictionObject | setRestrictions(?TrackRestrictionObject restrictions): void |
| `name` | `?string` | Optional | The name of the track. | getName(): ?string | setName(?string name): void |
| `popularity` | `?int` | Optional | The popularity of the track. The value will be between 0 and 100, with 100 being the most popular.<br/>The popularity of a track is a value between 0 and 100, with 100 being the most popular. The popularity is calculated by algorithm and is based, in the most part, on the total number of plays the track has had and how recent those plays are.<br/>Generally speaking, songs that are being played a lot now will have a higher popularity than songs that were played a lot in the past. Duplicate tracks (e.g. the same track from a single and an album) are rated independently. Artist and album popularity is derived mathematically from track popularity. _**Note**: the popularity value may lag actual popularity by a few days: the value is not updated in real time._ | getPopularity(): ?int | setPopularity(?int popularity): void |
| `previewUrl` | `?string` | Optional | A link to a 30 second preview (MP3 format) of the track. Can be `null` | getPreviewUrl(): ?string | setPreviewUrl(?string previewUrl): void |
| `trackNumber` | `?int` | Optional | The number of the track. If an album has several discs, the track number is the number on the specified disc. | getTrackNumber(): ?int | setTrackNumber(?int trackNumber): void |
| `type` | [`?string(Type3)`](../../doc/models/type-3.md) | Optional | - | getType(): ?string | setType(?string type): void |
| `uri` | `?string` | Optional | The [Spotify URI](https://developer.spotify.com/documentation/web-api/concepts/spotify-uris-ids) for the track. | getUri(): ?string | setUri(?string uri): void |
| `isLocal` | `?bool` | Optional | Whether or not the track is from a local file. | getIsLocal(): ?bool | setIsLocal(?bool isLocal): void |
| `additionalProperties` | `array<string, array>` | Optional | - | findAdditionalProperty(string key): array | additionalProperty(string key, array value): void |

## Example

```php
use SpotifyWebApiLib\Models\Builders\TrackObjectBuilder;
use SpotifyWebApiLib\Models\Builders\SimplifiedAlbumObjectBuilder;
use SpotifyWebApiLib\Models\AlbumType;
use SpotifyWebApiLib\Models\Builders\ExternalUrlObjectBuilder;
use SpotifyWebApiLib\ApiHelper;
use SpotifyWebApiLib\Models\Builders\ImageObjectBuilder;
use SpotifyWebApiLib\Models\ReleaseDatePrecision;
use SpotifyWebApiLib\Models\Type2;
use SpotifyWebApiLib\Models\Builders\SimplifiedArtistObjectBuilder;
use SpotifyWebApiLib\Models\Type;
use SpotifyWebApiLib\Models\Builders\AlbumRestrictionObjectBuilder;
use SpotifyWebApiLib\Models\Reason;
use SpotifyWebApiLib\Models\Builders\ArtistObjectBuilder;
use SpotifyWebApiLib\Models\Builders\FollowersObjectBuilder;

$trackObject = TrackObjectBuilder::init()
    ->album(
        SimplifiedAlbumObjectBuilder::init(
            AlbumType::SINGLE,
            170,
            [
                'available_markets2',
                'available_markets3'
            ],
            ExternalUrlObjectBuilder::init()
                ->spotify('spotify6')
                ->additionalProperty('exampleAdditionalProperty', ApiHelper::deserialize('{"key1":"val1","key2":"val2"}'))
                ->build(),
            'href0',
            'id8',
            [
                ImageObjectBuilder::init(
                    'url6'
                )
                    ->height(182)
                    ->width(222)
                    ->additionalProperty('exampleAdditionalProperty', ApiHelper::deserialize('{"key1":"val1","key2":"val2"}'))
                    ->build()
            ],
            'name8',
            'release_date6',
            ReleaseDatePrecision::DAY,
            Type2::ALBUM,
            'uri2',
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
                    ->build(),
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
            ]
        )
            ->restrictions(
                AlbumRestrictionObjectBuilder::init()
                    ->reason(Reason::EXPLICIT)
                    ->additionalProperty('exampleAdditionalProperty', ApiHelper::deserialize('{"key1":"val1","key2":"val2"}'))
                    ->build()
            )
            ->additionalProperty('exampleAdditionalProperty', ApiHelper::deserialize('{"key1":"val1","key2":"val2"}'))
            ->build()
    )
    ->artists(
        [
            ArtistObjectBuilder::init()
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
                        'genres7',
                        'genres8'
                    ]
                )
                ->href('href2')
                ->id('id0')
                ->additionalProperty('exampleAdditionalProperty', ApiHelper::deserialize('{"key1":"val1","key2":"val2"}'))
                ->build(),
            ArtistObjectBuilder::init()
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
                        'genres7',
                        'genres8'
                    ]
                )
                ->href('href2')
                ->id('id0')
                ->additionalProperty('exampleAdditionalProperty', ApiHelper::deserialize('{"key1":"val1","key2":"val2"}'))
                ->build()
        ]
    )
    ->availableMarkets(
        [
            'available_markets2',
            'available_markets3',
            'available_markets4'
        ]
    )
    ->discNumber(182)
    ->durationMs(246)
    ->additionalProperty('exampleAdditionalProperty', ApiHelper::deserialize('{"key1":"val1","key2":"val2"}'))
    ->build();
```

