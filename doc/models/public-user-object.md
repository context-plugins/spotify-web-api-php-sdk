
# Public User Object

*This model accepts additional fields of type array.*

## Structure

`PublicUserObject`

## Fields

| Name | Type | Tags | Description | Getter | Setter |
|  --- | --- | --- | --- | --- | --- |
| `displayName` | `?string` | Optional | The name displayed on the user's profile. `null` if not available. | getDisplayName(): ?string | setDisplayName(?string displayName): void |
| `externalUrls` | [`?ExternalUrlObject`](../../doc/models/external-url-object.md) | Optional | - | getExternalUrls(): ?ExternalUrlObject | setExternalUrls(?ExternalUrlObject externalUrls): void |
| `followers` | [`?FollowersObject`](../../doc/models/followers-object.md) | Optional | - | getFollowers(): ?FollowersObject | setFollowers(?FollowersObject followers): void |
| `href` | `?string` | Optional | A link to the Web API endpoint for this user. | getHref(): ?string | setHref(?string href): void |
| `id` | `?string` | Optional | The [Spotify user ID](https://developer.spotify.com/documentation/web-api/concepts/spotify-uris-ids) for this user. | getId(): ?string | setId(?string id): void |
| `images` | [`?(ImageObject[])`](../../doc/models/image-object.md) | Optional | The user's profile image. | getImages(): ?array | setImages(?array images): void |
| `type` | [`?string(Type4)`](../../doc/models/type-4.md) | Optional | - | getType(): ?string | setType(?string type): void |
| `uri` | `?string` | Optional | The [Spotify URI](https://developer.spotify.com/documentation/web-api/concepts/spotify-uris-ids) for this user. | getUri(): ?string | setUri(?string uri): void |
| `additionalProperties` | `array<string, array>` | Optional | - | findAdditionalProperty(string key): array | additionalProperty(string key, array value): void |

## Example

```php
use SpotifyWebApiLib\Models\Builders\PublicUserObjectBuilder;
use SpotifyWebApiLib\Models\Builders\ExternalUrlObjectBuilder;
use SpotifyWebApiLib\ApiHelper;
use SpotifyWebApiLib\Models\Builders\FollowersObjectBuilder;

$publicUserObject = PublicUserObjectBuilder::init()
    ->displayName('display_name0')
    ->externalUrls(
        ExternalUrlObjectBuilder::init()
            ->spotify('spotify6')
            ->additionalProperty('exampleAdditionalProperty', ApiHelper::deserialize('{"key1":"val1","key2":"val2"}'))
            ->build()
    )
    ->followers(
        FollowersObjectBuilder::init()
            ->href('href0')
            ->total(82)
            ->additionalProperty('exampleAdditionalProperty', ApiHelper::deserialize('{"key1":"val1","key2":"val2"}'))
            ->build()
    )
    ->href('href2')
    ->id('id0')
    ->additionalProperty('exampleAdditionalProperty', ApiHelper::deserialize('{"key1":"val1","key2":"val2"}'))
    ->build();
```

