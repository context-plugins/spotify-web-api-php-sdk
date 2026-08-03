
# Paging Simplified Episode Object

*This model accepts additional fields of type array.*

## Structure

`PagingSimplifiedEpisodeObject`

## Fields

| Name | Type | Tags | Description | Getter | Setter |
|  --- | --- | --- | --- | --- | --- |
| `href` | `string` | Required | A link to the Web API endpoint returning the full result of the request | getHref(): string | setHref(string href): void |
| `limit` | `int` | Required | The maximum number of items in the response (as set in the query or by default). | getLimit(): int | setLimit(int limit): void |
| `next` | `?string` | Required | URL to the next page of items. ( `null` if none) | getNext(): ?string | setNext(?string next): void |
| `offset` | `int` | Required | The offset of the items returned (as set in the query or by default) | getOffset(): int | setOffset(int offset): void |
| `previous` | `?string` | Required | URL to the previous page of items. ( `null` if none) | getPrevious(): ?string | setPrevious(?string previous): void |
| `total` | `int` | Required | The total number of items available to return. | getTotal(): int | setTotal(int total): void |
| `items` | [`EpisodeBase[]`](../../doc/models/episode-base.md) | Required | - | getItems(): array | setItems(array items): void |
| `additionalProperties` | `array<string, array>` | Optional | - | findAdditionalProperty(string key): array | additionalProperty(string key, array value): void |

## Example

```php
use SpotifyWebApiLib\Models\Builders\PagingSimplifiedEpisodeObjectBuilder;
use SpotifyWebApiLib\Models\Builders\EpisodeBaseBuilder;
use SpotifyWebApiLib\Models\Builders\ExternalUrlObjectBuilder;
use SpotifyWebApiLib\ApiHelper;
use SpotifyWebApiLib\Models\Builders\ImageObjectBuilder;
use SpotifyWebApiLib\Models\ReleaseDatePrecision;
use SpotifyWebApiLib\Models\Type5;
use SpotifyWebApiLib\Models\Builders\ResumePointObjectBuilder;
use SpotifyWebApiLib\Models\Builders\TrackRestrictionObjectBuilder;

$pagingSimplifiedEpisodeObject = PagingSimplifiedEpisodeObjectBuilder::init(
    'https://api.spotify.com/v1/me/shows?offset=0&limit=20
',
    20,
    0,
    4,
    [
        EpisodeBaseBuilder::init(
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
            ReleaseDatePrecision::MONTH,
            Type5::EPISODE,
            'spotify:episode:0zLhl3WsOCQHbe1BPTiHgr'
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
    ->next('https://api.spotify.com/v1/me/shows?offset=1&limit=1')
    ->previous('https://api.spotify.com/v1/me/shows?offset=1&limit=1')
    ->additionalProperty('exampleAdditionalProperty', ApiHelper::deserialize('{"key1":"val1","key2":"val2"}'))
    ->build();
```

