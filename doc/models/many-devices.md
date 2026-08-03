
# Many Devices

*This model accepts additional fields of type array.*

## Structure

`ManyDevices`

## Fields

| Name | Type | Tags | Description | Getter | Setter |
|  --- | --- | --- | --- | --- | --- |
| `devices` | [`DeviceObject[]`](../../doc/models/device-object.md) | Required | - | getDevices(): array | setDevices(array devices): void |
| `additionalProperties` | `array<string, array>` | Optional | - | findAdditionalProperty(string key): array | additionalProperty(string key, array value): void |

## Example

```php
use SpotifyWebApiLib\Models\Builders\ManyDevicesBuilder;
use SpotifyWebApiLib\Models\Builders\DeviceObjectBuilder;
use SpotifyWebApiLib\ApiHelper;

$manyDevices = ManyDevicesBuilder::init(
    [
        DeviceObjectBuilder::init()
            ->id('id4')
            ->isActive(false)
            ->isPrivateSession(false)
            ->isRestricted(false)
            ->name('Kitchen speaker')
            ->type('computer')
            ->volumePercent(59)
            ->additionalProperty('exampleAdditionalProperty', ApiHelper::deserialize('{"key1":"val1","key2":"val2"}'))
            ->build()
    ]
)
    ->additionalProperty('exampleAdditionalProperty', ApiHelper::deserialize('{"key1":"val1","key2":"val2"}'))
    ->build();
```

