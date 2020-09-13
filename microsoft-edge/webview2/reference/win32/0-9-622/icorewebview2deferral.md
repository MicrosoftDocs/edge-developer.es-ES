---
description: Insertar tecnologías web (HTML, CSS y JavaScript) en las aplicaciones nativas con el control Microsoft Edge WebView2
title: WebView2 Win32 C++ ICoreWebView2Deferral
author: MSEdgeTeam
ms.author: msedgedevrel
ms.date: 09/09/2020
ms.topic: reference
ms.prod: microsoft-edge
ms.technology: webview
keywords: IWebView2, IWebView2WebView, webview2, WebView, aplicaciones Win32, Win32, Edge, ICoreWebView2, ICoreWebView2Controller, control de explorador, HTML Edge, ICoreWebView2Deferral
ms.openlocfilehash: d8abff93df317a42c1bfe89dd32ac1d5f7e8c329
ms.sourcegitcommit: 0faf538d5033508af4320b9b89c4ed99872f0574
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/10/2020
ms.locfileid: "11012764"
---
# interfaz ICoreWebView2Deferral 

```
interface ICoreWebView2Deferral
  : public IUnknown
```

Esta interfaz se usa para completar aplazamientos en argumentos de evento que admiten la obtención de aplazamientos a través de su método GetDeferral.

## Resumen

 Miembros                        | Descripciones
--------------------------------|---------------------------------------------
[Completar](#complete) | Completa el evento diferido asociado.

## Miembros

#### Completar 

Completa el evento diferido asociado.

> HRESULT público [completado](#complete)()

Solo se debe llamar a complete una vez por cada aplazamiento tomado.
