# WooletClient\UserApi

All URIs are relative to *https://api.woleet.io/v1*

Method | HTTP request | Description
------------- | ------------- | -------------
[**getCallbackSecret**](UserApi.md#getcallbacksecret) | **GET** /user/callbackSecret | Get the current callback secret (null if not set).
[**getCredits**](UserApi.md#getcredits) | **GET** /user/credits | Get user&#x27;s credits.
[**getTokens**](UserApi.md#gettokens) | **GET** /user/tokens | Get user&#x27;s registered JWT tokens.
[**putTokens**](UserApi.md#puttokens) | **PUT** /user/tokens | Update user&#x27;s registered JWT tokens.
[**updateCallbackSecret**](UserApi.md#updatecallbacksecret) | **PUT** /user/callbackSecret | Generates a new callback secret.

# **getCallbackSecret**
> \WooletClient\Model\CallbackSecret getCallbackSecret()

Get the current callback secret (null if not set).

Use this operation to get the API callback secret.

### Example
```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');
// Configure HTTP basic authorization: BasicAuth
$config = WooletClient\Configuration::getDefaultConfiguration()
              ->setUsername('YOUR_USERNAME')
              ->setPassword('YOUR_PASSWORD');
// Configure API key authorization: JWTAuth
$config = WooletClient\Configuration::getDefaultConfiguration()->setApiKey('Authorization', 'YOUR_API_KEY');
// Uncomment below to setup prefix (e.g. Bearer) for API key, if needed
// $config = WooletClient\Configuration::getDefaultConfiguration()->setApiKeyPrefix('Authorization', 'Bearer');

$apiInstance = new WooletClient\API\UserApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);

try {
    $result = $apiInstance->getCallbackSecret();
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling UserApi->getCallbackSecret: ', $e->getMessage(), PHP_EOL;
}
?>
```

### Parameters
This endpoint does not need any parameter.

### Return type

[**\WooletClient\Model\CallbackSecret**](../Model/CallbackSecret.md)

### Authorization

[BasicAuth](../../README.md#BasicAuth), [JWTAuth](../../README.md#JWTAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

# **getCredits**
> \WooletClient\Model\Credits getCredits()

Get user's credits.

Use this operation to get the remaining signature and anchoring credits of the authenticated user.

### Example
```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');
// Configure HTTP basic authorization: BasicAuth
$config = WooletClient\Configuration::getDefaultConfiguration()
              ->setUsername('YOUR_USERNAME')
              ->setPassword('YOUR_PASSWORD');
// Configure API key authorization: JWTAuth
$config = WooletClient\Configuration::getDefaultConfiguration()->setApiKey('Authorization', 'YOUR_API_KEY');
// Uncomment below to setup prefix (e.g. Bearer) for API key, if needed
// $config = WooletClient\Configuration::getDefaultConfiguration()->setApiKeyPrefix('Authorization', 'Bearer');

$apiInstance = new WooletClient\API\UserApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);

try {
    $result = $apiInstance->getCredits();
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling UserApi->getCredits: ', $e->getMessage(), PHP_EOL;
}
?>
```

### Parameters
This endpoint does not need any parameter.

### Return type

[**\WooletClient\Model\Credits**](../Model/Credits.md)

### Authorization

[BasicAuth](../../README.md#BasicAuth), [JWTAuth](../../README.md#JWTAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

# **getTokens**
> \WooletClient\Model\Tokens getTokens()

Get user's registered JWT tokens.

Use this operation to list all JWT tokens registered for the authenticated user.

### Example
```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');
// Configure HTTP basic authorization: BasicAuth
$config = WooletClient\Configuration::getDefaultConfiguration()
              ->setUsername('YOUR_USERNAME')
              ->setPassword('YOUR_PASSWORD');
// Configure API key authorization: JWTAuth
$config = WooletClient\Configuration::getDefaultConfiguration()->setApiKey('Authorization', 'YOUR_API_KEY');
// Uncomment below to setup prefix (e.g. Bearer) for API key, if needed
// $config = WooletClient\Configuration::getDefaultConfiguration()->setApiKeyPrefix('Authorization', 'Bearer');

$apiInstance = new WooletClient\API\UserApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);

try {
    $result = $apiInstance->getTokens();
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling UserApi->getTokens: ', $e->getMessage(), PHP_EOL;
}
?>
```

### Parameters
This endpoint does not need any parameter.

### Return type

[**\WooletClient\Model\Tokens**](../Model/Tokens.md)

### Authorization

[BasicAuth](../../README.md#BasicAuth), [JWTAuth](../../README.md#JWTAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

# **putTokens**
> putTokens($body)

Update user's registered JWT tokens.

Use this operation to update the list of JWT tokens registered for the authenticated user.

### Example
```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');
// Configure HTTP basic authorization: BasicAuth
$config = WooletClient\Configuration::getDefaultConfiguration()
              ->setUsername('YOUR_USERNAME')
              ->setPassword('YOUR_PASSWORD');
// Configure API key authorization: JWTAuth
$config = WooletClient\Configuration::getDefaultConfiguration()->setApiKey('Authorization', 'YOUR_API_KEY');
// Uncomment below to setup prefix (e.g. Bearer) for API key, if needed
// $config = WooletClient\Configuration::getDefaultConfiguration()->setApiKeyPrefix('Authorization', 'Bearer');

$apiInstance = new WooletClient\API\UserApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$body = new \WooletClient\Model\Tokens(); // \WooletClient\Model\Tokens | The list of JWT tokens to update.

try {
    $apiInstance->putTokens($body);
} catch (Exception $e) {
    echo 'Exception when calling UserApi->putTokens: ', $e->getMessage(), PHP_EOL;
}
?>
```

### Parameters

Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **body** | [**\WooletClient\Model\Tokens**](../Model/Tokens.md)| The list of JWT tokens to update. |

### Return type

void (empty response body)

### Authorization

[BasicAuth](../../README.md#BasicAuth), [JWTAuth](../../README.md#JWTAuth)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: Not defined

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

# **updateCallbackSecret**
> \WooletClient\Model\CallbackSecret updateCallbackSecret()

Generates a new callback secret.

Use this operation to generate the API callback secret.

### Example
```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');
// Configure HTTP basic authorization: BasicAuth
$config = WooletClient\Configuration::getDefaultConfiguration()
              ->setUsername('YOUR_USERNAME')
              ->setPassword('YOUR_PASSWORD');
// Configure API key authorization: JWTAuth
$config = WooletClient\Configuration::getDefaultConfiguration()->setApiKey('Authorization', 'YOUR_API_KEY');
// Uncomment below to setup prefix (e.g. Bearer) for API key, if needed
// $config = WooletClient\Configuration::getDefaultConfiguration()->setApiKeyPrefix('Authorization', 'Bearer');

$apiInstance = new WooletClient\API\UserApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);

try {
    $result = $apiInstance->updateCallbackSecret();
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling UserApi->updateCallbackSecret: ', $e->getMessage(), PHP_EOL;
}
?>
```

### Parameters
This endpoint does not need any parameter.

### Return type

[**\WooletClient\Model\CallbackSecret**](../Model/CallbackSecret.md)

### Authorization

[BasicAuth](../../README.md#BasicAuth), [JWTAuth](../../README.md#JWTAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

