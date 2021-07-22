# Watcher

## Properties
Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**email** | **string** | The email of the watcher. | 
**common_name** | **string** | The full name of the watcher. | [optional] 
**vars** | **object** | A set of variables (key/value pairs) that can be used to customize the signature request workflow for this watcher.&lt;br&gt; Values must be of type null, boolean, string or number: nested JSON objects are not allowed.&lt;br&gt; Variables defined here overwrites the ones defined at signature request level when emailing the watcher. | [optional] 
**lang** | **string** | The preferred language (provided as an ISO 639-1 string) to use when emailing the watcher.&lt;br&gt; If set, this property overwrites the &#x60;lang&#x60; property defined at signature request level. | [optional] 

[[Back to Model list]](../../README.md#documentation-for-models) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to README]](../../README.md)

