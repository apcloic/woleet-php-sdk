# WooletClient\ReceiptApi

All URIs are relative to *https://api.woleet.io/v1*

Method | HTTP request | Description
------------- | ------------- | -------------
[**getOTSReceipt**](ReceiptApi.md#getotsreceipt) | **GET** /receipt/{anchorId}/ots | Get the proof receipt of an anchor (OpenTimestamps proof format).
[**getReceipt**](ReceiptApi.md#getreceipt) | **GET** /receipt/{anchorId} | Get the proof receipt of an anchor.
[**verifyReceipt**](ReceiptApi.md#verifyreceipt) | **POST** /receipt/verify | Verify a proof receipt.

# **getOTSReceipt**
> \WooletClient\Model\OtsReceipt getOTSReceipt($anchor_id)

Get the proof receipt of an anchor (OpenTimestamps proof format).

Use this operation to retrieve the OpenTimestamps proof receipt associated to a given data anchor (note that this operation is NOT available for signature anchors).<br> This binary file is only available once the anchor status is SENT.<br> This is a publicly accessible endpoint: authentication is not required to retrieve a proof receipt (but the anchor identifier need to be known).

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

$apiInstance = new WooletClient\API\ReceiptApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$anchor_id = "anchor_id_example"; // string | Identifier of the data anchor for which to build the proof receipt.

try {
    $result = $apiInstance->getOTSReceipt($anchor_id);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling ReceiptApi->getOTSReceipt: ', $e->getMessage(), PHP_EOL;
}
?>
```

### Parameters

Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **anchor_id** | **string**| Identifier of the data anchor for which to build the proof receipt. |

### Return type

[**\WooletClient\Model\OtsReceipt**](../Model/OtsReceipt.md)

### Authorization

[BasicAuth](../../README.md#BasicAuth), [JWTAuth](../../README.md#JWTAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

# **getReceipt**
> \WooletClient\Model\Receipt getReceipt($anchor_id, $allow_partial)

Get the proof receipt of an anchor.

Use this operation to retrieve the proof receipt associated to a given anchor.<br> This JSON file is only available once the anchor status is SENT.<br> This is a publicly accessible endpoint: authentication is not required to retrieve a proof receipt (but the anchor identifier need to be known).

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

$apiInstance = new WooletClient\API\ReceiptApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$anchor_id = "anchor_id_example"; // string | Identifier of the anchor for which to build the proof receipt.
$allow_partial = true; // bool | `true` if a partial proof receipt is to be returned when the proof of timestamp is not yet available (ie. the data or the signature has not yet been anchored).<br> If the proof of timestamp is availalble (anchor is SENT or CONFIRMED) a regular proof receipt is returned (with response code 200). Otherwise, a partial proof receipt not including the proof of timestamp is returned (response code 202).<br> The partial proof receipt of a signature anchor allows to verify the signature and the identity of the signer immediatly after signing, without having to wait for the anchoring process to complete.

try {
    $result = $apiInstance->getReceipt($anchor_id, $allow_partial);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling ReceiptApi->getReceipt: ', $e->getMessage(), PHP_EOL;
}
?>
```

### Parameters

Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **anchor_id** | **string**| Identifier of the anchor for which to build the proof receipt. |
 **allow_partial** | **bool**| &#x60;true&#x60; if a partial proof receipt is to be returned when the proof of timestamp is not yet available (ie. the data or the signature has not yet been anchored).&lt;br&gt; If the proof of timestamp is availalble (anchor is SENT or CONFIRMED) a regular proof receipt is returned (with response code 200). Otherwise, a partial proof receipt not including the proof of timestamp is returned (response code 202).&lt;br&gt; The partial proof receipt of a signature anchor allows to verify the signature and the identity of the signer immediatly after signing, without having to wait for the anchoring process to complete. | [optional]

### Return type

[**\WooletClient\Model\Receipt**](../Model/Receipt.md)

### Authorization

[BasicAuth](../../README.md#BasicAuth), [JWTAuth](../../README.md#JWTAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

# **verifyReceipt**
> \WooletClient\Model\ReceiptVerificationStatus verifyReceipt($body)

Verify a proof receipt.

Use this operation to verify a proof receipt and get the timestamp of the proof.<br> For proof of signature receipts including an identity URL, this operation also verifies and returns information about the signer's identity.<br> This is a publicly accessible endpoint: authentication is not required to verify a proof receipt.

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

$apiInstance = new WooletClient\API\ReceiptApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$body = new \WooletClient\Model\Receipt(); // \WooletClient\Model\Receipt | Proof receipt to verify.

try {
    $result = $apiInstance->verifyReceipt($body);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling ReceiptApi->verifyReceipt: ', $e->getMessage(), PHP_EOL;
}
?>
```

### Parameters

Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **body** | [**\WooletClient\Model\Receipt**](../Model/Receipt.md)| Proof receipt to verify. |

### Return type

[**\WooletClient\Model\ReceiptVerificationStatus**](../Model/ReceiptVerificationStatus.md)

### Authorization

[BasicAuth](../../README.md#BasicAuth), [JWTAuth](../../README.md#JWTAuth)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

