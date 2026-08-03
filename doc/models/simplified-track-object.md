
# Simplified Track Object

*This model accepts additional fields of type array.*

## Structure

`SimplifiedTrackObject`

## Fields

| Name | Type | Tags | Description | Getter | Setter |
|  --- | --- | --- | --- | --- | --- |
| `artists` | [`?(SimplifiedArtistObject[])`](../../doc/models/simplified-artist-object.md) | Optional | The artists who performed the track. Each artist object includes a link in `href` to more detailed information about the artist. | getArtists(): ?array | setArtists(?array artists): void |
| `availableMarkets` | `?(string[])` | Optional | A list of the countries in which the track can be played, identified by their [ISO 3166-1 alpha-2](http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2) code. | getAvailableMarkets(): ?array | setAvailableMarkets(?array availableMarkets): void |
| `discNumber` | `?int` | Optional | The disc number (usually `1` unless the album consists of more than one disc). | getDiscNumber(): ?int | setDiscNumber(?int discNumber): void |
| `durationMs` | `?int` | Optional | The track length in milliseconds. | getDurationMs(): ?int | setDurationMs(?int durationMs): void |
| `explicit` | `?bool` | Optional | Whether or not the track has explicit lyrics ( `true` = yes it does; `false` = no it does not OR unknown). | getExplicit(): ?bool | setExplicit(?bool explicit): void |
| `externalUrls` | [`?ExternalUrlObject`](../../doc/models/external-url-object.md) | Optional | - | getExternalUrls(): ?ExternalUrlObject | setExternalUrls(?ExternalUrlObject externalUrls): void |
| `href` | `?string` | Optional | A link to the Web API endpoint providing full details of the track. | getHref(): ?string | setHref(?string href): void |
| `id` | `?string` | Optional | The [Spotify ID](https://developer.spotify.com/documentation/web-api/concepts/spotify-uris-ids) for the track. | getId(): ?string | setId(?string id): void |
| `isPlayable` | `?bool` | Optional | Part of the response when [Track Relinking](https://developer.spotify.com/documentation/web-api/concepts/track-relinking/) is applied. If `true`, the track is playable in the given market. Otherwise `false`. | getIsPlayable(): ?bool | setIsPlayable(?bool isPlayable): void |
| `linkedFrom` | [`?LinkedTrackObject`](../../doc/models/linked-track-object.md) | Optional | - | getLinkedFrom(): ?LinkedTrackObject | setLinkedFrom(?LinkedTrackObject linkedFrom): void |
| `restrictions` | [`?TrackRestrictionObject`](../../doc/models/track-restriction-object.md) | Optional | - | getRestrictions(): ?TrackRestrictionObject | setRestrictions(?TrackRestrictionObject restrictions): void |
| `name` | `?string` | Optional | The name of the track. | getName(): ?string | setName(?string name): void |
| `previewUrl` | `?string` | Optional | A URL to a 30 second preview (MP3 format) of the track. | getPreviewUrl(): ?string | setPreviewUrl(?string previewUrl): void |
| `trackNumber` | `?int` | Optional | The number of the track. If an album has several discs, the track number is the number on the specified disc. | getTrackNumber(): ?int | setTrackNumber(?int trackNumber): void |
| `type` | `?string` | Optional | The object type: "track". | getType(): ?string | setType(?string type): void |
| `uri` | `?string` | Optional | The [Spotify URI](https://developer.spotify.com/documentation/web-api/concepts/spotify-uris-ids) for the track. | getUri(): ?string | setUri(?string uri): void |
| `isLocal` | `?bool` | Optional | Whether or not the track is from a local file. | getIsLocal(): ?bool | setIsLocal(?bool isLocal): void |
| `additionalProperties` | `array<string, array>` | Optional | - | findAdditionalProperty(string key): array | additionalProperty(string key, array value): void |

## Example

```php
use SpotifyWebApiLib\Models\Builders\SimplifiedTrackObjectBuilder;
use SpotifyWebApiLib\Models\Builders\SimplifiedArtistObjectBuilder;
use SpotifyWebApiLib\Models\Builders\ExternalUrlObjectBuilder;
use SpotifyWebApiLib\ApiHelper;
use SpotifyWebApiLib\Models\Type;

$simplifiedTrackObject = SimplifiedTrackObjectBuilder::init()
    ->artists(
        [
            SimplifiedArtistObjectBuilder::init()
                ->externalUrls(
                    ExternalUrlObjectBuilder::init()
                        ->spotify('spotify6')
                        ->additionalProperty('exampleAdditionalProperty', ApiHelper::deserialize('{"key1":"val1","key2":"val2"}'))
                        ->build()
                )
                ->href('href2')
                ->id('id0')
                ->name('name0')
                ->type(Type::ARTIST)
                ->additionalProperty('exampleAdditionalProperty', ApiHelper::deserialize('{"key1":"val1","key2":"val2"}'))
                ->build(),
            SimplifiedArtistObjectBuilder::init()
                ->externalUrls(
                    ExternalUrlObjectBuilder::init()
                        ->spotify('spotify6')
                        ->additionalProperty('exampleAdditionalProperty', ApiHelper::deserialize('{"key1":"val1","key2":"val2"}'))
                        ->build()
                )
                ->href('href2')
                ->id('id0')
                ->name('name0')
                ->type(Type::ARTIST)
                ->additionalProperty('exampleAdditionalProperty', ApiHelper::deserialize('{"key1":"val1","key2":"val2"}'))
                ->build()
        ]
    )
    ->availableMarkets(
        [
            'available_markets0',
            'available_markets1',
            'available_markets2'
        ]
    )
    ->discNumber(180)
    ->durationMs(244)
    ->explicit(false)
    ->additionalProperty('exampleAdditionalProperty', ApiHelper::deserialize('{"key1":"val1","key2":"val2"}'))
    ->build();
```

