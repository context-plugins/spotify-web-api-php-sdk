
# Client Class Documentation

The following parameters are configurable for the API Client:

| Parameter | Type | Description |
|  --- | --- | --- |
| environment | [`Environment`](../README.md#environments) | The API environment. <br> **Default: `Environment.PRODUCTION`** |
| timeout | `int` | Timeout for API calls in seconds.<br>*Default*: `30` |
| enableRetries | `bool` | Whether to enable retries and backoff feature.<br>*Default*: `false` |
| numberOfRetries | `int` | The number of retries to make.<br>*Default*: `0` |
| retryInterval | `float` | The retry time interval between the endpoint calls.<br>*Default*: `1` |
| backOffFactor | `float` | Exponential backoff factor to increase interval between retries.<br>*Default*: `2` |
| maximumRetryWaitTime | `int` | The maximum wait time in seconds for overall retrying requests.<br>*Default*: `0` |
| retryOnTimeout | `bool` | Whether to retry on request timeout.<br>*Default*: `true` |
| httpStatusCodesToRetry | `array` | Http status codes to retry against.<br>*Default*: `408, 413, 429, 500, 502, 503, 504, 521, 522, 524, 408, 413, 429, 500, 502, 503, 504, 521, 522, 524` |
| httpMethodsToRetry | `array` | Http methods to retry against.<br>*Default*: `'GET', 'PUT', 'GET', 'PUT'` |
| loggingConfiguration | [`LoggingConfigurationBuilder`](../doc/logging-configuration-builder.md) | Represents the logging configurations for API calls |
| proxyConfiguration | [`ProxyConfigurationBuilder`](../doc/proxy-configuration-builder.md) | Represents the proxy configurations for API calls |
| authorizationCodeAuth | [`AuthorizationCodeAuth`](auth/oauth-2-authorization-code-grant.md) | The Credentials Setter for OAuth 2 Authorization Code Grant |

The API client can be initialized as follows:

```php
use SpotifyWebApiLib\Logging\LoggingConfigurationBuilder;
use SpotifyWebApiLib\Logging\RequestLoggingConfigurationBuilder;
use SpotifyWebApiLib\Logging\ResponseLoggingConfigurationBuilder;
use Psr\Log\LogLevel;
use SpotifyWebApiLib\Environment;
use SpotifyWebApiLib\Authentication\AuthorizationCodeAuthCredentialsBuilder;
use SpotifyWebApiLib\Models\OauthScope;
use SpotifyWebApiLib\SpotifyWebApiClientBuilder;

$client = SpotifyWebApiClientBuilder::init()
    ->authorizationCodeAuthCredentials(
        AuthorizationCodeAuthCredentialsBuilder::init(
            'OAuthClientId',
            'OAuthClientSecret',
            'OAuthRedirectUri'
        )
            ->oauthScopes(
                [
                    OauthScope::APP_REMOTE_CONTROL,
                    OauthScope::PLAYLIST_READ_PRIVATE
                ]
            )
    )
    ->environment(Environment::PRODUCTION)
    ->loggingConfiguration(
        LoggingConfigurationBuilder::init()
            ->level(LogLevel::INFO)
            ->requestConfiguration(RequestLoggingConfigurationBuilder::init()->body(true))
            ->responseConfiguration(ResponseLoggingConfigurationBuilder::init()->headers(true))
    )
    ->build();
```

## Spotify Web API Client

The gateway for the SDK. This class acts as a factory for the Apis and also holds the configuration of the SDK.

## Apis

| Name | Description |
|  --- | --- |
| getAlbumsApi() | Gets AlbumsApi |
| getArtistsApi() | Gets ArtistsApi |
| getAudiobooksApi() | Gets AudiobooksApi |
| getCategoriesApi() | Gets CategoriesApi |
| getChaptersApi() | Gets ChaptersApi |
| getEpisodesApi() | Gets EpisodesApi |
| getGenresApi() | Gets GenresApi |
| getMarketsApi() | Gets MarketsApi |
| getPlayerApi() | Gets PlayerApi |
| getPlaylistsApi() | Gets PlaylistsApi |
| getSearchApi() | Gets SearchApi |
| getShowsApi() | Gets ShowsApi |
| getTracksApi() | Gets TracksApi |
| getUsersApi() | Gets UsersApi |
| getOauthAuthorizationApi() | Gets OauthAuthorizationApi |

