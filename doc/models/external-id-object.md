
# External Id Object

*This model accepts additional fields of type array.*

## Structure

`ExternalIdObject`

## Fields

| Name | Type | Tags | Description | Getter | Setter |
|  --- | --- | --- | --- | --- | --- |
| `isrc` | `?string` | Optional | [International Standard Recording Code](http://en.wikipedia.org/wiki/International_Standard_Recording_Code) | getIsrc(): ?string | setIsrc(?string isrc): void |
| `ean` | `?string` | Optional | [International Article Number](http://en.wikipedia.org/wiki/International_Article_Number_%28EAN%29) | getEan(): ?string | setEan(?string ean): void |
| `upc` | `?string` | Optional | [Universal Product Code](http://en.wikipedia.org/wiki/Universal_Product_Code) | getUpc(): ?string | setUpc(?string upc): void |
| `additionalProperties` | `array<string, array>` | Optional | - | findAdditionalProperty(string key): array | additionalProperty(string key, array value): void |

## Example

```php
use SpotifyWebApiLib\Models\Builders\ExternalIdObjectBuilder;
use SpotifyWebApiLib\ApiHelper;

$externalIdObject = ExternalIdObjectBuilder::init()
    ->isrc('isrc4')
    ->ean('ean2')
    ->upc('upc6')
    ->additionalProperty('exampleAdditionalProperty', ApiHelper::deserialize('{"key1":"val1","key2":"val2"}'))
    ->build();
```

