
# Many Episodes

*This model accepts additional fields of type array.*

## Structure

`ManyEpisodes`

## Fields

| Name | Type | Tags | Description | Getter | Setter |
|  --- | --- | --- | --- | --- | --- |
| `episodes` | [`EpisodeObject[]`](../../doc/models/episode-object.md) | Required | - | getEpisodes(): array | setEpisodes(array episodes): void |
| `additionalProperties` | `array<string, array>` | Optional | - | findAdditionalProperty(string key): array | additionalProperty(string key, array value): void |

## Example

```php
use SpotifyWebApiLib\Models\Builders\ManyEpisodesBuilder;
use SpotifyWebApiLib\Models\Builders\EpisodeObjectBuilder;
use SpotifyWebApiLib\Models\Builders\ExternalUrlObjectBuilder;
use SpotifyWebApiLib\ApiHelper;
use SpotifyWebApiLib\Models\Builders\ImageObjectBuilder;
use SpotifyWebApiLib\Models\ReleaseDatePrecision;
use SpotifyWebApiLib\Models\Type5;
use SpotifyWebApiLib\Models\Builders\ShowBaseBuilder;
use SpotifyWebApiLib\Models\Builders\CopyrightObjectBuilder;
use SpotifyWebApiLib\Models\Type6;
use SpotifyWebApiLib\Models\Builders\ResumePointObjectBuilder;
use SpotifyWebApiLib\Models\Builders\TrackRestrictionObjectBuilder;

$manyEpisodes = ManyEpisodesBuilder::init(
    [
        EpisodeObjectBuilder::init(
            'A Spotify podcast sharing fresh insights on important topics of the moment—in a way only Spotify can. You’ll hear from experts in the music, podcast and tech industries as we discover and uncover stories about our work and the world around us.
',
            '<p>A Spotify podcast sharing fresh insights on important topics of the moment—in a way only Spotify can. You’ll hear from experts in the music, podcast and tech industries as we discover and uncover stories about our work and the world around us.</p>
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
            false,
            [
                'fr',
                'en'
            ],
            'Starting Your Own Podcast: Tips, Tricks, and Advice From Anchor Creators
',
            '1981-12-15',
            ReleaseDatePrecision::DAY,
            Type5::EPISODE,
            'spotify:episode:0zLhl3WsOCQHbe1BPTiHgr',
            ShowBaseBuilder::init(
                [
                    'available_markets0',
                    'available_markets1',
                    'available_markets2'
                ],
                [
                    CopyrightObjectBuilder::init()
                        ->text('text2')
                        ->type('type2')
                        ->additionalProperty('exampleAdditionalProperty', ApiHelper::deserialize('{"key1":"val1","key2":"val2"}'))
                        ->build()
                ],
                'description4',
                'html_description4',
                false,
                ExternalUrlObjectBuilder::init()
                    ->spotify('spotify6')
                    ->additionalProperty('exampleAdditionalProperty', ApiHelper::deserialize('{"key1":"val1","key2":"val2"}'))
                    ->build(),
                'href8',
                'id6',
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
                    'languages7',
                    'languages6',
                    'languages5'
                ],
                'media_type6',
                'name6',
                'publisher6',
                Type6::SHOW,
                'uri0',
                198
            )
                ->additionalProperty('exampleAdditionalProperty', ApiHelper::deserialize('{"key1":"val1","key2":"val2"}'))
                ->build()
        )
            ->audioPreviewUrl('https://p.scdn.co/mp3-preview/2f37da1d4221f40b9d1a98cd191f4d6f1646ad17')
            ->language('en')
            ->resumePoint(
                ResumePointObjectBuilder::init()
                    ->fullyPlayed(false)
                    ->resumePositionMs(254)
                    ->additionalProperty('exampleAdditionalProperty', ApiHelper::deserialize('{"key1":"val1","key2":"val2"}'))
                    ->build()
            )
            ->restrictions(
                TrackRestrictionObjectBuilder::init()
                    ->reason('reason0')
                    ->additionalProperty('exampleAdditionalProperty', ApiHelper::deserialize('{"key1":"val1","key2":"val2"}'))
                    ->build()
            )
            ->additionalProperty('exampleAdditionalProperty', ApiHelper::deserialize('{"key1":"val1","key2":"val2"}'))
            ->build()
    ]
)
    ->additionalProperty('exampleAdditionalProperty', ApiHelper::deserialize('{"key1":"val1","key2":"val2"}'))
    ->build();
```

