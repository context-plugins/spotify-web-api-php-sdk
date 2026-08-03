
# Paging Simplified Audiobook Object

*This model accepts additional fields of type array.*

## Structure

`PagingSimplifiedAudiobookObject`

## Fields

| Name | Type | Tags | Description | Getter | Setter |
|  --- | --- | --- | --- | --- | --- |
| `href` | `string` | Required | A link to the Web API endpoint returning the full result of the request | getHref(): string | setHref(string href): void |
| `limit` | `int` | Required | The maximum number of items in the response (as set in the query or by default). | getLimit(): int | setLimit(int limit): void |
| `next` | `?string` | Required | URL to the next page of items. ( `null` if none) | getNext(): ?string | setNext(?string next): void |
| `offset` | `int` | Required | The offset of the items returned (as set in the query or by default) | getOffset(): int | setOffset(int offset): void |
| `previous` | `?string` | Required | URL to the previous page of items. ( `null` if none) | getPrevious(): ?string | setPrevious(?string previous): void |
| `total` | `int` | Required | The total number of items available to return. | getTotal(): int | setTotal(int total): void |
| `items` | [`AudiobookBase[]`](../../doc/models/audiobook-base.md) | Required | - | getItems(): array | setItems(array items): void |
| `additionalProperties` | `array<string, array>` | Optional | - | findAdditionalProperty(string key): array | additionalProperty(string key, array value): void |

## Example

```php
use SpotifyWebApiLib\Models\Builders\PagingSimplifiedAudiobookObjectBuilder;
use SpotifyWebApiLib\Models\Builders\AudiobookBaseBuilder;
use SpotifyWebApiLib\Models\Builders\AuthorObjectBuilder;
use SpotifyWebApiLib\ApiHelper;
use SpotifyWebApiLib\Models\Builders\CopyrightObjectBuilder;
use SpotifyWebApiLib\Models\Builders\ExternalUrlObjectBuilder;
use SpotifyWebApiLib\Models\Builders\ImageObjectBuilder;
use SpotifyWebApiLib\Models\Builders\NarratorObjectBuilder;
use SpotifyWebApiLib\Models\Type9;

$pagingSimplifiedAudiobookObject = PagingSimplifiedAudiobookObjectBuilder::init(
    'https://api.spotify.com/v1/me/shows?offset=0&limit=20
',
    20,
    0,
    4,
    [
        AudiobookBaseBuilder::init(
            [
                AuthorObjectBuilder::init()
                    ->name('name0')
                    ->additionalProperty('exampleAdditionalProperty', ApiHelper::deserialize('{"key1":"val1","key2":"val2"}'))
                    ->build()
            ],
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
                    'https://i.scdn.co/image/ab67616d00001e02ff9ca10b55ce82ae553c8228
'
                )
                    ->height(300)
                    ->width(300)
                    ->additionalProperty('exampleAdditionalProperty', ApiHelper::deserialize('{"key1":"val1","key2":"val2"}'))
                    ->build()
            ],
            [
                'languages5'
            ],
            'media_type4',
            'name8',
            [
                NarratorObjectBuilder::init()
                    ->name('name0')
                    ->additionalProperty('exampleAdditionalProperty', ApiHelper::deserialize('{"key1":"val1","key2":"val2"}'))
                    ->build()
            ],
            'publisher4',
            Type9::AUDIOBOOK,
            'uri2',
            202
        )
            ->edition('Unabridged')
            ->additionalProperty('exampleAdditionalProperty', ApiHelper::deserialize('{"key1":"val1","key2":"val2"}'))
            ->build()
    ]
)
    ->next('https://api.spotify.com/v1/me/shows?offset=1&limit=1')
    ->previous('https://api.spotify.com/v1/me/shows?offset=1&limit=1')
    ->additionalProperty('exampleAdditionalProperty', ApiHelper::deserialize('{"key1":"val1","key2":"val2"}'))
    ->build();
```

