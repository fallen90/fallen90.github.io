
# Bulk Delete Merchant Custom Attributes Response Merchant Custom Attribute Delete Response

Represents an individual delete response in a [BulkDeleteMerchantCustomAttributes](../api/merchant-custom-attributes.md#bulk-delete-merchant-custom-attributes)
request.

## Structure

`BulkDeleteMerchantCustomAttributesResponseMerchantCustomAttributeDeleteResponse`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `errors` | [`Error[] \| undefined`](../models/error.md) | Optional | Errors that occurred while processing the individual MerchantCustomAttributeDeleteRequest request |

## Example (as JSON)

```json
{
  "errors": [],
  "merchant_id": "DM7VKY8Q63GNP"
}
```

