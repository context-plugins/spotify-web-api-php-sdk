
# Cursor Paged Artists

*This model accepts additional fields of type array.*

## Structure

`CursorPagedArtists`

## Fields

| Name | Type | Tags | Description | Getter | Setter |
|  --- | --- | --- | --- | --- | --- |
| `artists` | [`CursorPagingSimplifiedArtistObject`](../../doc/models/cursor-paging-simplified-artist-object.md) | Required | - | getArtists(): CursorPagingSimplifiedArtistObject | setArtists(CursorPagingSimplifiedArtistObject artists): void |
| `additionalProperties` | `array<string, array>` | Optional | - | findAdditionalProperty(string key): array | additionalProperty(string key, array value): void |

## Example

```php
use SpotifyWebApiLib\Models\Builders\CursorPagedArtistsBuilder;
use SpotifyWebApiLib\Models\Builders\CursorPagingSimplifiedArtistObjectBuilder;
use SpotifyWebApiLib\Models\Builders\CursorObjectBuilder;
use SpotifyWebApiLib\ApiHelper;

$cursorPagedArtists = CursorPagedArtistsBuilder::init(
    CursorPagingSimplifiedArtistObjectBuilder::init()
        ->href('href2')
        ->limit(214)
        ->next('next2')
        ->cursors(
            CursorObjectBuilder::init()
                ->after('after8')
                ->before('before6')
                ->additionalProperty('exampleAdditionalProperty', ApiHelper::deserialize('{"key1":"val1","key2":"val2"}'))
                ->build()
        )
        ->total(52)
        ->additionalProperty('exampleAdditionalProperty', ApiHelper::deserialize('{"key1":"val1","key2":"val2"}'))
        ->build()
)
    ->additionalProperty('exampleAdditionalProperty', ApiHelper::deserialize('{"key1":"val1","key2":"val2"}'))
    ->build();
```

