---
description: Hospedar contenido web en la aplicación Win32 con el control Microsoft Edge WebView2
title: Microsoft Edge WebView2 para aplicaciones Win32
author: MSEdgeTeam
ms.author: msedgedevrel
ms.date: 12/09/2019
ms.topic: reference
ms.prod: microsoft-edge
ms.technology: webview
keywords: IWebView2, IWebView2WebView, webview2, WebView, aplicaciones Win32, Win32, Edge
ms.openlocfilehash: 5b15d6205306e558d1d8709cceed8b7a68a77bce
ms.sourcegitcommit: 07cda56425e5fdf90eeb3972e17041261bf720cd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/14/2020
ms.locfileid: "10655277"
---
# interfaz IWebView2AcceleratorKeyPressedEventArgs 

> [!NOTE]
> Esta interfaz puede modificarse o no estar disponible para las versiones posteriores a la versión de SDK 0.8.355. Consulta la [referencia](../../../webview2-api-reference.md) de la API más reciente.

```
interface IWebView2AcceleratorKeyPressedEventArgs
  : public IUnknown
```

Argumentos de evento para el evento AcceleratorKeyPressed.

## Resumen

 Miembros                        | Descripciones
--------------------------------|---------------------------------------------
[get_KeyEventType](#get_keyeventtype) | El tipo de evento de clave que causó el evento que se va a desencadenar.
[get_VirtualKey](#get_virtualkey) | El código de tecla virtual Win32 de la tecla que se ha presionado o soltado.
[get_KeyEventLParam](#get_keyeventlparam) | El valor LPARAM que acompañaba al mensaje de ventana.
[get_PhysicalKeyStatus](#get_physicalkeystatus) | Estructura que representa la información que se pasa en el LPARAM del mensaje de la ventana.
[Indicador](#handle) | Al llamar, se permitirá que continúe el proceso del explorador.

## Miembros

#### get_KeyEventType 

El tipo de evento de clave que causó el evento que se va a desencadenar.

> [get_KeyEventType](#get_keyeventtype)de HRESULT público (WEBVIEW2_KEY_EVENT_TYPE * KeyEventType)

Esta es una de WEBVIEW2_KEY_EVENT_TYPE_KEY_DOWN, WEBVIEW2_KEY_EVENT_TYPE_KEY_UP, WEBVIEW2_KEY_EVENT_TYPE_SYSTEM_KEY_DOWN o WEBVIEW2_KEY_EVENT_TYPE_SYSTEM_KEY_UP.

#### get_VirtualKey 

El código de tecla virtual Win32 de la tecla que se ha presionado o soltado.

> [get_VirtualKey](#get_virtualkey)pública HRESULT (uint * VirtualKey)

Será una de las constantes de la clave virtual de Win32, como VK_RETURN o un valor ASCII (en mayúsculas), como "A". Puede comprobar si las teclas Ctrl o Alt se presionan llamando a GetKeyState (VK_CONTROL) o GetKeyState (VK_MENU).

#### get_KeyEventLParam 

El valor LPARAM que acompañaba al mensaje de ventana.

> [get_KeyEventLParam](#get_keyeventlparam)de HRESULT público (int * lParam)

Consulte la documentación de los mensajes de WM_KEYDOWN y WM_KEYUP.

#### get_PhysicalKeyStatus 

Estructura que representa la información que se pasa en el LPARAM del mensaje de la ventana.

> [get_PhysicalKeyStatus](#get_physicalkeystatus)de HRESULT público (WEBVIEW2_PHYSICAL_KEY_STATUS * PhysicalKeyStatus)

#### Indicador 

Al llamar, se permitirá que continúe el proceso del explorador.

> [identificador](#handle)de HRESULT público (bool Handled)

Si se pasa TRUE, el explorador no podrá realizar la acción predeterminada para esta tecla de aceleración. Si el controlador de eventos vuelve sin llamar al [controlador ()](#handle), es equivalente a llamar a handle (false). Llamar a [HANDLE ()](#handle) después de que ya se ha llamado o el controlador de eventos se ha devuelto no hará nada.
