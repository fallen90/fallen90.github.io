
# V1 Settlement Entry

V1SettlementEntry

## Structure

`V1SettlementEntry`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `paymentId` | `string \| null \| undefined` | Optional | The settlement's unique identifier. |
| `type` | [`string \| undefined`](../models/v1-settlement-entry-type.md) | Optional | - |
| `amountMoney` | [`V1Money \| undefined`](../models/v1-money.md) | Optional | - |
| `feeMoney` | [`V1Money \| undefined`](../models/v1-money.md) | Optional | - |

## Example (as JSON)

```json
{
  "payment_id": "payment_id0",
  "type": "RETURNED_PAYOUT",
  "amount_money": {
    "amount": 186,
    "currency_code": "UZS"
  },
  "fee_money": {
    "amount": 108,
    "currency_code": "ILS"
  }
}
```

