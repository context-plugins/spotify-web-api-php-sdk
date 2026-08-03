
# Paging Featured Playlist Object

*This model accepts additional fields of type array.*

## Structure

`PagingFeaturedPlaylistObject`

## Fields

| Name | Type | Tags | Description | Getter | Setter |
|  --- | --- | --- | --- | --- | --- |
| `message` | `?string` | Optional | The localized message of a playlist. | getMessage(): ?string | setMessage(?string message): void |
| `playlists` | [`?PagingPlaylistObject`](../../doc/models/paging-playlist-object.md) | Optional | - | getPlaylists(): ?PagingPlaylistObject | setPlaylists(?PagingPlaylistObject playlists): void |
| `additionalProperties` | `array<string, array>` | Optional | - | findAdditionalProperty(string key): array | additionalProperty(string key, array value): void |

## Example

```php
use SpotifyWebApiLib\Models\Builders\PagingFeaturedPlaylistObjectBuilder;
use SpotifyWebApiLib\Models\Builders\PagingPlaylistObjectBuilder;
use SpotifyWebApiLib\Models\Builders\SimplifiedPlaylistObjectBuilder;
use SpotifyWebApiLib\Models\Builders\ExternalUrlObjectBuilder;
use SpotifyWebApiLib\ApiHelper;

$pagingFeaturedPlaylistObject = PagingFeaturedPlaylistObjectBuilder::init()
    ->message('Popular Playlists')
    ->playlists(
        PagingPlaylistObjectBuilder::init(
            'href2',
            68,
            164,
            162,
            [
                SimplifiedPlaylistObjectBuilder::init()
                    ->collaborative(false)
                    ->description('description2')
                    ->externalUrls(
                        ExternalUrlObjectBuilder::init()
                            ->spotify('spotify6')
                            ->additionalProperty('exampleAdditionalProperty', ApiHelper::deserialize('{"key1":"val1","key2":"val2"}'))
                            ->build()
                    )
                    ->href('href0')
                    ->id('id8')
                    ->additionalProperty('exampleAdditionalProperty', ApiHelper::deserialize('{"key1":"val1","key2":"val2"}'))
                    ->build(),
                SimplifiedPlaylistObjectBuilder::init()
                    ->collaborative(false)
                    ->description('description2')
                    ->externalUrls(
                        ExternalUrlObjectBuilder::init()
                            ->spotify('spotify6')
                            ->additionalProperty('exampleAdditionalProperty', ApiHelper::deserialize('{"key1":"val1","key2":"val2"}'))
                            ->build()
                    )
                    ->href('href0')
                    ->id('id8')
                    ->additionalProperty('exampleAdditionalProperty', ApiHelper::deserialize('{"key1":"val1","key2":"val2"}'))
                    ->build(),
                SimplifiedPlaylistObjectBuilder::init()
                    ->collaborative(false)
                    ->description('description2')
                    ->externalUrls(
                        ExternalUrlObjectBuilder::init()
                            ->spotify('spotify6')
                            ->additionalProperty('exampleAdditionalProperty', ApiHelper::deserialize('{"key1":"val1","key2":"val2"}'))
                            ->build()
                    )
                    ->href('href0')
                    ->id('id8')
                    ->additionalProperty('exampleAdditionalProperty', ApiHelper::deserialize('{"key1":"val1","key2":"val2"}'))
                    ->build()
            ]
        )
            ->next('next2')
            ->previous('previous8')
            ->additionalProperty('exampleAdditionalProperty', ApiHelper::deserialize('{"key1":"val1","key2":"val2"}'))
            ->build()
    )
    ->additionalProperty('exampleAdditionalProperty', ApiHelper::deserialize('{"key1":"val1","key2":"val2"}'))
    ->build();
```

