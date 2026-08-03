
# Too Many Requests 1 Exception

*This model accepts additional fields of type array.*

## Structure

`TooManyRequests1Exception`

## Fields

| Name | Type | Tags | Description | Getter | Setter |
|  --- | --- | --- | --- | --- | --- |
| `error` | [`ErrorObject`](../../doc/models/error-object.md) | Required | - | getError(): ErrorObject | setError(ErrorObject error): void |
| `additionalProperties` | `array<string, array>` | Optional | - | findAdditionalProperty(string key): array | additionalProperty(string key, array value): void |

