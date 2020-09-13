---
description: Insertar tecnologías web (HTML, CSS y JavaScript) en las aplicaciones nativas con el control Microsoft Edge WebView2
title: WebView2 Win32 C++ ICoreWebView2EnvironmentOptions
author: MSEdgeTeam
ms.author: msedgedevrel
ms.date: 09/09/2020
ms.topic: reference
ms.prod: microsoft-edge
ms.technology: webview
keywords: IWebView2, IWebView2WebView, webview2, WebView, aplicaciones Win32, Win32, Edge, ICoreWebView2, ICoreWebView2Controller, control de explorador, HTML Edge, ICoreWebView2EnvironmentOptions
ms.openlocfilehash: a4e51dc08e2c31664cb77e4e6ee0136bab2f261d
ms.sourcegitcommit: 0faf538d5033508af4320b9b89c4ed99872f0574
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/10/2020
ms.locfileid: "11012759"
---
# interfaz ICoreWebView2EnvironmentOptions 

```
interface ICoreWebView2EnvironmentOptions
  : public IUnknown
```

Opciones usadas para crear un entorno WebView2.

## Resumen

 Miembros                        | Descripciones
--------------------------------|---------------------------------------------
[get_AdditionalBrowserArguments](#get_additionalbrowserarguments) | AdditionalBrowserArguments se puede especificar para cambiar el comportamiento de la vista en WebView.
[get_AllowSingleSignOnUsingOSPrimaryAccount](#get_allowsinglesignonusingosprimaryaccount) | La propiedad AllowSingleSignOnUsingOSPrimaryAccount se usa para habilitar el inicio de sesión único con recursos de Azure Active Directory (AAD) dentro de la vista Web, usando la cuenta de inicio de sesión de Windows y el inicio de sesión único con los sitios web asociados a la cuenta de inicio de sesión de Windows.
[get_Language](#get_language) | El idioma predeterminado con el que se ejecutará la vista previa.
[get_TargetCompatibleBrowserVersion](#get_targetcompatiblebrowserversion) | La versión de los binarios de la WebView2 en tiempo de ejecución para que sea compatible con la aplicación de llamada.
[put_AdditionalBrowserArguments](#put_additionalbrowserarguments) | Establezca la propiedad AdditionalBrowserArguments.
[put_AllowSingleSignOnUsingOSPrimaryAccount](#put_allowsinglesignonusingosprimaryaccount) | Establezca la propiedad AllowSingleSignOnUsingOSPrimaryAccount.
[put_Language](#put_language) | Establezca la propiedad de idioma.
[put_TargetCompatibleBrowserVersion](#put_targetcompatiblebrowserversion) | Establezca la propiedad TargetCompatibleBrowserVersion.

Se proporciona una implementación predeterminada en WebView2EnvironmentOptions. h.

```cpp
    auto options = Microsoft::WRL::Make<CoreWebView2EnvironmentOptions>();
    CHECK_FAILURE(options->put_AllowSingleSignOnUsingOSPrimaryAccount(
        m_AADSSOEnabled ? TRUE : FALSE));
    if (!m_language.empty())
        CHECK_FAILURE(options->put_Language(m_language.c_str()));
    HRESULT hr = CreateCoreWebView2EnvironmentWithOptions(
        subFolder, nullptr, options.Get(),
        Callback<ICoreWebView2CreateCoreWebView2EnvironmentCompletedHandler>(
            this, &AppWindow::OnCreateEnvironmentCompleted)
            .Get());
```

## Miembros

#### get_AdditionalBrowserArguments 

AdditionalBrowserArguments se puede especificar para cambiar el comportamiento de la vista en WebView.

> [get_AdditionalBrowserArguments](#get_additionalbrowserarguments)de HRESULT público (valor LPWStr *)

Se pasarán al proceso de explorador como parte de la línea de comandos. Consulte [Ejecutar cromo con marcas](https://aka.ms/RunChromiumWithFlags) para obtener más información acerca de los modificadores de la línea de comandos para el proceso del explorador. Si la aplicación se inicia con un modificador de línea de comandos, `--edge-webview-switches=xxx` el valor de ese modificador (XXX en el ejemplo anterior) también se anexará a la línea de comandos del proceso del explorador. Algunos conmutadores como los `--user-data-dir` de WebView son internos y importantes. Estos conmutadores se ignorarán incluso si se especifican. Si se especifican los mismos modificadores varias veces, se gana la última. No hay ningún intento de combinar los distintos valores del mismo modificador, excepto para las características deshabilitado y habilitado. Las características especificadas por `--enable-features` y se `--disable-features` combinarán con lógica simple: las características serán la Unión de las características especificadas y las características integradas, y si una característica está deshabilitada, se quitará de la lista de características habilitadas. El valor de la línea de comandos del proceso de la aplicación `--edge-webview-switches` se procesa después de que se procese el parámetro additionalBrowserArguments. Ciertas características están deshabilitadas internamente y no se pueden habilitar. Si se produjo un error de análisis en los modificadores especificados, se ignorarán. El valor predeterminado es ejecutar el proceso del explorador sin ningún marcador adicional.

#### get_AllowSingleSignOnUsingOSPrimaryAccount 

La propiedad AllowSingleSignOnUsingOSPrimaryAccount se usa para habilitar el inicio de sesión único con recursos de Azure Active Directory (AAD) dentro de la vista Web, usando la cuenta de inicio de sesión de Windows y el inicio de sesión único con los sitios web asociados a la cuenta de inicio de sesión de Windows.

> [get_AllowSingleSignOnUsingOSPrimaryAccount](#get_allowsinglesignonusingosprimaryaccount)de HRESULT público (bool * allow)

El valor predeterminado es deshabilitado. Las aplicaciones de la plataforma universal de Windows también deben declarar la [funcionalidad restringida](https://docs.microsoft.com/windows/uwp/packaging/app-capability-declarations#restricted-capabilities) de enterpriseCloudSSO para que funcione el inicio de sesión único.

#### get_Language 

El idioma predeterminado con el que se ejecutará la vista previa.

> [get_Language](#get_language)de HRESULT público (valor LPWStr *)

Se aplica a ius del explorador, como menús contextuales y cuadros de diálogo. También se aplica al encabezado HTTP Accept-Languages que la vista Web envía a los sitios Web. Está en el formato de `language[-country]` donde `language` es el código de 2 Letras de ISO 639 y `country` es el código de 2 letras de ISO 3166.

#### get_TargetCompatibleBrowserVersion 

La versión de los binarios de la WebView2 en tiempo de ejecución para que sea compatible con la aplicación de llamada.

> [get_TargetCompatibleBrowserVersion](#get_targetcompatiblebrowserversion)de HRESULT público (valor LPWStr *)

De forma predeterminada, la versión de tiempo de ejecución de Edge WebView2 que corresponde a la versión del SDK que usa la aplicación. El formato de este valor es el mismo que el formato de la propiedad BrowserVersionString y otros valores de BrowserVersion. Solo se respeta la parte de versión del valor BrowserVersion. El sufijo de canal, si existe, se pasa por alto. La versión de los binarios de tiempo de ejecución de WebView2 que se usó en realidad puede ser diferente de la TargetCompatibleBrowserVersion especificada. Solo se garantiza que son compatibles. Puedes comprobar la versión real en la propiedad BrowserVersionString de la ICoreWebView2Environment.

#### put_AdditionalBrowserArguments 

Establezca la propiedad AdditionalBrowserArguments.

> [put_AdditionalBrowserArguments](#put_additionalbrowserarguments)de HRESULT público (valor de LPCWSTR)

#### put_AllowSingleSignOnUsingOSPrimaryAccount 

Establezca la propiedad AllowSingleSignOnUsingOSPrimaryAccount.

> [put_AllowSingleSignOnUsingOSPrimaryAccount](#put_allowsinglesignonusingosprimaryaccount)de HRESULT público (bool allow)

#### put_Language 

Establezca la propiedad de idioma.

> [put_Language](#put_language)de HRESULT público (valor de LPCWSTR)

#### put_TargetCompatibleBrowserVersion 

Establezca la propiedad TargetCompatibleBrowserVersion.

> [put_TargetCompatibleBrowserVersion](#put_targetcompatiblebrowserversion)de HRESULT público (valor de LPCWSTR)
