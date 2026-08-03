
# Track

*This model accepts additional fields of type array.*

## Structure

`Track`

## Fields

| Name | Type | Tags | Description | Getter | Setter |
|  --- | --- | --- | --- | --- | --- |
| `numSamples` | `?int` | Optional | The exact number of audio samples analyzed from this track. See also `analysis_sample_rate`. | getNumSamples(): ?int | setNumSamples(?int numSamples): void |
| `duration` | `?float` | Optional | Length of the track in seconds. | getDuration(): ?float | setDuration(?float duration): void |
| `sampleMd5` | `?string` | Optional | This field will always contain the empty string. | getSampleMd5(): ?string | setSampleMd5(?string sampleMd5): void |
| `offsetSeconds` | `?int` | Optional | An offset to the start of the region of the track that was analyzed. (As the entire track is analyzed, this should always be 0.) | getOffsetSeconds(): ?int | setOffsetSeconds(?int offsetSeconds): void |
| `windowSeconds` | `?int` | Optional | The length of the region of the track was analyzed, if a subset of the track was analyzed. (As the entire track is analyzed, this should always be 0.) | getWindowSeconds(): ?int | setWindowSeconds(?int windowSeconds): void |
| `analysisSampleRate` | `?int` | Optional | The sample rate used to decode and analyze this track. May differ from the actual sample rate of this track available on Spotify. | getAnalysisSampleRate(): ?int | setAnalysisSampleRate(?int analysisSampleRate): void |
| `analysisChannels` | `?int` | Optional | The number of channels used for analysis. If 1, all channels are summed together to mono before analysis. | getAnalysisChannels(): ?int | setAnalysisChannels(?int analysisChannels): void |
| `endOfFadeIn` | `?float` | Optional | The time, in seconds, at which the track's fade-in period ends. If the track has no fade-in, this will be 0.0. | getEndOfFadeIn(): ?float | setEndOfFadeIn(?float endOfFadeIn): void |
| `startOfFadeOut` | `?float` | Optional | The time, in seconds, at which the track's fade-out period starts. If the track has no fade-out, this should match the track's length. | getStartOfFadeOut(): ?float | setStartOfFadeOut(?float startOfFadeOut): void |
| `loudness` | `?float` | Optional | The overall loudness of a track in decibels (dB). Loudness values are averaged across the entire track and are useful for comparing relative loudness of tracks. Loudness is the quality of a sound that is the primary psychological correlate of physical strength (amplitude). Values typically range between -60 and 0 db. | getLoudness(): ?float | setLoudness(?float loudness): void |
| `tempo` | `?float` | Optional | The overall estimated tempo of a track in beats per minute (BPM). In musical terminology, tempo is the speed or pace of a given piece and derives directly from the average beat duration. | getTempo(): ?float | setTempo(?float tempo): void |
| `tempoConfidence` | `?float` | Optional | The confidence, from 0.0 to 1.0, of the reliability of the `tempo`.<br><br>**Constraints**: `>= 0`, `<= 1` | getTempoConfidence(): ?float | setTempoConfidence(?float tempoConfidence): void |
| `timeSignature` | `?int` | Optional | An estimated time signature. The time signature (meter) is a notational convention to specify how many beats are in each bar (or measure). The time signature ranges from 3 to 7 indicating time signatures of "3/4", to "7/4".<br><br>**Constraints**: `>= 3`, `<= 7` | getTimeSignature(): ?int | setTimeSignature(?int timeSignature): void |
| `timeSignatureConfidence` | `?float` | Optional | The confidence, from 0.0 to 1.0, of the reliability of the `time_signature`.<br><br>**Constraints**: `>= 0`, `<= 1` | getTimeSignatureConfidence(): ?float | setTimeSignatureConfidence(?float timeSignatureConfidence): void |
| `key` | `?int` | Optional | The key the track is in. Integers map to pitches using standard [Pitch Class notation](https://en.wikipedia.org/wiki/Pitch_class). E.g. 0 = C, 1 = C♯/D♭, 2 = D, and so on. If no key was detected, the value is -1.<br><br>**Constraints**: `>= -1`, `<= 11` | getKey(): ?int | setKey(?int key): void |
| `keyConfidence` | `?float` | Optional | The confidence, from 0.0 to 1.0, of the reliability of the `key`.<br><br>**Constraints**: `>= 0`, `<= 1` | getKeyConfidence(): ?float | setKeyConfidence(?float keyConfidence): void |
| `mode` | `?int` | Optional | Mode indicates the modality (major or minor) of a track, the type of scale from which its melodic content is derived. Major is represented by 1 and minor is 0. | getMode(): ?int | setMode(?int mode): void |
| `modeConfidence` | `?float` | Optional | The confidence, from 0.0 to 1.0, of the reliability of the `mode`.<br><br>**Constraints**: `>= 0`, `<= 1` | getModeConfidence(): ?float | setModeConfidence(?float modeConfidence): void |
| `codestring` | `?string` | Optional | An [Echo Nest Musical Fingerprint (ENMFP)](https://academiccommons.columbia.edu/doi/10.7916/D8Q248M4) codestring for this track. | getCodestring(): ?string | setCodestring(?string codestring): void |
| `codeVersion` | `?float` | Optional | A version number for the Echo Nest Musical Fingerprint format used in the codestring field. | getCodeVersion(): ?float | setCodeVersion(?float codeVersion): void |
| `echoprintstring` | `?string` | Optional | An [EchoPrint](https://github.com/spotify/echoprint-codegen) codestring for this track. | getEchoprintstring(): ?string | setEchoprintstring(?string echoprintstring): void |
| `echoprintVersion` | `?float` | Optional | A version number for the EchoPrint format used in the echoprintstring field. | getEchoprintVersion(): ?float | setEchoprintVersion(?float echoprintVersion): void |
| `synchstring` | `?string` | Optional | A [Synchstring](https://github.com/echonest/synchdata) for this track. | getSynchstring(): ?string | setSynchstring(?string synchstring): void |
| `synchVersion` | `?float` | Optional | A version number for the Synchstring used in the synchstring field. | getSynchVersion(): ?float | setSynchVersion(?float synchVersion): void |
| `rhythmstring` | `?string` | Optional | A Rhythmstring for this track. The format of this string is similar to the Synchstring. | getRhythmstring(): ?string | setRhythmstring(?string rhythmstring): void |
| `rhythmVersion` | `?float` | Optional | A version number for the Rhythmstring used in the rhythmstring field. | getRhythmVersion(): ?float | setRhythmVersion(?float rhythmVersion): void |
| `additionalProperties` | `array<string, array>` | Optional | - | findAdditionalProperty(string key): array | additionalProperty(string key, array value): void |

## Example

```php
use SpotifyWebApiLib\Models\Builders\TrackBuilder;
use SpotifyWebApiLib\ApiHelper;

$track = TrackBuilder::init()
    ->numSamples(4585515)
    ->duration(207.95985)
    ->sampleMd5('sample_md56')
    ->offsetSeconds(0)
    ->windowSeconds(0)
    ->analysisSampleRate(22050)
    ->analysisChannels(1)
    ->endOfFadeIn(0)
    ->startOfFadeOut(201.13705)
    ->loudness(-5.883)
    ->tempo(118.211)
    ->tempoConfidence(0.73)
    ->timeSignature(4)
    ->timeSignatureConfidence(0.994)
    ->key(9)
    ->keyConfidence(0.408)
    ->mode(0)
    ->modeConfidence(0.485)
    ->codeVersion(3.15)
    ->echoprintVersion(4.15)
    ->synchVersion(1)
    ->rhythmVersion(1)
    ->additionalProperty('exampleAdditionalProperty', ApiHelper::deserialize('{"key1":"val1","key2":"val2"}'))
    ->build();
```

