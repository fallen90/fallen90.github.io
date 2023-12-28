# Employees

```ts
const employeesApi = client.employeesApi;
```

## Class Name

`EmployeesApi`

## Methods

* [List Employees](../api/employees.md#list-employees)
* [Retrieve Employee](../api/employees.md#retrieve-employee)


# List Employees

**This endpoint is deprecated.**

```ts
async listEmployees(
  locationId?: string,
  status?: string,
  limit?: number,
  cursor?: string,
  requestOptions?: RequestOptions
): Promise<ApiResponse<ListEmployeesResponse>>
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `locationId` | `string \| undefined` | Query, Optional | - |
| `status` | [`string \| undefined`](../models/employee-status.md) | Query, Optional | Specifies the EmployeeStatus to filter the employee by. |
| `limit` | `number \| undefined` | Query, Optional | The number of employees to be returned on each page. |
| `cursor` | `string \| undefined` | Query, Optional | The token required to retrieve the specified page of results. |
| `requestOptions` | `RequestOptions \| undefined` | Optional | Pass additional request options. |

## Response Type

[`ListEmployeesResponse`](../models/list-employees-response.md)

## Example Usage

```ts
try {
  // @ts-expect-error: unused variables
  // eslint-disable-next-line @typescript-eslint/no-unused-vars
  const { result, ...httpResponse } = await employeesApi.listEmployees();
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


# Retrieve Employee

**This endpoint is deprecated.**

```ts
async retrieveEmployee(
  id: string,
  requestOptions?: RequestOptions
): Promise<ApiResponse<RetrieveEmployeeResponse>>
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `id` | `string` | Template, Required | UUID for the employee that was requested. |
| `requestOptions` | `RequestOptions \| undefined` | Optional | Pass additional request options. |

## Response Type

[`RetrieveEmployeeResponse`](../models/retrieve-employee-response.md)

## Example Usage

```ts
const id = 'id0';

try {
  // @ts-expect-error: unused variables
  // eslint-disable-next-line @typescript-eslint/no-unused-vars
  const { result, ...httpResponse } = await employeesApi.retrieveEmployee(id);
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

