
# Gift Card Activity Unblock

Represents details about an `UNBLOCK` [gift card activity type](../models/gift-card-activity-type.md).

## Structure

`GiftCardActivityUnblock`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `reason` | `string` | Required, Constant | Indicates the reason for unblocking a [gift card](../models/gift-card.md).<br/>**Default**: `'CHARGEBACK_UNBLOCK'` |

## Example (as JSON)

```json
{
  "reason": "CHARGEBACK_UNBLOCK"
}
```

