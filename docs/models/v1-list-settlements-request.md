
# V1 List Settlements Request

## Structure

`V1ListSettlementsRequest`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `order` | [`string \| undefined`](../models/sort-order.md) | Optional | The order (e.g., chronological or alphabetical) in which results from a request are returned. |
| `beginTime` | `string \| null \| undefined` | Optional | The beginning of the requested reporting period, in ISO 8601 format. If this value is before January 1, 2013 (2013-01-01T00:00:00Z), this endpoint returns an error. Default value: The current time minus one year. |
| `endTime` | `string \| null \| undefined` | Optional | The end of the requested reporting period, in ISO 8601 format. If this value is more than one year greater than begin_time, this endpoint returns an error. Default value: The current time. |
| `limit` | `number \| null \| undefined` | Optional | The maximum number of settlements to return in a single response. This value cannot exceed 200. |
| `status` | [`string \| undefined`](../models/v1-list-settlements-request-status.md) | Optional | - |
| `batchToken` | `string \| null \| undefined` | Optional | A pagination cursor to retrieve the next set of results for your<br/>original query to the endpoint. |

## Example (as JSON)

```json
{
  "order": "DESC",
  "begin_time": "begin_time8",
  "end_time": "end_time2",
  "limit": 226,
  "status": "SENT"
}
```

