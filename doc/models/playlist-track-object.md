
# Playlist Track Object

*This model accepts additional fields of type array.*

## Structure

`PlaylistTrackObject`

## Fields

| Name | Type | Tags | Description | Getter | Setter |
|  --- | --- | --- | --- | --- | --- |
| `addedAt` | `?DateTime` | Optional | The date and time the track or episode was added. _**Note**: some very old playlists may return `null` in this field._ | getAddedAt(): ?\DateTime | setAddedAt(?\DateTime addedAt): void |
| `addedBy` | [`?PlaylistUserObject`](../../doc/models/playlist-user-object.md) | Optional | - | getAddedBy(): ?PlaylistUserObject | setAddedBy(?PlaylistUserObject addedBy): void |
| `isLocal` | `?bool` | Optional | Whether this track or episode is a [local file](https://developer.spotify.com/documentation/web-api/concepts/playlists/#local-files) or not. | getIsLocal(): ?bool | setIsLocal(?bool isLocal): void |
| `track` | [TrackObject](../../doc/models/track-object.md)\|[EpisodeObject](../../doc/models/episode-object.md)\|null | Optional | This is a container for one-of cases. | getTrack(): | setTrack( track): void |
| `additionalProperties` | `array<string, array>` | Optional | - | findAdditionalProperty(string key): array | additionalProperty(string key, array value): void |

## Example

```php
use SpotifyWebApiLib\Models\Builders\PlaylistTrackObjectBuilder;
use SpotifyWebApiLib\Utils\DateTimeHelper;
use SpotifyWebApiLib\Models\Builders\PlaylistUserObjectBuilder;
use SpotifyWebApiLib\Models\Builders\ExternalUrlObjectBuilder;
use SpotifyWebApiLib\ApiHelper;
use SpotifyWebApiLib\Models\Builders\FollowersObjectBuilder;
use SpotifyWebApiLib\Models\Type4;
use SpotifyWebApiLib\Models\Builders\TrackObjectBuilder;
use SpotifyWebApiLib\Models\Builders\SimplifiedAlbumObjectBuilder;
use SpotifyWebApiLib\Models\AlbumType;
use SpotifyWebApiLib\Models\Builders\ImageObjectBuilder;
use SpotifyWebApiLib\Models\ReleaseDatePrecision;
use SpotifyWebApiLib\Models\Type2;
use SpotifyWebApiLib\Models\Builders\SimplifiedArtistObjectBuilder;
use SpotifyWebApiLib\Models\Type;
use SpotifyWebApiLib\Models\Builders\AlbumRestrictionObjectBuilder;
use SpotifyWebApiLib\Models\Reason;
use SpotifyWebApiLib\Models\Builders\ArtistObjectBuilder;

$playlistTrackObject = PlaylistTrackObjectBuilder::init()
    ->addedAt(DateTimeHelper::fromRfc3339DateTime('2016-03-13T12:52:32.123Z'))
    ->addedBy(
        PlaylistUserObjectBuilder::init()
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
            ->href('href6')
            ->id('id4')
            ->type(Type4::USER)
            ->additionalProperty('exampleAdditionalProperty', ApiHelper::deserialize('{"key1":"val1","key2":"val2"}'))
            ->build()
    )
    ->isLocal(false)
    ->track(
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
    ->additionalProperty('exampleAdditionalProperty', ApiHelper::deserialize('{"key1":"val1","key2":"val2"}'))
    ->build();
```

