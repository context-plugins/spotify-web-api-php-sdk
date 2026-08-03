
# Error Object

*This model accepts additional fields of type array.*

## Structure

`ErrorObject`

## Fields

| Name | Type | Tags | Description | Getter | Setter |
|  --- | --- | --- | --- | --- | --- |
| `status` | `int` | Required | The HTTP status code (also returned in the response header; see [Response Status Codes](https://developer.spotify.com/documentation/web-api/concepts/api-calls#response-status-codes) for more information).<br><br>**Constraints**: `>= 400`, `<= 599` | getStatus(): int | setStatus(int status): void |
| `message` | `string` | Required | A short description of the cause of the error. | getMessage(): string | setMessage(string message): void |
| `additionalProperties` | `array<string, array>` | Optional | - | findAdditionalProperty(string key): array | additionalProperty(string key, array value): void |

## Example

```php
use SpotifyWebApiLib\Models\Builders\ErrorObjectBuilder;
use SpotifyWebApiLib\ApiHelper;

$errorObject = ErrorObjectBuilder::init(
    400,
    'message2'
)
    ->additionalProperty('exampleAdditionalProperty', ApiHelper::deserialize('{"key1":"val1","key2":"val2"}'))
    ->build();
```

