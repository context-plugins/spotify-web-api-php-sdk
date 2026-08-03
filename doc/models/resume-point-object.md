
# Resume Point Object

*This model accepts additional fields of type array.*

## Structure

`ResumePointObject`

## Fields

| Name | Type | Tags | Description | Getter | Setter |
|  --- | --- | --- | --- | --- | --- |
| `fullyPlayed` | `?bool` | Optional | Whether or not the episode has been fully played by the user. | getFullyPlayed(): ?bool | setFullyPlayed(?bool fullyPlayed): void |
| `resumePositionMs` | `?int` | Optional | The user's most recent position in the episode in milliseconds. | getResumePositionMs(): ?int | setResumePositionMs(?int resumePositionMs): void |
| `additionalProperties` | `array<string, array>` | Optional | - | findAdditionalProperty(string key): array | additionalProperty(string key, array value): void |

## Example

```php
use SpotifyWebApiLib\Models\Builders\ResumePointObjectBuilder;
use SpotifyWebApiLib\ApiHelper;

$resumePointObject = ResumePointObjectBuilder::init()
    ->fullyPlayed(false)
    ->resumePositionMs(106)
    ->additionalProperty('exampleAdditionalProperty', ApiHelper::deserialize('{"key1":"val1","key2":"val2"}'))
    ->build();
```

