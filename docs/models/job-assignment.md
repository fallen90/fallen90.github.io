
# Job Assignment

An object describing a job that a team member is assigned to.

## Structure

`JobAssignment`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `jobTitle` | `string` | Required | The title of the job.<br/>**Constraints**: *Minimum Length*: `1` |
| `payType` | [`string`](../models/job-assignment-pay-type.md) | Required | Enumerates the possible pay types that a job can be assigned. |
| `hourlyRate` | [`Money \| undefined`](../models/money.md) | Optional | Represents an amount of money. `Money` fields can be signed or unsigned.<br/>Fields that do not explicitly define whether they are signed or unsigned are<br/>considered unsigned and can only hold positive amounts. For signed fields, the<br/>sign of the value indicates the purpose of the money transfer. See<br/>[Working with Monetary Amounts](https://developer.squareup.com/docs/build-basics/working-with-monetary-amounts)<br/>for more information. |
| `annualRate` | [`Money \| undefined`](../models/money.md) | Optional | Represents an amount of money. `Money` fields can be signed or unsigned.<br/>Fields that do not explicitly define whether they are signed or unsigned are<br/>considered unsigned and can only hold positive amounts. For signed fields, the<br/>sign of the value indicates the purpose of the money transfer. See<br/>[Working with Monetary Amounts](https://developer.squareup.com/docs/build-basics/working-with-monetary-amounts)<br/>for more information. |
| `weeklyHours` | `number \| null \| undefined` | Optional | The planned hours per week for the job. Set if the job `PayType` is `SALARY`. |

## Example (as JSON)

```json
{
  "job_title": "job_title6",
  "pay_type": "NONE",
  "hourly_rate": {
    "amount": 172,
    "currency": "OMR"
  },
  "annual_rate": {
    "amount": 232,
    "currency": "SBD"
  },
  "weekly_hours": 120
}
```
