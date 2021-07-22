# WooletClient\DomainApi

All URIs are relative to *https://api.woleet.io/v1*

Method | HTTP request | Description
------------- | ------------- | -------------
[**createDomainUser**](DomainApi.md#createdomainuser) | **POST** /domain/admin/user | Create a new domain user.
[**deleteDomainUser**](DomainApi.md#deletedomainuser) | **DELETE** /domain/admin/user/{userId} | Delete a domain user.
[**getDomainUser**](DomainApi.md#getdomainuser) | **GET** /domain/admin/user/{userId} | Get a domain user by its identifier.
[**searchDomainUsers**](DomainApi.md#searchdomainusers) | **GET** /domain/admin/users | Search for domain users.
[**updateDomainUser**](DomainApi.md#updatedomainuser) | **PUT** /domain/admin/user/{userId} | Update a domain user.

# **createDomainUser**
> \WooletClient\Model\User createDomainUser($body)

Create a new domain user.

Use this operation to create a new domain user.<br> The properties `id`, `created`, `lastModified`, `info` and `status` are read-only and so must not be provided: they are managed by the platform and added to the returned user.

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

$apiInstance = new WooletClient\API\DomainApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$body = new \WooletClient\Model\User(); // \WooletClient\Model\User | User object to create (password must be provided).

try {
    $result = $apiInstance->createDomainUser($body);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling DomainApi->createDomainUser: ', $e->getMessage(), PHP_EOL;
}
?>
```

### Parameters

Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **body** | [**\WooletClient\Model\User**](../Model/User.md)| User object to create (password must be provided). |

### Return type

[**\WooletClient\Model\User**](../Model/User.md)

### Authorization

[BasicAuth](../../README.md#BasicAuth), [JWTAuth](../../README.md#JWTAuth)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

# **deleteDomainUser**
> deleteDomainUser($user_id)

Delete a domain user.

Use this operation to delete a domain user.

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

$apiInstance = new WooletClient\API\DomainApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$user_id = "user_id_example"; // string | Identifier of the domain user to delete.

try {
    $apiInstance->deleteDomainUser($user_id);
} catch (Exception $e) {
    echo 'Exception when calling DomainApi->deleteDomainUser: ', $e->getMessage(), PHP_EOL;
}
?>
```

### Parameters

Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **user_id** | **string**| Identifier of the domain user to delete. |

### Return type

void (empty response body)

### Authorization

[BasicAuth](../../README.md#BasicAuth), [JWTAuth](../../README.md#JWTAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: Not defined

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

# **getDomainUser**
> \WooletClient\Model\User getDomainUser($user_id)

Get a domain user by its identifier.

Use this operation to retrieve a domain user by its identifier.

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

$apiInstance = new WooletClient\API\DomainApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$user_id = "user_id_example"; // string | Identifier of the domain user to retrieve.

try {
    $result = $apiInstance->getDomainUser($user_id);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling DomainApi->getDomainUser: ', $e->getMessage(), PHP_EOL;
}
?>
```

### Parameters

Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **user_id** | **string**| Identifier of the domain user to retrieve. |

### Return type

[**\WooletClient\Model\User**](../Model/User.md)

### Authorization

[BasicAuth](../../README.md#BasicAuth), [JWTAuth](../../README.md#JWTAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

# **searchDomainUsers**
> \WooletClient\Model\Users searchDomainUsers($page, $size, $direction, $sort, $email)

Search for domain users.

Use this operation to list all domain users or search for domain users given their email.<br> Paging and sorting is supported.

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

$apiInstance = new WooletClient\API\DomainApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$page = 0; // int | Index of the page to retrieve (from 0).
$size = 20; // int | Number of users per page.
$direction = "ASC"; // string | Sorting direction: ASC for ascending DESC for descending.
$sort = "created"; // string | Sorting property: possible values are `email`, `created`, `roles`, `info.firstName`, `info.lastName`, `status`.
$email = "email_example"; // string | `email` to search for: a sub-string of the email.

try {
    $result = $apiInstance->searchDomainUsers($page, $size, $direction, $sort, $email);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling DomainApi->searchDomainUsers: ', $e->getMessage(), PHP_EOL;
}
?>
```

### Parameters

Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **page** | **int**| Index of the page to retrieve (from 0). | [optional] [default to 0]
 **size** | **int**| Number of users per page. | [optional] [default to 20]
 **direction** | **string**| Sorting direction: ASC for ascending DESC for descending. | [optional] [default to ASC]
 **sort** | **string**| Sorting property: possible values are &#x60;email&#x60;, &#x60;created&#x60;, &#x60;roles&#x60;, &#x60;info.firstName&#x60;, &#x60;info.lastName&#x60;, &#x60;status&#x60;. | [optional] [default to created]
 **email** | **string**| &#x60;email&#x60; to search for: a sub-string of the email. | [optional]

### Return type

[**\WooletClient\Model\Users**](../Model/Users.md)

### Authorization

[BasicAuth](../../README.md#BasicAuth), [JWTAuth](../../README.md#JWTAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

# **updateDomainUser**
> \WooletClient\Model\User updateDomainUser($body, $user_id)

Update a domain user.

Use this operation to update a domain user.

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

$apiInstance = new WooletClient\API\DomainApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$body = new \WooletClient\Model\User(); // \WooletClient\Model\User | User object to update.
$user_id = "user_id_example"; // string | Identifier of the domain user to update.

try {
    $result = $apiInstance->updateDomainUser($body, $user_id);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling DomainApi->updateDomainUser: ', $e->getMessage(), PHP_EOL;
}
?>
```

### Parameters

Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **body** | [**\WooletClient\Model\User**](../Model/User.md)| User object to update. |
 **user_id** | **string**| Identifier of the domain user to update. |

### Return type

[**\WooletClient\Model\User**](../Model/User.md)

### Authorization

[BasicAuth](../../README.md#BasicAuth), [JWTAuth](../../README.md#JWTAuth)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

