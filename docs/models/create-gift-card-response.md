
# Create Gift Card Response

A response that contains a `GiftCard`. The response might contain a set of `Error` objects if the request
resulted in errors.

## Structure

`CreateGiftCardResponse`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `errors` | [`Error[] \| undefined`](../models/error.md) | Optional | Any errors that occurred during the request. |
| `giftCard` | [`GiftCard \| undefined`](../models/gift-card.md) | Optional | Represents a Square gift card. |

## Example (as JSON)

```json
{
  "gift_card": {
    "balance_money": {
      "amount": 0,
      "currency": "USD"
    },
    "created_at": "2021-05-20T22:26:54.000Z",
    "gan": "7783320006753271",
    "gan_source": "SQUARE",
    "id": "gftc:6cbacbb64cf54e2ca9f573d619038059",
    "state": "PENDING",
    "type": "DIGITAL"
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

