
# Image Object

*This model accepts additional fields of type array.*

## Structure

`ImageObject`

## Fields

| Name | Type | Tags | Description | Getter | Setter |
|  --- | --- | --- | --- | --- | --- |
| `url` | `string` | Required | The source URL of the image. | getUrl(): string | setUrl(string url): void |
| `height` | `?int` | Required | The image height in pixels. | getHeight(): ?int | setHeight(?int height): void |
| `width` | `?int` | Required | The image width in pixels. | getWidth(): ?int | setWidth(?int width): void |
| `additionalProperties` | `array<string, array>` | Optional | - | findAdditionalProperty(string key): array | additionalProperty(string key, array value): void |

## Example

```php
use SpotifyWebApiLib\Models\Builders\ImageObjectBuilder;
use SpotifyWebApiLib\ApiHelper;

$imageObject = ImageObjectBuilder::init(
    'https://i.scdn.co/image/ab67616d00001e02ff9ca10b55ce82ae553c8228
'
)
    ->height(300)
    ->width(300)
    ->additionalProperty('exampleAdditionalProperty', ApiHelper::deserialize('{"key1":"val1","key2":"val2"}'))
    ->build();
```

