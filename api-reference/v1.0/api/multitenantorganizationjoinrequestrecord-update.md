---
title: "Update multiTenantOrganizationJoinRequestRecord"
description: "Join a multitenant organization."
author: "rolyon"
ms.localizationpriority: medium
ms.subservice: "entra-sign-in"
doc_type: apiPageType
---

# Update multiTenantOrganizationJoinRequestRecord
Namespace: microsoft.graph

Join a multitenant organization, after the owner of the multitenant organization has added your tenant to the multitenant organization as pending.

Before a tenant added to a multitenant organization can participate in the multitenant organization, the administrator of the joining tenant must submit a join request.

To allow for asynchronous processing, you must wait **up to 2 hours** before joining a multitenant organization is completed.

[!INCLUDE [national-cloud-support](../../includes/global-only.md)]

## Permissions
Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](/graph/permissions-reference).

<!-- { "blockType": "permissions", "name": "multitenantorganizationjoinrequestrecord_update" } -->
[!INCLUDE [permissions-table](../includes/permissions/multitenantorganizationjoinrequestrecord-update-permissions.md)]

[!INCLUDE [rbac-multitenantorganization-apis-write](../includes/rbac-for-apis/rbac-multitenantorganization-apis-write.md)]

## HTTP request

<!-- {
  "blockType": "ignored"
}
-->
``` http
PATCH /tenantRelationships/multiTenantOrganization/joinRequest
```

## Request headers
|Name|Description|
|:---|:---|
|Authorization|Bearer {token}. Required.|
|Content-Type|application/json. Required.|

## Request body
[!INCLUDE [table-intro](../../includes/update-property-table-intro.md)]


|Property|Type|Description|
|:---|:---|:---|
|addedByTenantId|String|Tenant ID of the Microsoft Entra tenant that added the current tenant to the multitenant organization. To reset a failed join request, set `addedByTenantId` to `00000000-0000-0000-0000-000000000000`. Required.|


## Response

If successful, this method returns a `204 No Content` response code.

A join request might be unsuccessful. The following are some scenarios:

* The joining tenant has not been added to the multitenant organization by its owner.
* The owner or joiner tenant exceeds the maximum number of internal users per tenant.
* The multitenant organization would exceed the maximum number of tenants.
* The joining tenant is already part of a different multitenant organization.

## Examples

### Example 1: Join a multitenant organization

The following example shows a request by the current tenant to join a multitenant organization. It can take a few minutes for the join to complete. If the join succeeds, the state of the tenant is changed to `active`.

#### Request

<!-- {
  "blockType": "request",
  "name": "update_multitenantorganizationjoinrequestrecord"
}
-->
``` http
PATCH https://graph.microsoft.com/v1.0/tenantRelationships/multiTenantOrganization/joinRequest
Content-Type: application/json

{
    "addedByTenantId": "1fd6544e-e994-4de2-9f1b-787b51c7d325"
}
```

#### Response

<!-- {
  "blockType": "response",
  "truncated": true
}
-->
``` http
HTTP/1.1 204 No Content
```

### Example 2: Reset a failed join request

The following example shows a request by the current tenant to reset a failed join request. To reset a failed join request, set `addedByTenantId` to `00000000-0000-0000-0000-000000000000`.

#### Request

<!-- {
  "blockType": "request",
  "name": "update_multitenantorganizationjoinrequestrecord_joinfailed"
}
-->
``` http
PATCH https://graph.microsoft.com/v1.0/tenantRelationships/multiTenantOrganization/joinRequest
Content-Type: application/json

{
    "addedByTenantId": "00000000-0000-0000-0000-000000000000"
}
```

#### Response

<!-- {
  "blockType": "response",
  "truncated": true
}
-->
``` http
HTTP/1.1 204 No Content
```
