
# V1 Payment Discount

V1PaymentDiscount

## Structure

`V1PaymentDiscount`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `name` | `string \| null \| undefined` | Optional | The discount's name. |
| `appliedMoney` | [`V1Money \| undefined`](../models/v1-money.md) | Optional | - |
| `discountId` | `string \| null \| undefined` | Optional | The ID of the applied discount, if available. Discounts applied in older versions of Square Register might not have an ID. |

## Example (as JSON)

```json
{
  "name": "name4",
  "applied_money": {
    "amount": 196,
    "currency_code": "IQD"
  },
  "discount_id": "discount_id2"
}
```

