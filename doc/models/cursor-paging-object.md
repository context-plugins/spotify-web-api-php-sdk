
# Cursor Paging Object

*This model accepts additional fields of type array.*

## Structure

`CursorPagingObject`

## Fields

| Name | Type | Tags | Description | Getter | Setter |
|  --- | --- | --- | --- | --- | --- |
| `href` | `?string` | Optional | A link to the Web API endpoint returning the full result of the request. | getHref(): ?string | setHref(?string href): void |
| `limit` | `?int` | Optional | The maximum number of items in the response (as set in the query or by default). | getLimit(): ?int | setLimit(?int limit): void |
| `next` | `?string` | Optional | URL to the next page of items. ( `null` if none) | getNext(): ?string | setNext(?string next): void |
| `cursors` | [`?CursorObject`](../../doc/models/cursor-object.md) | Optional | - | getCursors(): ?CursorObject | setCursors(?CursorObject cursors): void |
| `total` | `?int` | Optional | The total number of items available to return. | getTotal(): ?int | setTotal(?int total): void |
| `additionalProperties` | `array<string, array>` | Optional | - | findAdditionalProperty(string key): array | additionalProperty(string key, array value): void |

## Example

```php
use SpotifyWebApiLib\Models\Builders\CursorPagingObjectBuilder;
use SpotifyWebApiLib\Models\Builders\CursorObjectBuilder;
use SpotifyWebApiLib\ApiHelper;

$cursorPagingObject = CursorPagingObjectBuilder::init()
    ->href('href8')
    ->limit(82)
    ->next('next6')
    ->cursors(
        CursorObjectBuilder::init()
            ->after('after8')
            ->before('before6')
            ->additionalProperty('exampleAdditionalProperty', ApiHelper::deserialize('{"key1":"val1","key2":"val2"}'))
            ->build()
    )
    ->total(176)
    ->additionalProperty('exampleAdditionalProperty', ApiHelper::deserialize('{"key1":"val1","key2":"val2"}'))
    ->build();
```

