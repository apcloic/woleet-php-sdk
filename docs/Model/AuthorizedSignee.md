# AuthorizedSignee

## Properties
Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**common_name** | **string** | The full name of the signer. | [optional] 
**email** | **string** | The email of the signer.&lt;br&gt; Two signers cannot have the same email.&lt;br&gt; If set, &#x60;commonName&#x60; must also be set. | [optional] 
**country_calling_code** | **string** | The country calling code of the signer (numbers only, no white space). | [optional] 
**phone** | **string** | The phone number of the signer (not including the country calling code, numbers only, no white spaces).&lt;br&gt; Two signers cannot have the same phone number.&lt;br&gt; If set, &#x60;commonName&#x60; must also be set.&lt;br&gt; This phone number must support SMS delivery. | [optional] 
**requires_otp** | **bool** | &#x60;true&#x60; if the signer must provide an OTP to sign.&lt;br&gt; If &#x60;true&#x60;, &#x60;phone&#x60; must be set, since the OTP is sent by SMS. | [optional] 
**signs_face_to_face** | **bool** | &#x60;true&#x60; if the signer must sign face-to-face, or &#x60;false&#x60; (or unset) if the signer must sign using the regular signature workflow.&lt;br&gt; If &#x60;true&#x60;, &#x60;requiresOTP&#x60; must also be &#x60;true&#x60;. | [optional] 
**vars** | **object** | A set of variables (key/value pairs) that can be used to customize the signature request workflow for this signer.&lt;br&gt; Values must be of type null, boolean, string or number: nested JSON objects are not allowed.&lt;br&gt; Variables defined here overwrites the ones defined at signature request level when emailing the signer.&lt;br&gt; **This property is only available to the owner and the signers of the signature request.** | [optional] 
**lang** | **string** | The preferred language (provided as an ISO 639-1 string) to use when emailing the signer.&lt;br&gt; If set, this property overwrites the &#x60;lang&#x60; property defined at signature request level. | [optional] 
**pub_key** | **string** | The public key the signer must use to sign.&lt;br&gt; If not set, the signer can use any key to sign.&lt;br&gt; **Currently only Bitcoin addresses are supported.** | [optional] 
**device** | **string** | The type of device the signer should use to sign:&lt;br&gt; - SERVER: Woleet.ID Server or equivalent&lt;br&gt; - MOBILE: Woleet.ID Mobile or equivalent&lt;br&gt; - NANO: Ledger Nano S or equivalent&lt;br&gt; If set, the signature application can use it to propose only the corresponding signature mode. | [optional] 
**identity_url** | **string** | Web hook to use to verify the signer&#x27;s identity.&lt;br&gt; If set, this property overwrites the &#x60;identityURL&#x60; property defined at signature request level. | [optional] 
**feedback_subject** | **string** | Last feedback subject reported by the signer to the owner of the signature request.&lt;br&gt; **This property is only available to the owner of the signature request.** | [optional] 
**feedback_message** | **string** | Last feedback message reported by the signer to the owner of the signature request.&lt;br&gt; **This property is only available to the owner of the signature request.** | [optional] 
**anchor_id** | **string** | If the signer has signed, identifier of the signature anchor created. | [optional] 
**signed_on** | **int** | If the signer has signed, date of signature (in milliseconds since Unix epoch). | [optional] 
**audit_trail_id** | **string** | Identifier of the signer in the audit trail. | [optional] 
**id** | **string** | **WARNING: Do not use (test purpose only).** | [optional] 
**otp** | **string** | **WARNING: Do not use (test purpose only).** | [optional] 

[[Back to Model list]](../../README.md#documentation-for-models) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to README]](../../README.md)

