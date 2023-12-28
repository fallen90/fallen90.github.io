# Customers

```ts
const customersApi = client.customersApi;
```

## Class Name

`CustomersApi`

## Methods

* [List Customers](../api/customers.md#list-customers)
* [Create Customer](../api/customers.md#create-customer)
* [Search Customers](../api/customers.md#search-customers)
* [Delete Customer](../api/customers.md#delete-customer)
* [Retrieve Customer](../api/customers.md#retrieve-customer)
* [Update Customer](../api/customers.md#update-customer)
* [Create Customer Card](../api/customers.md#create-customer-card)
* [Delete Customer Card](../api/customers.md#delete-customer-card)
* [Remove Group From Customer](../api/customers.md#remove-group-from-customer)
* [Add Group to Customer](../api/customers.md#add-group-to-customer)


# List Customers

Lists customer profiles associated with a Square account.

Under normal operating conditions, newly created or updated customer profiles become available
for the listing operation in well under 30 seconds. Occasionally, propagation of the new or updated
profiles can take closer to one minute or longer, especially during network incidents and outages.

```ts
async listCustomers(
  cursor?: string,
  limit?: number,
  sortField?: string,
  sortOrder?: string,
  count?: boolean,
  requestOptions?: RequestOptions
): Promise<ApiResponse<ListCustomersResponse>>
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `cursor` | `string \| undefined` | Query, Optional | A pagination cursor returned by a previous call to this endpoint.<br/>Provide this cursor to retrieve the next set of results for your original query.<br/><br/>For more information, see [Pagination](https://developer.squareup.com/docs/build-basics/common-api-patterns/pagination). |
| `limit` | `number \| undefined` | Query, Optional | The maximum number of results to return in a single page. This limit is advisory. The response might contain more or fewer results.<br/>If the specified limit is less than 1 or greater than 100, Square returns a `400 VALUE_TOO_LOW` or `400 VALUE_TOO_HIGH` error. The default value is 100.<br/><br/>For more information, see [Pagination](https://developer.squareup.com/docs/build-basics/common-api-patterns/pagination). |
| `sortField` | [`string \| undefined`](../models/customer-sort-field.md) | Query, Optional | Indicates how customers should be sorted.<br/><br/>The default value is `DEFAULT`. |
| `sortOrder` | [`string \| undefined`](../models/sort-order.md) | Query, Optional | Indicates whether customers should be sorted in ascending (`ASC`) or<br/>descending (`DESC`) order.<br/><br/>The default value is `ASC`. |
| `count` | `boolean \| undefined` | Query, Optional | Indicates whether to return the total count of customers in the `count` field of the response.<br/><br/>The default value is `false`.<br/>**Default**: `false` |
| `requestOptions` | `RequestOptions \| undefined` | Optional | Pass additional request options. |

## Response Type

[`ListCustomersResponse`](../models/list-customers-response.md)

## Example Usage

```ts
const count = false;

try {
  // @ts-expect-error: unused variables
  // eslint-disable-next-line @typescript-eslint/no-unused-vars
  const { result, ...httpResponse } = await customersApi.listCustomers(
  undefined,
  undefined,
  undefined,
  undefined,
  count
);
  // Get more response info...
  // const { statusCode, headers } = httpResponse;
} catch (error) {
  if (error instanceof ApiError) {
    // @ts-expect-error: unused variables
    // eslint-disable-next-line @typescript-eslint/no-unused-vars
    const errors = error.result;
    // const { statusCode, headers } = error;
  }
}
```


# Create Customer

Creates a new customer for a business.

You must provide at least one of the following values in your request to this
endpoint:

- `given_name`
- `family_name`
- `company_name`
- `email_address`
- `phone_number`

```ts
async createCustomer(
  body: CreateCustomerRequest,
  requestOptions?: RequestOptions
): Promise<ApiResponse<CreateCustomerResponse>>
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `body` | [`CreateCustomerRequest`](../models/create-customer-request.md) | Body, Required | An object containing the fields to POST for the request.<br/><br/>See the corresponding object definition for field details. |
| `requestOptions` | `RequestOptions \| undefined` | Optional | Pass additional request options. |

## Response Type

[`CreateCustomerResponse`](../models/create-customer-response.md)

## Example Usage

```ts
const body: CreateCustomerRequest = {
  givenName: 'Amelia',
  familyName: 'Earhart',
  emailAddress: 'Amelia.Earhart@example.com',
  address: {
    addressLine1: '500 Electric Ave',
    addressLine2: 'Suite 600',
    locality: 'New York',
    administrativeDistrictLevel1: 'NY',
    postalCode: '10003',
    country: 'US',
  },
  phoneNumber: '+1-212-555-4240',
  referenceId: 'YOUR_REFERENCE_ID',
  note: 'a customer',
};

try {
  // @ts-expect-error: unused variables
  // eslint-disable-next-line @typescript-eslint/no-unused-vars
  const { result, ...httpResponse } = await customersApi.createCustomer(body);
  // Get more response info...
  // const { statusCode, headers } = httpResponse;
} catch (error) {
  if (error instanceof ApiError) {
    // @ts-expect-error: unused variables
    // eslint-disable-next-line @typescript-eslint/no-unused-vars
    const errors = error.result;
    // const { statusCode, headers } = error;
  }
}
```


# Search Customers

Searches the customer profiles associated with a Square account using one or more supported query filters.

Calling `SearchCustomers` without any explicit query filter returns all
customer profiles ordered alphabetically based on `given_name` and
`family_name`.

Under normal operating conditions, newly created or updated customer profiles become available
for the search operation in well under 30 seconds. Occasionally, propagation of the new or updated
profiles can take closer to one minute or longer, especially during network incidents and outages.

```ts
async searchCustomers(
  body: SearchCustomersRequest,
  requestOptions?: RequestOptions
): Promise<ApiResponse<SearchCustomersResponse>>
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `body` | [`SearchCustomersRequest`](../models/search-customers-request.md) | Body, Required | An object containing the fields to POST for the request.<br/><br/>See the corresponding object definition for field details. |
| `requestOptions` | `RequestOptions \| undefined` | Optional | Pass additional request options. |

## Response Type

[`SearchCustomersResponse`](../models/search-customers-response.md)

## Example Usage

```ts
const body: SearchCustomersRequest = {
  limit: BigInt(2),
  query: {
    filter: {
      creationSource: {
        values: [
          'THIRD_PARTY'
        ],
        rule: 'INCLUDE',
      },
      createdAt: {
        startAt: '2018-01-01T00:00:00-00:00',
        endAt: '2018-02-01T00:00:00-00:00',
      },
      emailAddress: {
        fuzzy: 'example.com',
      },
      groupIds: {
        all: [
          '545AXB44B4XXWMVQ4W8SBT3HHF'
        ],
      },
    },
    sort: {
      field: 'CREATED_AT',
      order: 'ASC',
    },
  },
};

try {
  // @ts-expect-error: unused variables
  // eslint-disable-next-line @typescript-eslint/no-unused-vars
  const { result, ...httpResponse } = await customersApi.searchCustomers(body);
  // Get more response info...
  // const { statusCode, headers } = httpResponse;
} catch (error) {
  if (error instanceof ApiError) {
    // @ts-expect-error: unused variables
    // eslint-disable-next-line @typescript-eslint/no-unused-vars
    const errors = error.result;
    // const { statusCode, headers } = error;
  }
}
```


# Delete Customer

Deletes a customer profile from a business. This operation also unlinks any associated cards on file.

As a best practice, include the `version` field in the request to enable [optimistic concurrency](https://developer.squareup.com/docs/build-basics/common-api-patterns/optimistic-concurrency) control.
If included, the value must be set to the current version of the customer profile.

To delete a customer profile that was created by merging existing profiles, you must use the ID of the newly created profile.

```ts
async deleteCustomer(
  customerId: string,
  version?: bigint,
  requestOptions?: RequestOptions
): Promise<ApiResponse<DeleteCustomerResponse>>
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `customerId` | `string` | Template, Required | The ID of the customer to delete. |
| `version` | `bigint \| undefined` | Query, Optional | The current version of the customer profile.<br/><br/>As a best practice, you should include this parameter to enable [optimistic concurrency](https://developer.squareup.com/docs/build-basics/common-api-patterns/optimistic-concurrency) control.  For more information, see [Delete a customer profile](https://developer.squareup.com/docs/customers-api/use-the-api/keep-records#delete-customer-profile). |
| `requestOptions` | `RequestOptions \| undefined` | Optional | Pass additional request options. |

## Response Type

[`DeleteCustomerResponse`](../models/delete-customer-response.md)

## Example Usage

```ts
const customerId = 'customer_id8';

try {
  // @ts-expect-error: unused variables
  // eslint-disable-next-line @typescript-eslint/no-unused-vars
  const { result, ...httpResponse } = await customersApi.deleteCustomer(customerId);
  // Get more response info...
  // const { statusCode, headers } = httpResponse;
} catch (error) {
  if (error instanceof ApiError) {
    // @ts-expect-error: unused variables
    // eslint-disable-next-line @typescript-eslint/no-unused-vars
    const errors = error.result;
    // const { statusCode, headers } = error;
  }
}
```


# Retrieve Customer

Returns details for a single customer.

```ts
async retrieveCustomer(
  customerId: string,
  requestOptions?: RequestOptions
): Promise<ApiResponse<RetrieveCustomerResponse>>
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `customerId` | `string` | Template, Required | The ID of the customer to retrieve. |
| `requestOptions` | `RequestOptions \| undefined` | Optional | Pass additional request options. |

## Response Type

[`RetrieveCustomerResponse`](../models/retrieve-customer-response.md)

## Example Usage

```ts
const customerId = 'customer_id8';

try {
  // @ts-expect-error: unused variables
  // eslint-disable-next-line @typescript-eslint/no-unused-vars
  const { result, ...httpResponse } = await customersApi.retrieveCustomer(customerId);
  // Get more response info...
  // const { statusCode, headers } = httpResponse;
} catch (error) {
  if (error instanceof ApiError) {
    // @ts-expect-error: unused variables
    // eslint-disable-next-line @typescript-eslint/no-unused-vars
    const errors = error.result;
    // const { statusCode, headers } = error;
  }
}
```


# Update Customer

Updates a customer profile. This endpoint supports sparse updates, so only new or changed fields are required in the request.
To add or update a field, specify the new value. To remove a field, specify `null` and include the `X-Clear-Null` header set to `true`
(recommended) or specify an empty string (string fields only).

As a best practice, include the `version` field in the request to enable [optimistic concurrency](https://developer.squareup.com/docs/build-basics/common-api-patterns/optimistic-concurrency) control.
If included, the value must be set to the current version of the customer profile.

To update a customer profile that was created by merging existing profiles, you must use the ID of the newly created profile.

You cannot use this endpoint to change cards on file. To make changes, use the [Cards API](../api/cards.md) or [Gift Cards API](../api/gift-cards.md).

```ts
async updateCustomer(
  customerId: string,
  body: UpdateCustomerRequest,
  requestOptions?: RequestOptions
): Promise<ApiResponse<UpdateCustomerResponse>>
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `customerId` | `string` | Template, Required | The ID of the customer to update. |
| `body` | [`UpdateCustomerRequest`](../models/update-customer-request.md) | Body, Required | An object containing the fields to POST for the request.<br/><br/>See the corresponding object definition for field details. |
| `requestOptions` | `RequestOptions \| undefined` | Optional | Pass additional request options. |

## Response Type

[`UpdateCustomerResponse`](../models/update-customer-response.md)

## Example Usage

```ts
const customerId = 'customer_id8';

const body: UpdateCustomerRequest = {
  emailAddress: 'New.Amelia.Earhart@example.com',
  phoneNumber: '',
  note: 'updated customer note',
  version: BigInt(2),
};

try {
  // @ts-expect-error: unused variables
  // eslint-disable-next-line @typescript-eslint/no-unused-vars
  const { result, ...httpResponse } = await customersApi.updateCustomer(
  customerId,
  body
);
  // Get more response info...
  // const { statusCode, headers } = httpResponse;
} catch (error) {
  if (error instanceof ApiError) {
    // @ts-expect-error: unused variables
    // eslint-disable-next-line @typescript-eslint/no-unused-vars
    const errors = error.result;
    // const { statusCode, headers } = error;
  }
}
```


# Create Customer Card

**This endpoint is deprecated.**

Adds a card on file to an existing customer.

As with charges, calls to `CreateCustomerCard` are idempotent. Multiple
calls with the same card nonce return the same card record that was created
with the provided nonce during the _first_ call.

```ts
async createCustomerCard(
  customerId: string,
  body: CreateCustomerCardRequest,
  requestOptions?: RequestOptions
): Promise<ApiResponse<CreateCustomerCardResponse>>
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `customerId` | `string` | Template, Required | The Square ID of the customer profile the card is linked to. |
| `body` | [`CreateCustomerCardRequest`](../models/create-customer-card-request.md) | Body, Required | An object containing the fields to POST for the request.<br/><br/>See the corresponding object definition for field details. |
| `requestOptions` | `RequestOptions \| undefined` | Optional | Pass additional request options. |

## Response Type

[`CreateCustomerCardResponse`](../models/create-customer-card-response.md)

## Example Usage

```ts
const customerId = 'customer_id8';

const body: CreateCustomerCardRequest = {
  cardNonce: 'YOUR_CARD_NONCE',
  billingAddress: {
    addressLine1: '500 Electric Ave',
    addressLine2: 'Suite 600',
    locality: 'New York',
    administrativeDistrictLevel1: 'NY',
    postalCode: '10003',
    country: 'US',
  },
  cardholderName: 'Amelia Earhart',
};

try {
  // @ts-expect-error: unused variables
  // eslint-disable-next-line @typescript-eslint/no-unused-vars
  const { result, ...httpResponse } = await customersApi.createCustomerCard(
  customerId,
  body
);
  // Get more response info...
  // const { statusCode, headers } = httpResponse;
} catch (error) {
  if (error instanceof ApiError) {
    // @ts-expect-error: unused variables
    // eslint-disable-next-line @typescript-eslint/no-unused-vars
    const errors = error.result;
    // const { statusCode, headers } = error;
  }
}
```


# Delete Customer Card

**This endpoint is deprecated.**

Removes a card on file from a customer.

```ts
async deleteCustomerCard(
  customerId: string,
  cardId: string,
  requestOptions?: RequestOptions
): Promise<ApiResponse<DeleteCustomerCardResponse>>
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `customerId` | `string` | Template, Required | The ID of the customer that the card on file belongs to. |
| `cardId` | `string` | Template, Required | The ID of the card on file to delete. |
| `requestOptions` | `RequestOptions \| undefined` | Optional | Pass additional request options. |

## Response Type

[`DeleteCustomerCardResponse`](../models/delete-customer-card-response.md)

## Example Usage

```ts
const customerId = 'customer_id8';

const cardId = 'card_id4';

try {
  // @ts-expect-error: unused variables
  // eslint-disable-next-line @typescript-eslint/no-unused-vars
  const { result, ...httpResponse } = await customersApi.deleteCustomerCard(
  customerId,
  cardId
);
  // Get more response info...
  // const { statusCode, headers } = httpResponse;
} catch (error) {
  if (error instanceof ApiError) {
    // @ts-expect-error: unused variables
    // eslint-disable-next-line @typescript-eslint/no-unused-vars
    const errors = error.result;
    // const { statusCode, headers } = error;
  }
}
```


# Remove Group From Customer

Removes a group membership from a customer.

The customer is identified by the `customer_id` value
and the customer group is identified by the `group_id` value.

```ts
async removeGroupFromCustomer(
  customerId: string,
  groupId: string,
  requestOptions?: RequestOptions
): Promise<ApiResponse<RemoveGroupFromCustomerResponse>>
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `customerId` | `string` | Template, Required | The ID of the customer to remove from the group. |
| `groupId` | `string` | Template, Required | The ID of the customer group to remove the customer from. |
| `requestOptions` | `RequestOptions \| undefined` | Optional | Pass additional request options. |

## Response Type

[`RemoveGroupFromCustomerResponse`](../models/remove-group-from-customer-response.md)

## Example Usage

```ts
const customerId = 'customer_id8';

const groupId = 'group_id0';

try {
  // @ts-expect-error: unused variables
  // eslint-disable-next-line @typescript-eslint/no-unused-vars
  const { result, ...httpResponse } = await customersApi.removeGroupFromCustomer(
  customerId,
  groupId
);
  // Get more response info...
  // const { statusCode, headers } = httpResponse;
} catch (error) {
  if (error instanceof ApiError) {
    // @ts-expect-error: unused variables
    // eslint-disable-next-line @typescript-eslint/no-unused-vars
    const errors = error.result;
    // const { statusCode, headers } = error;
  }
}
```


# Add Group to Customer

Adds a group membership to a customer.

The customer is identified by the `customer_id` value
and the customer group is identified by the `group_id` value.

```ts
async addGroupToCustomer(
  customerId: string,
  groupId: string,
  requestOptions?: RequestOptions
): Promise<ApiResponse<AddGroupToCustomerResponse>>
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `customerId` | `string` | Template, Required | The ID of the customer to add to a group. |
| `groupId` | `string` | Template, Required | The ID of the customer group to add the customer to. |
| `requestOptions` | `RequestOptions \| undefined` | Optional | Pass additional request options. |

## Response Type

[`AddGroupToCustomerResponse`](../models/add-group-to-customer-response.md)

## Example Usage

```ts
const customerId = 'customer_id8';

const groupId = 'group_id0';

try {
  // @ts-expect-error: unused variables
  // eslint-disable-next-line @typescript-eslint/no-unused-vars
  const { result, ...httpResponse } = await customersApi.addGroupToCustomer(
  customerId,
  groupId
);
  // Get more response info...
  // const { statusCode, headers } = httpResponse;
} catch (error) {
  if (error instanceof ApiError) {
    // @ts-expect-error: unused variables
    // eslint-disable-next-line @typescript-eslint/no-unused-vars
    const errors = error.result;
    // const { statusCode, headers } = error;
  }
}
```

