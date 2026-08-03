
# Section Object

*This model accepts additional fields of type array.*

## Structure

`SectionObject`

## Fields

| Name | Type | Tags | Description | Getter | Setter |
|  --- | --- | --- | --- | --- | --- |
| `start` | `?float` | Optional | The starting point (in seconds) of the section. | getStart(): ?float | setStart(?float start): void |
| `duration` | `?float` | Optional | The duration (in seconds) of the section. | getDuration(): ?float | setDuration(?float duration): void |
| `confidence` | `?float` | Optional | The confidence, from 0.0 to 1.0, of the reliability of the section's "designation".<br><br>**Constraints**: `>= 0`, `<= 1` | getConfidence(): ?float | setConfidence(?float confidence): void |
| `loudness` | `?float` | Optional | The overall loudness of the section in decibels (dB). Loudness values are useful for comparing relative loudness of sections within tracks. | getLoudness(): ?float | setLoudness(?float loudness): void |
| `tempo` | `?float` | Optional | The overall estimated tempo of the section in beats per minute (BPM). In musical terminology, tempo is the speed or pace of a given piece and derives directly from the average beat duration. | getTempo(): ?float | setTempo(?float tempo): void |
| `tempoConfidence` | `?float` | Optional | The confidence, from 0.0 to 1.0, of the reliability of the tempo. Some tracks contain tempo changes or sounds which don't contain tempo (like pure speech) which would correspond to a low value in this field.<br><br>**Constraints**: `>= 0`, `<= 1` | getTempoConfidence(): ?float | setTempoConfidence(?float tempoConfidence): void |
| `key` | `?int` | Optional | The estimated overall key of the section. The values in this field ranging from 0 to 11 mapping to pitches using standard Pitch Class notation (E.g. 0 = C, 1 = C♯/D♭, 2 = D, and so on). If no key was detected, the value is -1. | getKey(): ?int | setKey(?int key): void |
| `keyConfidence` | `?float` | Optional | The confidence, from 0.0 to 1.0, of the reliability of the key. Songs with many key changes may correspond to low values in this field.<br><br>**Constraints**: `>= 0`, `<= 1` | getKeyConfidence(): ?float | setKeyConfidence(?float keyConfidence): void |
| `mode` | [`?int(Mode)`](../../doc/models/mode.md) | Optional | - | getMode(): ?int | setMode(?int mode): void |
| `modeConfidence` | `?float` | Optional | The confidence, from 0.0 to 1.0, of the reliability of the `mode`.<br><br>**Constraints**: `>= 0`, `<= 1` | getModeConfidence(): ?float | setModeConfidence(?float modeConfidence): void |
| `timeSignature` | `?int` | Optional | An estimated time signature. The time signature (meter) is a notational convention to specify how many beats are in each bar (or measure). The time signature ranges from 3 to 7 indicating time signatures of "3/4", to "7/4".<br><br>**Constraints**: `>= 3`, `<= 7` | getTimeSignature(): ?int | setTimeSignature(?int timeSignature): void |
| `timeSignatureConfidence` | `?float` | Optional | The confidence, from 0.0 to 1.0, of the reliability of the `time_signature`. Sections with time signature changes may correspond to low values in this field.<br><br>**Constraints**: `>= 0`, `<= 1` | getTimeSignatureConfidence(): ?float | setTimeSignatureConfidence(?float timeSignatureConfidence): void |
| `additionalProperties` | `array<string, array>` | Optional | - | findAdditionalProperty(string key): array | additionalProperty(string key, array value): void |

## Example

```php
use SpotifyWebApiLib\Models\Builders\SectionObjectBuilder;
use SpotifyWebApiLib\ApiHelper;

$sectionObject = SectionObjectBuilder::init()
    ->start(0)
    ->duration(6.97092)
    ->confidence(1)
    ->loudness(-14.938)
    ->tempo(113.178)
    ->tempoConfidence(0.647)
    ->key(9)
    ->keyConfidence(0.297)
    ->modeConfidence(0.471)
    ->timeSignature(4)
    ->timeSignatureConfidence(1)
    ->additionalProperty('exampleAdditionalProperty', ApiHelper::deserialize('{"key1":"val1","key2":"val2"}'))
    ->build();
```

