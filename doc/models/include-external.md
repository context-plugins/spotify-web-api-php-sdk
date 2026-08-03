
# Include External

If `include_external=audio` is specified it signals that the client can play externally hosted audio content, and marks
the content as playable in the response. By default externally hosted audio content is marked as unplayable in the response.

## Enumeration

`IncludeExternal`

## Fields

| Name |
|  --- |
| `AUDIO` |

## Example

```php
use SpotifyWebApiLib\Models\IncludeExternal;

$includeExternal = IncludeExternal::AUDIO;
```

