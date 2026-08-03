
# Paged Albums

*This model accepts additional fields of type array.*

## Structure

`PagedAlbums`

## Fields

| Name | Type | Tags | Description | Getter | Setter |
|  --- | --- | --- | --- | --- | --- |
| `albums` | [`PagingSimplifiedAlbumObject`](../../doc/models/paging-simplified-album-object.md) | Required | - | getAlbums(): PagingSimplifiedAlbumObject | setAlbums(PagingSimplifiedAlbumObject albums): void |
| `additionalProperties` | `array<string, array>` | Optional | - | findAdditionalProperty(string key): array | additionalProperty(string key, array value): void |

## Example

```php
use SpotifyWebApiLib\Models\Builders\PagedAlbumsBuilder;
use SpotifyWebApiLib\Models\Builders\PagingSimplifiedAlbumObjectBuilder;
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

$pagedAlbums = PagedAlbumsBuilder::init(
    PagingSimplifiedAlbumObjectBuilder::init(
        'https://api.spotify.com/v1/me/shows?offset=0&limit=20
',
        20,
        0,
        4,
        [
            SimplifiedAlbumObjectBuilder::init(
                AlbumType::ALBUM,
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
                ReleaseDatePrecision::MONTH,
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
        ->next('https://api.spotify.com/v1/me/shows?offset=1&limit=1')
        ->previous('https://api.spotify.com/v1/me/shows?offset=1&limit=1')
        ->additionalProperty('exampleAdditionalProperty', ApiHelper::deserialize('{"key1":"val1","key2":"val2"}'))
        ->build()
)
    ->additionalProperty('exampleAdditionalProperty', ApiHelper::deserialize('{"key1":"val1","key2":"val2"}'))
    ->build();
```

