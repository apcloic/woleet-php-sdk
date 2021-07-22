# WooletClient\TokenApi

All URIs are relative to *https://api.woleet.io/v1*

Method | HTTP request | Description
------------- | ------------- | -------------
[**generateToken**](TokenApi.md#generatetoken) | **GET** /token | Generate a JWT token.
[**revokeToken**](TokenApi.md#revoketoken) | **DELETE** /token | Revoke a JWT token.

# **generateToken**
> \WooletClient\Model\Token generateToken($cdata)

Generate a JWT token.

Use this operation to generate a new JWT token.<br> JWT tokens can be used to authenticate to the API, using the `Bearer` scheme of the `Authorization` header, like:<br> `Authorization: Bearer {JWT token}`

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

$apiInstance = new WooletClient\API\TokenApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$cdata = "cdata_example"; // string | Client data to inject into the generated JWT token (64 characters max).<br> This data is not processed by the platform, and can be easily retrieved from the token by Base64 decoding its `payload`.

try {
    $result = $apiInstance->generateToken($cdata);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling TokenApi->generateToken: ', $e->getMessage(), PHP_EOL;
}
?>
```

### Parameters

Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **cdata** | **string**| Client data to inject into the generated JWT token (64 characters max).&lt;br&gt; This data is not processed by the platform, and can be easily retrieved from the token by Base64 decoding its &#x60;payload&#x60;. | [optional]

### Return type

[**\WooletClient\Model\Token**](../Model/Token.md)

### Authorization

[BasicAuth](../../README.md#BasicAuth), [JWTAuth](../../README.md#JWTAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

# **revokeToken**
> revokeToken($token)

Revoke a JWT token.

Use this operation to revoke a JWT token.<br> JWT tokens have no expiration date so are always valid: if you need to invalidate a token (eg. because you think it is compromised) you need to use this endpoint to inform the platform that this token must no longer be accepted.

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

$apiInstance = new WooletClient\API\TokenApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$token = "token_example"; // string | JWT token to revoke.

try {
    $apiInstance->revokeToken($token);
} catch (Exception $e) {
    echo 'Exception when calling TokenApi->revokeToken: ', $e->getMessage(), PHP_EOL;
}
?>
```

### Parameters

Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **token** | **string**| JWT token to revoke. |

### Return type

void (empty response body)

### Authorization

[BasicAuth](../../README.md#BasicAuth), [JWTAuth](../../README.md#JWTAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: Not defined

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

