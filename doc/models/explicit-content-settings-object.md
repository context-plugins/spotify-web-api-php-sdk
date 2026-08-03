
# Explicit Content Settings Object

*This model accepts additional fields of type array.*

## Structure

`ExplicitContentSettingsObject`

## Fields

| Name | Type | Tags | Description | Getter | Setter |
|  --- | --- | --- | --- | --- | --- |
| `filterEnabled` | `?bool` | Optional | When `true`, indicates that explicit content should not be played. | getFilterEnabled(): ?bool | setFilterEnabled(?bool filterEnabled): void |
| `filterLocked` | `?bool` | Optional | When `true`, indicates that the explicit content setting is locked and can't be changed by the user. | getFilterLocked(): ?bool | setFilterLocked(?bool filterLocked): void |
| `additionalProperties` | `array<string, array>` | Optional | - | findAdditionalProperty(string key): array | additionalProperty(string key, array value): void |

## Example

```php
use SpotifyWebApiLib\Models\Builders\ExplicitContentSettingsObjectBuilder;
use SpotifyWebApiLib\ApiHelper;

$explicitContentSettingsObject = ExplicitContentSettingsObjectBuilder::init()
    ->filterEnabled(false)
    ->filterLocked(false)
    ->additionalProperty('exampleAdditionalProperty', ApiHelper::deserialize('{"key1":"val1","key2":"val2"}'))
    ->build();
```

