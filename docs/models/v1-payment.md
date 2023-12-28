
# V1 Payment

A payment represents a paid transaction between a Square merchant and a
customer. Payment details are usually available from Connect API endpoints
within a few minutes after the transaction completes.

Each Payment object includes several fields that end in `_money`. These fields
describe the various amounts of money that contribute to the payment total:

<ul>
<li>
Monetary values are <b>positive</b> if they represent an
<em>increase</em> in the amount of money the merchant receives (e.g.,
<code>tax_money</code>, <code>tip_money</code>).
</li>
<li>
Monetary values are <b>negative</b> if they represent an
<em>decrease</em> in the amount of money the merchant receives (e.g.,
<code>discount_money</code>, <code>refunded_money</code>).
</li>
</ul>


## Structure

`V1Payment`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `id` | `string \| undefined` | Optional | The payment's unique identifier. |
| `merchantId` | `string \| null \| undefined` | Optional | The unique identifier of the merchant that took the payment. |
| `createdAt` | `string \| undefined` | Optional | The time when the payment was created, in ISO 8601 format. Reflects the time of the first payment if the object represents an incomplete partial payment, and the time of the last or complete payment otherwise. |
| `creatorId` | `string \| null \| undefined` | Optional | The unique identifier of the Square account that took the payment. |
| `device` | [`V1Device \| undefined`](../models/v1-device.md) | Optional | - |
| `paymentUrl` | `string \| null \| undefined` | Optional | The URL of the payment's detail page in the merchant dashboard. The merchant must be signed in to the merchant dashboard to view this page. |
| `receiptUrl` | `string \| null \| undefined` | Optional | The URL of the receipt for the payment. Note that for split tender<br/>payments, this URL corresponds to the receipt for the first tender<br/>listed in the payment's tender field. Each Tender object has its own<br/>receipt_url field you can use to get the other receipts associated with<br/>a split tender payment. |
| `inclusiveTaxMoney` | [`V1Money \| undefined`](../models/v1-money.md) | Optional | - |
| `additiveTaxMoney` | [`V1Money \| undefined`](../models/v1-money.md) | Optional | - |
| `taxMoney` | [`V1Money \| undefined`](../models/v1-money.md) | Optional | - |
| `tipMoney` | [`V1Money \| undefined`](../models/v1-money.md) | Optional | - |
| `discountMoney` | [`V1Money \| undefined`](../models/v1-money.md) | Optional | - |
| `totalCollectedMoney` | [`V1Money \| undefined`](../models/v1-money.md) | Optional | - |
| `processingFeeMoney` | [`V1Money \| undefined`](../models/v1-money.md) | Optional | - |
| `netTotalMoney` | [`V1Money \| undefined`](../models/v1-money.md) | Optional | - |
| `refundedMoney` | [`V1Money \| undefined`](../models/v1-money.md) | Optional | - |
| `swedishRoundingMoney` | [`V1Money \| undefined`](../models/v1-money.md) | Optional | - |
| `grossSalesMoney` | [`V1Money \| undefined`](../models/v1-money.md) | Optional | - |
| `netSalesMoney` | [`V1Money \| undefined`](../models/v1-money.md) | Optional | - |
| `inclusiveTax` | [`V1PaymentTax[] \| null \| undefined`](../models/v1-payment-tax.md) | Optional | All of the inclusive taxes associated with the payment. |
| `additiveTax` | [`V1PaymentTax[] \| null \| undefined`](../models/v1-payment-tax.md) | Optional | All of the additive taxes associated with the payment. |
| `tender` | [`V1Tender[] \| null \| undefined`](../models/v1-tender.md) | Optional | All of the tenders associated with the payment. |
| `refunds` | [`V1Refund[] \| null \| undefined`](../models/v1-refund.md) | Optional | All of the refunds applied to the payment. Note that the value of all refunds on a payment can exceed the value of all tenders if a merchant chooses to refund money to a tender after previously accepting returned goods as part of an exchange. |
| `itemizations` | [`V1PaymentItemization[] \| null \| undefined`](../models/v1-payment-itemization.md) | Optional | The items purchased in the payment. |
| `surchargeMoney` | [`V1Money \| undefined`](../models/v1-money.md) | Optional | - |
| `surcharges` | [`V1PaymentSurcharge[] \| null \| undefined`](../models/v1-payment-surcharge.md) | Optional | A list of all surcharges associated with the payment. |
| `isPartial` | `boolean \| null \| undefined` | Optional | Indicates whether or not the payment is only partially paid for.<br/>If true, this payment will have the tenders collected so far, but the<br/>itemizations will be empty until the payment is completed. |

## Example (as JSON)

```json
{
  "id": "id2",
  "merchant_id": "merchant_id8",
  "created_at": "created_at0",
  "creator_id": "creator_id2",
  "device": {
    "id": "id6",
    "name": "name6"
  }
}
```

