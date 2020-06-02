---
description: Proporciona información de eventos sobre la solicitud de permiso actual.
title: Objeto PermissionRequestedEvent
author: MSEdgeTeam
ms.author: msedgedevrel
ms.date: 06/04/2018
ms.topic: reference
ms.prod: microsoft-edge
keywords: WebView, aplicaciones para Windows 10, UWP, Edge
ms.openlocfilehash: 07fccebc9e061d4ee7a85e48271aaf9c0574e1ef
ms.sourcegitcommit: 6860234c25a8be863b7f29a54838e78e120dbb62
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/09/2020
ms.locfileid: "10574794"
---
# <span data-ttu-id="4d2f3-104">Objeto PermissionRequestedEvent</span><span class="sxs-lookup"><span data-stu-id="4d2f3-104">PermissionRequestedEvent object</span></span>

<span data-ttu-id="4d2f3-105">Proporciona información de eventos sobre la solicitud de permiso actual.</span><span class="sxs-lookup"><span data-stu-id="4d2f3-105">Provides event information about the current permission request.</span></span>

```js
webview.addEventListener("MSWebViewPermissionRequested", permissionRequestedEventArgs => {
    const permissionRequest = permissionRequestedEventArgs.permissionRequest;
    switch (permissionRequest.type) {
        case "geolocation":
        case "media":
        case "pointerlock":
        case "webnotifications":
        case "screen":
        case "immersiveview":
            if (permissionRequest.uri.startsWith("https://www.example.com/")) {
                // Implicitly trust particular URI
                permissionRequest.allow();
            }
            else if (permissionRequest.uri.startsWith("https://")) {
                // Defer the request so we can ask the user to allow or deny the request
                permissionRequest.defer();
                // Later we'll need to use webview.getDeferredPermissionRequestById for this
                // request and call allow or deny.
                promptUserForDeferredPermissionRequest(
                    permissionRequest.id,
                    permissionRequest.uri,
                    permissionRequest.type);
            }
            else {
                // Implicitly deny non-https URIs
                permissionRequest.deny();
            }
            break;

        case "unlimitedIndexedDBQuota":
        default:
            permissionRequest.deny();
            break;
    }
});
```

## <span data-ttu-id="4d2f3-106">Propiedades</span><span class="sxs-lookup"><span data-stu-id="4d2f3-106">Properties</span></span>

### <span data-ttu-id="4d2f3-107">permissionRequest</span><span class="sxs-lookup"><span data-stu-id="4d2f3-107">permissionRequest</span></span>

<span data-ttu-id="4d2f3-108">Devuelve un objeto **[PermissionRequest](permissionrequest.md)** que representa la solicitud de permiso de usuario final que realiza el contenido de la [vista en WebView](../webview.md).</span><span class="sxs-lookup"><span data-stu-id="4d2f3-108">Returns a **[PermissionRequest](permissionrequest.md)** object that represents the end-user permission request made by content of the [webview](../webview.md).</span></span>

<span data-ttu-id="4d2f3-109">Esta propiedad es de solo lectura.</span><span class="sxs-lookup"><span data-stu-id="4d2f3-109">This property is read-only.</span></span>