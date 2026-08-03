
# Paging Saved Album Object

*This model accepts additional fields of type array.*

## Structure

`PagingSavedAlbumObject`

## Fields

| Name | Type | Tags | Description | Getter | Setter |
|  --- | --- | --- | --- | --- | --- |
| `href` | `string` | Required | A link to the Web API endpoint returning the full result of the request | getHref(): string | setHref(string href): void |
| `limit` | `int` | Required | The maximum number of items in the response (as set in the query or by default). | getLimit(): int | setLimit(int limit): void |
| `next` | `?string` | Required | URL to the next page of items. ( `null` if none) | getNext(): ?string | setNext(?string next): void |
| `offset` | `int` | Required | The offset of the items returned (as set in the query or by default) | getOffset(): int | setOffset(int offset): void |
| `previous` | `?string` | Required | URL to the previous page of items. ( `null` if none) | getPrevious(): ?string | setPrevious(?string previous): void |
| `total` | `int` | Required | The total number of items available to return. | getTotal(): int | setTotal(int total): void |
| `items` | [`SavedAlbumObject[]`](../../doc/models/saved-album-object.md) | Required | - | getItems(): array | setItems(array items): void |
| `additionalProperties` | `array<string, array>` | Optional | - | findAdditionalProperty(string key): array | additionalProperty(string key, array value): void |

## Example

```php
use SpotifyWebApiLib\Models\Builders\PagingSavedAlbumObjectBuilder;
use SpotifyWebApiLib\Models\Builders\SavedAlbumObjectBuilder;
use SpotifyWebApiLib\Utils\DateTimeHelper;
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

$pagingSavedAlbumObject = PagingSavedAlbumObjectBuilder::init(
    'https://api.spotify.com/v1/me/shows?offset=0&limit=20
',
    20,
    0,
    4,
    [
        SavedAlbumObjectBuilder::init()
            ->addedAt(DateTimeHelper::fromRfc3339DateTime('2016-03-13T12:52:32.123Z'))
            ->album(
                AlbumObjectBuilder::init(
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
                    ],
                    PagingSimplifiedTrackObjectBuilder::init(
                        'href6',
                        142,
                        238,
                        236,
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
                        ->next('next8')
                        ->previous('previous2')
                        ->additionalProperty('exampleAdditionalProperty', ApiHelper::deserialize('{"key1":"val1","key2":"val2"}'))
                        ->build(),
                    [
                        CopyrightObjectBuilder::init()
                            ->text('text2')
                            ->type('type2')
                            ->additionalProperty('exampleAdditionalProperty', ApiHelper::deserialize('{"key1":"val1","key2":"val2"}'))
                            ->build(),
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
                        'genres5',
                        'genres6',
                        'genres7'
                    ],
                    'label8',
                    78
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
            ->additionalProperty('exampleAdditionalProperty', ApiHelper::deserialize('{"key1":"val1","key2":"val2"}'))
            ->build()
    ]
)
    ->next('https://api.spotify.com/v1/me/shows?offset=1&limit=1')
    ->previous('https://api.spotify.com/v1/me/shows?offset=1&limit=1')
    ->additionalProperty('exampleAdditionalProperty', ApiHelper::deserialize('{"key1":"val1","key2":"val2"}'))
    ->build();
```

