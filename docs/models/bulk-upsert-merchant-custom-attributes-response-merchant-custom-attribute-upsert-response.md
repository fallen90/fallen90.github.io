
# Bulk Upsert Merchant Custom Attributes Response Merchant Custom Attribute Upsert Response

Represents a response for an individual upsert request in a [BulkUpsertMerchantCustomAttributes](../api/merchant-custom-attributes.md#bulk-upsert-merchant-custom-attributes) operation.

## Structure

`BulkUpsertMerchantCustomAttributesResponseMerchantCustomAttributeUpsertResponse`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `merchantId` | `string \| undefined` | Optional | The ID of the merchant associated with the custom attribute. |
| `customAttribute` | [`CustomAttribute \| undefined`](../models/custom-attribute.md) | Optional | A custom attribute value. Each custom attribute value has a corresponding<br/>`CustomAttributeDefinition` object. |
| `errors` | [`Error[] \| undefined`](../models/error.md) | Optional | Any errors that occurred while processing the individual request. |

## Example (as JSON)

```json
{
  "merchant_id": "merchant_id0",
  "custom_attribute": {
    "key": "key2",
    "value": {
      "key1": "val1",
      "key2": "val2"
    },
    "version": 102,
    "visibility": "VISIBILITY_READ_ONLY",
    "definition": {
      "key": "key0",
      "schema": {
        "key1": "val1",
        "key2": "val2"
      },
      "name": "name0",
      "description": "description0",
      "visibility": "VISIBILITY_HIDDEN"
    }
  },
  "errors": [
    {
      "category": "MERCHANT_SUBSCRIPTION_ERROR",
      "code": "MAP_KEY_LENGTH_TOO_LONG",
      "detail": "detail6",
      "field": "field4"
    },
    {
      "category": "MERCHANT_SUBSCRIPTION_ERROR",
      "code": "MAP_KEY_LENGTH_TOO_LONG",
      "detail": "detail6",
      "field": "field4"
    },
    {
      "category": "MERCHANT_SUBSCRIPTION_ERROR",
      "code": "MAP_KEY_LENGTH_TOO_LONG",
      "detail": "detail6",
      "field": "field4"
    }
  ]
}
```
