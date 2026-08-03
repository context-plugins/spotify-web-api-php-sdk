
# Many Audiobooks

*This model accepts additional fields of type array.*

## Structure

`ManyAudiobooks`

## Fields

| Name | Type | Tags | Description | Getter | Setter |
|  --- | --- | --- | --- | --- | --- |
| `audiobooks` | [`AudiobookObject[]`](../../doc/models/audiobook-object.md) | Required | - | getAudiobooks(): array | setAudiobooks(array audiobooks): void |
| `additionalProperties` | `array<string, array>` | Optional | - | findAdditionalProperty(string key): array | additionalProperty(string key, array value): void |

## Example

```php
use SpotifyWebApiLib\Models\Builders\ManyAudiobooksBuilder;
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

$manyAudiobooks = ManyAudiobooksBuilder::init(
    [
        AudiobookObjectBuilder::init(
            [
                AuthorObjectBuilder::init()
                    ->name('name0')
                    ->additionalProperty('exampleAdditionalProperty', ApiHelper::deserialize('{"key1":"val1","key2":"val2"}'))
                    ->build()
            ],
            [
                'available_markets8'
            ],
            [
                CopyrightObjectBuilder::init()
                    ->text('text2')
                    ->type('type2')
                    ->additionalProperty('exampleAdditionalProperty', ApiHelper::deserialize('{"key1":"val1","key2":"val2"}'))
                    ->build()
            ],
            'description4',
            'html_description6',
            false,
            ExternalUrlObjectBuilder::init()
                ->spotify('spotify6')
                ->additionalProperty('exampleAdditionalProperty', ApiHelper::deserialize('{"key1":"val1","key2":"val2"}'))
                ->build(),
            'href6',
            'id4',
            [
                ImageObjectBuilder::init(
                    'https://i.scdn.co/image/ab67616d00001e02ff9ca10b55ce82ae553c8228
'
                )
                    ->height(300)
                    ->width(300)
                    ->additionalProperty('exampleAdditionalProperty', ApiHelper::deserialize('{"key1":"val1","key2":"val2"}'))
                    ->build()
            ],
            [
                'languages1'
            ],
            'media_type8',
            'name4',
            [
                NarratorObjectBuilder::init()
                    ->name('name0')
                    ->additionalProperty('exampleAdditionalProperty', ApiHelper::deserialize('{"key1":"val1","key2":"val2"}'))
                    ->build()
            ],
            'publisher8',
            Type9::AUDIOBOOK,
            'uri8',
            186,
            PagingSimplifiedChapterObjectBuilder::init(
                'https://api.spotify.com/v1/me/shows?offset=0&limit=20
',
                20,
                0,
                4,
                [
                    ChapterBaseBuilder::init(
                        1,
                        'We kept on ascending, with occasional periods of quick descent, but in the main always ascending. Suddenly, I became conscious of the fact that the driver was in the act of pulling up the horses in the courtyard of a vast ruined castle, from whose tall black windows came no ray of light, and whose broken battlements showed a jagged line against the moonlit sky.
',
                        '<p>We kept on ascending, with occasional periods of quick descent, but in the main always ascending. Suddenly, I became conscious of the fact that the driver was in the act of pulling up the horses in the courtyard of a vast ruined castle, from whose tall black windows came no ray of light, and whose broken battlements showed a jagged line against the moonlit sky.</p>
',
                        1686230,
                        false,
                        ExternalUrlObjectBuilder::init()
                            ->spotify('spotify6')
                            ->additionalProperty('exampleAdditionalProperty', ApiHelper::deserialize('{"key1":"val1","key2":"val2"}'))
                            ->build(),
                        'https://api.spotify.com/v1/episodes/5Xt5DXGzch68nYYamXrNxZ',
                        '5Xt5DXGzch68nYYamXrNxZ',
                        [
                            ImageObjectBuilder::init(
                                'https://i.scdn.co/image/ab67616d00001e02ff9ca10b55ce82ae553c8228
'
                            )
                                ->height(300)
                                ->width(300)
                                ->additionalProperty('exampleAdditionalProperty', ApiHelper::deserialize('{"key1":"val1","key2":"val2"}'))
                                ->build()
                        ],
                        false,
                        [
                            'fr',
                            'en'
                        ],
                        'Starting Your Own Podcast: Tips, Tricks, and Advice From Anchor Creators
',
                        '1981-12-15',
                        ReleaseDatePrecision::MONTH,
                        Type5::EPISODE,
                        'spotify:episode:0zLhl3WsOCQHbe1BPTiHgr'
                    )
                        ->audioPreviewUrl('https://p.scdn.co/mp3-preview/2f37da1d4221f40b9d1a98cd191f4d6f1646ad17')
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
                ->next('https://api.spotify.com/v1/me/shows?offset=1&limit=1')
                ->previous('https://api.spotify.com/v1/me/shows?offset=1&limit=1')
                ->additionalProperty('exampleAdditionalProperty', ApiHelper::deserialize('{"key1":"val1","key2":"val2"}'))
                ->build()
        )
            ->edition('Unabridged')
            ->additionalProperty('exampleAdditionalProperty', ApiHelper::deserialize('{"key1":"val1","key2":"val2"}'))
            ->build()
    ]
)
    ->additionalProperty('exampleAdditionalProperty', ApiHelper::deserialize('{"key1":"val1","key2":"val2"}'))
    ->build();
```

