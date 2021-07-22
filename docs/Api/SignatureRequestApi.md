# WooletClient\SignatureRequestApi

All URIs are relative to *https://api.woleet.io/v1*

Method | HTTP request | Description
------------- | ------------- | -------------
[**createSignatureRequest**](SignatureRequestApi.md#createsignaturerequest) | **POST** /signatureRequest | Create a new signature request.
[**delegateSignatureRequest**](SignatureRequestApi.md#delegatesignaturerequest) | **POST** /signatureRequest/{requestId}/delegate | Sign a signature request by delegating the signature.
[**deleteSignatureRequest**](SignatureRequestApi.md#deletesignaturerequest) | **DELETE** /signatureRequest/{requestId} | Delete a signature request.
[**downloadSignatureRequestFile**](SignatureRequestApi.md#downloadsignaturerequestfile) | **GET** /signatureRequest/{requestId}/file | Download the file to sign.
[**getSignatureRequest**](SignatureRequestApi.md#getsignaturerequest) | **GET** /signatureRequest/{requestId} | Get a signature request by its identifier.
[**getSignatureRequestAttestation**](SignatureRequestApi.md#getsignaturerequestattestation) | **GET** /signatureRequest/{requestId}/attestation | Download the Signature Attestation document of a signature request.
[**getSignatureRequestProofBundle**](SignatureRequestApi.md#getsignaturerequestproofbundle) | **GET** /signatureRequest/{requestId}/proofbundle | Get the proof bundle of a signature request.
[**reportSignatureRequestEvent**](SignatureRequestApi.md#reportsignaturerequestevent) | **POST** /signatureRequest/{requestId}/event | Report an event on a signature request.
[**reportSignatureRequestFeedback**](SignatureRequestApi.md#reportsignaturerequestfeedback) | **POST** /signatureRequest/{requestId}/feedback | Report a feedback about a signature request.
[**searchSignatureRequestIds**](SignatureRequestApi.md#searchsignaturerequestids) | **GET** /signatureRequestIds | Search for public signature request identifiers.
[**searchSignatureRequests**](SignatureRequestApi.md#searchsignaturerequests) | **GET** /signatureRequests | Search for signature requests.
[**sendSignatureRequestOTP**](SignatureRequestApi.md#sendsignaturerequestotp) | **GET** /signatureRequest/{requestId}/otp/{signeeId} | Generate and send an OTP to a signer of a signature request.
[**sendSignatureRequestReminder**](SignatureRequestApi.md#sendsignaturerequestreminder) | **POST** /signatureRequest/{requestId}/remind | Send a reminder email to a set of signers of a signature request.
[**signSignatureRequest**](SignatureRequestApi.md#signsignaturerequest) | **POST** /signatureRequest/{requestId}/sign | Sign a signature request by registering a signature.
[**transitionSignatureRequest**](SignatureRequestApi.md#transitionsignaturerequest) | **POST** /signatureRequest/{requestId}/transition | Change the state of a signature request.
[**updateSignatureRequest**](SignatureRequestApi.md#updatesignaturerequest) | **PUT** /signatureRequest/{requestId} | Update a signature request.
[**uploadSignatureRequestFile**](SignatureRequestApi.md#uploadsignaturerequestfile) | **POST** /signatureRequest/{requestId}/file | Upload the file to sign.

# **createSignatureRequest**
> \WooletClient\Model\SignatureRequest createSignatureRequest($body)

Create a new signature request.

Use this operation to create a new signature request.<br> The properties `id`, `created` and `lastModified` are read-only and so must not be provided: they are managed by the platform and added to the returned request.<br> Only the properties `name` and `hashToSign` are required: the `hashToSign` property must be the SHA256 hash of the file to sign.<br> Be sure to have enough signature and anchoring credits on your account to fulfill the signature request (each registered signature costs you 1 signature and 1 anchoring credit).<br>

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

$apiInstance = new WooletClient\API\SignatureRequestApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$body = new \WooletClient\Model\SignatureRequest(); // \WooletClient\Model\SignatureRequest | SignatureRequest object to create.

try {
    $result = $apiInstance->createSignatureRequest($body);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling SignatureRequestApi->createSignatureRequest: ', $e->getMessage(), PHP_EOL;
}
?>
```

### Parameters

Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **body** | [**\WooletClient\Model\SignatureRequest**](../Model/SignatureRequest.md)| SignatureRequest object to create. |

### Return type

[**\WooletClient\Model\SignatureRequest**](../Model/SignatureRequest.md)

### Authorization

[BasicAuth](../../README.md#BasicAuth), [JWTAuth](../../README.md#JWTAuth)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

# **delegateSignatureRequest**
> \WooletClient\Model\SignatureRequestSignResult delegateSignatureRequest($body, $request_id)

Sign a signature request by delegating the signature.

A signer can use this operation to sign a signature request by delegating the signature to the platform.<br> When using this signature mode, the signature key of the signer is controled by the platform, which acts as a trusted third party.<br> The signature is automatically anchored on behalf of the owner of the signature request.<br> The signature anchor created is added to the list of signature anchors of the signature request.<br> This is a publicly accessible endpoint: authentication is not required to delegate a signature (authentication of the signer rely on the knowledge of his secret identifier and OTP, or on the control of his public key).

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

$apiInstance = new WooletClient\API\SignatureRequestApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$body = new \WooletClient\Model\SignatureRequestDelegate(); // \WooletClient\Model\SignatureRequestDelegate | Authentication information about the signer.
$request_id = "request_id_example"; // string | Identifier of the signature request.

try {
    $result = $apiInstance->delegateSignatureRequest($body, $request_id);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling SignatureRequestApi->delegateSignatureRequest: ', $e->getMessage(), PHP_EOL;
}
?>
```

### Parameters

Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **body** | [**\WooletClient\Model\SignatureRequestDelegate**](../Model/SignatureRequestDelegate.md)| Authentication information about the signer. |
 **request_id** | **string**| Identifier of the signature request. |

### Return type

[**\WooletClient\Model\SignatureRequestSignResult**](../Model/SignatureRequestSignResult.md)

### Authorization

[BasicAuth](../../README.md#BasicAuth), [JWTAuth](../../README.md#JWTAuth)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

# **deleteSignatureRequest**
> deleteSignatureRequest($request_id)

Delete a signature request.

Use this operation to delete a signature request.<br> **WARNING: You should never delete a signature request, otherwise you will no longer be able to download its proof bundle or Signature Attestation document.<br> Use this for test purpose only.**

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

$apiInstance = new WooletClient\API\SignatureRequestApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$request_id = "request_id_example"; // string | Identifier of the signature request to delete.

try {
    $apiInstance->deleteSignatureRequest($request_id);
} catch (Exception $e) {
    echo 'Exception when calling SignatureRequestApi->deleteSignatureRequest: ', $e->getMessage(), PHP_EOL;
}
?>
```

### Parameters

Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **request_id** | **string**| Identifier of the signature request to delete. |

### Return type

void (empty response body)

### Authorization

[BasicAuth](../../README.md#BasicAuth), [JWTAuth](../../README.md#JWTAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: Not defined

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

# **downloadSignatureRequestFile**
> string downloadSignatureRequestFile($request_id)

Download the file to sign.

Use this operation to download the file to be signed for a signature request.<br> The name of the file is included in the `Content-Disposition` header (see https://www.ietf.org/rfc/rfc6266.txt).

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

$apiInstance = new WooletClient\API\SignatureRequestApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$request_id = "request_id_example"; // string | Identifier of the signature request.

try {
    $result = $apiInstance->downloadSignatureRequestFile($request_id);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling SignatureRequestApi->downloadSignatureRequestFile: ', $e->getMessage(), PHP_EOL;
}
?>
```

### Parameters

Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **request_id** | **string**| Identifier of the signature request. |

### Return type

**string**

### Authorization

[BasicAuth](../../README.md#BasicAuth), [JWTAuth](../../README.md#JWTAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/octet-stream

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

# **getSignatureRequest**
> \WooletClient\Model\SignatureRequest getSignatureRequest($request_id, $signee_id)

Get a signature request by its identifier.

Use this operation to retrieve a signature request by its identifier.

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

$apiInstance = new WooletClient\API\SignatureRequestApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$request_id = "request_id_example"; // string | Identifier of the signature request to retrieve.
$signee_id = "signee_id_example"; // string | Secret identifier of the signer wanting to retrieve the signature request.<br> If set, information related to this signer is guaranteed to be returned in `authorizedSignees[0]`.<br> **This secret identifier is generated by the platform and provided by email to the signer only. It allows the platform to authenticate the signer and verify his email address.**

try {
    $result = $apiInstance->getSignatureRequest($request_id, $signee_id);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling SignatureRequestApi->getSignatureRequest: ', $e->getMessage(), PHP_EOL;
}
?>
```

### Parameters

Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **request_id** | **string**| Identifier of the signature request to retrieve. |
 **signee_id** | **string**| Secret identifier of the signer wanting to retrieve the signature request.&lt;br&gt; If set, information related to this signer is guaranteed to be returned in &#x60;authorizedSignees[0]&#x60;.&lt;br&gt; **This secret identifier is generated by the platform and provided by email to the signer only. It allows the platform to authenticate the signer and verify his email address.** | [optional]

### Return type

[**\WooletClient\Model\SignatureRequest**](../Model/SignatureRequest.md)

### Authorization

[BasicAuth](../../README.md#BasicAuth), [JWTAuth](../../README.md#JWTAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

# **getSignatureRequestAttestation**
> \WooletClient\Model\PdfFile getSignatureRequestAttestation($request_id)

Download the Signature Attestation document of a signature request.

Use this operation to retrieve the Signature Attestation document of a signature request.<br> This PDF file summarizes the signature request and includes the proof bundle as an attachement.<br> The proof bundle is a JSON file containing all the pieces of evidence:<br> - the audit trail<br> - the proof receipt of the signature of the audit trail by the platform<br> - the proof receipts of the signature of the file by the signers<br> Consequently, the signature attestation is only available once all the following conditions are met:<br> - the signature request is COMPLETED (by the platform) or CLOSED (by the requester)<br> - all the proof receipts are available (ie. all signatures have been anchored)<br> - the audit trail is generated and signed by the platform and its proof receipt is available (ie. its signature has been anchored)<br> Once these conditions are met, the platform sets the `proofBundleComplete` property to `true`.<br> This is a publicly accessible endpoint: authentication is not required to retrieve the signature attestation of a signature request (but its identifier needs to be known).

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

$apiInstance = new WooletClient\API\SignatureRequestApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$request_id = "request_id_example"; // string | Identifier of the signature request.

try {
    $result = $apiInstance->getSignatureRequestAttestation($request_id);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling SignatureRequestApi->getSignatureRequestAttestation: ', $e->getMessage(), PHP_EOL;
}
?>
```

### Parameters

Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **request_id** | **string**| Identifier of the signature request. |

### Return type

[**\WooletClient\Model\PdfFile**](../Model/PdfFile.md)

### Authorization

[BasicAuth](../../README.md#BasicAuth), [JWTAuth](../../README.md#JWTAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

# **getSignatureRequestProofBundle**
> \WooletClient\Model\SignatureRequestProofBundle getSignatureRequestProofBundle($request_id)

Get the proof bundle of a signature request.

Use this operation to retrieve the proof bundle of a signature request.<br> The proof bundle is a JSON file containing all the pieces of evidence:<br> - the audit trail<br> - the proof receipt of the signature of the audit trail by the platform<br> - the proof receipts of the signature of the file by the signers<br> Consequently, the proof bundle is only available once all the following conditions are met:<br> - the signature request is COMPLETED (by the platform) or CLOSED (by the requester)<br> - all the proof receipts are available (ie. all signatures have been anchored)<br> - the audit trail is generated and signed by the platform and its proof receipt is available (ie. its signature has been anchored)<br> Once these conditions are met, the platform sets the `proofBundleComplete` property to `true`.<br> If this endpoint is called before all these conditions are met, it returns only the available proof receipts (with a 202 status).<br> This is a publicly accessible endpoint: authentication is not required to retrieve the proof receipts of a signature request (but its identifier needs to be known).

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

$apiInstance = new WooletClient\API\SignatureRequestApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$request_id = "request_id_example"; // string | Identifier of the signature request.

try {
    $result = $apiInstance->getSignatureRequestProofBundle($request_id);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling SignatureRequestApi->getSignatureRequestProofBundle: ', $e->getMessage(), PHP_EOL;
}
?>
```

### Parameters

Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **request_id** | **string**| Identifier of the signature request. |

### Return type

[**\WooletClient\Model\SignatureRequestProofBundle**](../Model/SignatureRequestProofBundle.md)

### Authorization

[BasicAuth](../../README.md#BasicAuth), [JWTAuth](../../README.md#JWTAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

# **reportSignatureRequestEvent**
> reportSignatureRequestEvent($body, $request_id)

Report an event on a signature request.

A signer can use this operation to report an event on a signature request.<br> Events reported are included in the audit trail of the signature request.<br> This is a publicly accessible endpoint: authentication is not required to report an event (authentication of the signer rely on the knowledge of his secret identifier).

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

$apiInstance = new WooletClient\API\SignatureRequestApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$body = new \WooletClient\Model\SignatureRequestEvent(); // \WooletClient\Model\SignatureRequestEvent | Event to report.
$request_id = "request_id_example"; // string | Identifier of the signature request.

try {
    $apiInstance->reportSignatureRequestEvent($body, $request_id);
} catch (Exception $e) {
    echo 'Exception when calling SignatureRequestApi->reportSignatureRequestEvent: ', $e->getMessage(), PHP_EOL;
}
?>
```

### Parameters

Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **body** | [**\WooletClient\Model\SignatureRequestEvent**](../Model/SignatureRequestEvent.md)| Event to report. |
 **request_id** | **string**| Identifier of the signature request. |

### Return type

void (empty response body)

### Authorization

[BasicAuth](../../README.md#BasicAuth), [JWTAuth](../../README.md#JWTAuth)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: Not defined

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

# **reportSignatureRequestFeedback**
> reportSignatureRequestFeedback($body, $request_id)

Report a feedback about a signature request.

A signer can use this operation to report a feedback to the owner of a signature request.<br> This is a publicly accessible endpoint: authentication is not required to report a feedback (authentication of the signer rely on the knowledge of his secret identifier).

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

$apiInstance = new WooletClient\API\SignatureRequestApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$body = new \WooletClient\Model\SignatureRequestFeedback(); // \WooletClient\Model\SignatureRequestFeedback | Feedback to report.
$request_id = "request_id_example"; // string | Identifier of the signature request.

try {
    $apiInstance->reportSignatureRequestFeedback($body, $request_id);
} catch (Exception $e) {
    echo 'Exception when calling SignatureRequestApi->reportSignatureRequestFeedback: ', $e->getMessage(), PHP_EOL;
}
?>
```

### Parameters

Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **body** | [**\WooletClient\Model\SignatureRequestFeedback**](../Model/SignatureRequestFeedback.md)| Feedback to report. |
 **request_id** | **string**| Identifier of the signature request. |

### Return type

void (empty response body)

### Authorization

[BasicAuth](../../README.md#BasicAuth), [JWTAuth](../../README.md#JWTAuth)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: Not defined

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

# **searchSignatureRequestIds**
> \WooletClient\Model\SignatureRequestIds searchSignatureRequestIds($page, $size, $hash_to_sign)

Search for public signature request identifiers.

Use this operation to retrieve the identifiers of all public signature requests having a given `hashToSign` property.<br> Only public signature request identifiers are returned.<br> This is a publicly accessible endpoint: authentication is not required to retrieve public signature request identifiers.<br> Paging is supported.

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

$apiInstance = new WooletClient\API\SignatureRequestApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$page = 0; // int | Index of the page to retrieve (from 0).
$size = 20; // int | Number of signature request identifiers per page.
$hash_to_sign = "hash_to_sign_example"; // string | `hashToSign` to search for: all public signature requests whose `hashToSign` property is equal are returned.

try {
    $result = $apiInstance->searchSignatureRequestIds($page, $size, $hash_to_sign);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling SignatureRequestApi->searchSignatureRequestIds: ', $e->getMessage(), PHP_EOL;
}
?>
```

### Parameters

Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **page** | **int**| Index of the page to retrieve (from 0). | [optional] [default to 0]
 **size** | **int**| Number of signature request identifiers per page. | [optional] [default to 20]
 **hash_to_sign** | **string**| &#x60;hashToSign&#x60; to search for: all public signature requests whose &#x60;hashToSign&#x60; property is equal are returned. | [optional]

### Return type

[**\WooletClient\Model\SignatureRequestIds**](../Model/SignatureRequestIds.md)

### Authorization

[BasicAuth](../../README.md#BasicAuth), [JWTAuth](../../README.md#JWTAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

# **searchSignatureRequests**
> \WooletClient\Model\SignatureRequests searchSignatureRequests($page, $size, $direction, $sort, $name, $hash_to_sign, $states)

Search for signature requests.

Use this operation to retrieve all signature requests having a given `name` and/or `hashToSign` property.<br> Only requests belonging to the authenticated user are returned.<br> Paging and sorting is supported.

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

$apiInstance = new WooletClient\API\SignatureRequestApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$page = 0; // int | Index of the page to retrieve (from 0).
$size = 20; // int | Number of anchors per page.
$direction = "ASC"; // string | Sorting direction: ASC for ascending DESC for descending.
$sort = "created"; // string | Sorting property: possible values are limited to `created` and `hashToSign`.
$name = "name_example"; // string | `name` to search for: all signature requests whose `name` property contains this sub-string are returned.<br> **WARNING: Searching by name can timeout on a large signature request set.**
$hash_to_sign = "hash_to_sign_example"; // string | `hashToSign` to search for: all signature requests whose `hashToSign` property is equal are returned.
$states = array("states_example"); // string[] | States to search for: all signature requests whose `state` property is part of theses states are returned.

try {
    $result = $apiInstance->searchSignatureRequests($page, $size, $direction, $sort, $name, $hash_to_sign, $states);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling SignatureRequestApi->searchSignatureRequests: ', $e->getMessage(), PHP_EOL;
}
?>
```

### Parameters

Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **page** | **int**| Index of the page to retrieve (from 0). | [optional] [default to 0]
 **size** | **int**| Number of anchors per page. | [optional] [default to 20]
 **direction** | **string**| Sorting direction: ASC for ascending DESC for descending. | [optional] [default to ASC]
 **sort** | **string**| Sorting property: possible values are limited to &#x60;created&#x60; and &#x60;hashToSign&#x60;. | [optional] [default to created]
 **name** | **string**| &#x60;name&#x60; to search for: all signature requests whose &#x60;name&#x60; property contains this sub-string are returned.&lt;br&gt; **WARNING: Searching by name can timeout on a large signature request set.** | [optional]
 **hash_to_sign** | **string**| &#x60;hashToSign&#x60; to search for: all signature requests whose &#x60;hashToSign&#x60; property is equal are returned. | [optional]
 **states** | [**string[]**](../Model/string.md)| States to search for: all signature requests whose &#x60;state&#x60; property is part of theses states are returned. | [optional]

### Return type

[**\WooletClient\Model\SignatureRequests**](../Model/SignatureRequests.md)

### Authorization

[BasicAuth](../../README.md#BasicAuth), [JWTAuth](../../README.md#JWTAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

# **sendSignatureRequestOTP**
> sendSignatureRequestOTP($request_id, $signee_id)

Generate and send an OTP to a signer of a signature request.

Use this operation to generate and send a new OTP (One Time Password) by SMS to a signer of a signature request.<br> This OTP can be used to sign during a maximum period of 10 mn.

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

$apiInstance = new WooletClient\API\SignatureRequestApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$request_id = "request_id_example"; // string | Identifier of the signature request.
$signee_id = "signee_id_example"; // string | Secret identifier of the signer wanting to retrieve his OTP.<br> **This secret identifier is generated by the platform and provided by email to the signer only. It allows the platform to authenticate the signer and verify his email address.**

try {
    $apiInstance->sendSignatureRequestOTP($request_id, $signee_id);
} catch (Exception $e) {
    echo 'Exception when calling SignatureRequestApi->sendSignatureRequestOTP: ', $e->getMessage(), PHP_EOL;
}
?>
```

### Parameters

Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **request_id** | **string**| Identifier of the signature request. |
 **signee_id** | **string**| Secret identifier of the signer wanting to retrieve his OTP.&lt;br&gt; **This secret identifier is generated by the platform and provided by email to the signer only. It allows the platform to authenticate the signer and verify his email address.** |

### Return type

void (empty response body)

### Authorization

[BasicAuth](../../README.md#BasicAuth), [JWTAuth](../../README.md#JWTAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: Not defined

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

# **sendSignatureRequestReminder**
> sendSignatureRequestReminder($body, $request_id)

Send a reminder email to a set of signers of a signature request.

Use this operation to send a reminder email to a set of signers of a signature request.<br> This email reminds them that they have a document to sign.

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

$apiInstance = new WooletClient\API\SignatureRequestApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$body = array("body_example"); // string[] | The list of emails of the authorized signers who will receive the reminder email.

$request_id = "request_id_example"; // string | Identifier of the signature request.

try {
    $apiInstance->sendSignatureRequestReminder($body, $request_id);
} catch (Exception $e) {
    echo 'Exception when calling SignatureRequestApi->sendSignatureRequestReminder: ', $e->getMessage(), PHP_EOL;
}
?>
```

### Parameters

Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **body** | [**string[]**](../Model/string.md)| The list of emails of the authorized signers who will receive the reminder email.
 |
 **request_id** | **string**| Identifier of the signature request. |

### Return type

void (empty response body)

### Authorization

[BasicAuth](../../README.md#BasicAuth), [JWTAuth](../../README.md#JWTAuth)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: Not defined

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

# **signSignatureRequest**
> \WooletClient\Model\SignatureRequestSignResult signSignatureRequest($body, $request_id)

Sign a signature request by registering a signature.

A signer can use this operation to sign a signature request by registering a signature he procuded on his own.<br> The signature is automatically anchored on behalf of the owner of the signature request.<br> The signature anchor created is added to the list of signature anchors of the signature request.<br> This is a publicly accessible endpoint: authentication is not required to register a signature (authentication of the signer rely on the knowledge of his secret identifier and OTP, or on the control of his public key).

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

$apiInstance = new WooletClient\API\SignatureRequestApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$body = new \WooletClient\Model\SignatureRequestSign(); // \WooletClient\Model\SignatureRequestSign | Signature to register.
$request_id = "request_id_example"; // string | Identifier of the signature request.

try {
    $result = $apiInstance->signSignatureRequest($body, $request_id);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling SignatureRequestApi->signSignatureRequest: ', $e->getMessage(), PHP_EOL;
}
?>
```

### Parameters

Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **body** | [**\WooletClient\Model\SignatureRequestSign**](../Model/SignatureRequestSign.md)| Signature to register. |
 **request_id** | **string**| Identifier of the signature request. |

### Return type

[**\WooletClient\Model\SignatureRequestSignResult**](../Model/SignatureRequestSignResult.md)

### Authorization

[BasicAuth](../../README.md#BasicAuth), [JWTAuth](../../README.md#JWTAuth)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

# **transitionSignatureRequest**
> \WooletClient\Model\SignatureRequest transitionSignatureRequest($body, $request_id)

Change the state of a signature request.

Use this operation to transition a **stateful** signature request to a new state.<br> Possible transitions are:<br> - from DRAFT to PENDING: start the signature request: the platform wait for the activation date (if any) and transition to IN_PROGRESS<br> - from PENDING to DRAFT: suspend the signature request: allow it to be updated<br> - from PENDING to CANCELED: cancel the signature request without waiting for the  activation date<br> - from IN_PROGRESS to CLOSED: close the signature request without waiting for all signatures to be colleted<br> - from IN_PROGRESS to CANCELED: cancel the signature request before all signatures get colleted<br> Note that **stateless** signature requests can only be transitioned to CLOLSED or CANCELED, which triggers the generation of the audit trail and its signature by the platform.

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

$apiInstance = new WooletClient\API\SignatureRequestApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$body = "body_example"; // string | New state of the signature request.
$request_id = "request_id_example"; // string | Identifier of the signature request.

try {
    $result = $apiInstance->transitionSignatureRequest($body, $request_id);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling SignatureRequestApi->transitionSignatureRequest: ', $e->getMessage(), PHP_EOL;
}
?>
```

### Parameters

Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **body** | [**string**](../Model/string.md)| New state of the signature request. |
 **request_id** | **string**| Identifier of the signature request. |

### Return type

[**\WooletClient\Model\SignatureRequest**](../Model/SignatureRequest.md)

### Authorization

[BasicAuth](../../README.md#BasicAuth), [JWTAuth](../../README.md#JWTAuth)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

# **updateSignatureRequest**
> \WooletClient\Model\SignatureRequest updateSignatureRequest($body, $request_id)

Update a signature request.

Use this operation to update a signature request.<br> Only the properties `name`, `public`, `callbackURL`, `activation`, `deadline`, `identityURL`, `fileName`, `fileURL`, `lang`, `vars`, `maxSignatures` and `authorizedSignees` can be modified.<br> Only **stateless** signature requests or **stateful** signature request in 'DRAFT' state can be updated.

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

$apiInstance = new WooletClient\API\SignatureRequestApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$body = new \WooletClient\Model\SignatureRequest(); // \WooletClient\Model\SignatureRequest | SignatureRequest object to update.
$request_id = "request_id_example"; // string | Identifier of signature request to update.

try {
    $result = $apiInstance->updateSignatureRequest($body, $request_id);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling SignatureRequestApi->updateSignatureRequest: ', $e->getMessage(), PHP_EOL;
}
?>
```

### Parameters

Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **body** | [**\WooletClient\Model\SignatureRequest**](../Model/SignatureRequest.md)| SignatureRequest object to update. |
 **request_id** | **string**| Identifier of signature request to update. |

### Return type

[**\WooletClient\Model\SignatureRequest**](../Model/SignatureRequest.md)

### Authorization

[BasicAuth](../../README.md#BasicAuth), [JWTAuth](../../README.md#JWTAuth)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

# **uploadSignatureRequestFile**
> \WooletClient\Model\SignatureRequest uploadSignatureRequestFile($file, $request_id)

Upload the file to sign.

Use this operation to upload the file to be signed for a signature request.<br> The SHA256 hash of the uploaded file must be equal to the `hashToSign` property of the signature request or the upload fails.<br> Once uploaded, the file is stored and the `fileURL` property of the signature request is set, so that it can be used by a signature application to download and present the file to the signers.<br> Only **stateless** signature requests or **stateful** signature request in 'DRAFT' state can be updated. **WARNING: the storage of the file to be signed is provided for convenience only: it is not required, and you should never upload a file if you have any concern about its privacy.**

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

$apiInstance = new WooletClient\API\SignatureRequestApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$file = "file_example"; // string | 
$request_id = "request_id_example"; // string | Identifier of the signature request.

try {
    $result = $apiInstance->uploadSignatureRequestFile($file, $request_id);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling SignatureRequestApi->uploadSignatureRequestFile: ', $e->getMessage(), PHP_EOL;
}
?>
```

### Parameters

Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **file** | **string****string**|  |
 **request_id** | **string**| Identifier of the signature request. |

### Return type

[**\WooletClient\Model\SignatureRequest**](../Model/SignatureRequest.md)

### Authorization

[BasicAuth](../../README.md#BasicAuth), [JWTAuth](../../README.md#JWTAuth)

### HTTP request headers

 - **Content-Type**: multipart/form-data
 - **Accept**: application/json

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

