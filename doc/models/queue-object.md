
# Queue Object

*This model accepts additional fields of type array.*

## Structure

`QueueObject`

## Fields

| Name | Type | Tags | Description | Getter | Setter |
|  --- | --- | --- | --- | --- | --- |
| `currentlyPlaying` | [TrackObject](../../doc/models/track-object.md)\|[EpisodeObject](../../doc/models/episode-object.md)\|null | Optional | This is a container for one-of cases. | getCurrentlyPlaying(): | setCurrentlyPlaying( currentlyPlaying): void |
| `queue` | array<[TrackObject](../../doc/models/track-object.md)\|[EpisodeObject](../../doc/models/episode-object.md)>\|null | Optional | This is Array of a container for one-of cases. | getQueue(): ?array | setQueue(?array queue): void |
| `additionalProperties` | `array<string, array>` | Optional | - | findAdditionalProperty(string key): array | additionalProperty(string key, array value): void |

## Example

```php
use SpotifyWebApiLib\Models\Builders\QueueObjectBuilder;
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

$queueObject = QueueObjectBuilder::init()
    ->currentlyPlaying(
        TrackObjectBuilder::init()
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
                    'available_markets6',
                    'available_markets7'
                ]
            )
            ->discNumber(30)
            ->durationMs(222)
            ->additionalProperty('exampleAdditionalProperty', ApiHelper::deserialize('{"key1":"val1","key2":"val2"}'))
            ->build()
    )
    ->queue(
        [
            TrackObjectBuilder::init()
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
                        'available_markets6',
                        'available_markets7'
                    ]
                )
                ->discNumber(30)
                ->durationMs(222)
                ->additionalProperty('exampleAdditionalProperty', ApiHelper::deserialize('{"key1":"val1","key2":"val2"}'))
                ->build(),
            TrackObjectBuilder::init()
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
                        'available_markets6',
                        'available_markets7'
                    ]
                )
                ->discNumber(30)
                ->durationMs(222)
                ->additionalProperty('exampleAdditionalProperty', ApiHelper::deserialize('{"key1":"val1","key2":"val2"}'))
                ->build(),
            TrackObjectBuilder::init()
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
                        'available_markets6',
                        'available_markets7'
                    ]
                )
                ->discNumber(30)
                ->durationMs(222)
                ->additionalProperty('exampleAdditionalProperty', ApiHelper::deserialize('{"key1":"val1","key2":"val2"}'))
                ->build()
        ]
    )
    ->additionalProperty('exampleAdditionalProperty', ApiHelper::deserialize('{"key1":"val1","key2":"val2"}'))
    ->build();
```

