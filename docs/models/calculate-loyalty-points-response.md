
# Calculate Loyalty Points Response

Represents a [CalculateLoyaltyPoints](../api/loyalty.md#calculate-loyalty-points) response.

## Structure

`CalculateLoyaltyPointsResponse`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `errors` | [`Error[] \| undefined`](../models/error.md) | Optional | Any errors that occurred during the request. |
| `points` | `number \| undefined` | Optional | The number of points that the buyer can earn from the base loyalty program. |
| `promotionPoints` | `number \| undefined` | Optional | The number of points that the buyer can earn from a loyalty promotion. To be eligible<br/>to earn promotion points, the purchase must first qualify for program points. When `order_id`<br/>is not provided in the request, this value is always 0. |

## Example (as JSON)

```json
{
  "points": 6,
  "promotion_points": 12,
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

