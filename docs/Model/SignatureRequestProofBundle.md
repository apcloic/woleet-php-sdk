# SignatureRequestProofBundle

## Properties
Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**signature_receipts** | [**\WooletClient\Model\Receipt[]**](Receipt.md) | Proof receipts of the signatures of the file by the signers | [optional] 
**audit_trail_receipt** | [**\WooletClient\Model\Receipt**](Receipt.md) |  | [optional] 
**audit_trail_data** | **string** | Audit trail data (Base64 encoded JSON object) | [optional] 
**complete** | **bool** | &#x60;true&#x60; if all pieces of evidence are present in the proof bundle, or &#x60;false&#x60; if not&lt;br&gt; All the following conditions must be met:&lt;br&gt; - the signature request is COMPLETED (by the platform) or CLOSED (by the requester)&lt;br&gt; - the audit trail is generated and signed by the platform&lt;br&gt; - all the proof receipts are available | [optional] 

[[Back to Model list]](../../README.md#documentation-for-models) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to README]](../../README.md)

