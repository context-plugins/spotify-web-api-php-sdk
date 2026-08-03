
# Paging Simplified Chapter Object

*This model accepts additional fields of type array.*

## Structure

`PagingSimplifiedChapterObject`

## Fields

| Name | Type | Tags | Description | Getter | Setter |
|  --- | --- | --- | --- | --- | --- |
| `href` | `string` | Required | A link to the Web API endpoint returning the full result of the request | getHref(): string | setHref(string href): void |
| `limit` | `int` | Required | The maximum number of items in the response (as set in the query or by default). | getLimit(): int | setLimit(int limit): void |
| `next` | `?string` | Required | URL to the next page of items. ( `null` if none) | getNext(): ?string | setNext(?string next): void |
| `offset` | `int` | Required | The offset of the items returned (as set in the query or by default) | getOffset(): int | setOffset(int offset): void |
| `previous` | `?string` | Required | URL to the previous page of items. ( `null` if none) | getPrevious(): ?string | setPrevious(?string previous): void |
| `total` | `int` | Required | The total number of items available to return. | getTotal(): int | setTotal(int total): void |
| `items` | [`ChapterBase[]`](../../doc/models/chapter-base.md) | Required | - | getItems(): array | setItems(array items): void |
| `additionalProperties` | `array<string, array>` | Optional | - | findAdditionalProperty(string key): array | additionalProperty(string key, array value): void |

## Example

```php
use SpotifyWebApiLib\Models\Builders\PagingSimplifiedChapterObjectBuilder;
use SpotifyWebApiLib\Models\Builders\ChapterBaseBuilder;
use SpotifyWebApiLib\Models\Builders\ExternalUrlObjectBuilder;
use SpotifyWebApiLib\ApiHelper;
use SpotifyWebApiLib\Models\Builders\ImageObjectBuilder;
use SpotifyWebApiLib\Models\ReleaseDatePrecision;
use SpotifyWebApiLib\Models\Type5;
use SpotifyWebApiLib\Models\Builders\ResumePointObjectBuilder;
use SpotifyWebApiLib\Models\Builders\ChapterRestrictionObjectBuilder;

$pagingSimplifiedChapterObject = PagingSimplifiedChapterObjectBuilder::init(
    'https://api.spotify.com/v1/me/shows?offset=0&limit=20
',
    20,
    0,
    4,
    [
        ChapterBaseBuilder::init(
            1,
            'We kept on ascending, with occasional periods of quick descent, but in the main always ascending. Suddenly, I became conscious of the fact that the driver was in the act of pulling up the horses in the courtyard of a vast ruined castle, from whose tall black windows came no ray of light, and whose broken battlements showed a jagged line against the moonlit sky.
',
            '<p>We kept on ascending, with occasional periods of quick descent, but in the main always ascending. Suddenly, I became conscious of the fact that the driver was in the act of pulling up the horses in the courtyard of a vast ruined castle, from whose tall black windows came no ray of light, and whose broken battlements showed a jagged line against the moonlit sky.</p>
',
            1686230,
            false,
            ExternalUrlObjectBuilder::init()
                ->spotify('spotify6')
                ->additionalProperty('exampleAdditionalProperty', ApiHelper::deserialize('{"key1":"val1","key2":"val2"}'))
                ->build(),
            'https://api.spotify.com/v1/episodes/5Xt5DXGzch68nYYamXrNxZ',
            '5Xt5DXGzch68nYYamXrNxZ',
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
            false,
            [
                'fr',
                'en'
            ],
            'Starting Your Own Podcast: Tips, Tricks, and Advice From Anchor Creators
',
            '1981-12-15',
            ReleaseDatePrecision::MONTH,
            Type5::EPISODE,
            'spotify:episode:0zLhl3WsOCQHbe1BPTiHgr'
        )
            ->audioPreviewUrl('https://p.scdn.co/mp3-preview/2f37da1d4221f40b9d1a98cd191f4d6f1646ad17')
            ->availableMarkets(
                [
                    'available_markets2'
                ]
            )
            ->resumePoint(
                ResumePointObjectBuilder::init()
                    ->fullyPlayed(false)
                    ->resumePositionMs(254)
                    ->additionalProperty('exampleAdditionalProperty', ApiHelper::deserialize('{"key1":"val1","key2":"val2"}'))
                    ->build()
            )
            ->restrictions(
                ChapterRestrictionObjectBuilder::init()
                    ->reason('reason0')
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

