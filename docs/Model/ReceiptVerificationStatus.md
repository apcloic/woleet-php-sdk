# ReceiptVerificationStatus

## Properties
Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**code** | **string** | Proof receipt verification status code:&lt;br&gt; - VERIFIED: success: the proof receipt is verified: both the proof of timestamp AND the proof of signature (if applicable) are valid&lt;br&gt; - INVALID_SIGNATURE: error: the proof of signature is invalid&lt;br&gt; - any other verification status code: the proof of timestamp is not ready or invalid | [optional] 
**text** | **string** | Proof receipt verification status text giving more insight about verification errors. | [optional] 
**timestamp** | **int** | Proven timestamp of the data (for a data anchor) or of the signature (for a signature anchor).&lt;br&gt; This is actually the time of the Bitcoin block into which the anchoring process occurred (in milliseconds since Unix epoch). | [optional] 
**confirmations** | **int** | Number of confirmations of the Bitcoin block into which the anchoring process occurred. | [optional] 
**timestamp_verification_status** | [**\WooletClient\Model\TimestampVerificationStatus**](TimestampVerificationStatus.md) |  | [optional] 
**signature_verification_status** | [**\WooletClient\Model\SignatureVerificationStatus**](SignatureVerificationStatus.md) |  | [optional] 
**identity_verification_status** | [**\WooletClient\Model\IdentityVerificationStatus**](IdentityVerificationStatus.md) |  | [optional] 

[[Back to Model list]](../../README.md#documentation-for-models) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to README]](../../README.md)

