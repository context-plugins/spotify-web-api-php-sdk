
# Track 1

*This model accepts additional fields of type array.*

## Structure

`Track1`

## Fields

| Name | Type | Tags | Description | Getter | Setter |
|  --- | --- | --- | --- | --- | --- |
| `uri` | `?string` | Optional | Spotify URI | getUri(): ?string | setUri(?string uri): void |
| `additionalProperties` | `array<string, array>` | Optional | - | findAdditionalProperty(string key): array | additionalProperty(string key, array value): void |

## Example

```php
use SpotifyWebApiLib\Models\Builders\Track1Builder;
use SpotifyWebApiLib\ApiHelper;

$track1 = Track1Builder::init()
    ->uri('uri0')
    ->additionalProperty('exampleAdditionalProperty', ApiHelper::deserialize('{"key1":"val1","key2":"val2"}'))
    ->build();
```

