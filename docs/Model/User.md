# User

## Properties
Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**id** | **string** | User identifier. It is allocated by the platform, and so must not be provided at creation time. | [optional] 
**created** | **int** | Date of creation (in milliseconds since Unix epoch). | [optional] 
**last_modified** | **int** | Date of last modification (in milliseconds since Unix epoch). | [optional] 
**email** | **string** | Email of the user. | 
**password** | **string** | Password of the user (it must be provided at creation time). | 
**roles** | **string[]** | Array of user roles. | 
**info** | [**\WooletClient\Model\Info**](Info.md) |  | 
**status** | **string** | The status of the user:&lt;br&gt; - PENDING: the user email need to be validated&lt;br&gt; - APPROVED: the user can loging&lt;br&gt; - DISABLED: the user cannot login | [default to 'PENDING']

[[Back to Model list]](../../README.md#documentation-for-models) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to README]](../../README.md)

