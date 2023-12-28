# Orders

```ts
const ordersApi = client.ordersApi;
```

## Class Name

`OrdersApi`

## Methods

* [Create Order](../api/orders.md#create-order)
* [Batch Retrieve Orders](../api/orders.md#batch-retrieve-orders)
* [Calculate Order](../api/orders.md#calculate-order)
* [Clone Order](../api/orders.md#clone-order)
* [Search Orders](../api/orders.md#search-orders)
* [Retrieve Order](../api/orders.md#retrieve-order)
* [Update Order](../api/orders.md#update-order)
* [Pay Order](../api/orders.md#pay-order)


# Create Order

Creates a new [order](../models/order.md) that can include information about products for
purchase and settings to apply to the purchase.

To pay for a created order, see
[Pay for Orders](https://developer.squareup.com/docs/orders-api/pay-for-orders).

You can modify open orders using the [UpdateOrder](../api/orders.md#update-order) endpoint.

```ts
async createOrder(
  body: CreateOrderRequest,
  requestOptions?: RequestOptions
): Promise<ApiResponse<CreateOrderResponse>>
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `body` | [`CreateOrderRequest`](../models/create-order-request.md) | Body, Required | An object containing the fields to POST for the request.<br/><br/>See the corresponding object definition for field details. |
| `requestOptions` | `RequestOptions \| undefined` | Optional | Pass additional request options. |

## Response Type

[`CreateOrderResponse`](../models/create-order-response.md)

## Example Usage

```ts
const body: CreateOrderRequest = {
  order: {
    locationId: '057P5VYJ4A5X1',
    referenceId: 'my-order-001',
    lineItems: [
      {
        quantity: '1',
        name: 'New York Strip Steak',
        basePriceMoney: {
          amount: BigInt(1599),
          currency: 'USD',
        },
      },
      {
        quantity: '2',
        catalogObjectId: 'BEMYCSMIJL46OCDV4KYIKXIB',
        modifiers: [
          {
            catalogObjectId: 'CHQX7Y4KY6N5KINJKZCFURPZ',
          }
        ],
        appliedDiscounts: [
          {
            discountUid: 'one-dollar-off',
          }
        ],
      }
    ],
    taxes: [
      {
        uid: 'state-sales-tax',
        name: 'State Sales Tax',
        percentage: '9',
        scope: 'ORDER',
      }
    ],
    discounts: [
      {
        uid: 'labor-day-sale',
        name: 'Labor Day Sale',
        percentage: '5',
        scope: 'ORDER',
      },
      {
        uid: 'membership-discount',
        catalogObjectId: 'DB7L55ZH2BGWI4H23ULIWOQ7',
        scope: 'ORDER',
      },
      {
        uid: 'one-dollar-off',
        name: 'Sale - $1.00 off',
        amountMoney: {
          amount: BigInt(100),
          currency: 'USD',
        },
        scope: 'LINE_ITEM',
      }
    ],
  },
  idempotencyKey: '8193148c-9586-11e6-99f9-28cfe92138cf',
};

try {
  // @ts-expect-error: unused variables
  // eslint-disable-next-line @typescript-eslint/no-unused-vars
  const { result, ...httpResponse } = await ordersApi.createOrder(body);
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


# Batch Retrieve Orders

Retrieves a set of [orders](../models/order.md) by their IDs.

If a given order ID does not exist, the ID is ignored instead of generating an error.

```ts
async batchRetrieveOrders(
  body: BatchRetrieveOrdersRequest,
  requestOptions?: RequestOptions
): Promise<ApiResponse<BatchRetrieveOrdersResponse>>
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `body` | [`BatchRetrieveOrdersRequest`](../models/batch-retrieve-orders-request.md) | Body, Required | An object containing the fields to POST for the request.<br/><br/>See the corresponding object definition for field details. |
| `requestOptions` | `RequestOptions \| undefined` | Optional | Pass additional request options. |

## Response Type

[`BatchRetrieveOrdersResponse`](../models/batch-retrieve-orders-response.md)

## Example Usage

```ts
const body: BatchRetrieveOrdersRequest = {
  orderIds: [
    'CAISEM82RcpmcFBM0TfOyiHV3es',
    'CAISENgvlJ6jLWAzERDzjyHVybY'
  ],
  locationId: '057P5VYJ4A5X1',
};

try {
  // @ts-expect-error: unused variables
  // eslint-disable-next-line @typescript-eslint/no-unused-vars
  const { result, ...httpResponse } = await ordersApi.batchRetrieveOrders(body);
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


# Calculate Order

Enables applications to preview order pricing without creating an order.

```ts
async calculateOrder(
  body: CalculateOrderRequest,
  requestOptions?: RequestOptions
): Promise<ApiResponse<CalculateOrderResponse>>
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `body` | [`CalculateOrderRequest`](../models/calculate-order-request.md) | Body, Required | An object containing the fields to POST for the request.<br/><br/>See the corresponding object definition for field details. |
| `requestOptions` | `RequestOptions \| undefined` | Optional | Pass additional request options. |

## Response Type

[`CalculateOrderResponse`](../models/calculate-order-response.md)

## Example Usage

```ts
const body: CalculateOrderRequest = {
  order: {
    locationId: 'D7AVYMEAPJ3A3',
    lineItems: [
      {
        quantity: '1',
        name: 'Item 1',
        basePriceMoney: {
          amount: BigInt(500),
          currency: 'USD',
        },
      },
      {
        quantity: '2',
        name: 'Item 2',
        basePriceMoney: {
          amount: BigInt(300),
          currency: 'USD',
        },
      }
    ],
    discounts: [
      {
        name: '50% Off',
        percentage: '50',
        scope: 'ORDER',
      }
    ],
  },
};

try {
  // @ts-expect-error: unused variables
  // eslint-disable-next-line @typescript-eslint/no-unused-vars
  const { result, ...httpResponse } = await ordersApi.calculateOrder(body);
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


# Clone Order

Creates a new order, in the `DRAFT` state, by duplicating an existing order. The newly created order has
only the core fields (such as line items, taxes, and discounts) copied from the original order.

```ts
async cloneOrder(
  body: CloneOrderRequest,
  requestOptions?: RequestOptions
): Promise<ApiResponse<CloneOrderResponse>>
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `body` | [`CloneOrderRequest`](../models/clone-order-request.md) | Body, Required | An object containing the fields to POST for the request.<br/><br/>See the corresponding object definition for field details. |
| `requestOptions` | `RequestOptions \| undefined` | Optional | Pass additional request options. |

## Response Type

[`CloneOrderResponse`](../models/clone-order-response.md)

## Example Usage

```ts
const body: CloneOrderRequest = {
  orderId: 'ZAISEM52YcpmcWAzERDOyiWS123',
  version: 3,
  idempotencyKey: 'UNIQUE_STRING',
};

try {
  // @ts-expect-error: unused variables
  // eslint-disable-next-line @typescript-eslint/no-unused-vars
  const { result, ...httpResponse } = await ordersApi.cloneOrder(body);
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


# Search Orders

Search all orders for one or more locations. Orders include all sales,
returns, and exchanges regardless of how or when they entered the Square
ecosystem (such as Point of Sale, Invoices, and Connect APIs).

`SearchOrders` requests need to specify which locations to search and define a
[SearchOrdersQuery](../models/search-orders-query.md) object that controls
how to sort or filter the results. Your `SearchOrdersQuery` can:

Set filter criteria.
Set the sort order.
Determine whether to return results as complete `Order` objects or as
[OrderEntry](../models/order-entry.md) objects.

Note that details for orders processed with Square Point of Sale while in
offline mode might not be transmitted to Square for up to 72 hours. Offline
orders have a `created_at` value that reflects the time the order was created,
not the time it was subsequently transmitted to Square.

```ts
async searchOrders(
  body: SearchOrdersRequest,
  requestOptions?: RequestOptions
): Promise<ApiResponse<SearchOrdersResponse>>
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `body` | [`SearchOrdersRequest`](../models/search-orders-request.md) | Body, Required | An object containing the fields to POST for the request.<br/><br/>See the corresponding object definition for field details. |
| `requestOptions` | `RequestOptions \| undefined` | Optional | Pass additional request options. |

## Response Type

[`SearchOrdersResponse`](../models/search-orders-response.md)

## Example Usage

```ts
const body: SearchOrdersRequest = {
  locationIds: [
    '057P5VYJ4A5X1',
    '18YC4JDH91E1H'
  ],
  query: {
    filter: {
      stateFilter: {
        states: [
          'COMPLETED'
        ],
      },
      dateTimeFilter: {
        closedAt: {
          startAt: '2018-03-03T20:00:00+00:00',
          endAt: '2019-03-04T21:54:45+00:00',
        },
      },
    },
    sort: {
      sortField: 'CLOSED_AT',
      sortOrder: 'DESC',
    },
  },
  limit: 3,
  returnEntries: true,
};

try {
  // @ts-expect-error: unused variables
  // eslint-disable-next-line @typescript-eslint/no-unused-vars
  const { result, ...httpResponse } = await ordersApi.searchOrders(body);
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


# Retrieve Order

Retrieves an [Order](../models/order.md) by ID.

```ts
async retrieveOrder(
  orderId: string,
  requestOptions?: RequestOptions
): Promise<ApiResponse<RetrieveOrderResponse>>
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `orderId` | `string` | Template, Required | The ID of the order to retrieve. |
| `requestOptions` | `RequestOptions \| undefined` | Optional | Pass additional request options. |

## Response Type

[`RetrieveOrderResponse`](../models/retrieve-order-response.md)

## Example Usage

```ts
const orderId = 'order_id6';

try {
  // @ts-expect-error: unused variables
  // eslint-disable-next-line @typescript-eslint/no-unused-vars
  const { result, ...httpResponse } = await ordersApi.retrieveOrder(orderId);
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


# Update Order

Updates an open [order](../models/order.md) by adding, replacing, or deleting
fields. Orders with a `COMPLETED` or `CANCELED` state cannot be updated.

An `UpdateOrder` request requires the following:

- The `order_id` in the endpoint path, identifying the order to update.
- The latest `version` of the order to update.
- The [sparse order](https://developer.squareup.com/docs/orders-api/manage-orders/update-orders#sparse-order-objects)
  containing only the fields to update and the version to which the update is
  being applied.
- If deleting fields, the [dot notation paths](https://developer.squareup.com/docs/orders-api/manage-orders/update-orders#identifying-fields-to-delete)
  identifying the fields to clear.

To pay for an order, see
[Pay for Orders](https://developer.squareup.com/docs/orders-api/pay-for-orders).

```ts
async updateOrder(
  orderId: string,
  body: UpdateOrderRequest,
  requestOptions?: RequestOptions
): Promise<ApiResponse<UpdateOrderResponse>>
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `orderId` | `string` | Template, Required | The ID of the order to update. |
| `body` | [`UpdateOrderRequest`](../models/update-order-request.md) | Body, Required | An object containing the fields to POST for the request.<br/><br/>See the corresponding object definition for field details. |
| `requestOptions` | `RequestOptions \| undefined` | Optional | Pass additional request options. |

## Response Type

[`UpdateOrderResponse`](../models/update-order-response.md)

## Example Usage

```ts
const orderId = 'order_id6';

const body: UpdateOrderRequest = {};

try {
  // @ts-expect-error: unused variables
  // eslint-disable-next-line @typescript-eslint/no-unused-vars
  const { result, ...httpResponse } = await ordersApi.updateOrder(
  orderId,
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


# Pay Order

Pay for an [order](../models/order.md) using one or more approved [payments](../models/payment.md)
or settle an order with a total of `0`.

The total of the `payment_ids` listed in the request must be equal to the order
total. Orders with a total amount of `0` can be marked as paid by specifying an empty
array of `payment_ids` in the request.

To be used with `PayOrder`, a payment must:

- Reference the order by specifying the `order_id` when [creating the payment](../api/payments.md#create-payment).
  Any approved payments that reference the same `order_id` not specified in the
  `payment_ids` is canceled.
- Be approved with [delayed capture](https://developer.squareup.com/docs/payments-api/take-payments/card-payments/delayed-capture).
  Using a delayed capture payment with `PayOrder` completes the approved payment.

```ts
async payOrder(
  orderId: string,
  body: PayOrderRequest,
  requestOptions?: RequestOptions
): Promise<ApiResponse<PayOrderResponse>>
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `orderId` | `string` | Template, Required | The ID of the order being paid. |
| `body` | [`PayOrderRequest`](../models/pay-order-request.md) | Body, Required | An object containing the fields to POST for the request.<br/><br/>See the corresponding object definition for field details. |
| `requestOptions` | `RequestOptions \| undefined` | Optional | Pass additional request options. |

## Response Type

[`PayOrderResponse`](../models/pay-order-response.md)

## Example Usage

```ts
const orderId = 'order_id6';

const body: PayOrderRequest = {
  idempotencyKey: 'c043a359-7ad9-4136-82a9-c3f1d66dcbff',
  paymentIds: [
    'EnZdNAlWCmfh6Mt5FMNST1o7taB',
    '0LRiVlbXVwe8ozu4KbZxd12mvaB'
  ],
};

try {
  // @ts-expect-error: unused variables
  // eslint-disable-next-line @typescript-eslint/no-unused-vars
  const { result, ...httpResponse } = await ordersApi.payOrder(
  orderId,
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

