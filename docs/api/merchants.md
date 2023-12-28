# Merchants

```ts
const merchantsApi = client.merchantsApi;
```

## Class Name

`MerchantsApi`

## Methods

* [List Merchants](../api/merchants.md#list-merchants)
* [Retrieve Merchant](../api/merchants.md#retrieve-merchant)


# List Merchants

Provides details about the merchant associated with a given access token.

The access token used to connect your application to a Square seller is associated
with a single merchant. That means that `ListMerchants` returns a list
with a single `Merchant` object. You can specify your personal access token
to get your own merchant information or specify an OAuth token to get the
information for the merchant that granted your application access.

If you know the merchant ID, you can also use the [RetrieveMerchant](../api/merchants.md#retrieve-merchant)
endpoint to retrieve the merchant information.

```ts
async listMerchants(
  cursor?: number,
  requestOptions?: RequestOptions
): Promise<ApiResponse<ListMerchantsResponse>>
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `cursor` | `number \| undefined` | Query, Optional | The cursor generated by the previous response. |
| `requestOptions` | `RequestOptions \| undefined` | Optional | Pass additional request options. |

## Response Type

[`ListMerchantsResponse`](../models/list-merchants-response.md)

## Example Usage

```ts
try {
  // @ts-expect-error: unused variables
  // eslint-disable-next-line @typescript-eslint/no-unused-vars
  const { result, ...httpResponse } = await merchantsApi.listMerchants();
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


# Retrieve Merchant

Retrieves the `Merchant` object for the given `merchant_id`.

```ts
async retrieveMerchant(
  merchantId: string,
  requestOptions?: RequestOptions
): Promise<ApiResponse<RetrieveMerchantResponse>>
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `merchantId` | `string` | Template, Required | The ID of the merchant to retrieve. If the string "me" is supplied as the ID,<br/>then retrieve the merchant that is currently accessible to this call. |
| `requestOptions` | `RequestOptions \| undefined` | Optional | Pass additional request options. |

## Response Type

[`RetrieveMerchantResponse`](../models/retrieve-merchant-response.md)

## Example Usage

```ts
const merchantId = 'merchant_id0';

try {
  // @ts-expect-error: unused variables
  // eslint-disable-next-line @typescript-eslint/no-unused-vars
  const { result, ...httpResponse } = await merchantsApi.retrieveMerchant(merchantId);
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
