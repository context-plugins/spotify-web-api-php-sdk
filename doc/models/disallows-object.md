
# Disallows Object

*This model accepts additional fields of type array.*

## Structure

`DisallowsObject`

## Fields

| Name | Type | Tags | Description | Getter | Setter |
|  --- | --- | --- | --- | --- | --- |
| `interruptingPlayback` | `?bool` | Optional | Interrupting playback. Optional field. | getInterruptingPlayback(): ?bool | setInterruptingPlayback(?bool interruptingPlayback): void |
| `pausing` | `?bool` | Optional | Pausing. Optional field. | getPausing(): ?bool | setPausing(?bool pausing): void |
| `resuming` | `?bool` | Optional | Resuming. Optional field. | getResuming(): ?bool | setResuming(?bool resuming): void |
| `seeking` | `?bool` | Optional | Seeking playback location. Optional field. | getSeeking(): ?bool | setSeeking(?bool seeking): void |
| `skippingNext` | `?bool` | Optional | Skipping to the next context. Optional field. | getSkippingNext(): ?bool | setSkippingNext(?bool skippingNext): void |
| `skippingPrev` | `?bool` | Optional | Skipping to the previous context. Optional field. | getSkippingPrev(): ?bool | setSkippingPrev(?bool skippingPrev): void |
| `togglingRepeatContext` | `?bool` | Optional | Toggling repeat context flag. Optional field. | getTogglingRepeatContext(): ?bool | setTogglingRepeatContext(?bool togglingRepeatContext): void |
| `togglingShuffle` | `?bool` | Optional | Toggling shuffle flag. Optional field. | getTogglingShuffle(): ?bool | setTogglingShuffle(?bool togglingShuffle): void |
| `togglingRepeatTrack` | `?bool` | Optional | Toggling repeat track flag. Optional field. | getTogglingRepeatTrack(): ?bool | setTogglingRepeatTrack(?bool togglingRepeatTrack): void |
| `transferringPlayback` | `?bool` | Optional | Transfering playback between devices. Optional field. | getTransferringPlayback(): ?bool | setTransferringPlayback(?bool transferringPlayback): void |
| `additionalProperties` | `array<string, array>` | Optional | - | findAdditionalProperty(string key): array | additionalProperty(string key, array value): void |

## Example

```php
use SpotifyWebApiLib\Models\Builders\DisallowsObjectBuilder;
use SpotifyWebApiLib\ApiHelper;

$disallowsObject = DisallowsObjectBuilder::init()
    ->interruptingPlayback(false)
    ->pausing(false)
    ->resuming(false)
    ->seeking(false)
    ->skippingNext(false)
    ->additionalProperty('exampleAdditionalProperty', ApiHelper::deserialize('{"key1":"val1","key2":"val2"}'))
    ->build();
```

