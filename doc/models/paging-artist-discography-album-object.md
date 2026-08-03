
# Paging Artist Discography Album Object

*This model accepts additional fields of type array.*

## Structure

`PagingArtistDiscographyAlbumObject`

## Fields

| Name | Type | Tags | Description | Getter | Setter |
|  --- | --- | --- | --- | --- | --- |
| `href` | `string` | Required | A link to the Web API endpoint returning the full result of the request | getHref(): string | setHref(string href): void |
| `limit` | `int` | Required | The maximum number of items in the response (as set in the query or by default). | getLimit(): int | setLimit(int limit): void |
| `next` | `?string` | Required | URL to the next page of items. ( `null` if none) | getNext(): ?string | setNext(?string next): void |
| `offset` | `int` | Required | The offset of the items returned (as set in the query or by default) | getOffset(): int | setOffset(int offset): void |
| `previous` | `?string` | Required | URL to the previous page of items. ( `null` if none) | getPrevious(): ?string | setPrevious(?string previous): void |
| `total` | `int` | Required | The total number of items available to return. | getTotal(): int | setTotal(int total): void |
| `items` | [`ArtistDiscographyAlbumObject[]`](../../doc/models/artist-discography-album-object.md) | Required | - | getItems(): array | setItems(array items): void |
| `additionalProperties` | `array<string, array>` | Optional | - | findAdditionalProperty(string key): array | additionalProperty(string key, array value): void |

## Example

```php
use SpotifyWebApiLib\Models\Builders\PagingArtistDiscographyAlbumObjectBuilder;
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

$pagingArtistDiscographyAlbumObject = PagingArtistDiscographyAlbumObjectBuilder::init(
    'https://api.spotify.com/v1/me/shows?offset=0&limit=20
',
    20,
    0,
    4,
    [
        ArtistDiscographyAlbumObjectBuilder::init(
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
            ->build()
    ]
)
    ->next('https://api.spotify.com/v1/me/shows?offset=1&limit=1')
    ->previous('https://api.spotify.com/v1/me/shows?offset=1&limit=1')
    ->additionalProperty('exampleAdditionalProperty', ApiHelper::deserialize('{"key1":"val1","key2":"val2"}'))
    ->build();
```

