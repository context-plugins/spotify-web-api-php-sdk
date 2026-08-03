
# Category Object

*This model accepts additional fields of type array.*

## Structure

`CategoryObject`

## Fields

| Name | Type | Tags | Description | Getter | Setter |
|  --- | --- | --- | --- | --- | --- |
| `href` | `string` | Required | A link to the Web API endpoint returning full details of the category. | getHref(): string | setHref(string href): void |
| `icons` | [`ImageObject[]`](../../doc/models/image-object.md) | Required | The category icon, in various sizes. | getIcons(): array | setIcons(array icons): void |
| `id` | `string` | Required | The [Spotify category ID](https://developer.spotify.com/documentation/web-api/concepts/spotify-uris-ids) of the category. | getId(): string | setId(string id): void |
| `name` | `string` | Required | The name of the category. | getName(): string | setName(string name): void |
| `additionalProperties` | `array<string, array>` | Optional | - | findAdditionalProperty(string key): array | additionalProperty(string key, array value): void |

## Example

```php
use SpotifyWebApiLib\Models\Builders\CategoryObjectBuilder;
use SpotifyWebApiLib\Models\Builders\ImageObjectBuilder;
use SpotifyWebApiLib\ApiHelper;

$categoryObject = CategoryObjectBuilder::init(
    'href2',
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
    ->build();
```

