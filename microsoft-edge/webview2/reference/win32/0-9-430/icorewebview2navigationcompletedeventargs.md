---
description: Hospedar contenido web en la aplicación Win32 con el control Microsoft Edge WebView2
title: Microsoft Edge WebView2 para aplicaciones Win32
author: MSEdgeTeam
ms.author: msedgedevrel
ms.date: 02/24/2020
ms.topic: reference
ms.prod: microsoft-edge
ms.technology: webview
keywords: IWebView2, IWebView2WebView, webview2, WebView, aplicaciones Win32, Win32, Edge, ICoreWebView2, ICoreWebView2Host, control de explorador, HTML Edge
ms.openlocfilehash: f9d24d10d9487198988b4c6d3ad4a941a32dc396
ms.sourcegitcommit: 07cda56425e5fdf90eeb3972e17041261bf720cd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/14/2020
ms.locfileid: "10655475"
---
# interfaz ICoreWebView2NavigationCompletedEventArgs 

> [!NOTE]
> Esta interfaz puede modificarse o no estar disponible para las versiones posteriores a la versión de SDK 0.9.430. Consulta la [referencia](../../../webview2-api-reference.md) de la API más reciente.

```
interface ICoreWebView2NavigationCompletedEventArgs
  : public IUnknown
```

Argumentos de evento para el evento NavigationCompleted.

## Resumen

 Miembros                        | Descripciones
--------------------------------|---------------------------------------------
[get_IsSuccess](#get_issuccess) | Es verdadero cuando la navegación es correcta.
[get_WebErrorStatus](#get_weberrorstatus) | El código de error si se produjo un error en la navegación.
[get_NavigationId](#get_navigationid) | IDENTIFICADOR de la navegación.

## Miembros

#### get_IsSuccess 

Es verdadero cuando la navegación es correcta.

> [get_IsSuccess](#get_issuccess)de HRESULT público (bool * IsSuccess)

Esto es falso para una navegación que terminó en una página de error (errores debidos a ausencia de red, error de búsqueda DNS, el servidor HTTP responde con 4xx), pero también podría ser falso si se llamase a Window. STOP () en la página desplazada.

#### get_WebErrorStatus 

El código de error si se produjo un error en la navegación.

> [get_WebErrorStatus](#get_weberrorstatus)de HRESULT público (CORE_WEBVIEW2_WEB_ERROR_STATUS * CORE_WEBVIEW2_WEB_ERROR_STATUS)

#### get_NavigationId 

IDENTIFICADOR de la navegación.

> [get_NavigationId](#get_navigationid)de HRESULT público (UINT64 * navigation_id)
