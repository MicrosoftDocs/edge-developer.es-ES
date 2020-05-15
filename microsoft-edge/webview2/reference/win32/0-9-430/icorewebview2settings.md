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
ms.openlocfilehash: 79f6e2712cab6d18025bd49ab0e7ceba01495d65
ms.sourcegitcommit: 07cda56425e5fdf90eeb3972e17041261bf720cd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/14/2020
ms.locfileid: "10655460"
---
# interfaz ICoreWebView2Settings 

> [!NOTE]
> Esta interfaz puede modificarse o no estar disponible para las versiones posteriores a la versión de SDK 0.9.430. Consulta la [referencia](../../../webview2-api-reference.md) de la API más reciente.

```
interface ICoreWebView2Settings
  : public IUnknown
```

Define las propiedades que habilitan, deshabilitan o modifican las características de vista de vista.

## Resumen

 Miembros                        | Descripciones
--------------------------------|---------------------------------------------
[get_IsScriptEnabled](#get_isscriptenabled) | Controla si la ejecución de JavaScript está habilitada en todas las navegaciones futuras de WebView.
[put_IsScriptEnabled](#put_isscriptenabled) | Establezca la propiedad IsScriptEnabled.
[get_IsWebMessageEnabled](#get_iswebmessageenabled) | La propiedad IsWebMessageEnabled se usa al cargar un nuevo documento HTML.
[put_IsWebMessageEnabled](#put_iswebmessageenabled) | Establezca la propiedad IsWebMessageEnabled.
[get_AreDefaultScriptDialogsEnabled](#get_aredefaultscriptdialogsenabled) | AreDefaultScriptDialogsEnabled se usa al cargar un nuevo documento HTML.
[put_AreDefaultScriptDialogsEnabled](#put_aredefaultscriptdialogsenabled) | Establezca la propiedad AreDefaultScriptDialogsEnabled.
[get_IsStatusBarEnabled](#get_isstatusbarenabled) | IsStatusBarEnabled controla si se mostrará la barra de estado.
[put_IsStatusBarEnabled](#put_isstatusbarenabled) | Establezca la propiedad IsStatusBarEnabled.
[get_AreDevToolsEnabled](#get_aredevtoolsenabled) | AreDevToolsEnabled controla si el usuario puede usar el menú contextual o los métodos abreviados de teclado para abrir la ventana de DevTools.
[put_AreDevToolsEnabled](#put_aredevtoolsenabled) | Establezca la propiedad AreDevToolsEnabled.
[get_AreDefaultContextMenusEnabled](#get_aredefaultcontextmenusenabled) | La propiedad AreDefaultContextMenusEnabled se usa para evitar que los usuarios de la vista vean los menús contextuales predeterminados.
[put_AreDefaultContextMenusEnabled](#put_aredefaultcontextmenusenabled) | Establezca la propiedad AreDefaultContextMenusEnabled.
[get_AreRemoteObjectsAllowed](#get_areremoteobjectsallowed) | La propiedad AreRemoteObjectsAllowed se usa para controlar si se puede tener acceso a los objetos remotos desde la página de WebView.
[put_AreRemoteObjectsAllowed](#put_areremoteobjectsallowed) | Establezca la propiedad AreRemoteObjectsAllowed.
[get_IsZoomControlEnabled](#get_iszoomcontrolenabled) | La propiedad IsZoomControlEnabled se usa para evitar que el usuario afecte al zoom de la vista en WebView.
[put_IsZoomControlEnabled](#put_iszoomcontrolenabled) | Establezca la propiedad IsZoomControlEnabled.

Los cambios de configuración realizados después del evento NavigationStarting no se aplicarán hasta la siguiente navegación de nivel superior.

## Miembros

#### get_IsScriptEnabled 

Controla si la ejecución de JavaScript está habilitada en todas las navegaciones futuras de WebView.

> [get_IsScriptEnabled](#get_isscriptenabled)de HRESULT público (bool * IsScriptEnabled)

Esto solo afecta a los scripts del documento. los scripts inyectados con ExecuteScript se ejecutarán incluso si el script está deshabilitado. Es verdadero de forma predeterminada.

```cpp
        // Changes to settings will apply at the next navigation, which includes the
        // navigation after a NavigationStarting event.  We can use this to change
        // settings according to what site we're visiting.
        if (ShouldBlockScriptForUri(uri.get()))
        {
            m_settings->put_IsScriptEnabled(FALSE);
        }
        else
        {
            m_settings->put_IsScriptEnabled(m_isScriptEnabled);
        }
```

#### put_IsScriptEnabled 

Establezca la propiedad IsScriptEnabled.

> [put_IsScriptEnabled](#put_isscriptenabled)de HRESULT público (bool IsScriptEnabled)

#### get_IsWebMessageEnabled 

La propiedad IsWebMessageEnabled se usa al cargar un nuevo documento HTML.

> [get_IsWebMessageEnabled](#get_iswebmessageenabled)de HRESULT público (bool * IsWebMessageEnabled)

Si se establece en true, se permite la comunicación desde el host al documento HTML de nivel superior de la WebView a través de PostWebMessageAsJson, PostWebMessageAsString y Window. Chrome. evento de mensaje de WebView (consulte la documentación de PostWebMessageAsJson para obtener más información). Se permite la comunicación desde el documento HTML de nivel superior de WebView al host mediante Window. Chrome. función PostMessage de WebView y el método SetWebMessageReceivedEventHandler (consulte la documentación de SetWebMessageReceivedEventHandler para obtener más información). Si se establece en false, no se permite la comunicación. PostWebMessageAsJson y PostWebMessageAsString producirán errores con E_ACCESSDENIED y Window. Chrome. Webview. PostMessage producirá un error generando una instancia de un objeto de error. Es verdadero de forma predeterminada.

```cpp
    ComPtr<ICoreWebView2Settings> settings;
    CHECK_FAILURE(m_webView->get_Settings(&settings));

    CHECK_FAILURE(settings->put_IsWebMessageEnabled(TRUE));
```

#### put_IsWebMessageEnabled 

Establezca la propiedad IsWebMessageEnabled.

> [put_IsWebMessageEnabled](#put_iswebmessageenabled)de HRESULT público (bool IsWebMessageEnabled)

#### get_AreDefaultScriptDialogsEnabled 

AreDefaultScriptDialogsEnabled se usa al cargar un nuevo documento HTML.

> [get_AreDefaultScriptDialogsEnabled](#get_aredefaultscriptdialogsenabled)de HRESULT público (bool * AreDefaultScriptDialogsEnabled)

Si se establece en false, WebView no procesará el cuadro de diálogo predeterminado de JavaScript (específicamente los que se muestran en las alertas de JavaScript, CONFIRM, prompt functions y beforeunload Event). En su lugar, si un controlador de eventos se establece mediante SetScriptDialogOpeningEventHandler, WebView enviará un evento que contendrá toda la información del cuadro de diálogo y permitirá que la aplicación host muestre su propia interfaz de usuario personalizada.

#### put_AreDefaultScriptDialogsEnabled 

Establezca la propiedad AreDefaultScriptDialogsEnabled.

> [put_AreDefaultScriptDialogsEnabled](#put_aredefaultscriptdialogsenabled)de HRESULT público (bool AreDefaultScriptDialogsEnabled)

#### get_IsStatusBarEnabled 

IsStatusBarEnabled controla si se mostrará la barra de estado.

> [get_IsStatusBarEnabled](#get_isstatusbarenabled)de HRESULT público (bool * IsStatusBarEnabled)

Normalmente, la barra de estado se muestra en la parte inferior izquierda de la vista WebView y muestra aspectos como el URI de un vínculo cuando el usuario mantiene el puntero sobre él y otra información. Es verdadero de forma predeterminada.

#### put_IsStatusBarEnabled 

Establezca la propiedad IsStatusBarEnabled.

> [put_IsStatusBarEnabled](#put_isstatusbarenabled)de HRESULT público (bool IsStatusBarEnabled)

#### get_AreDevToolsEnabled 

AreDevToolsEnabled controla si el usuario puede usar el menú contextual o los métodos abreviados de teclado para abrir la ventana de DevTools.

> [get_AreDevToolsEnabled](#get_aredevtoolsenabled)de HRESULT público (bool * AreDevToolsEnabled)

Es verdadero de forma predeterminada.

#### put_AreDevToolsEnabled 

Establezca la propiedad AreDevToolsEnabled.

> [put_AreDevToolsEnabled](#put_aredevtoolsenabled)de HRESULT público (bool AreDevToolsEnabled)

#### get_AreDefaultContextMenusEnabled 

La propiedad AreDefaultContextMenusEnabled se usa para evitar que los usuarios de la vista vean los menús contextuales predeterminados.

> [get_AreDefaultContextMenusEnabled](#get_aredefaultcontextmenusenabled)de HRESULT público (bool * Enabled)

El valor predeterminado es TRUE.

```cpp
            BOOL allowContextMenus;
            CHECK_FAILURE(m_settings->get_AreDefaultContextMenusEnabled(
                &allowContextMenus));
            if (allowContextMenus) {
                CHECK_FAILURE(m_settings->put_AreDefaultContextMenusEnabled(FALSE));
                MessageBox(nullptr,
                L"Context menus will be disabled after the next navigation.",
                L"Settings change", MB_OK);
            }
            else {
                CHECK_FAILURE(m_settings->put_AreDefaultContextMenusEnabled(TRUE));
                MessageBox(nullptr,
                    L"Context menus will be enabled after the next navigation.",
                    L"Settings change", MB_OK);
            }
```

#### put_AreDefaultContextMenusEnabled 

Establezca la propiedad AreDefaultContextMenusEnabled.

> [put_AreDefaultContextMenusEnabled](#put_aredefaultcontextmenusenabled)de HRESULT público (bool Enabled)

#### get_AreRemoteObjectsAllowed 

La propiedad AreRemoteObjectsAllowed se usa para controlar si se puede tener acceso a los objetos remotos desde la página de WebView.

> [get_AreRemoteObjectsAllowed](#get_areremoteobjectsallowed)de HRESULT público (bool * allowed)

El valor predeterminado es TRUE.

```cpp
            BOOL allowRemoteObjects;
            CHECK_FAILURE(m_settings->get_AreRemoteObjectsAllowed(&allowRemoteObjects));
            if (allowRemoteObjects)
            {
                CHECK_FAILURE(m_settings->put_AreRemoteObjectsAllowed(FALSE));
                MessageBox(
                    nullptr, L"Access to remote objects will be denied after the next navigation.",
                    L"Settings change", MB_OK);
            }
            else
            {
                CHECK_FAILURE(m_settings->put_AreRemoteObjectsAllowed(TRUE));
                MessageBox(
                    nullptr, L"Access to remote objects will be allowed after the next navigation.",
                    L"Settings change", MB_OK);
            }
```

#### put_AreRemoteObjectsAllowed 

Establezca la propiedad AreRemoteObjectsAllowed.

> [put_AreRemoteObjectsAllowed](#put_areremoteobjectsallowed)de HRESULT público (se permite bool)

#### get_IsZoomControlEnabled 

La propiedad IsZoomControlEnabled se usa para evitar que el usuario afecte al zoom de la vista en WebView.

> [get_IsZoomControlEnabled](#get_iszoomcontrolenabled)de HRESULT público (bool * Enabled)

El valor predeterminado es TRUE. Cuando está deshabilitado, el usuario no podrá hacer zoom con Ctrl +/o Ctrl + rueda del mouse, pero el zoom se puede establecer mediante put_ZoomFactor API.

```cpp
            BOOL zoomControlEnabled;
            CHECK_FAILURE(m_settings->get_IsZoomControlEnabled(&zoomControlEnabled));
            if (zoomControlEnabled)
            {
                CHECK_FAILURE(m_settings->put_IsZoomControlEnabled(FALSE));
                MessageBox(
                    nullptr, L"Zoom control is disabled after the next navigation.", L"Settings change",
                    MB_OK);
            }
            else
            {
                CHECK_FAILURE(m_settings->put_IsZoomControlEnabled(TRUE));
                MessageBox(
                    nullptr, L"Zoom control is enabled after the next navigation.", L"Settings change",
                    MB_OK);
            }
```

#### put_IsZoomControlEnabled 

Establezca la propiedad IsZoomControlEnabled.

> [put_IsZoomControlEnabled](#put_iszoomcontrolenabled)de HRESULT público (bool Enabled)
