
# Register Domain Response

Defines the fields that are included in the response body of
a request to the [RegisterDomain](../api/apple-pay.md#register-domain) endpoint.

Either `errors` or `status` are present in a given response (never both).

## Structure

`RegisterDomainResponse`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `errors` | [`Error[] \| undefined`](../models/error.md) | Optional | Any errors that occurred during the request. |
| `status` | [`string \| undefined`](../models/register-domain-response-status.md) | Optional | The status of the domain registration. |

## Example (as JSON)

```json
{
  "status": "VERIFIED",
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

