
# V1 Payment Itemization

Payment include an`itemizations` field that lists the items purchased,
along with associated fees, modifiers, and discounts. Each itemization has an
`itemization_type` field that indicates which of the following the itemization
represents:

<ul>
<li>An item variation from the merchant's item library</li>
<li>A custom monetary amount</li>
<li>
An action performed on a Square gift card, such as activating or
reloading it.
</li>
</ul>
*Note**: itemization information included in a `Payment` object reflects
details collected **at the time of the payment**. Details such as the name or
price of items might have changed since the payment was processed.

## Structure

`V1PaymentItemization`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `name` | `string \| null \| undefined` | Optional | The item's name. |
| `quantity` | `number \| null \| undefined` | Optional | The quantity of the item purchased. This can be a decimal value. |
| `itemizationType` | [`string \| undefined`](../models/v1-payment-itemization-itemization-type.md) | Optional | - |
| `itemDetail` | [`V1PaymentItemDetail \| undefined`](../models/v1-payment-item-detail.md) | Optional | V1PaymentItemDetail |
| `notes` | `string \| null \| undefined` | Optional | Notes entered by the merchant about the item at the time of payment, if any. |
| `itemVariationName` | `string \| null \| undefined` | Optional | The name of the item variation purchased, if any. |
| `totalMoney` | [`V1Money \| undefined`](../models/v1-money.md) | Optional | - |
| `singleQuantityMoney` | [`V1Money \| undefined`](../models/v1-money.md) | Optional | - |
| `grossSalesMoney` | [`V1Money \| undefined`](../models/v1-money.md) | Optional | - |
| `discountMoney` | [`V1Money \| undefined`](../models/v1-money.md) | Optional | - |
| `netSalesMoney` | [`V1Money \| undefined`](../models/v1-money.md) | Optional | - |
| `taxes` | [`V1PaymentTax[] \| null \| undefined`](../models/v1-payment-tax.md) | Optional | All taxes applied to this itemization. |
| `discounts` | [`V1PaymentDiscount[] \| null \| undefined`](../models/v1-payment-discount.md) | Optional | All discounts applied to this itemization. |
| `modifiers` | [`V1PaymentModifier[] \| null \| undefined`](../models/v1-payment-modifier.md) | Optional | All modifier options applied to this itemization. |

## Example (as JSON)

```json
{
  "name": "name4",
  "quantity": 253.5,
  "itemization_type": "GIFT_CARD_UNKNOWN",
  "item_detail": {
    "category_name": "category_name0",
    "sku": "sku6",
    "item_id": "item_id2",
    "item_variation_id": "item_variation_id2"
  },
  "notes": "notes4"
}
```

