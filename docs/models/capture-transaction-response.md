
# Capture Transaction Response

Defines the fields that are included in the response body of
a request to the [CaptureTransaction](api-endpoint:Transactions-CaptureTransaction) endpoint.

## Structure

`CaptureTransactionResponse`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `errors` | [`Error[] \| undefined`](../models/error.md) | Optional | Any errors that occurred during the request. |

## Example (as JSON)

```json
{
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

