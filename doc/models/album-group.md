
# Album Group

This field describes the relationship between the artist and the album.

## Enumeration

`AlbumGroup`

## Fields

| Name |
|  --- |
| `ALBUM` |
| `SINGLE` |
| `COMPILATION` |
| `APPEARS_ON` |

## Example

```php
use SpotifyWebApiLib\Models\AlbumGroup;

$albumGroup = AlbumGroup::COMPILATION;
```

