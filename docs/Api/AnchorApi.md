# WooletClient\AnchorApi

All URIs are relative to *https://api.woleet.io/v1*

Method | HTTP request | Description
------------- | ------------- | -------------
[**createAnchor**](AnchorApi.md#createanchor) | **POST** /anchor | Create a new anchor.
[**deleteAnchor**](AnchorApi.md#deleteanchor) | **DELETE** /anchor/{anchorId} | Delete an anchor.
[**getAnchor**](AnchorApi.md#getanchor) | **GET** /anchor/{anchorId} | Get an anchor by its identifier.
[**getAnchorAttestation**](AnchorApi.md#getanchorattestation) | **GET** /anchor/{anchorId}/attestation | Download the Proof Attestation document of an anchor.
[**searchAnchorIds**](AnchorApi.md#searchanchorids) | **GET** /anchorIds | Search for public anchor identifiers.
[**searchAnchors**](AnchorApi.md#searchanchors) | **GET** /anchors | Search for anchors.
[**updateAnchor**](AnchorApi.md#updateanchor) | **PUT** /anchor/{anchorId} | Update an anchor.

# **createAnchor**
> \WooletClient\Model\Anchor createAnchor($body)

Create a new anchor.

Use this operation to create a new anchor of one of these two types:<br> - a data anchor (generating a proof of existence receipt) allows to prove the existence of some data at some point in time.<br> - a signature anchor (generating a proof of signature receipt) allows to prove the existence of the signature of some data at some point in time, the validity of the signature and the signer's identity.<br> The properties `id`, `created`, `lastModified`, `status`, `timestamp` and `confirmations` are read-only and so must not be provided: they are managed by the platform and added to the returned anchor.<br> For data anchors, only the properties `name` and `hash` are required: the `hash` property must be the SHA256 hash of the data to anchor, and must be computed caller side. This allows not to leak the original data.<br> For signature anchors, only the properties `name`, `signedHash`, `signature` and `pubKey` are required (though the `identityURL` property is highly recommended).<br> Be sure to have at least 1 anchoring credit on your account.

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

$apiInstance = new WooletClient\API\AnchorApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$body = new \WooletClient\Model\Anchor(); // \WooletClient\Model\Anchor | Anchor object to create.

try {
    $result = $apiInstance->createAnchor($body);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling AnchorApi->createAnchor: ', $e->getMessage(), PHP_EOL;
}
?>
```

### Parameters

Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **body** | [**\WooletClient\Model\Anchor**](../Model/Anchor.md)| Anchor object to create. |

### Return type

[**\WooletClient\Model\Anchor**](../Model/Anchor.md)

### Authorization

[BasicAuth](../../README.md#BasicAuth), [JWTAuth](../../README.md#JWTAuth)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

# **deleteAnchor**
> deleteAnchor($anchor_id)

Delete an anchor.

Use this operation to delete an anchor.<br> **WARNING: You should never delete an anchor, otherwise you will no longer be able to download its proof receipt.<br> Use this for test purpose only.**

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

$apiInstance = new WooletClient\API\AnchorApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$anchor_id = "anchor_id_example"; // string | Identifier of the anchor to delete.

try {
    $apiInstance->deleteAnchor($anchor_id);
} catch (Exception $e) {
    echo 'Exception when calling AnchorApi->deleteAnchor: ', $e->getMessage(), PHP_EOL;
}
?>
```

### Parameters

Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **anchor_id** | **string**| Identifier of the anchor to delete. |

### Return type

void (empty response body)

### Authorization

[BasicAuth](../../README.md#BasicAuth), [JWTAuth](../../README.md#JWTAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: Not defined

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

# **getAnchor**
> \WooletClient\Model\Anchor getAnchor($anchor_id)

Get an anchor by its identifier.

Use this operation to retrieve an anchor by its identifier.

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

$apiInstance = new WooletClient\API\AnchorApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$anchor_id = "anchor_id_example"; // string | Identifier of the anchor to retrieve.

try {
    $result = $apiInstance->getAnchor($anchor_id);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling AnchorApi->getAnchor: ', $e->getMessage(), PHP_EOL;
}
?>
```

### Parameters

Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **anchor_id** | **string**| Identifier of the anchor to retrieve. |

### Return type

[**\WooletClient\Model\Anchor**](../Model/Anchor.md)

### Authorization

[BasicAuth](../../README.md#BasicAuth), [JWTAuth](../../README.md#JWTAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

# **getAnchorAttestation**
> \WooletClient\Model\PdfFile getAnchorAttestation($anchor_id)

Download the Proof Attestation document of an anchor.

Use this operation to retrieve the Proof Attestation document of an anchor.<br> This PDF file is only available once the anchor is CONFIRMED.

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

$apiInstance = new WooletClient\API\AnchorApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$anchor_id = "anchor_id_example"; // string | Identifier of the anchor.

try {
    $result = $apiInstance->getAnchorAttestation($anchor_id);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling AnchorApi->getAnchorAttestation: ', $e->getMessage(), PHP_EOL;
}
?>
```

### Parameters

Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **anchor_id** | **string**| Identifier of the anchor. |

### Return type

[**\WooletClient\Model\PdfFile**](../Model/PdfFile.md)

### Authorization

[BasicAuth](../../README.md#BasicAuth), [JWTAuth](../../README.md#JWTAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

# **searchAnchorIds**
> \WooletClient\Model\AnchorIds searchAnchorIds($page, $size, $hash, $signed_hash)

Search for public anchor identifiers.

Use this operation to retrieve the identifiers of all public anchors having a given `hash` and/or `signedHash` property.<br> Only public anchor identifiers are returned.<br> This is a publicly accessible endpoint: authentication is not required to retrieve public anchor identifiers.<br> Paging is supported.

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

$apiInstance = new WooletClient\API\AnchorApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$page = 0; // int | Index of the page to retrieve (from 0).
$size = 20; // int | Number of anchor identifiers per page.
$hash = "hash_example"; // string | `hash` to search for: all public anchors whose `hash` property is equal are returned.
$signed_hash = "signed_hash_example"; // string | `signedHash` to search for: all public anchors whose `signedHash` property is equal are returned.

try {
    $result = $apiInstance->searchAnchorIds($page, $size, $hash, $signed_hash);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling AnchorApi->searchAnchorIds: ', $e->getMessage(), PHP_EOL;
}
?>
```

### Parameters

Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **page** | **int**| Index of the page to retrieve (from 0). | [optional] [default to 0]
 **size** | **int**| Number of anchor identifiers per page. | [optional] [default to 20]
 **hash** | **string**| &#x60;hash&#x60; to search for: all public anchors whose &#x60;hash&#x60; property is equal are returned. | [optional]
 **signed_hash** | **string**| &#x60;signedHash&#x60; to search for: all public anchors whose &#x60;signedHash&#x60; property is equal are returned. | [optional]

### Return type

[**\WooletClient\Model\AnchorIds**](../Model/AnchorIds.md)

### Authorization

[BasicAuth](../../README.md#BasicAuth), [JWTAuth](../../README.md#JWTAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

# **searchAnchors**
> \WooletClient\Model\Anchors searchAnchors($page, $size, $direction, $sort, $name, $hash, $signed_hash, $tags)

Search for anchors.

Use this operation to retrieve all anchors having a given `name`, `hash`, `signedHash` and/or `tags` property.<br> Only anchors belonging to the authenticated user are returned.<br> Paging and sorting is supported.

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

$apiInstance = new WooletClient\API\AnchorApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$page = 0; // int | Index of the page to retrieve (from 0).
$size = 20; // int | Number of anchors per page.
$direction = "ASC"; // string | Sorting direction: ASC for ascending DESC for descending.
$sort = "created"; // string | Sorting property: possible values are limited to `created`, `hash` and `signedHash`.
$name = "name_example"; // string | `name` to search for: all anchors whose `name` property contains this sub-string are returned.<br> **WARNING: Searching by name can timeout on a large anchor set.**
$hash = "hash_example"; // string | `hash` to search for: all anchors whose `hash` property is equal are returned.
$signed_hash = "signed_hash_example"; // string | `signedHash` to search for: all anchors whose `signedHash` property is equal are returned.
$tags = array("tags_example"); // string[] | Tags to search for: all anchors having all of these tags sets are returned.

try {
    $result = $apiInstance->searchAnchors($page, $size, $direction, $sort, $name, $hash, $signed_hash, $tags);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling AnchorApi->searchAnchors: ', $e->getMessage(), PHP_EOL;
}
?>
```

### Parameters

Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **page** | **int**| Index of the page to retrieve (from 0). | [optional] [default to 0]
 **size** | **int**| Number of anchors per page. | [optional] [default to 20]
 **direction** | **string**| Sorting direction: ASC for ascending DESC for descending. | [optional] [default to ASC]
 **sort** | **string**| Sorting property: possible values are limited to &#x60;created&#x60;, &#x60;hash&#x60; and &#x60;signedHash&#x60;. | [optional] [default to created]
 **name** | **string**| &#x60;name&#x60; to search for: all anchors whose &#x60;name&#x60; property contains this sub-string are returned.&lt;br&gt; **WARNING: Searching by name can timeout on a large anchor set.** | [optional]
 **hash** | **string**| &#x60;hash&#x60; to search for: all anchors whose &#x60;hash&#x60; property is equal are returned. | [optional]
 **signed_hash** | **string**| &#x60;signedHash&#x60; to search for: all anchors whose &#x60;signedHash&#x60; property is equal are returned. | [optional]
 **tags** | [**string[]**](../Model/string.md)| Tags to search for: all anchors having all of these tags sets are returned. | [optional]

### Return type

[**\WooletClient\Model\Anchors**](../Model/Anchors.md)

### Authorization

[BasicAuth](../../README.md#BasicAuth), [JWTAuth](../../README.md#JWTAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

# **updateAnchor**
> \WooletClient\Model\Anchor updateAnchor($body, $anchor_id)

Update an anchor.

Use this operation to update an anchor.<br> Only the properties `name`, `public`, `tags`, `metadata` and `callbackURL` can be modified.

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

$apiInstance = new WooletClient\API\AnchorApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$body = new \WooletClient\Model\Anchor(); // \WooletClient\Model\Anchor | Anchor object to update.
$anchor_id = "anchor_id_example"; // string | Identifier of anchor to update.

try {
    $result = $apiInstance->updateAnchor($body, $anchor_id);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling AnchorApi->updateAnchor: ', $e->getMessage(), PHP_EOL;
}
?>
```

### Parameters

Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **body** | [**\WooletClient\Model\Anchor**](../Model/Anchor.md)| Anchor object to update. |
 **anchor_id** | **string**| Identifier of anchor to update. |

### Return type

[**\WooletClient\Model\Anchor**](../Model/Anchor.md)

### Authorization

[BasicAuth](../../README.md#BasicAuth), [JWTAuth](../../README.md#JWTAuth)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

