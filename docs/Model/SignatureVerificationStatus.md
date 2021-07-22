# SignatureVerificationStatus

## Properties
Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**code** | **string** | Signature verification status code:&lt;br&gt; - VERIFIED: success: the receipt&#x27;s &#x60;signature&#x60; property is a valid signature of &#x60;signedHash&#x60;, or, if any of &#x60;signedIdentity&#x60; or &#x60;signedIssuerDomain&#x60; is provided, a valid signature of SHA256(&#x60;signedHash&#x60; + &#x60;signedIdentity&#x60; + &#x60;signedIssuerDomain&#x60;) using the public key &#x60;pubKey&#x60;.&lt;br&gt; - SIGNATURE_MISMATCH_RECEIPT: error: the receipt&#x27;s &#x60;targetHash&#x60; does not match the SHA256 hash of &#x60;signature&#x60;.&lt;br&gt; - INVALID_SIGNATURE: error: the receipt&#x27;s &#x60;signature&#x60; property is invalid. | [optional] 
**text** | **string** | Signature verification status text (gives more insights about the verification process). | [optional] 

[[Back to Model list]](../../README.md#documentation-for-models) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to README]](../../README.md)

