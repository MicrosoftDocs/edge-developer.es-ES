---
description: Hospedar contenido web en la aplicación Win32 con el control Microsoft Edge WebView2
title: Microsoft Edge WebView2 para aplicaciones Win32
author: MSEdgeTeam
ms.author: msedgedevrel
ms.date: 02/26/2020
ms.topic: reference
ms.prod: microsoft-edge
ms.technology: webview
keywords: IWebView2, IWebView2WebView, webview2, WebView, aplicaciones Win32, Win32, Edge, ICoreWebView2, ICoreWebView2Host, control de explorador, HTML Edge
ms.openlocfilehash: 8fd3533d8f479866989f719be6e48c437fae4ddb
ms.sourcegitcommit: 07cda56425e5fdf90eeb3972e17041261bf720cd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/14/2020
ms.locfileid: "10655421"
---
# interfaz ICoreWebView2HistoryChangedEventHandler 

> [!NOTE]
> Esta interfaz puede modificarse o no estar disponible para las versiones posteriores a la versión de SDK 0.9.430. Consulta la [referencia](../../../webview2-api-reference.md) de la API más reciente.

```
interface ICoreWebView2HistoryChangedEventHandler
  : public IUnknown
```

La persona que llama implementa esta interfaz para recibir el evento HistoryChanged.

## Resumen

 Miembros                        | Descripciones
--------------------------------|---------------------------------------------
[Invoke](#invoke) | No hay argumentos de evento y el parámetro args será null.

## Miembros

#### Invoke 

No hay argumentos de evento y el parámetro args será null.

> invocación [Invoke](#invoke)pública de HRESULT ([ICoreWebView2](ICoreWebView2.md) * WebView, IUnknown * args)
