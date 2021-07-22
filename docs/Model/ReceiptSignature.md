# ReceiptSignature

## Properties
Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**signed_hash** | **string** | SHA256 hash (ie. the fingerprint) of the signed file. | [optional] 
**signed_identity** | **string** | X500 Distinguished Name representing the signed identity. | [optional] 
**signed_issuer_domain** | **string** | Domain name of the identity issuer (ie. of the organization who verified the identity). | [optional] 
**pub_key** | **string** | Public key of the signer.&lt;br&gt; **Currently only Bitcoin addresses are supported.** | [optional] 
**signature** | **string** | Signature of the &#x60;signedHash&#x60; property using the public key &#x60;pubKey&#x60;, or, if any of &#x60;signedIdentity&#x60; or &#x60;signedIssuerDomain&#x60; is provided, signature of SHA256(&#x60;signedHash&#x60; + &#x60;signedIdentity&#x60; + &#x60;signedIssuerDomain&#x60;) using the public key &#x60;pubKey&#x60;. | [optional] 
**identity_url** | **string** | Web hook to use to verify the signer&#x27;s identity. | [optional] 

[[Back to Model list]](../../README.md#documentation-for-models) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to README]](../../README.md)

