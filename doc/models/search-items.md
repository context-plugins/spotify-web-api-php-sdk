
# Search Items

*This model accepts additional fields of type array.*

## Structure

`SearchItems`

## Fields

| Name | Type | Tags | Description | Getter | Setter |
|  --- | --- | --- | --- | --- | --- |
| `tracks` | [`?PagingTrackObject`](../../doc/models/paging-track-object.md) | Optional | - | getTracks(): ?PagingTrackObject | setTracks(?PagingTrackObject tracks): void |
| `artists` | [`?PagingArtistObject`](../../doc/models/paging-artist-object.md) | Optional | - | getArtists(): ?PagingArtistObject | setArtists(?PagingArtistObject artists): void |
| `albums` | [`?PagingSimplifiedAlbumObject`](../../doc/models/paging-simplified-album-object.md) | Optional | - | getAlbums(): ?PagingSimplifiedAlbumObject | setAlbums(?PagingSimplifiedAlbumObject albums): void |
| `playlists` | [`?PagingPlaylistObject`](../../doc/models/paging-playlist-object.md) | Optional | - | getPlaylists(): ?PagingPlaylistObject | setPlaylists(?PagingPlaylistObject playlists): void |
| `shows` | [`?PagingSimplifiedShowObject`](../../doc/models/paging-simplified-show-object.md) | Optional | - | getShows(): ?PagingSimplifiedShowObject | setShows(?PagingSimplifiedShowObject shows): void |
| `episodes` | [`?PagingSimplifiedEpisodeObject`](../../doc/models/paging-simplified-episode-object.md) | Optional | - | getEpisodes(): ?PagingSimplifiedEpisodeObject | setEpisodes(?PagingSimplifiedEpisodeObject episodes): void |
| `audiobooks` | [`?PagingSimplifiedAudiobookObject`](../../doc/models/paging-simplified-audiobook-object.md) | Optional | - | getAudiobooks(): ?PagingSimplifiedAudiobookObject | setAudiobooks(?PagingSimplifiedAudiobookObject audiobooks): void |
| `additionalProperties` | `array<string, array>` | Optional | - | findAdditionalProperty(string key): array | additionalProperty(string key, array value): void |

## Example

```php
use SpotifyWebApiLib\Models\Builders\SearchItemsBuilder;
use SpotifyWebApiLib\Models\Builders\PagingTrackObjectBuilder;
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
use SpotifyWebApiLib\Models\Builders\PagingArtistObjectBuilder;
use SpotifyWebApiLib\Models\Builders\PagingSimplifiedAlbumObjectBuilder;
use SpotifyWebApiLib\Models\Builders\PagingPlaylistObjectBuilder;
use SpotifyWebApiLib\Models\Builders\SimplifiedPlaylistObjectBuilder;
use SpotifyWebApiLib\Models\Builders\PagingSimplifiedShowObjectBuilder;
use SpotifyWebApiLib\Models\Builders\ShowBaseBuilder;
use SpotifyWebApiLib\Models\Builders\CopyrightObjectBuilder;
use SpotifyWebApiLib\Models\Type6;

$searchItems = SearchItemsBuilder::init()
    ->tracks(
        PagingTrackObjectBuilder::init(
            'href6',
            142,
            238,
            236,
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
                                ->build()
                        ]
                    )
                    ->availableMarkets(
                        [
                            'available_markets2'
                        ]
                    )
                    ->discNumber(244)
                    ->durationMs(52)
                    ->additionalProperty('exampleAdditionalProperty', ApiHelper::deserialize('{"key1":"val1","key2":"val2"}'))
                    ->build()
            ]
        )
            ->next('next8')
            ->previous('previous2')
            ->additionalProperty('exampleAdditionalProperty', ApiHelper::deserialize('{"key1":"val1","key2":"val2"}'))
            ->build()
    )
    ->artists(
        PagingArtistObjectBuilder::init(
            'href2',
            214,
            54,
            52,
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
                            'genres5',
                            'genres6'
                        ]
                    )
                    ->href('href0')
                    ->id('id8')
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
                            'genres5',
                            'genres6'
                        ]
                    )
                    ->href('href0')
                    ->id('id8')
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
                            'genres5',
                            'genres6'
                        ]
                    )
                    ->href('href0')
                    ->id('id8')
                    ->additionalProperty('exampleAdditionalProperty', ApiHelper::deserialize('{"key1":"val1","key2":"val2"}'))
                    ->build()
            ]
        )
            ->next('next2')
            ->previous('previous8')
            ->additionalProperty('exampleAdditionalProperty', ApiHelper::deserialize('{"key1":"val1","key2":"val2"}'))
            ->build()
    )
    ->albums(
        PagingSimplifiedAlbumObjectBuilder::init(
            'href0',
            0,
            96,
            94,
            [
                SimplifiedAlbumObjectBuilder::init(
                    AlbumType::ALBUM,
                    196,
                    [
                        'available_markets2'
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
                            ->build(),
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
                    ReleaseDatePrecision::MONTH,
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
            ]
        )
            ->next('next4')
            ->previous('previous6')
            ->additionalProperty('exampleAdditionalProperty', ApiHelper::deserialize('{"key1":"val1","key2":"val2"}'))
            ->build()
    )
    ->playlists(
        PagingPlaylistObjectBuilder::init(
            'href2',
            68,
            164,
            162,
            [
                SimplifiedPlaylistObjectBuilder::init()
                    ->collaborative(false)
                    ->description('description2')
                    ->externalUrls(
                        ExternalUrlObjectBuilder::init()
                            ->spotify('spotify6')
                            ->additionalProperty('exampleAdditionalProperty', ApiHelper::deserialize('{"key1":"val1","key2":"val2"}'))
                            ->build()
                    )
                    ->href('href0')
                    ->id('id8')
                    ->additionalProperty('exampleAdditionalProperty', ApiHelper::deserialize('{"key1":"val1","key2":"val2"}'))
                    ->build(),
                SimplifiedPlaylistObjectBuilder::init()
                    ->collaborative(false)
                    ->description('description2')
                    ->externalUrls(
                        ExternalUrlObjectBuilder::init()
                            ->spotify('spotify6')
                            ->additionalProperty('exampleAdditionalProperty', ApiHelper::deserialize('{"key1":"val1","key2":"val2"}'))
                            ->build()
                    )
                    ->href('href0')
                    ->id('id8')
                    ->additionalProperty('exampleAdditionalProperty', ApiHelper::deserialize('{"key1":"val1","key2":"val2"}'))
                    ->build(),
                SimplifiedPlaylistObjectBuilder::init()
                    ->collaborative(false)
                    ->description('description2')
                    ->externalUrls(
                        ExternalUrlObjectBuilder::init()
                            ->spotify('spotify6')
                            ->additionalProperty('exampleAdditionalProperty', ApiHelper::deserialize('{"key1":"val1","key2":"val2"}'))
                            ->build()
                    )
                    ->href('href0')
                    ->id('id8')
                    ->additionalProperty('exampleAdditionalProperty', ApiHelper::deserialize('{"key1":"val1","key2":"val2"}'))
                    ->build()
            ]
        )
            ->next('next2')
            ->previous('previous8')
            ->additionalProperty('exampleAdditionalProperty', ApiHelper::deserialize('{"key1":"val1","key2":"val2"}'))
            ->build()
    )
    ->shows(
        PagingSimplifiedShowObjectBuilder::init(
            'href0',
            248,
            88,
            86,
            [
                ShowBaseBuilder::init(
                    [
                        'available_markets2'
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
                            'url6'
                        )
                            ->height(182)
                            ->width(222)
                            ->additionalProperty('exampleAdditionalProperty', ApiHelper::deserialize('{"key1":"val1","key2":"val2"}'))
                            ->build(),
                        ImageObjectBuilder::init(
                            'url6'
                        )
                            ->height(182)
                            ->width(222)
                            ->additionalProperty('exampleAdditionalProperty', ApiHelper::deserialize('{"key1":"val1","key2":"val2"}'))
                            ->build()
                    ],
                    false,
                    [
                        'languages5'
                    ],
                    'media_type4',
                    'name8',
                    'publisher4',
                    Type6::SHOW,
                    'uri2',
                    166
                )
                    ->additionalProperty('exampleAdditionalProperty', ApiHelper::deserialize('{"key1":"val1","key2":"val2"}'))
                    ->build(),
                ShowBaseBuilder::init(
                    [
                        'available_markets2'
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
                            'url6'
                        )
                            ->height(182)
                            ->width(222)
                            ->additionalProperty('exampleAdditionalProperty', ApiHelper::deserialize('{"key1":"val1","key2":"val2"}'))
                            ->build(),
                        ImageObjectBuilder::init(
                            'url6'
                        )
                            ->height(182)
                            ->width(222)
                            ->additionalProperty('exampleAdditionalProperty', ApiHelper::deserialize('{"key1":"val1","key2":"val2"}'))
                            ->build()
                    ],
                    false,
                    [
                        'languages5'
                    ],
                    'media_type4',
                    'name8',
                    'publisher4',
                    Type6::SHOW,
                    'uri2',
                    166
                )
                    ->additionalProperty('exampleAdditionalProperty', ApiHelper::deserialize('{"key1":"val1","key2":"val2"}'))
                    ->build(),
                ShowBaseBuilder::init(
                    [
                        'available_markets2'
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
                            'url6'
                        )
                            ->height(182)
                            ->width(222)
                            ->additionalProperty('exampleAdditionalProperty', ApiHelper::deserialize('{"key1":"val1","key2":"val2"}'))
                            ->build(),
                        ImageObjectBuilder::init(
                            'url6'
                        )
                            ->height(182)
                            ->width(222)
                            ->additionalProperty('exampleAdditionalProperty', ApiHelper::deserialize('{"key1":"val1","key2":"val2"}'))
                            ->build()
                    ],
                    false,
                    [
                        'languages5'
                    ],
                    'media_type4',
                    'name8',
                    'publisher4',
                    Type6::SHOW,
                    'uri2',
                    166
                )
                    ->additionalProperty('exampleAdditionalProperty', ApiHelper::deserialize('{"key1":"val1","key2":"val2"}'))
                    ->build()
            ]
        )
            ->next('next6')
            ->previous('previous6')
            ->additionalProperty('exampleAdditionalProperty', ApiHelper::deserialize('{"key1":"val1","key2":"val2"}'))
            ->build()
    )
    ->additionalProperty('exampleAdditionalProperty', ApiHelper::deserialize('{"key1":"val1","key2":"val2"}'))
    ->build();
```

