
# Checkout Merchant Settings Payment Methods Afterpay Clearpay

The settings allowed for AfterpayClearpay.

## Structure

`CheckoutMerchantSettingsPaymentMethodsAfterpayClearpay`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `orderEligibilityRange` | [`CheckoutMerchantSettingsPaymentMethodsAfterpayClearpayEligibilityRange \| undefined`](../models/checkout-merchant-settings-payment-methods-afterpay-clearpay-eligibility-range.md) | Optional | A range of purchase price that qualifies. |
| `itemEligibilityRange` | [`CheckoutMerchantSettingsPaymentMethodsAfterpayClearpayEligibilityRange \| undefined`](../models/checkout-merchant-settings-payment-methods-afterpay-clearpay-eligibility-range.md) | Optional | A range of purchase price that qualifies. |
| `enabled` | `boolean \| undefined` | Optional | Indicates whether the payment method is enabled for the account. |

## Example (as JSON)

```json
{
  "order_eligibility_range": {
    "min": {
      "amount": 34,
      "currency": "ISK"
    },
    "max": {
      "amount": 140,
      "currency": "OMR"
    }
  },
  "item_eligibility_range": {
    "min": {
      "amount": 34,
      "currency": "ISK"
    },
    "max": {
      "amount": 140,
      "currency": "OMR"
    }
  },
  "enabled": false
}
```

