
# Saved Audiobook Object

*This model accepts additional fields of type array.*

## Structure

`SavedAudiobookObject`

## Fields

| Name | Type | Tags | Description | Getter | Setter |
|  --- | --- | --- | --- | --- | --- |
| `addedAt` | `?DateTime` | Optional | The date and time the audiobook was saved<br>Timestamps are returned in ISO 8601 format as Coordinated Universal Time (UTC) with a zero offset: YYYY-MM-DDTHH:MM:SSZ.<br>If the time is imprecise (for example, the date/time of an album release), an additional field indicates the precision; see for example, release_date in an album object. | getAddedAt(): ?\DateTime | setAddedAt(?\DateTime addedAt): void |
| `audiobook` | [`?AudiobookObject`](../../doc/models/audiobook-object.md) | Optional | - | getAudiobook(): ?AudiobookObject | setAudiobook(?AudiobookObject audiobook): void |
| `additionalProperties` | `array<string, array>` | Optional | - | findAdditionalProperty(string key): array | additionalProperty(string key, array value): void |

## Example

```php
use SpotifyWebApiLib\Models\Builders\SavedAudiobookObjectBuilder;
use SpotifyWebApiLib\Utils\DateTimeHelper;
use SpotifyWebApiLib\Models\Builders\AudiobookObjectBuilder;
use SpotifyWebApiLib\Models\Builders\AuthorObjectBuilder;
use SpotifyWebApiLib\ApiHelper;
use SpotifyWebApiLib\Models\Builders\CopyrightObjectBuilder;
use SpotifyWebApiLib\Models\Builders\ExternalUrlObjectBuilder;
use SpotifyWebApiLib\Models\Builders\ImageObjectBuilder;
use SpotifyWebApiLib\Models\Builders\NarratorObjectBuilder;
use SpotifyWebApiLib\Models\Type9;
use SpotifyWebApiLib\Models\Builders\PagingSimplifiedChapterObjectBuilder;
use SpotifyWebApiLib\Models\Builders\ChapterBaseBuilder;
use SpotifyWebApiLib\Models\ReleaseDatePrecision;
use SpotifyWebApiLib\Models\Type5;
use SpotifyWebApiLib\Models\Builders\ResumePointObjectBuilder;
use SpotifyWebApiLib\Models\Builders\ChapterRestrictionObjectBuilder;

$savedAudiobookObject = SavedAudiobookObjectBuilder::init()
    ->addedAt(DateTimeHelper::fromRfc3339DateTime('2016-03-13T12:52:32.123Z'))
    ->audiobook(
        AudiobookObjectBuilder::init(
            [
                AuthorObjectBuilder::init()
                    ->name('name0')
                    ->additionalProperty('exampleAdditionalProperty', ApiHelper::deserialize('{"key1":"val1","key2":"val2"}'))
                    ->build()
            ],
            [
                'available_markets2',
                'available_markets3',
                'available_markets4'
            ],
            [
                CopyrightObjectBuilder::init()
                    ->text('text2')
                    ->type('type2')
                    ->additionalProperty('exampleAdditionalProperty', ApiHelper::deserialize('{"key1":"val1","key2":"val2"}'))
                    ->build(),
                CopyrightObjectBuilder::init()
                    ->text('text2')
                    ->type('type2')
                    ->additionalProperty('exampleAdditionalProperty', ApiHelper::deserialize('{"key1":"val1","key2":"val2"}'))
                    ->build(),
                CopyrightObjectBuilder::init()
                    ->text('text2')
                    ->type('type2')
                    ->additionalProperty('exampleAdditionalProperty', ApiHelper::deserialize('{"key1":"val1","key2":"val2"}'))
                    ->build()
            ],
            'description2',
            'html_description2',
            false,
            ExternalUrlObjectBuilder::init()
                ->spotify('spotify6')
                ->additionalProperty('exampleAdditionalProperty', ApiHelper::deserialize('{"key1":"val1","key2":"val2"}'))
                ->build(),
            'href0',
            'id8',
            [
                ImageObjectBuilder::init(
                    'url6'
                )
                    ->height(182)
                    ->width(222)
                    ->additionalProperty('exampleAdditionalProperty', ApiHelper::deserialize('{"key1":"val1","key2":"val2"}'))
                    ->build(),
                ImageObjectBuilder::init(
                    'url6'
                )
                    ->height(182)
                    ->width(222)
                    ->additionalProperty('exampleAdditionalProperty', ApiHelper::deserialize('{"key1":"val1","key2":"val2"}'))
                    ->build(),
                ImageObjectBuilder::init(
                    'url6'
                )
                    ->height(182)
                    ->width(222)
                    ->additionalProperty('exampleAdditionalProperty', ApiHelper::deserialize('{"key1":"val1","key2":"val2"}'))
                    ->build()
            ],
            [
                'languages3',
                'languages4'
            ],
            'media_type4',
            'name8',
            [
                NarratorObjectBuilder::init()
                    ->name('name0')
                    ->additionalProperty('exampleAdditionalProperty', ApiHelper::deserialize('{"key1":"val1","key2":"val2"}'))
                    ->build(),
                NarratorObjectBuilder::init()
                    ->name('name0')
                    ->additionalProperty('exampleAdditionalProperty', ApiHelper::deserialize('{"key1":"val1","key2":"val2"}'))
                    ->build()
            ],
            'publisher4',
            Type9::AUDIOBOOK,
            'uri2',
            186,
            PagingSimplifiedChapterObjectBuilder::init(
                'href4',
                230,
                122,
                136,
                [
                    ChapterBaseBuilder::init(
                        164,
                        'description2',
                        'html_description2',
                        52,
                        false,
                        ExternalUrlObjectBuilder::init()
                            ->spotify('spotify6')
                            ->additionalProperty('exampleAdditionalProperty', ApiHelper::deserialize('{"key1":"val1","key2":"val2"}'))
                            ->build(),
                        'href0',
                        'id8',
                        [
                            ImageObjectBuilder::init(
                                'url6'
                            )
                                ->height(182)
                                ->width(222)
                                ->additionalProperty('exampleAdditionalProperty', ApiHelper::deserialize('{"key1":"val1","key2":"val2"}'))
                                ->build(),
                            ImageObjectBuilder::init(
                                'url6'
                            )
                                ->height(182)
                                ->width(222)
                                ->additionalProperty('exampleAdditionalProperty', ApiHelper::deserialize('{"key1":"val1","key2":"val2"}'))
                                ->build()
                        ],
                        false,
                        [
                            'languages5'
                        ],
                        'name8',
                        'release_date6',
                        ReleaseDatePrecision::MONTH,
                        Type5::EPISODE,
                        'uri2'
                    )
                        ->audioPreviewUrl('audio_preview_url4')
                        ->availableMarkets(
                            [
                                'available_markets2'
                            ]
                        )
                        ->resumePoint(
                            ResumePointObjectBuilder::init()
                                ->fullyPlayed(false)
                                ->resumePositionMs(254)
                                ->additionalProperty('exampleAdditionalProperty', ApiHelper::deserialize('{"key1":"val1","key2":"val2"}'))
                                ->build()
                        )
                        ->restrictions(
                            ChapterRestrictionObjectBuilder::init()
                                ->reason('reason0')
                                ->additionalProperty('exampleAdditionalProperty', ApiHelper::deserialize('{"key1":"val1","key2":"val2"}'))
                                ->build()
                        )
                        ->additionalProperty('exampleAdditionalProperty', ApiHelper::deserialize('{"key1":"val1","key2":"val2"}'))
                        ->build()
                ]
            )
                ->next('next0')
                ->previous('previous0')
                ->additionalProperty('exampleAdditionalProperty', ApiHelper::deserialize('{"key1":"val1","key2":"val2"}'))
                ->build()
        )
            ->edition('edition8')
            ->additionalProperty('exampleAdditionalProperty', ApiHelper::deserialize('{"key1":"val1","key2":"val2"}'))
            ->build()
    )
    ->additionalProperty('exampleAdditionalProperty', ApiHelper::deserialize('{"key1":"val1","key2":"val2"}'))
    ->build();
```

