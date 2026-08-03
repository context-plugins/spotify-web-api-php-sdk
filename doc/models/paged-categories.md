
# Paged Categories

*This model accepts additional fields of type array.*

## Structure

`PagedCategories`

## Fields

| Name | Type | Tags | Description | Getter | Setter |
|  --- | --- | --- | --- | --- | --- |
| `categories` | [`Categories`](../../doc/models/categories.md) | Required | - | getCategories(): Categories | setCategories(Categories categories): void |
| `additionalProperties` | `array<string, array>` | Optional | - | findAdditionalProperty(string key): array | additionalProperty(string key, array value): void |

## Example

```php
use SpotifyWebApiLib\Models\Builders\PagedCategoriesBuilder;
use SpotifyWebApiLib\Models\Builders\CategoriesBuilder;
use SpotifyWebApiLib\Models\Builders\CategoryObjectBuilder;
use SpotifyWebApiLib\Models\Builders\ImageObjectBuilder;
use SpotifyWebApiLib\ApiHelper;

$pagedCategories = PagedCategoriesBuilder::init(
    CategoriesBuilder::init(
        'https://api.spotify.com/v1/me/shows?offset=0&limit=20
',
        20,
        0,
        4,
        [
            CategoryObjectBuilder::init(
                'href0',
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
                'equal',
                'EQUAL'
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

