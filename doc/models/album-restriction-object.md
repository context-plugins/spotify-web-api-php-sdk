
# Album Restriction Object

*This model accepts additional fields of type array.*

## Structure

`AlbumRestrictionObject`

## Fields

| Name | Type | Tags | Description | Getter | Setter |
|  --- | --- | --- | --- | --- | --- |
| `reason` | [`?string(Reason)`](../../doc/models/reason.md) | Optional | - | getReason(): ?string | setReason(?string reason): void |
| `additionalProperties` | `array<string, array>` | Optional | - | findAdditionalProperty(string key): array | additionalProperty(string key, array value): void |

## Example

```php
use SpotifyWebApiLib\Models\Builders\AlbumRestrictionObjectBuilder;
use SpotifyWebApiLib\Models\Reason;
use SpotifyWebApiLib\ApiHelper;

$albumRestrictionObject = AlbumRestrictionObjectBuilder::init()
    ->reason(Reason::MARKET)
    ->additionalProperty('exampleAdditionalProperty', ApiHelper::deserialize('{"key1":"val1","key2":"val2"}'))
    ->build();
```

