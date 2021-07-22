# SignatureRequestSign

## Properties
Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**signature** | **string** | Signature of the &#x60;hashToSign&#x60; property of the signature request using the public key &#x60;pubKey&#x60;, or, if any of &#x60;signedIdentity&#x60; or &#x60;signedIssuerDomain&#x60; is provided, signature of SHA256(&#x60;hashToSign&#x60; + &#x60;signedIdentity&#x60; + &#x60;signedIssuerDomain&#x60;) using the public key &#x60;pubKey&#x60;. | 
**pub_key** | **string** | Public key used to sign. | 
**signed_identity** | **string** | X500 Distinguished Name representing the signed identity.&lt;br&gt; If set, the CN (common name) and EMAILADDRESS (email address) attributes must match the common name and email address of the signer as set in the signature request. | [optional] 
**signed_issuer_domain** | **string** | Domain name of the identity issuer (ie. of the organization who verified the identity).&lt;br&gt; If set, the domain name of the identity URL must be included in the &#x60;signedIssuerDomain&#x60; domain name. | [optional] 
**identity_url** | **string** | Web hook to use to verify the signer&#x27;s identity.&lt;br&gt; If set, it is used in place of the &#x60;identityURL&#x60; property of the signer to create the signature anchor. | [optional] 
**device** | **string** | Type of device used to sign:&lt;br&gt; - SERVER: Woleet.ID Server or equivalent&lt;br&gt; - MOBILE: Woleet.ID Mobile or equivalent&lt;br&gt; - NANO: Ledger Nano S or equivalent | [optional] 
**signee_id** | **string** | Secret identifier of the signer (provided by email).&lt;br&gt; Only required if &#x60;pubKey&#x60; was not set for thìs signer. | [optional] 
**otp** | **string** | OTP of the signer (only required if &#x60;requiresOTP&#x60; was set to &#x60;true&#x60; for thìs signer). | [optional] 

[[Back to Model list]](../../README.md#documentation-for-models) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to README]](../../README.md)

