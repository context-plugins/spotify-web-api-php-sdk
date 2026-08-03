
# Paging Simplified Track Object

*This model accepts additional fields of type array.*

## Structure

`PagingSimplifiedTrackObject`

## Fields

| Name | Type | Tags | Description | Getter | Setter |
|  --- | --- | --- | --- | --- | --- |
| `href` | `string` | Required | A link to the Web API endpoint returning the full result of the request | getHref(): string | setHref(string href): void |
| `limit` | `int` | Required | The maximum number of items in the response (as set in the query or by default). | getLimit(): int | setLimit(int limit): void |
| `next` | `?string` | Required | URL to the next page of items. ( `null` if none) | getNext(): ?string | setNext(?string next): void |
| `offset` | `int` | Required | The offset of the items returned (as set in the query or by default) | getOffset(): int | setOffset(int offset): void |
| `previous` | `?string` | Required | URL to the previous page of items. ( `null` if none) | getPrevious(): ?string | setPrevious(?string previous): void |
| `total` | `int` | Required | The total number of items available to return. | getTotal(): int | setTotal(int total): void |
| `items` | [`SimplifiedTrackObject[]`](../../doc/models/simplified-track-object.md) | Required | - | getItems(): array | setItems(array items): void |
| `additionalProperties` | `array<string, array>` | Optional | - | findAdditionalProperty(string key): array | additionalProperty(string key, array value): void |

## Example

```php
use SpotifyWebApiLib\Models\Builders\PagingSimplifiedTrackObjectBuilder;
use SpotifyWebApiLib\Models\Builders\SimplifiedTrackObjectBuilder;
use SpotifyWebApiLib\Models\Builders\SimplifiedArtistObjectBuilder;
use SpotifyWebApiLib\Models\Builders\ExternalUrlObjectBuilder;
use SpotifyWebApiLib\ApiHelper;
use SpotifyWebApiLib\Models\Type;

$pagingSimplifiedTrackObject = PagingSimplifiedTrackObjectBuilder::init(
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
    ->build();
```

