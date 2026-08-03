
# Paging Saved Episode Object

*This model accepts additional fields of type array.*

## Structure

`PagingSavedEpisodeObject`

## Fields

| Name | Type | Tags | Description | Getter | Setter |
|  --- | --- | --- | --- | --- | --- |
| `href` | `string` | Required | A link to the Web API endpoint returning the full result of the request | getHref(): string | setHref(string href): void |
| `limit` | `int` | Required | The maximum number of items in the response (as set in the query or by default). | getLimit(): int | setLimit(int limit): void |
| `next` | `?string` | Required | URL to the next page of items. ( `null` if none) | getNext(): ?string | setNext(?string next): void |
| `offset` | `int` | Required | The offset of the items returned (as set in the query or by default) | getOffset(): int | setOffset(int offset): void |
| `previous` | `?string` | Required | URL to the previous page of items. ( `null` if none) | getPrevious(): ?string | setPrevious(?string previous): void |
| `total` | `int` | Required | The total number of items available to return. | getTotal(): int | setTotal(int total): void |
| `items` | [`SavedEpisodeObject[]`](../../doc/models/saved-episode-object.md) | Required | - | getItems(): array | setItems(array items): void |
| `additionalProperties` | `array<string, array>` | Optional | - | findAdditionalProperty(string key): array | additionalProperty(string key, array value): void |

## Example

```php
use SpotifyWebApiLib\Models\Builders\PagingSavedEpisodeObjectBuilder;
use SpotifyWebApiLib\Models\Builders\SavedEpisodeObjectBuilder;
use SpotifyWebApiLib\Utils\DateTimeHelper;
use SpotifyWebApiLib\Models\Builders\EpisodeObjectBuilder;
use SpotifyWebApiLib\Models\Builders\ExternalUrlObjectBuilder;
use SpotifyWebApiLib\ApiHelper;
use SpotifyWebApiLib\Models\Builders\ImageObjectBuilder;
use SpotifyWebApiLib\Models\ReleaseDatePrecision;
use SpotifyWebApiLib\Models\Type5;
use SpotifyWebApiLib\Models\Builders\ShowBaseBuilder;
use SpotifyWebApiLib\Models\Builders\CopyrightObjectBuilder;
use SpotifyWebApiLib\Models\Type6;
use SpotifyWebApiLib\Models\Builders\ResumePointObjectBuilder;
use SpotifyWebApiLib\Models\Builders\TrackRestrictionObjectBuilder;

$pagingSavedEpisodeObject = PagingSavedEpisodeObjectBuilder::init(
    'https://api.spotify.com/v1/me/shows?offset=0&limit=20
',
    20,
    0,
    4,
    [
        SavedEpisodeObjectBuilder::init()
            ->addedAt(DateTimeHelper::fromRfc3339DateTime('2016-03-13T12:52:32.123Z'))
            ->episode(
                EpisodeObjectBuilder::init(
                    'description2',
                    'html_description8',
                    46,
                    false,
                    ExternalUrlObjectBuilder::init()
                        ->spotify('spotify6')
                        ->additionalProperty('exampleAdditionalProperty', ApiHelper::deserialize('{"key1":"val1","key2":"val2"}'))
                        ->build(),
                    'href4',
                    'id2',
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
                    false,
                    [
                        'languages9',
                        'languages0',
                        'languages1'
                    ],
                    'name2',
                    'release_date0',
                    ReleaseDatePrecision::YEAR,
                    Type5::EPISODE,
                    'uri6',
                    ShowBaseBuilder::init(
                        [
                            'available_markets0',
                            'available_markets1',
                            'available_markets2'
                        ],
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
                                ->build(),
                            CopyrightObjectBuilder::init()
                                ->text('text2')
                                ->type('type2')
                                ->additionalProperty('exampleAdditionalProperty', ApiHelper::deserialize('{"key1":"val1","key2":"val2"}'))
                                ->build()
                        ],
                        'description4',
                        'html_description4',
                        false,
                        ExternalUrlObjectBuilder::init()
                            ->spotify('spotify6')
                            ->additionalProperty('exampleAdditionalProperty', ApiHelper::deserialize('{"key1":"val1","key2":"val2"}'))
                            ->build(),
                        'href8',
                        'id6',
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
                            'languages7',
                            'languages6',
                            'languages5'
                        ],
                        'media_type6',
                        'name6',
                        'publisher6',
                        Type6::SHOW,
                        'uri0',
                        198
                    )
                        ->additionalProperty('exampleAdditionalProperty', ApiHelper::deserialize('{"key1":"val1","key2":"val2"}'))
                        ->build()
                )
                    ->audioPreviewUrl('audio_preview_url8')
                    ->language('language4')
                    ->resumePoint(
                        ResumePointObjectBuilder::init()
                            ->fullyPlayed(false)
                            ->resumePositionMs(254)
                            ->additionalProperty('exampleAdditionalProperty', ApiHelper::deserialize('{"key1":"val1","key2":"val2"}'))
                            ->build()
                    )
                    ->restrictions(
                        TrackRestrictionObjectBuilder::init()
                            ->reason('reason0')
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

