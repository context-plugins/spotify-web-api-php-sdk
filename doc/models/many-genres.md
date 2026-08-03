
# Many Genres

*This model accepts additional fields of type array.*

## Structure

`ManyGenres`

## Fields

| Name | Type | Tags | Description | Getter | Setter |
|  --- | --- | --- | --- | --- | --- |
| `genres` | `string[]` | Required | - | getGenres(): array | setGenres(array genres): void |
| `additionalProperties` | `array<string, array>` | Optional | - | findAdditionalProperty(string key): array | additionalProperty(string key, array value): void |

## Example

```php
use SpotifyWebApiLib\Models\Builders\ManyGenresBuilder;
use SpotifyWebApiLib\ApiHelper;

$manyGenres = ManyGenresBuilder::init(
    [
        'alternative',
        'samba'
    ]
)
    ->additionalProperty('exampleAdditionalProperty', ApiHelper::deserialize('{"key1":"val1","key2":"val2"}'))
    ->build();
```

