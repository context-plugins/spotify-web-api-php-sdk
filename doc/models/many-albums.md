
# Many Albums

*This model accepts additional fields of type array.*

## Structure

`ManyAlbums`

## Fields

| Name | Type | Tags | Description | Getter | Setter |
|  --- | --- | --- | --- | --- | --- |
| `albums` | [`AlbumObject[]`](../../doc/models/album-object.md) | Required | - | getAlbums(): array | setAlbums(array albums): void |
| `additionalProperties` | `array<string, array>` | Optional | - | findAdditionalProperty(string key): array | additionalProperty(string key, array value): void |

## Example

```php
use SpotifyWebApiLib\Models\Builders\ManyAlbumsBuilder;
use SpotifyWebApiLib\Models\Builders\AlbumObjectBuilder;
use SpotifyWebApiLib\Models\AlbumType;
use SpotifyWebApiLib\Models\Builders\ExternalUrlObjectBuilder;
use SpotifyWebApiLib\ApiHelper;
use SpotifyWebApiLib\Models\Builders\ImageObjectBuilder;
use SpotifyWebApiLib\Models\ReleaseDatePrecision;
use SpotifyWebApiLib\Models\Type2;
use SpotifyWebApiLib\Models\Builders\SimplifiedArtistObjectBuilder;
use SpotifyWebApiLib\Models\Type;
use SpotifyWebApiLib\Models\Builders\PagingSimplifiedTrackObjectBuilder;
use SpotifyWebApiLib\Models\Builders\SimplifiedTrackObjectBuilder;
use SpotifyWebApiLib\Models\Builders\CopyrightObjectBuilder;
use SpotifyWebApiLib\Models\Builders\ExternalIdObjectBuilder;
use SpotifyWebApiLib\Models\Builders\AlbumRestrictionObjectBuilder;
use SpotifyWebApiLib\Models\Reason;

$manyAlbums = ManyAlbumsBuilder::init(
    [
        AlbumObjectBuilder::init(
            AlbumType::SINGLE,
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
            'href0',
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
            'name8',
            '1981-12',
            ReleaseDatePrecision::DAY,
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
            PagingSimplifiedTrackObjectBuilder::init(
                'https://api.spotify.com/v1/me/shows?offset=0&limit=20
',
                20,
                0,
                4,
                [
                    SimplifiedTrackObjectBuilder::init()
                        ->artists(
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
                        ->availableMarkets(
                            [
                                'available_markets2'
                            ]
                        )
                        ->discNumber(244)
                        ->durationMs(52)
                        ->explicit(false)
                        ->additionalProperty('exampleAdditionalProperty', ApiHelper::deserialize('{"key1":"val1","key2":"val2"}'))
                        ->build()
                ]
            )
                ->next('https://api.spotify.com/v1/me/shows?offset=1&limit=1')
                ->previous('https://api.spotify.com/v1/me/shows?offset=1&limit=1')
                ->additionalProperty('exampleAdditionalProperty', ApiHelper::deserialize('{"key1":"val1","key2":"val2"}'))
                ->build(),
            [
                CopyrightObjectBuilder::init()
                    ->text('text2')
                    ->type('type2')
                    ->additionalProperty('exampleAdditionalProperty', ApiHelper::deserialize('{"key1":"val1","key2":"val2"}'))
                    ->build()
            ],
            ExternalIdObjectBuilder::init()
                ->isrc('isrc8')
                ->ean('ean8')
                ->upc('upc2')
                ->additionalProperty('exampleAdditionalProperty', ApiHelper::deserialize('{"key1":"val1","key2":"val2"}'))
                ->build(),
            [
                'Egg punk',
                'Noise rock'
            ],
            'label8',
            66
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
    ->additionalProperty('exampleAdditionalProperty', ApiHelper::deserialize('{"key1":"val1","key2":"val2"}'))
    ->build();
```

