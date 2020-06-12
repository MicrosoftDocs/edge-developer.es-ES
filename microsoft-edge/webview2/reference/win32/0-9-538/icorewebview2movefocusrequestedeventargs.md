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
ms.openlocfilehash: c94687868ce11fead5112e1df3fb9a0e0d47d77e
ms.sourcegitcommit: 8dca1c1367853e45a0a975bc89b1818adb117bd4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/08/2020
ms.locfileid: "10699471"
---
# interfaz ICoreWebView2MoveFocusRequestedEventArgs 

```
interface ICoreWebView2MoveFocusRequestedEventArgs
  : public IUnknown
```

Argumentos de evento para el evento MoveFocusRequested.

## Resumen

 Miembros                        | Descripciones
--------------------------------|---------------------------------------------
[get_Handled](#get_handled) | Indicar si la aplicación ha controlado el evento.
[get_Reason](#get_reason) | El motivo de la vista en WebView para activar el evento solicitado MoveFocus.
[put_Handled](#put_handled) | Establecer la propiedad Handled.

## Miembros

#### get_Handled 

Indicar si la aplicación ha controlado el evento.

> [get_Handled](#get_handled)de HRESULT público (bool * Value)

Si la aplicación ha movido el foco a la ubicación deseada, debe establecer la propiedad Handled en TRUE. Cuando la propiedad Handled es false después de que el controlador de eventos devuelva, se realiza una acción predeterminada. La acción predeterminada es intentar buscar la siguiente ventana secundaria de la pestaña detener en la aplicación e intentar mover el foco a esa ventana. Si no hay ninguna otra ventana de este tipo para mover el foco, el foco se reactivará dentro del contenido Web de WebView.

#### get_Reason 

El motivo de la vista en WebView para activar el evento solicitado MoveFocus.

> [get_Reason](#get_reason)de HRESULT público (valor COREWEBVIEW2_MOVE_FOCUS_REASON *)

#### put_Handled 

Establecer la propiedad Handled.

> [put_Handled](#put_handled)de HRESULT público (valor bool)
