
# Cursor Object

*This model accepts additional fields of type array.*

## Structure

`CursorObject`

## Fields

| Name | Type | Tags | Description | Getter | Setter |
|  --- | --- | --- | --- | --- | --- |
| `after` | `?string` | Optional | The cursor to use as key to find the next page of items. | getAfter(): ?string | setAfter(?string after): void |
| `before` | `?string` | Optional | The cursor to use as key to find the previous page of items. | getBefore(): ?string | setBefore(?string before): void |
| `additionalProperties` | `array<string, array>` | Optional | - | findAdditionalProperty(string key): array | additionalProperty(string key, array value): void |

## Example

```php
use SpotifyWebApiLib\Models\Builders\CursorObjectBuilder;
use SpotifyWebApiLib\ApiHelper;

$cursorObject = CursorObjectBuilder::init()
    ->after('after0')
    ->before('before8')
    ->additionalProperty('exampleAdditionalProperty', ApiHelper::deserialize('{"key1":"val1","key2":"val2"}'))
    ->build();
```

