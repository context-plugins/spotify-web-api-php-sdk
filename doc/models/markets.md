
# Markets

*This model accepts additional fields of type array.*

## Structure

`Markets`

## Fields

| Name | Type | Tags | Description | Getter | Setter |
|  --- | --- | --- | --- | --- | --- |
| `markets` | `?(string[])` | Optional | - | getMarkets(): ?array | setMarkets(?array markets): void |
| `additionalProperties` | `array<string, array>` | Optional | - | findAdditionalProperty(string key): array | additionalProperty(string key, array value): void |

## Example

```php
use SpotifyWebApiLib\Models\Builders\MarketsBuilder;
use SpotifyWebApiLib\ApiHelper;

$markets = MarketsBuilder::init()
    ->markets(
        [
            'CA',
            'BR',
            'IT'
        ]
    )
    ->additionalProperty('exampleAdditionalProperty', ApiHelper::deserialize('{"key1":"val1","key2":"val2"}'))
    ->build();
```

