---
title: "Get multiTenantOrganizationIdentitySyncPolicyTemplate"
description: "Get the cross-tenant access policy template with user synchronization settings for a multitenant organization."
author: "rolyon"
ms.localizationpriority: medium
ms.subservice: "entra-sign-in"
doc_type: apiPageType
---

# Get multiTenantOrganizationIdentitySyncPolicyTemplate
Namespace: microsoft.graph

Get the cross-tenant access policy template with user synchronization settings for a multitenant organization.

[!INCLUDE [national-cloud-support](../../includes/global-only.md)]

## Permissions
Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](/graph/permissions-reference).

<!-- { "blockType": "permissions", "name": "multitenantorganizationidentitysyncpolicytemplate_get" } -->
[!INCLUDE [permissions-table](../includes/permissions/multitenantorganizationidentitysyncpolicytemplate-get-permissions.md)]

[!INCLUDE [rbac-multitenantorganization-apis-read](../includes/rbac-for-apis/rbac-multitenantorganization-apis-read.md)]

## HTTP request

<!-- {
  "blockType": "ignored"
}
-->
``` http
GET /policies/crossTenantAccessPolicy/templates/multiTenantOrganizationIdentitySynchronization
```

## Optional query parameters
This method supports the `$select` OData query parameter to help customize the response. For general information, see [OData query parameters](/graph/query-parameters).

## Request headers
|Name|Description|
|:---|:---|
|Authorization|Bearer {token}. Required.|

## Request body
Don't supply a request body for this method.

## Response

If successful, this method returns a `200 OK` response code and a [multiTenantOrganizationIdentitySyncPolicyTemplate](../resources/multitenantorganizationidentitysyncpolicytemplate.md) object in the response body.

## Examples

The following example gets the user synchronization settings of the template.

### Request

<!-- {
  "blockType": "request",
  "name": "get_multitenantorganizationidentitysyncpolicytemplate"
}
-->
``` http
GET https://graph.microsoft.com/v1.0/policies/crossTenantAccessPolicy/templates/multiTenantOrganizationIdentitySynchronization
```

### Response

The following example response shows the unconfigured (or reset) state of the cross-tenant access policy template for user synchronization settings for multitenant organization tenants.

<!-- {
  "blockType": "response",
  "truncated": true,
  "@odata.type": "microsoft.graph.multiTenantOrganizationIdentitySyncPolicyTemplate"
}
-->
``` http
HTTP/1.1 200 OK
Content-Type: application/json

{
    "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#policies/crossTenantAccessPolicy/templates/multiTenantOrganizationIdentitySynchronization/$entity",
    "templateApplicationLevel": "newPartners,existingPartners",
    "id": "0e7aad84-cb46-4b8e-a881-522ef25939f1",
    "userSyncInbound": {
        "isSyncAllowed": null
    }
}
```

The following example response shows a configured state of the cross-tenant access policy template for user synchronization settings, after inbound user synchronization has been configured.

``` http
HTTP/1.1 200 OK
Content-Type: application/json

{
    "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#policies/crossTenantAccessPolicy/templates/multiTenantOrganizationIdentitySynchronization/$entity",
    "id": "e1a11ff3-01f1-4c48-9784-b9d931571474",
    "templateApplicationLevel": "newPartners,existingPartners",
    "userSyncInbound": {
        "isSyncAllowed": true
    }
}
```
