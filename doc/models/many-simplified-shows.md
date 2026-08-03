
# Many Simplified Shows

*This model accepts additional fields of type array.*

## Structure

`ManySimplifiedShows`

## Fields

| Name | Type | Tags | Description | Getter | Setter |
|  --- | --- | --- | --- | --- | --- |
| `shows` | [`ShowBase[]`](../../doc/models/show-base.md) | Required | - | getShows(): array | setShows(array shows): void |
| `additionalProperties` | `array<string, array>` | Optional | - | findAdditionalProperty(string key): array | additionalProperty(string key, array value): void |

## Example

```php
use SpotifyWebApiLib\Models\Builders\ManySimplifiedShowsBuilder;
use SpotifyWebApiLib\Models\Builders\ShowBaseBuilder;
use SpotifyWebApiLib\Models\Builders\CopyrightObjectBuilder;
use SpotifyWebApiLib\ApiHelper;
use SpotifyWebApiLib\Models\Builders\ExternalUrlObjectBuilder;
use SpotifyWebApiLib\Models\Builders\ImageObjectBuilder;
use SpotifyWebApiLib\Models\Type6;

$manySimplifiedShows = ManySimplifiedShowsBuilder::init(
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
            'description8',
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
            false,
            [
                'languages5'
            ],
            'media_type4',
            'name8',
            'publisher4',
            Type6::SHOW,
            'uri2',
            196
        )
            ->additionalProperty('exampleAdditionalProperty', ApiHelper::deserialize('{"key1":"val1","key2":"val2"}'))
            ->build()
    ]
)
    ->additionalProperty('exampleAdditionalProperty', ApiHelper::deserialize('{"key1":"val1","key2":"val2"}'))
    ->build();
```

