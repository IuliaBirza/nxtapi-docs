# Check if Employee Exists

**Endpoint:** `GET /Employee/DoesCompositeIdExist`

## Business Context
This endpoint is part of the **employee onboarding process**.  
It is used to check if an employee already exists in the system by their CompositeId.  
This helps prevent creating duplicate employee records.

## When to Use
- Before creating a new employee during onboarding.
- When validating an import file containing employee IDs.

## Parameters
| Name            | Type   | Required | Description |
|-----------------|--------|----------|-------------|
| `organisationId` | int    | Yes      | The OrganisationId of the current user. |
| `ServiceAgencyId`| int    | Yes      | The service bureau number of the agency. |
| `EmployerId`     | int    | Yes      | Unique employer identifier. |
| `EmployeeId`     | int64  | Yes      | The employee number. |

## Responses
- **200 OK** – Returns `true` if the employee exists, otherwise `false`.
- **400 Bad Request** – Missing or invalid parameters.
- **401 Unauthorized / 403 Forbidden** – Caller not authorized.
- **500 Internal Server Error** – Unexpected issue.

## Example Request
```http
GET /Employee/DoesCompositeIdExist?organisationId=1&ServiceAgencyId=1819&EmployerId=1&EmployeeId=1004
