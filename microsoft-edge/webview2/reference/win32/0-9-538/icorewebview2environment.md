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
ms.openlocfilehash: 0e5befd6a5c07c9f877c1e94f54d927d7ed250c0
ms.sourcegitcommit: 8dca1c1367853e45a0a975bc89b1818adb117bd4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/08/2020
ms.locfileid: "10699355"
---
# <span data-ttu-id="2369c-104">interfaz ICoreWebView2Environment</span><span class="sxs-lookup"><span data-stu-id="2369c-104">interface ICoreWebView2Environment</span></span> 

```
interface ICoreWebView2Environment
  : public IUnknown
```

<span data-ttu-id="2369c-105">Esto representa el entorno de WebView2.</span><span class="sxs-lookup"><span data-stu-id="2369c-105">This represents the WebView2 Environment.</span></span>

## <span data-ttu-id="2369c-106">Resumen</span><span class="sxs-lookup"><span data-stu-id="2369c-106">Summary</span></span>

 <span data-ttu-id="2369c-107">Miembros</span><span class="sxs-lookup"><span data-stu-id="2369c-107">Members</span></span>                        | <span data-ttu-id="2369c-108">Descripciones</span><span class="sxs-lookup"><span data-stu-id="2369c-108">Descriptions</span></span>
--------------------------------|---------------------------------------------
[<span data-ttu-id="2369c-109">add_NewBrowserVersionAvailable</span><span class="sxs-lookup"><span data-stu-id="2369c-109">add_NewBrowserVersionAvailable</span></span>](#add_newbrowserversionavailable) | <span data-ttu-id="2369c-110">El evento NewBrowserVersionAvailable se desencadena cuando se instala una versión más reciente del explorador Edge y está disponible para usarla a través de WebView2.</span><span class="sxs-lookup"><span data-stu-id="2369c-110">The NewBrowserVersionAvailable event fires when a newer version of the Edge browser is installed and available to use via WebView2.</span></span>
[<span data-ttu-id="2369c-111">CreateCoreWebView2Controller</span><span class="sxs-lookup"><span data-stu-id="2369c-111">CreateCoreWebView2Controller</span></span>](#createcorewebview2controller) | <span data-ttu-id="2369c-112">Cree de forma asincrónica una nueva vista de vista previa.</span><span class="sxs-lookup"><span data-stu-id="2369c-112">Asynchronously create a new WebView.</span></span>
[<span data-ttu-id="2369c-113">CreateWebResourceResponse</span><span class="sxs-lookup"><span data-stu-id="2369c-113">CreateWebResourceResponse</span></span>](#createwebresourceresponse) | <span data-ttu-id="2369c-114">Crear un nuevo objeto de respuesta de recursos Web.</span><span class="sxs-lookup"><span data-stu-id="2369c-114">Create a new web resource response object.</span></span>
[<span data-ttu-id="2369c-115">get_BrowserVersionString</span><span class="sxs-lookup"><span data-stu-id="2369c-115">get_BrowserVersionString</span></span>](#get_browserversionstring) | <span data-ttu-id="2369c-116">Información de versión del explorador del [ICoreWebView2Environment]()actual, incluido el nombre del canal si no es el canal estable.</span><span class="sxs-lookup"><span data-stu-id="2369c-116">The browser version info of the current [ICoreWebView2Environment](), including channel name if it is not the stable channel.</span></span>
[<span data-ttu-id="2369c-117">remove_NewBrowserVersionAvailable</span><span class="sxs-lookup"><span data-stu-id="2369c-117">remove_NewBrowserVersionAvailable</span></span>](#remove_newbrowserversionavailable) | <span data-ttu-id="2369c-118">Quitar un controlador de eventos agregado previamente con add_NewBrowserVersionAvailable.</span><span class="sxs-lookup"><span data-stu-id="2369c-118">Remove an event handler previously added with add_NewBrowserVersionAvailable.</span></span>

<span data-ttu-id="2369c-119">Las vistas web creadas a partir de un entorno se ejecutan en el proceso del explorador especificado con los parámetros de entorno y los objetos creados a partir de un entorno se deben usar en el mismo entorno.</span><span class="sxs-lookup"><span data-stu-id="2369c-119">WebViews created from an environment run on the Browser process specified with environment parameters and objects created from an environment should be used in the same environment.</span></span> <span data-ttu-id="2369c-120">No se garantiza que su uso en diferentes entornos sea compatible y podría fallar.</span><span class="sxs-lookup"><span data-stu-id="2369c-120">Using it in different environments are not guaranteed to be compatible and may fail.</span></span>

## <span data-ttu-id="2369c-121">Miembros</span><span class="sxs-lookup"><span data-stu-id="2369c-121">Members</span></span>

#### <span data-ttu-id="2369c-122">add_NewBrowserVersionAvailable</span><span class="sxs-lookup"><span data-stu-id="2369c-122">add_NewBrowserVersionAvailable</span></span> 

<span data-ttu-id="2369c-123">El evento NewBrowserVersionAvailable se desencadena cuando se instala una versión más reciente del explorador Edge y está disponible para usarla a través de WebView2.</span><span class="sxs-lookup"><span data-stu-id="2369c-123">The NewBrowserVersionAvailable event fires when a newer version of the Edge browser is installed and available to use via WebView2.</span></span>

> <span data-ttu-id="2369c-124">[add_NewBrowserVersionAvailable](#add_newbrowserversionavailable)de HRESULT público ([ICoreWebView2NewBrowserVersionAvailableEventHandler](icorewebview2newbrowserversionavailableeventhandler.md) \* EventHandler, EventRegistrationToken \* token)</span><span class="sxs-lookup"><span data-stu-id="2369c-124">public HRESULT [add_NewBrowserVersionAvailable](#add_newbrowserversionavailable)([ICoreWebView2NewBrowserVersionAvailableEventHandler](icorewebview2newbrowserversionavailableeventhandler.md) \* eventHandler, EventRegistrationToken \* token)</span></span>

<span data-ttu-id="2369c-125">Para usar la versión más reciente del explorador, debe crear un entorno y una vista Web nuevos.</span><span class="sxs-lookup"><span data-stu-id="2369c-125">To use the newer version of the browser you must create a new environment and WebView.</span></span> <span data-ttu-id="2369c-126">Este evento solo se activará para la nueva versión desde el mismo canal de borde desde el que se está ejecutando el código.</span><span class="sxs-lookup"><span data-stu-id="2369c-126">This event will only be fired for new version from the same Edge channel that the code is running from.</span></span> <span data-ttu-id="2369c-127">Cuando no se esté ejecutando con Edge instalado, no se desencadenará ningún evento.</span><span class="sxs-lookup"><span data-stu-id="2369c-127">When not running with installed Edge, no event will be fired.</span></span>

<span data-ttu-id="2369c-128">Puesto que una carpeta datos de usuario solo puede ser usada por un único proceso del explorador a la vez, si desea usar la misma carpeta datos de usuario en las vistas web con la nueva versión del explorador, debe cerrar primero el entorno y las vistas de web que usan la versión anterior del explorador.</span><span class="sxs-lookup"><span data-stu-id="2369c-128">Because a user data folder can only be used by one browser process at a time, if you want to use the same user data folder in the WebViews using the new version of the browser, you must close the environment and WebViews that are using the older version of the browser first.</span></span> <span data-ttu-id="2369c-129">O simplemente pide al usuario que reinicie la aplicación.</span><span class="sxs-lookup"><span data-stu-id="2369c-129">Or simply prompt the user to restart the app.</span></span>

```cpp
    // After the environment is successfully created,
    // register a handler for the NewBrowserVersionAvailable event.
    // This handler tells when there is a new Edge version available on the machine.
    CHECK_FAILURE(m_webViewEnvironment->add_NewBrowserVersionAvailable(
        Callback<ICoreWebView2NewBrowserVersionAvailableEventHandler>(
            [this](ICoreWebView2Environment* sender, IUnknown* args) -> HRESULT {
                std::wstring message = L"We detected there is a new version for the browser.";
                if (m_webView)
                {
                    message += L"Do you want to restart the app \n\n";
                    message += L"Click No if you only want to re-create the webviews. \n";
                    message += L"Click Cancel for no action. \n";
                }
                int response = MessageBox(
                    m_mainWindow, message.c_str(), L"New available version",
                    m_webView  MB_YESNOCANCEL : MB_OK);

                if (response == IDYES)
                {
                    RestartApp();
                }
                else if (response == IDNO)
                {
                    ReinitializeWebViewWithNewBrowser();
                }
                else
                {
                    // do nothing
                }

                return S_OK;
            })
            .Get(),
        nullptr));
```

#### <span data-ttu-id="2369c-130">CreateCoreWebView2Controller</span><span class="sxs-lookup"><span data-stu-id="2369c-130">CreateCoreWebView2Controller</span></span> 

<span data-ttu-id="2369c-131">Cree de forma asincrónica una nueva vista de vista previa.</span><span class="sxs-lookup"><span data-stu-id="2369c-131">Asynchronously create a new WebView.</span></span>

> <span data-ttu-id="2369c-132">[CREATECOREWEBVIEW2CONTROLLER](#createcorewebview2controller)HRESULT público (HWND ParentWindow, [ICoreWebView2CreateCoreWebView2ControllerCompletedHandler](icorewebview2createcorewebview2controllercompletedhandler.md) \* handler)</span><span class="sxs-lookup"><span data-stu-id="2369c-132">public HRESULT [CreateCoreWebView2Controller](#createcorewebview2controller)(HWND parentWindow, [ICoreWebView2CreateCoreWebView2ControllerCompletedHandler](icorewebview2createcorewebview2controllercompletedhandler.md) \* handler)</span></span>

<span data-ttu-id="2369c-133">parentWindow es el HWND en el que se debe mostrar la vista en la vista previa y desde la que se recibe la entrada.</span><span class="sxs-lookup"><span data-stu-id="2369c-133">parentWindow is the HWND in which the WebView should be displayed and from which receive input.</span></span> <span data-ttu-id="2369c-134">La vista en WebView agregará una ventana secundaria a la ventana proporcionada durante la creación de WebView.</span><span class="sxs-lookup"><span data-stu-id="2369c-134">The WebView will add a child window to the provided window during WebView creation.</span></span> <span data-ttu-id="2369c-135">El orden Z y otros elementos afectados por el orden de ventanas relacionados se verán afectados según corresponda.</span><span class="sxs-lookup"><span data-stu-id="2369c-135">Z-order and other things impacted by sibling window order will be affected accordingly.</span></span>

<span data-ttu-id="2369c-136">Se recomienda que el identificador de modelo de usuario de la aplicación conjunto de aplicaciones para el proceso o la ventana de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="2369c-136">It is recommended that the application set Application User Model ID for the process or the application window.</span></span> <span data-ttu-id="2369c-137">Si no se establece ninguna, durante la creación de WebView un identificador de modelo de usuario de aplicación generado se establece en la ventana raíz de parentWindow.</span><span class="sxs-lookup"><span data-stu-id="2369c-137">If none is set, during WebView creation a generated Application User Model ID is set to root window of parentWindow.</span></span> 
```cpp
// Create or recreate the WebView and its environment.
void AppWindow::InitializeWebView()
{
    // To ensure browser switches get applied correctly, we need to close
    // the existing WebView. This will result in a new browser process
    // getting created which will apply the browser switches.
    CloseWebView();
    m_dcompDevice = nullptr;
    m_wincompHelper = nullptr;
    LPCWSTR subFolder = nullptr;

    if (m_creationModeId == IDM_CREATION_MODE_VISUAL_DCOMP)
    {
        HRESULT hr = DCompositionCreateDevice2(nullptr, IID_PPV_ARGS(&m_dcompDevice));
        if (!SUCCEEDED(hr))
        {
            MessageBox(
                m_mainWindow,
                L"Attempting to create WebView using DComp Visual is not supported.\r\n"
                "DComp device creation failed.\r\n"
                "Current OS may not support DComp.",
                L"Create with Windowless DComp Visual Failed", MB_OK);
            return;
        }
    }
    else if (m_creationModeId == IDM_CREATION_MODE_VISUAL_WINCOMP)
    {
        HRESULT hr = CreateWinCompCompositor();
        if (!SUCCEEDED(hr))
        {
            MessageBox(
                m_mainWindow,
                L"Attempting to create WebView using WinComp Visual is not supported.\r\n"
                "WinComp compositor creation failed.\r\n"
                "Current OS may not support WinComp.",
                L"Create with Windowless WinComp Visual Failed", MB_OK);
            return;
        }
    }
    auto options = Microsoft::WRL::Make<CoreWebView2EnvironmentOptions>();
    if(!m_language.empty())
        CHECK_FAILURE(options->put_Language(m_language.c_str()));
    HRESULT hr = CreateCoreWebView2EnvironmentWithOptions(
        subFolder, nullptr, options.Get(),
        Callback<ICoreWebView2CreateCoreWebView2EnvironmentCompletedHandler>(
            this, &AppWindow::OnCreateEnvironmentCompleted)
            .Get());
    if (!SUCCEEDED(hr))
    {
        if (hr == HRESULT_FROM_WIN32(ERROR_FILE_NOT_FOUND))
        {
            MessageBox(
                m_mainWindow,
                L"Couldn't find Edge installation. "
                "Do you have a version installed that's compatible with this "
                "WebView2 SDK version?",
                nullptr, MB_OK);
        }
        else
        {
            ShowFailure(hr, L"Failed to create webview environment");
        }
    }
}
// This is the callback passed to CreateWebViewEnvironmentWithOptions.
// Here we simply create the WebView.
HRESULT AppWindow::OnCreateEnvironmentCompleted(
    HRESULT result, ICoreWebView2Environment* environment)
{
    CHECK_FAILURE(result);
    m_webViewEnvironment = environment;

    auto webViewExperimentalEnvironment =
        m_webViewEnvironment.try_query<ICoreWebView2ExperimentalEnvironment>();
    if (webViewExperimentalEnvironment && (m_dcompDevice || m_wincompHelper))
    {
        CHECK_FAILURE(webViewExperimentalEnvironment->CreateCoreWebView2CompositionController(
            m_mainWindow,
            Callback<
                ICoreWebView2ExperimentalCreateCoreWebView2CompositionControllerCompletedHandler>(
                [this](
                    HRESULT result,
                    ICoreWebView2ExperimentalCompositionController* compositionController) -> HRESULT {
                    auto controller =
                        wil::com_ptr<ICoreWebView2ExperimentalCompositionController>(compositionController)
                            .query<ICoreWebView2Controller>();
                    return OnCreateCoreWebView2ControllerCompleted(result, controller.get());
                })
                .Get()));
    }
    else
    {
        CHECK_FAILURE(m_webViewEnvironment->CreateCoreWebView2Controller(
            m_mainWindow, Callback<ICoreWebView2CreateCoreWebView2ControllerCompletedHandler>(
                              this, &AppWindow::OnCreateCoreWebView2ControllerCompleted)
                              .Get()));
    }

    return S_OK;
}
```
 <span data-ttu-id="2369c-138">Se recomienda que la aplicación se ocupe de los mensajes del administrador de reinicio para que se pueda reiniciar correctamente en el caso de que la aplicación esté usando Edge para WebView desde una instalación determinada y que la instalación se está desinstalando.</span><span class="sxs-lookup"><span data-stu-id="2369c-138">It is recommended that the application handles restart manager messages so that it can be restarted gracefully in the case when the app is using Edge for webview from a certain installation and that installation is being uninstalled.</span></span> <span data-ttu-id="2369c-139">Por ejemplo, si un usuario instala Edge desde el canal de desarrollo y opta por usar Edge de ese canal para probar la aplicación y, después, desinstala Edge de ese canal sin cerrar la aplicación, se reiniciará la aplicación para permitir que la desinstalación del canal de desarrollo se realice correctamente.</span><span class="sxs-lookup"><span data-stu-id="2369c-139">For example, if a user installs Edge from Dev channel and opts to use Edge from that channel for testing the app, and then uninstalls Edge from that channel without closing the app, the app will be restarted to allow uninstallation of the dev channel to succeed.</span></span> 
```cpp
    case WM_QUERYENDSESSION:
    {
        // yes, we can shut down
        // Register how we might be restarted
        RegisterApplicationRestart(L"--restore", RESTART_NO_CRASH | RESTART_NO_HANG);
        *result = TRUE;
        return true;
    }
    break;
    case WM_ENDSESSION:
    {
        if (wParam == TRUE)
        {
            // save app state and exit.
            PostQuitMessage(0);
            return true;
        }
    }
    break;
```
 <span data-ttu-id="2369c-140">Cuando la aplicación vuelve a intentar CreateCoreWebView2Controller cuando se produce un error, se recomienda que la aplicación se reinicie a partir de la creación de un nuevo entorno de WebView2.</span><span class="sxs-lookup"><span data-stu-id="2369c-140">When the application retries CreateCoreWebView2Controller upon failure, it is recommended that the application restarts from creating a new WebView2 Environment.</span></span> <span data-ttu-id="2369c-141">Si se produce una actualización perimetral, la versión asociada a un entorno de WebView2 se podría haber quitado y provocar que el objeto deje de funcionar.</span><span class="sxs-lookup"><span data-stu-id="2369c-141">If an Edge update happens, the version associated with a WebView2 Environment could have been removed and causing the object to no longer work.</span></span> <span data-ttu-id="2369c-142">La creación de un nuevo entorno de WebView2 funcionará porque usa la versión más reciente.</span><span class="sxs-lookup"><span data-stu-id="2369c-142">Creating a new WebView2 Environment will work as it uses the latest version.</span></span>

<span data-ttu-id="2369c-143">La creación de WebView generará un error si ya hay una instancia en ejecución con la misma carpeta datos de usuario y los objetos de entorno tienen diferentes EnvironmentOptions.</span><span class="sxs-lookup"><span data-stu-id="2369c-143">WebView creation will fail if there is already a running instance using the same user data folder, and the Environment objects have different EnvironmentOptions.</span></span> <span data-ttu-id="2369c-144">Por ejemplo, si ya hay una vista previa creada con un idioma, se producirá un error al intentar crear una vista previa con un idioma diferente con la misma carpeta de datos de usuario.</span><span class="sxs-lookup"><span data-stu-id="2369c-144">For example, if there is already a WebView created with one language, trying to create a WebView with a different language using the same user data folder will fail.</span></span>

#### <span data-ttu-id="2369c-145">CreateWebResourceResponse</span><span class="sxs-lookup"><span data-stu-id="2369c-145">CreateWebResourceResponse</span></span> 

<span data-ttu-id="2369c-146">Crear un nuevo objeto de respuesta de recursos Web.</span><span class="sxs-lookup"><span data-stu-id="2369c-146">Create a new web resource response object.</span></span>

> <span data-ttu-id="2369c-147">[CREATEWEBRESOURCERESPONSE](#createwebresourceresponse)HRESULT público (IStream \* Content, int STATUSCODE, LPCWSTR REASONPHRASE, LPCWSTR encabezados, [ICoreWebView2WebResourceResponse](icorewebview2webresourceresponse.md) \* \* Response)</span><span class="sxs-lookup"><span data-stu-id="2369c-147">public HRESULT [CreateWebResourceResponse](#createwebresourceresponse)(IStream \* content, int statusCode, LPCWSTR reasonPhrase, LPCWSTR headers, [ICoreWebView2WebResourceResponse](icorewebview2webresourceresponse.md) \*\* response)</span></span>

<span data-ttu-id="2369c-148">La cabecera es la cadena de encabezado de respuesta sin formato delimitada por newline.</span><span class="sxs-lookup"><span data-stu-id="2369c-148">The headers is the raw response header string delimited by newline.</span></span> <span data-ttu-id="2369c-149">También es posible crear este objeto con una cadena de encabezados vacía y, a continuación, usar el [ICoreWebView2HttpResponseHeaders](icorewebview2httpresponseheaders.md) para construir los encabezados línea a línea.</span><span class="sxs-lookup"><span data-stu-id="2369c-149">It's also possible to create this object with empty headers string and then use the [ICoreWebView2HttpResponseHeaders](icorewebview2httpresponseheaders.md) to construct the headers line by line.</span></span> <span data-ttu-id="2369c-150">Para obtener información sobre otros parámetros, consulte [ICoreWebView2WebResourceResponse](icorewebview2webresourceresponse.md).</span><span class="sxs-lookup"><span data-stu-id="2369c-150">For information on other parameters see [ICoreWebView2WebResourceResponse](icorewebview2webresourceresponse.md).</span></span>

```cpp
        if (m_blockImages)
        {
            m_webView->AddWebResourceRequestedFilter(L"*", COREWEBVIEW2_WEB_RESOURCE_CONTEXT_IMAGE);
            CHECK_FAILURE(m_webView->add_WebResourceRequested(
                Callback<ICoreWebView2WebResourceRequestedEventHandler>(
                    [this](
                        ICoreWebView2* sender,
                        ICoreWebView2WebResourceRequestedEventArgs* args) {
                        COREWEBVIEW2_WEB_RESOURCE_CONTEXT resourceContext;
                        CHECK_FAILURE(
                            args->get_ResourceContext(&resourceContext));
                        // Ensure that the type is image
                        if (resourceContext != COREWEBVIEW2_WEB_RESOURCE_CONTEXT_IMAGE)
                        {
                            return E_INVALIDARG;
                        }
                        // Override the response with an empty one to block the image.
                        // If put_Response is not called, the request will continue as normal.
                        wil::com_ptr<ICoreWebView2WebResourceResponse> response;
                        CHECK_FAILURE(m_webViewEnvironment->CreateWebResourceResponse(
                            nullptr, 403 /*NoContent*/, L"Blocked", L"", &response));
                        CHECK_FAILURE(args->put_Response(response.get()));
                        return S_OK;
                    })
                    .Get(),
                &m_webResourceRequestedTokenForImageBlocking));
        }
        else
        {
            CHECK_FAILURE(m_webView->remove_WebResourceRequested(
                m_webResourceRequestedTokenForImageBlocking));
        }
```

#### <span data-ttu-id="2369c-151">get_BrowserVersionString</span><span class="sxs-lookup"><span data-stu-id="2369c-151">get_BrowserVersionString</span></span> 

<span data-ttu-id="2369c-152">Información de versión del explorador del [ICoreWebView2Environment]()actual, incluido el nombre del canal si no es el canal estable.</span><span class="sxs-lookup"><span data-stu-id="2369c-152">The browser version info of the current [ICoreWebView2Environment](), including channel name if it is not the stable channel.</span></span>

> <span data-ttu-id="2369c-153">[get_BrowserVersionString](#get_browserversionstring)de HRESULT público (LPWStr \* versionInfo)</span><span class="sxs-lookup"><span data-stu-id="2369c-153">public HRESULT [get_BrowserVersionString](#get_browserversionstring)(LPWSTR \* versionInfo)</span></span>

<span data-ttu-id="2369c-154">Coincide con el formato de la API de GetAvailableCoreWebView2BrowserVersionString.</span><span class="sxs-lookup"><span data-stu-id="2369c-154">This matches the format of the GetAvailableCoreWebView2BrowserVersionString API.</span></span> <span data-ttu-id="2369c-155">Los nombres de los canales son ' beta ', ' dev ' y ' Canarias '.</span><span class="sxs-lookup"><span data-stu-id="2369c-155">Channel names are 'beta', 'dev', and 'canary'.</span></span>

```cpp
        wil::unique_cotaskmem_string version_info;
        m_webViewEnvironment->get_BrowserVersionString(&version_info);
        MessageBox(
            m_mainWindow, version_info.get(), L"Browser Version Info After WebView Creation",
            MB_OK);
```

#### <span data-ttu-id="2369c-156">remove_NewBrowserVersionAvailable</span><span class="sxs-lookup"><span data-stu-id="2369c-156">remove_NewBrowserVersionAvailable</span></span> 

<span data-ttu-id="2369c-157">Quitar un controlador de eventos agregado previamente con add_NewBrowserVersionAvailable.</span><span class="sxs-lookup"><span data-stu-id="2369c-157">Remove an event handler previously added with add_NewBrowserVersionAvailable.</span></span>

> <span data-ttu-id="2369c-158">[remove_NewBrowserVersionAvailable](#remove_newbrowserversionavailable)de HRESULT público (token EventRegistrationToken)</span><span class="sxs-lookup"><span data-stu-id="2369c-158">public HRESULT [remove_NewBrowserVersionAvailable](#remove_newbrowserversionavailable)(EventRegistrationToken token)</span></span>
