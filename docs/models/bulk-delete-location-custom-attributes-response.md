
# Bulk Delete Location Custom Attributes Response

Represents a [BulkDeleteLocationCustomAttributes](../api/location-custom-attributes.md#bulk-delete-location-custom-attributes) response,
which contains a map of responses that each corresponds to an individual delete request.

## Structure

`BulkDeleteLocationCustomAttributesResponse`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `values` | [`Record<string, BulkDeleteLocationCustomAttributesResponseLocationCustomAttributeDeleteResponse>`](../models/bulk-delete-location-custom-attributes-response-location-custom-attribute-delete-response.md) | Required | A map of responses that correspond to individual delete requests. Each response has the<br/>same key as the corresponding request. |
| `errors` | [`Error[] \| undefined`](../models/error.md) | Optional | Any errors that occurred during the request. |

## Example (as JSON)

```json
{
  "values": {
    "id1": {
      "errors": [],
      "location_id": "L0TBCBTB7P8RQ"
    },
    "id2": {
      "errors": [],
      "location_id": "L9XMD04V3STJX"
    },
    "id3": {
      "errors": [],
      "location_id": "L0TBCBTB7P8RQ"
    }
  },
  "errors": [
    {
      "category": "MERCHANT_SUBSCRIPTION_ERROR",
      "code": "MAP_KEY_LENGTH_TOO_LONG",
      "detail": "detail6",
      "field": "field4"
    }
  ]
}
```

