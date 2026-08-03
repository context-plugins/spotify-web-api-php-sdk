
# Episode Restriction Object

*This model accepts additional fields of type array.*

## Structure

`EpisodeRestrictionObject`

## Fields

| Name | Type | Tags | Description | Getter | Setter |
|  --- | --- | --- | --- | --- | --- |
| `reason` | `?string` | Optional | The reason for the restriction. Supported values:<br><br>- `market` - The content item is not available in the given market.<br>- `product` - The content item is not available for the user's subscription type.<br>- `explicit` - The content item is explicit and the user's account is set to not play explicit content.<br><br>Additional reasons may be added in the future.<br>**Note**: If you use this field, make sure that your application safely handles unknown values. | getReason(): ?string | setReason(?string reason): void |
| `additionalProperties` | `array<string, array>` | Optional | - | findAdditionalProperty(string key): array | additionalProperty(string key, array value): void |

## Example

```php
use SpotifyWebApiLib\Models\Builders\EpisodeRestrictionObjectBuilder;
use SpotifyWebApiLib\ApiHelper;

$episodeRestrictionObject = EpisodeRestrictionObjectBuilder::init()
    ->reason('reason8')
    ->additionalProperty('exampleAdditionalProperty', ApiHelper::deserialize('{"key1":"val1","key2":"val2"}'))
    ->build();
```

