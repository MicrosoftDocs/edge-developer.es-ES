---
description: Insertar tecnologías web (HTML, CSS y JavaScript) en las aplicaciones nativas con el control Microsoft Edge WebView2
title: Microsoft. Web. WebView2. Core. CoreWebView2Settings
author: MSEdgeTeam
ms.author: msedgedevrel
ms.date: 09/10/2020
ms.topic: reference
ms.prod: microsoft-edge
ms.technology: webview
keywords: Microsoft. Web. WebView2, Core, WebView2, WebView, dotnet, WPF, WinForms, App, Edge, CoreWebView2, CoreWebView2Controller, control de explorador, Edge HTML, Microsoft. Web. WebView2. Core. CoreWebView2Settings
ms.openlocfilehash: 87b78956c29dac74bd023556a8c495222d248e9f
ms.sourcegitcommit: 0faf538d5033508af4320b9b89c4ed99872f0574
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/10/2020
ms.locfileid: "11012633"
---
# Clase Microsoft. Web. WebView2. Core. CoreWebView2Settings 

Espacio de nombres: Microsoft. Web. WebView2. Core \
Ensamblado: Microsoft.Web.WebView2.Core.dll

Define las propiedades que habilitan, deshabilitan o modifican las características de vista de vista.

## Resumen

 Miembros                        | Descripciones
--------------------------------|---------------------------------------------
[AreDefaultContextMenusEnabled](#aredefaultcontextmenusenabled) | La propiedad AreDefaultContextMenusEnabled se usa para evitar que los usuarios de la vista vean los menús contextuales predeterminados.
[AreDefaultScriptDialogsEnabled](#aredefaultscriptdialogsenabled) | AreDefaultScriptDialogsEnabled se usa al cargar un nuevo documento HTML.
[AreDevToolsEnabled](#aredevtoolsenabled) | AreDevToolsEnabled controla si el usuario puede usar el menú contextual o los métodos abreviados de teclado para abrir la ventana de DevTools.
[AreHostObjectsAllowed](#arehostobjectsallowed) | La propiedad AreHostObjectsAllowed se usa para controlar si se puede acceder a los objetos host desde la página de WebView.
[IsBuiltInErrorPageEnabled](#isbuiltinerrorpageenabled) | La propiedad IsBuiltInErrorPageEnabled se usa para deshabilitar la página de error integrada para el error de navegación y el error del proceso de representación.
[IsScriptEnabled](#isscriptenabled) | Controla si la ejecución de JavaScript está habilitada en todas las navegaciones futuras de WebView.
[IsStatusBarEnabled](#isstatusbarenabled) | IsStatusBarEnabled controla si se mostrará la barra de estado.
[IsWebMessageEnabled](#iswebmessageenabled) | La propiedad IsWebMessageEnabled se usa al cargar un nuevo documento HTML.
[IsZoomControlEnabled](#iszoomcontrolenabled) | La propiedad IsZoomControlEnabled se usa para evitar que el usuario afecte al zoom de la vista en WebView.

Los cambios de configuración realizados después del evento NavigationStarting no se aplicarán hasta la siguiente navegación de nivel superior.

## Miembros

#### AreDefaultContextMenusEnabled 

La propiedad AreDefaultContextMenusEnabled se usa para evitar que los usuarios de la vista vean los menús contextuales predeterminados.

> Public bool [AreDefaultContextMenusEnabled](#aredefaultcontextmenusenabled)

Es verdadero de forma predeterminada.

#### AreDefaultScriptDialogsEnabled 

AreDefaultScriptDialogsEnabled se usa al cargar un nuevo documento HTML.

> Public bool [AreDefaultScriptDialogsEnabled](#aredefaultscriptdialogsenabled)

Si se establece en false, WebView no procesará el cuadro de diálogo predeterminado de JavaScript (específicamente los que se muestran en las alertas de JavaScript, CONFIRM, prompt functions y beforeunload Event). Si se establece en true, también se puede suscribir al evento ScriptDialogOpening que contendrá toda la información del cuadro de diálogo y permitir que la aplicación host muestre su propia interfaz de usuario personalizada. Es verdadero de forma predeterminada.

#### AreDevToolsEnabled 

AreDevToolsEnabled controla si el usuario puede usar el menú contextual o los métodos abreviados de teclado para abrir la ventana de DevTools.

> Public bool [AreDevToolsEnabled](#aredevtoolsenabled)

Es verdadero de forma predeterminada.

#### AreHostObjectsAllowed 

La propiedad AreHostObjectsAllowed se usa para controlar si se puede acceder a los objetos host desde la página de WebView.

> Public bool [AreHostObjectsAllowed](#arehostobjectsallowed)

Es verdadero de forma predeterminada.

#### IsBuiltInErrorPageEnabled 

La propiedad IsBuiltInErrorPageEnabled se usa para deshabilitar la página de error integrada para el error de navegación y el error del proceso de representación.

> Public bool [IsBuiltInErrorPageEnabled](#isbuiltinerrorpageenabled)

Es verdadero de forma predeterminada. Cuando se deshabilita, se muestra una página en blanco cuando se produce un error relacionado.

#### IsScriptEnabled 

Controla si la ejecución de JavaScript está habilitada en todas las navegaciones futuras de WebView.

> Public bool [IsScriptEnabled](#isscriptenabled)

Esto solo afecta a los scripts del documento. los scripts inyectados con ExecuteScript se ejecutarán incluso si el script está deshabilitado. Es verdadero de forma predeterminada.

#### IsStatusBarEnabled 

IsStatusBarEnabled controla si se mostrará la barra de estado.

> Public bool [IsStatusBarEnabled](#isstatusbarenabled)

Normalmente, la barra de estado se muestra en la parte inferior izquierda de la vista WebView y muestra aspectos como el URI de un vínculo cuando el usuario mantiene el puntero sobre él y otra información. Es verdadero de forma predeterminada.

#### IsWebMessageEnabled 

La propiedad IsWebMessageEnabled se usa al cargar un nuevo documento HTML.

> Public bool [IsWebMessageEnabled](#iswebmessageenabled)

Si se establece en true, se permite la comunicación desde el host al documento HTML de nivel superior de la WebView a través de PostWebMessageAsJson, PostWebMessageAsString y Window. Chrome. evento de mensaje de WebView (consulte la documentación de PostWebMessageAsJson para obtener más información). Se permite la comunicación desde el documento HTML de nivel superior de WebView al host mediante Window. Chrome. la función PostMessage de WebView y el evento WebMessageReceived (consulte la documentación de WebMessageReceived para obtener más información). Si se establece en false, no se permite la comunicación. PostWebMessageAsJson y PostWebMessageAsString producirán errores con E_ACCESSDENIED y Window. Chrome. Webview. PostMessage producirá un error generando una instancia de un objeto de error. Es verdadero de forma predeterminada.

#### IsZoomControlEnabled 

La propiedad IsZoomControlEnabled se usa para evitar que el usuario afecte al zoom de la vista en WebView.

> Public bool [IsZoomControlEnabled](#iszoomcontrolenabled)

Es verdadero de forma predeterminada. Cuando está deshabilitado, el usuario no podrá hacer zoom con Ctrl +/o Ctrl + rueda del mouse, pero el zoom puede establecerse a través de la API de ZoomFactor.
