
# Recommendation Seed Object

*This model accepts additional fields of type array.*

## Structure

`RecommendationSeedObject`

## Fields

| Name | Type | Tags | Description | Getter | Setter |
|  --- | --- | --- | --- | --- | --- |
| `afterFilteringSize` | `?int` | Optional | The number of tracks available after min\_\* and max\_\* filters have been applied. | getAfterFilteringSize(): ?int | setAfterFilteringSize(?int afterFilteringSize): void |
| `afterRelinkingSize` | `?int` | Optional | The number of tracks available after relinking for regional availability. | getAfterRelinkingSize(): ?int | setAfterRelinkingSize(?int afterRelinkingSize): void |
| `href` | `?string` | Optional | A link to the full track or artist data for this seed. For tracks this will be a link to a Track Object. For artists a link to an Artist Object. For genre seeds, this value will be `null`. | getHref(): ?string | setHref(?string href): void |
| `id` | `?string` | Optional | The id used to select this seed. This will be the same as the string used in the `seed_artists`, `seed_tracks` or `seed_genres` parameter. | getId(): ?string | setId(?string id): void |
| `initialPoolSize` | `?int` | Optional | The number of recommended tracks available for this seed. | getInitialPoolSize(): ?int | setInitialPoolSize(?int initialPoolSize): void |
| `type` | `?string` | Optional | The entity type of this seed. One of `artist`, `track` or `genre`. | getType(): ?string | setType(?string type): void |
| `additionalProperties` | `array<string, array>` | Optional | - | findAdditionalProperty(string key): array | additionalProperty(string key, array value): void |

## Example

```php
use SpotifyWebApiLib\Models\Builders\RecommendationSeedObjectBuilder;
use SpotifyWebApiLib\ApiHelper;

$recommendationSeedObject = RecommendationSeedObjectBuilder::init()
    ->afterFilteringSize(118)
    ->afterRelinkingSize(194)
    ->href('href0')
    ->id('id8')
    ->initialPoolSize(124)
    ->additionalProperty('exampleAdditionalProperty', ApiHelper::deserialize('{"key1":"val1","key2":"val2"}'))
    ->build();
```

