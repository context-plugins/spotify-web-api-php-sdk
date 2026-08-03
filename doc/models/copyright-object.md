
# Copyright Object

*This model accepts additional fields of type array.*

## Structure

`CopyrightObject`

## Fields

| Name | Type | Tags | Description | Getter | Setter |
|  --- | --- | --- | --- | --- | --- |
| `text` | `?string` | Optional | The copyright text for this content. | getText(): ?string | setText(?string text): void |
| `type` | `?string` | Optional | The type of copyright: `C` = the copyright, `P` = the sound recording (performance) copyright. | getType(): ?string | setType(?string type): void |
| `additionalProperties` | `array<string, array>` | Optional | - | findAdditionalProperty(string key): array | additionalProperty(string key, array value): void |

## Example

```php
use SpotifyWebApiLib\Models\Builders\CopyrightObjectBuilder;
use SpotifyWebApiLib\ApiHelper;

$copyrightObject = CopyrightObjectBuilder::init()
    ->text('text4')
    ->type('type4')
    ->additionalProperty('exampleAdditionalProperty', ApiHelper::deserialize('{"key1":"val1","key2":"val2"}'))
    ->build();
```

