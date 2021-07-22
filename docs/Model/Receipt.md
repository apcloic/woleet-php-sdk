# Receipt

## Properties
Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**target_hash** | **string** | SHA256 hash of the proven data or signature. | [optional] 
**type** | **string** | Chainpoint 2.x: Type of the proof receipt.&lt;br&gt; **Currently only &#x27;ChainpointSHA256v2&#x27; is supported.** | [optional] 
**merkle_root** | **string** | Chainpoint 2.x: Root of the Merkle tree. | [optional] 
**proof** | [**\WooletClient\Model\ReceiptProofNode[]**](ReceiptProofNode.md) | Chainpoint 2.x: Merkle proof (path from &#x60;targetHash&#x60; to &#x60;merkleRoot&#x60; in the Merkle tree). | [optional] 
**anchors** | [**\WooletClient\Model\ReceiptAnchorsNode[]**](ReceiptAnchorsNode.md) | Chainpoint 2.x: List of sources where the root of the Merkle proof is anchored. | [optional] 
**partial** | **bool** | &#x60;true&#x60; if the receipt is partial (ie. does not contain the Chainpoint 2.x proof of timestamp) | [optional] 
**signature** | [**\WooletClient\Model\ReceiptSignature**](ReceiptSignature.md) |  | [optional] 

[[Back to Model list]](../../README.md#documentation-for-models) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to README]](../../README.md)

