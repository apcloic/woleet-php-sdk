# SignatureRequestEvent

## Properties
Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**signee_id** | **string** | Secret identifier of the signer (provided by email). | 
**type** | **string** | Type of the event to report:&lt;br&gt; - DATA_VERIFIED: the signer verified the integrity (ie. hash) of the data to sign - DATA_REVIEWED: the signer reviewed and acceted the data to sign - TCU_ACCEPTED: the signer reviewed and accepted the TCU - TCU_REFUSED: the signer refused the TCU - SIGN_ACCEPTED: the signer accepted to sign the data - SIGN_REFUSED: the signer refused to sign the data | 
**comment** | **string** | Comment related to the event to report. | [optional] 

[[Back to Model list]](../../README.md#documentation-for-models) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to README]](../../README.md)

