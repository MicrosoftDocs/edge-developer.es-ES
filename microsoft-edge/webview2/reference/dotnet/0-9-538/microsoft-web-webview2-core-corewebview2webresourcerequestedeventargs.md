---
description: Hospedar contenido web en la aplicación Win32 con el control Microsoft Edge WebView2
title: Microsoft Edge WebView2 para aplicaciones Win32
author: MSEdgeTeam
ms.author: msedgedevrel
ms.date: 06/05/2020
ms.topic: reference
ms.prod: microsoft-edge
ms.technology: webview
keywords: IWebView2, IWebView2WebView, webview2, WebView, aplicaciones Win32, Win32, Edge, ICoreWebView2, ICoreWebView2Controller, control de explorador, HTML Edge
ms.openlocfilehash: 3d85b1116a3f75058bda59f1c374700555b42a5e
ms.sourcegitcommit: 8dca1c1367853e45a0a975bc89b1818adb117bd4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/08/2020
ms.locfileid: "10699442"
---
# Clase Microsoft. Web. WebView2. Core. CoreWebView2WebResourceRequestedEventArgs 

Espacio de nombres: Microsoft. Web. WebView2. Core \
Ensamblado: Microsoft. Web. WebView2. Core. dll

Argumentos de evento para el evento WebResourceRequested.

## Resumen

 Miembros                        | Descripciones
--------------------------------|---------------------------------------------
[Solicitud](#request) | La solicitud HTTP.
[ResourceContext](#resourcecontext) | Los contextos de solicitud de recursos Web.
[Respuesta](#response) | La respuesta HTTP.
[GetDeferral](#getdeferral) | Obtén un objeto CoreWebView2Deferral y coloca el evento en un estado diferido.

## Miembros

#### Solicitud 

La solicitud HTTP.

> [solicitud](#request) de HttpRequestMessage pública

#### ResourceContext 

Los contextos de solicitud de recursos Web.

> [CoreWebView2WebResourceContext](./namespace-microsoft-web-webview2-core.md) pública [ResourceContext](#resourcecontext)

#### Respuesta 

La respuesta HTTP.

> [respuesta](#response) de HttpResponseMessage pública

#### GetDeferral 

Obtén un objeto CoreWebView2Deferral y coloca el evento en un estado diferido.

> Public [CoreWebView2Deferral](microsoft-web-webview2-core-corewebview2deferral.md) [GetDeferral](#getdeferral)()

Puede usar el objeto CoreWebView2Deferral para completar la solicitud de red más adelante.
