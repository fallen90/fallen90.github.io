
# Delete Booking Custom Attribute Definition Response

Represents a [DeleteBookingCustomAttributeDefinition](../api/booking-custom-attributes.md#delete-booking-custom-attribute-definition) response
containing error messages when errors occurred during the request. The successful response does not contain any payload.

## Structure

`DeleteBookingCustomAttributeDefinitionResponse`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `errors` | [`Error[] \| undefined`](../models/error.md) | Optional | Any errors that occurred during the request. |

## Example (as JSON)

```json
{
  "errors": []
}
```

