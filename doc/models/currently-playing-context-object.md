
# Currently Playing Context Object

*This model accepts additional fields of type array.*

## Structure

`CurrentlyPlayingContextObject`

## Fields

| Name | Type | Tags | Description | Getter | Setter |
|  --- | --- | --- | --- | --- | --- |
| `device` | [`?DeviceObject`](../../doc/models/device-object.md) | Optional | - | getDevice(): ?DeviceObject | setDevice(?DeviceObject device): void |
| `repeatState` | `?string` | Optional | off, track, context | getRepeatState(): ?string | setRepeatState(?string repeatState): void |
| `shuffleState` | `?bool` | Optional | If shuffle is on or off. | getShuffleState(): ?bool | setShuffleState(?bool shuffleState): void |
| `context` | [`?ContextObject`](../../doc/models/context-object.md) | Optional | - | getContext(): ?ContextObject | setContext(?ContextObject context): void |
| `timestamp` | `?int` | Optional | Unix Millisecond Timestamp when data was fetched. | getTimestamp(): ?int | setTimestamp(?int timestamp): void |
| `progressMs` | `?int` | Optional | Progress into the currently playing track or episode. Can be `null`. | getProgressMs(): ?int | setProgressMs(?int progressMs): void |
| `isPlaying` | `?bool` | Optional | If something is currently playing, return `true`. | getIsPlaying(): ?bool | setIsPlaying(?bool isPlaying): void |
| `item` | [TrackObject](../../doc/models/track-object.md)\|[EpisodeObject](../../doc/models/episode-object.md)\|null | Optional | This is a container for one-of cases. | getItem(): | setItem( item): void |
| `currentlyPlayingType` | `?string` | Optional | The object type of the currently playing item. Can be one of `track`, `episode`, `ad` or `unknown`. | getCurrentlyPlayingType(): ?string | setCurrentlyPlayingType(?string currentlyPlayingType): void |
| `actions` | [`?DisallowsObject`](../../doc/models/disallows-object.md) | Optional | - | getActions(): ?DisallowsObject | setActions(?DisallowsObject actions): void |
| `additionalProperties` | `array<string, array>` | Optional | - | findAdditionalProperty(string key): array | additionalProperty(string key, array value): void |

## Example

```php
use SpotifyWebApiLib\Models\Builders\CurrentlyPlayingContextObjectBuilder;
use SpotifyWebApiLib\Models\Builders\DeviceObjectBuilder;
use SpotifyWebApiLib\ApiHelper;
use SpotifyWebApiLib\Models\Builders\ContextObjectBuilder;
use SpotifyWebApiLib\Models\Builders\ExternalUrlObjectBuilder;

$currentlyPlayingContextObject = CurrentlyPlayingContextObjectBuilder::init()
    ->device(
        DeviceObjectBuilder::init()
            ->id('id6')
            ->isActive(false)
            ->isPrivateSession(false)
            ->isRestricted(false)
            ->name('name6')
            ->additionalProperty('exampleAdditionalProperty', ApiHelper::deserialize('{"key1":"val1","key2":"val2"}'))
            ->build()
    )
    ->repeatState('repeat_state8')
    ->shuffleState(false)
    ->context(
        ContextObjectBuilder::init()
            ->type('type8')
            ->href('href4')
            ->externalUrls(
                ExternalUrlObjectBuilder::init()
                    ->spotify('spotify6')
                    ->additionalProperty('exampleAdditionalProperty', ApiHelper::deserialize('{"key1":"val1","key2":"val2"}'))
                    ->build()
            )
            ->uri('uri6')
            ->additionalProperty('exampleAdditionalProperty', ApiHelper::deserialize('{"key1":"val1","key2":"val2"}'))
            ->build()
    )
    ->timestamp(48)
    ->additionalProperty('exampleAdditionalProperty', ApiHelper::deserialize('{"key1":"val1","key2":"val2"}'))
    ->build();
```

