---
description: Mejorar progresivamente su PWA para Windows con características de aplicaciones nativas
title: Personalizar su PWA para Windows
author: MSEdgeTeam
ms.author: msedgedevrel
ms.date: 04/22/2020
ms.topic: article
ms.prod: microsoft-edge
keywords: aplicaciones web progresivas, PWA, Edge, Windows, WinRT, UWP, EdgeHTML
ms.openlocfilehash: 5bad708db5b13517fd1887214a5e1d5457796ee2
ms.sourcegitcommit: e07de36ee9fbe20422ffc2c62b98839851e1b02b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/28/2020
ms.locfileid: "10604014"
---
# <span data-ttu-id="f3f62-104">Personalizar su PWA (EdgeHTML) para Windows</span><span class="sxs-lookup"><span data-stu-id="f3f62-104">Tailor your PWA (EdgeHTML) for Windows</span></span>  

<span data-ttu-id="f3f62-105">PWAs instalado en Windows 10 disfruta de [todas las ventajas][PwaIndexWindows10] de ejecutar como aplicaciones de la [plataforma universal de Windows \ (UWP \)][WindowsUWPGetStartedGuide] , entre ellas, la protección mediante la seguridad de espacio aislado de aplicaciones de Windows y el acceso total a las API de [Windows Runtime \ (WinRT \))][UwpApiIndex] , incluidas las de:</span><span class="sxs-lookup"><span data-stu-id="f3f62-105">PWAs installed on Windows 10 enjoy [all the benefits][PwaIndexWindows10] of running as [Universal Windows Platform \(UWP\)][WindowsUWPGetStartedGuide] apps, including protection through Windows app sandboxing security and full access to [Windows Runtime \(WinRT\))][UwpApiIndex] APIs, including those for:</span></span>  

*   <span data-ttu-id="f3f62-106">Control de las características del dispositivo \ (como cámara, micrófono, GPS \)</span><span class="sxs-lookup"><span data-stu-id="f3f62-106">Controlling device features \(such as camera, microphone, GPS\)</span></span>  
*   <span data-ttu-id="f3f62-107">Acceso a los recursos de usuario \ (como calendario, contactos, documentos, música \)</span><span class="sxs-lookup"><span data-stu-id="f3f62-107">Accessing user resources \(such as calendar, contacts, documents, music\)</span></span>  
*   <span data-ttu-id="f3f62-108">Iniciar o navegar por la aplicación a través de los comandos de voz Cortana</span><span class="sxs-lookup"><span data-stu-id="f3f62-108">Launching / navigating your app through Cortana voice commands</span></span>  
*   <span data-ttu-id="f3f62-109">Integración con el sistema operativo Windows \ (a través del centro de actividades de Windows, barra de tareas de escritorio y menús contextuales \)</span><span class="sxs-lookup"><span data-stu-id="f3f62-109">Integrating with the Windows OS \(through the Windows Action Center, desktop taskbar, and context menus\)</span></span>  

<span data-ttu-id="f3f62-110">... y estas son solo algunas de las posibilidades agregadas para tu PWA \ \ (EdgeHTML \) en Windows.</span><span class="sxs-lookup"><span data-stu-id="f3f62-110">... and these are only a few of the added possibilities for your PWA \(EdgeHTML\) on Windows!</span></span>  

<span data-ttu-id="f3f62-111">En esta guía se muestra cómo instalar, ejecutar y mejorar el PWA \ (EdgeHTML \) como una aplicación de Windows 10, sin dejar de garantizar la compatibilidad entre exploradores y plataformas.</span><span class="sxs-lookup"><span data-stu-id="f3f62-111">This guide shows you how to install, run, and enhance your PWA \(EdgeHTML\) as a Windows 10 app, while still ensuring cross-browser and cross-platform compatibility.</span></span>  

## <span data-ttu-id="f3f62-112">Requisitos previos</span><span class="sxs-lookup"><span data-stu-id="f3f62-112">Prerequisites</span></span>  

*   <span data-ttu-id="f3f62-113">Un PWA \ (o una aplicación web hospedada \), ya sea un sitio activo o local.</span><span class="sxs-lookup"><span data-stu-id="f3f62-113">An existing PWA \(or hosted web app\), either a live or localhost site.</span></span>  <span data-ttu-id="f3f62-114">Esta guía usa el ejemplo PWA de introducción [a las aplicaciones web progresivas][PwaGetStarted].</span><span class="sxs-lookup"><span data-stu-id="f3f62-114">This guide uses the sample PWA from [Get started with Progressive Web Apps][PwaGetStarted].</span></span>  
*   <span data-ttu-id="f3f62-115">Descargar la \ (gratis \) [Visual Studio Community 2017][MicrosoftVisualStudio|::ref1::|].</span><span class="sxs-lookup"><span data-stu-id="f3f62-115">Download the \(free\) [Visual Studio Community 2017][MicrosoftVisualStudio|::ref1::|].</span></span>  <span data-ttu-id="f3f62-116">También puede usar las ediciones Professional, Enterprise o [Preview][MicrosoftVisualStudioPreview] .</span><span class="sxs-lookup"><span data-stu-id="f3f62-116">You are also able to use the Professional, Enterprise, or [Preview][MicrosoftVisualStudioPreview] editions.</span></span>  <span data-ttu-id="f3f62-117">Desde el instalador de Visual Studio, elija las siguientes cargas de trabajo:</span><span class="sxs-lookup"><span data-stu-id="f3f62-117">From the Visual Studio Installer, choose the following Workloads:</span></span>  
    *   **<span data-ttu-id="f3f62-118">Desarrollo de la plataforma universal de Windows</span><span class="sxs-lookup"><span data-stu-id="f3f62-118">Universal Windows Platform development</span></span>**  

## <span data-ttu-id="f3f62-119">Configurar y ejecutar la aplicación universal de Windows</span><span class="sxs-lookup"><span data-stu-id="f3f62-119">Set up and run your Universal Windows app</span></span>  

<span data-ttu-id="f3f62-120">Un PWA \ (EdgeHTML \) instalado como una aplicación de Windows 10 se ejecuta independientemente del explorador, en una ventana \ ( `WWAHost.exe` proceso \) independiente.</span><span class="sxs-lookup"><span data-stu-id="f3f62-120">A PWA \(EdgeHTML\) installed as a Windows 10 app runs independently from the browser, in a standalone \(`WWAHost.exe` process\) window.</span></span>  <span data-ttu-id="f3f62-121">Habilitar esta opción simplemente requiere un contenedor de aplicaciones ligero que contenga la aplicación web hospedada, que podrás configurar rápidamente con la plantilla de proyecto de Visual Studio `Progressive Web App (Universal Windows)` .</span><span class="sxs-lookup"><span data-stu-id="f3f62-121">Enabling this simply requires a lightweight app wrapper that contains your hosted web app, which you are able to quickly set up using the Visual Studio `Progressive Web App (Universal Windows)` project template.</span></span>  <span data-ttu-id="f3f62-122">\ (La lógica de la aplicación, incluido el envío de solicitudes de API nativas de Windows en tiempo de ejecución, sigue apareciendo en el código original de la aplicación Web. \)</span><span class="sxs-lookup"><span data-stu-id="f3f62-122">\(All your app logic, including sending native Windows Runtime API requests, still happens in your original web app code.\)</span></span>  

<span data-ttu-id="f3f62-123">Configure el entorno de desarrollo de aplicaciones de Windows en Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="f3f62-123">Set up your Windows app development environment in Visual Studio.</span></span>  

1.  <span data-ttu-id="f3f62-124">En la configuración de Windows, activa el [modo de desarrollador][WindowsUWPGetStartedEnable].</span><span class="sxs-lookup"><span data-stu-id="f3f62-124">In your Windows Settings, turn on [Developer mode][WindowsUWPGetStartedEnable].</span></span>  <span data-ttu-id="f3f62-125">\ (Escriba `developer mode` el SEARCHBAR de Windows para encontrarlo. \)</span><span class="sxs-lookup"><span data-stu-id="f3f62-125">\(Type `developer mode` in the Windows searchbar to find it.\)</span></span>  
1.  <span data-ttu-id="f3f62-126">Inicia Visual Studio y **crea un nuevo proyecto...**</span><span class="sxs-lookup"><span data-stu-id="f3f62-126">Launch Visual Studio and **Create a new project...**</span></span>  
1.  <span data-ttu-id="f3f62-127">Seleccione la plantilla de **proyecto de empaquetado de aplicaciones** de C# para Windows.</span><span class="sxs-lookup"><span data-stu-id="f3f62-127">Select the C# **Windows Application Packaging Project** template.</span></span>  <span data-ttu-id="f3f62-128">Si está usando una versión anterior de Visual Studio, busque la plantilla equivalente en **aplicación web hospedada (universal Windows)** o **aplicación web progresiva (Windows universal)**.</span><span class="sxs-lookup"><span data-stu-id="f3f62-128">If you are using a previous version of Visual Studio, find the equivalent template under **Hosted Web App (Universal Windows)** or **Progressive Web App (Universal Windows)**.</span></span>  
1.  <span data-ttu-id="f3f62-129">Seleccione la opción predeterminada Windows 10 `Target version` \ (versión más reciente \) y `Minimum version` \ (compilación 10586 o superior \) y haga clic en **Aceptar**.</span><span class="sxs-lookup"><span data-stu-id="f3f62-129">Select the default Windows 10 `Target version` \(most recent release\) and `Minimum version` \(build 10586 or higher\) and click **OK**.</span></span>  

    ![Cuadro de diálogo de selección de Visual Studio para compilaciones de destino de proyecto para UWP](media/vs-target-min-version.png)  

    <span data-ttu-id="f3f62-131">El nuevo proyecto se cargará con el diseñador package. appxmanifest abierto.</span><span class="sxs-lookup"><span data-stu-id="f3f62-131">Your new project loads with the package.appxmanifest designer open.</span></span>  <span data-ttu-id="f3f62-132">Aquí es donde se configuran los detalles de la aplicación, como la identidad del paquete, las dependencias de paquete, las características necesarias, los elementos visuales y los puntos de extensibilidad.</span><span class="sxs-lookup"><span data-stu-id="f3f62-132">This is where you configure the details of your app, including package identity, package dependencies, required capabilities, visual elements, and extensibility points.</span></span>  <span data-ttu-id="f3f62-133">Esta es una versión temporal, fácilmente configurable, del manifiesto del paquete de la aplicación usado durante el desarrollo de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="f3f62-133">This is an easily configurable, temporary version of the app package manifest used during app development.</span></span>  
    <span data-ttu-id="f3f62-134">Al compilar el proyecto de la aplicación, [Visual Studio genera un archivo AppxManifest. XML][UwpSchemasAppxpackageUapmanifestschemaGeneratePackageManifest] de estos metadatos, que se usa para instalar y ejecutar la aplicación.</span><span class="sxs-lookup"><span data-stu-id="f3f62-134">When you build your app project, [Visual Studio generates an AppxManifest.xml][UwpSchemasAppxpackageUapmanifestschemaGeneratePackageManifest] file from this metadata, which is used to install and run your app.</span></span>  <span data-ttu-id="f3f62-135">Cada vez que actualice el `package.appxmanifest` archivo, asegúrese de volver a crear el proyecto para que ambos se reflejen en el tiempo de `AppxManifest.xml` ejecución.</span><span class="sxs-lookup"><span data-stu-id="f3f62-135">Whenever you update your `package.appxmanifest` file, be sure to rebuild the project so both are reflected in your `AppxManifest.xml` at runtime.</span></span>  

1.  <span data-ttu-id="f3f62-136">En el panel de **aplicaciones** del diseñador de manifiestos, escriba la dirección URL de su PWA como `Start page` .</span><span class="sxs-lookup"><span data-stu-id="f3f62-136">In the manifest designer **Application** panel, enter the URL of your PWA as the `Start page`.</span></span>

    > [!NOTE]
    > <span data-ttu-id="f3f62-137">Los trabajadores del servicio son compatibles con todas las direcciones URL https \ (seguras, remotas) especificadas como `StartPage` .</span><span class="sxs-lookup"><span data-stu-id="f3f62-137">Service workers are supported for all https \(secure, remote\) urls specified as the `StartPage`.</span></span>  <span data-ttu-id="f3f62-138">Los trabajos de servicio no son compatibles de forma predeterminada en las aplicaciones web que especifican una página de inicio local.</span><span class="sxs-lookup"><span data-stu-id="f3f62-138">Service workers are not supported by default for web apps that specify a local start page.</span></span>  <span data-ttu-id="f3f62-139">Para habilitar la compatibilidad con los trabajadores del servicio en estos casos, agregue una entrada de [ApplicationContentUriRules](#set-application-content-uri-rules-acurs) explícita en el manifiesto, por ejemplo:</span><span class="sxs-lookup"><span data-stu-id="f3f62-139">To enable service worker support for these cases, add an explicit [ApplicationContentUriRules](#set-application-content-uri-rules-acurs) entry to the manifest, for example:</span></span> `<uap:Rule Match="http://web-platform.test/" Type="include" uap5:ServiceWorker="true"/>`  
    
    ![Panel de aplicación del diseñador package. appxmanifest](media/vs-manifest-application.png)  
    
    <span data-ttu-id="f3f62-141">También puede modificar el `Display name` y el `Description` como desee.</span><span class="sxs-lookup"><span data-stu-id="f3f62-141">You are able to also modify the `Display name` and `Description` as you like.</span></span>  
1.  <span data-ttu-id="f3f62-142">Guarde este archivo \ (u otra imagen de 512x512 de su elección \) en el escritorio.</span><span class="sxs-lookup"><span data-stu-id="f3f62-142">Save this file \(or another 512x512 image of your choosing\) to your desktop.</span></span>  
    <span data-ttu-id="f3f62-143">A continuación, en el panel **activos visuales** del diseñador de manifiestos, haga clic en el `Source` botón campo **...** , selecciónelo como archivo de origen y haga clic en **generar**.</span><span class="sxs-lookup"><span data-stu-id="f3f62-143">Then, in the manifest designer **Visual Assets** panel, click on the `Source` field **...** button, select it as your source file, and click **Generate**.</span></span>  <span data-ttu-id="f3f62-144">\ (A continuación, haga clic en **Aceptar** para sobrescribir las imágenes de marcador de posición predeterminadas \).</span><span class="sxs-lookup"><span data-stu-id="f3f62-144">\(Then click **OK** to overwrite the default placeholder images\).</span></span>  
    
    ![Panel activos visuales del diseñador de Package. appxmanifest](media/vs-manifest-visual-assets.png)  
    
    <span data-ttu-id="f3f62-146">Esto genera los activos visuales básicos para instalar, ejecutar, iniciar y distribuir tu aplicación en la tienda.</span><span class="sxs-lookup"><span data-stu-id="f3f62-146">This generates the basic visual assets for installing, running, launching, and distributing your app in the store.</span></span>  
    <span data-ttu-id="f3f62-147">Si ve algún error en rojo \ ( `X` \) que indica que faltan imágenes, puede hacer clic en los botones **...** para seleccionar manualmente un archivo de las imágenes generadas.</span><span class="sxs-lookup"><span data-stu-id="f3f62-147">If you see any red \(`X`\) errors indicating missing images, you are able to click on the **...** buttons to manually select a file from the generated images.</span></span>  
1.  <span data-ttu-id="f3f62-148">En el panel **URI de contenido** del diseñador de manifiestos, reemplaza `http://example.com` por la ubicación de tu PWA \ (por ejemplo, `Rule`  =  `include` y `WinRT Access`  =  `All` \).</span><span class="sxs-lookup"><span data-stu-id="f3f62-148">In the manifest designer **Content URIs** panel, replace `http://example.com` with the location of your PWA \(such that `Rule` = `include` and `WinRT Access` = `All`\).</span></span>  
    <span data-ttu-id="f3f62-149">Esto concede al permiso de PWA solicitudes de API de Windows Runtime \ (WinRT \) nativas cuando se ejecuta como una aplicación de Windows 10, que se trata un poco más adelante.</span><span class="sxs-lookup"><span data-stu-id="f3f62-149">This grants your PWA permission to send native Windows Runtime \(WinRT\) API requests when running as a Windows 10 app, which is covered a bit later.</span></span>   <span data-ttu-id="f3f62-150">Si su PWA real no requiere acceso a WinRT, puede cambiar el `WinRT Access` valor a `None` .</span><span class="sxs-lookup"><span data-stu-id="f3f62-150">If your actual PWA does not require WinRT access, you are able to switch the `WinRT Access` value to `None`.</span></span>  <span data-ttu-id="f3f62-151">De cualquier forma, asegúrese de eliminar la cadena predeterminada `http://example.com` con el URI de su PWA o de que la aplicación no pueda cargarse correctamente en tiempo de ejecución.</span><span class="sxs-lookup"><span data-stu-id="f3f62-151">Either way, be sure to sub out the default `http://example.com` string with the URI of your PWA, or your app is not able to properly load at runtime.</span></span>  
    <span data-ttu-id="f3f62-152">Ya está listo para ejecutar y depurar PWA como una aplicación de Windows 10.</span><span class="sxs-lookup"><span data-stu-id="f3f62-152">You are ready to run and debug your PWA as a Windows 10 app.</span></span>  <span data-ttu-id="f3f62-153">Si está usando un sitio localhost para recorrer esta guía, asegúrese de que se está ejecutando.</span><span class="sxs-lookup"><span data-stu-id="f3f62-153">If you are using a localhost site to step through this guide, make sure it is running.</span></span>  <span data-ttu-id="f3f62-154">Luego</span><span class="sxs-lookup"><span data-stu-id="f3f62-154">Then,</span></span>  
1.  <span data-ttu-id="f3f62-155">Compila \ ( `Ctrl` + `Shift` + `F5` \) y ejecuta \ ( `F5` \) el proyecto de PWA.</span><span class="sxs-lookup"><span data-stu-id="f3f62-155">Build \(`Ctrl`+`Shift`+`F5`\) and Run \(`F5`\) your PWA project.</span></span>  <span data-ttu-id="f3f62-156">Ahora, el sitio web debe iniciarse en una ventana de la aplicación independiente.</span><span class="sxs-lookup"><span data-stu-id="f3f62-156">Your website should now launch in a standalone app window.</span></span>  <span data-ttu-id="f3f62-157">No solo es una aplicación web hospedada; se está ejecutando como una aplicación web progresiva instalada en Windows 10.</span><span class="sxs-lookup"><span data-stu-id="f3f62-157">Not only is it a hosted web app; it is running as a Progressive Web App installed on Windows 10!</span></span>  

    ![PWA se ejecuta en una ventana de WWAHost. exe](media/wwahost.png)  

## <span data-ttu-id="f3f62-159">Depure su PWA \ (EdgeHTML \) como una aplicación de Windows</span><span class="sxs-lookup"><span data-stu-id="f3f62-159">Debug your PWA \(EdgeHTML\) as a Windows app</span></span>  

<span data-ttu-id="f3f62-160">Dado que un PWA \ (EdgeHTML \) es simplemente una aplicación web hospedada de forma progresiva, puede depurar el código de su servidor de la misma forma que cualquier aplicación Web, con el IDE y el flujo de trabajo habituales.</span><span class="sxs-lookup"><span data-stu-id="f3f62-160">Because a PWA \(EdgeHTML\) is simply a progressively enhanced hosted web app, you are able to debug your server-side code the same as any web app, using your usual IDE and workflow.</span></span>  <span data-ttu-id="f3f62-161">Los cambios que implemente en vivo se reflejarán en su PWA instalado la próxima vez que lo inicie \ (no es necesario que vuelva a implementar el paquete de la aplicación universal de Windows \).</span><span class="sxs-lookup"><span data-stu-id="f3f62-161">The changes you deploy live are reflected in your installed PWA the next time you launch it \(no need to redeploy your Universal Windows app package\).</span></span>

<span data-ttu-id="f3f62-162">Para la depuración del lado cliente dentro de la aplicación de Windows 10, debes tener la `Microsoft Edge DevTools Preview` aplicación.</span><span class="sxs-lookup"><span data-stu-id="f3f62-162">For client-side debugging within your Windows 10 app, you must have the `Microsoft Edge DevTools Preview` app.</span></span>  <span data-ttu-id="f3f62-163">Esta aplicación independiente incluye todas las funciones de la aplicación original en el explorador [Microsoft Edge DevTools][DevToolsGuide] \ (incluidas [las herramientas de PWA][DevToolsGuideServiceWorkers]\), además de compatibilidad con la [depuración remota][DevToolsProtocol01ClientsEdgePreview] básica y un [selector de destinos de depuración][DevToolsGuideMicrosoftStoreApp] para adjuntar a cualquier instancia en ejecución del motor de EdgeHTML, incluidos los complementos para Office, Cortana, webviews de aplicaciones, y obviamente</span><span class="sxs-lookup"><span data-stu-id="f3f62-163">This standalone app includes all the functionality of the original in-browser [Microsoft Edge DevTools][DevToolsGuide] \(including [PWA tools][DevToolsGuideServiceWorkers]\), plus basic [remote debugging][DevToolsProtocol01ClientsEdgePreview] support and a [Debug Target chooser][DevToolsGuideMicrosoftStoreApp] for attaching to any running instance of the EdgeHTML engine, including add-ins for Office, Cortana, app webviews, and of course, PWAs running on Windows.</span></span>  

<span data-ttu-id="f3f62-164">Aquí se describe cómo configurar la depuración de su PWA \ \ (EdgeHTML \).</span><span class="sxs-lookup"><span data-stu-id="f3f62-164">Here is how to set up debugging for your PWA \(EdgeHTML\).</span></span>  

1.  <span data-ttu-id="f3f62-165">Instale la aplicación [Microsoft Edge DevTools Preview][MicrosoftStoreEdgeDevtoolsPreview] desde Microsoft Store si aún no la tiene.</span><span class="sxs-lookup"><span data-stu-id="f3f62-165">Install the [Microsoft Edge DevTools Preview][MicrosoftStoreEdgeDevtoolsPreview] app from the Microsoft Store if you do not already have it.</span></span>  
1.  <span data-ttu-id="f3f62-166">Con el sitio de PWA en marcha y ejecutándose, inicie la aplicación DevTools.</span><span class="sxs-lookup"><span data-stu-id="f3f62-166">With your PWA site up and running, launch the DevTools app.</span></span>  
1.  <span data-ttu-id="f3f62-167">Desde Visual Studio, inicia la aplicación de Windows 10 con `Start Without Debugging` el `Ctrl` + `F5` comando ().</span><span class="sxs-lookup"><span data-stu-id="f3f62-167">From Visual Studio, launch your Windows 10 app with the `Start Without Debugging` (`Ctrl`+`F5`) command.</span></span>  <span data-ttu-id="f3f62-168">\ (La aplicación DevTools no se adjunta correctamente si el depurador de Visual Studio está activo. \)</span><span class="sxs-lookup"><span data-stu-id="f3f62-168">\(The DevTools app does not attach properly if the Visual Studio debugger is active.\)</span></span>  
1.  <span data-ttu-id="f3f62-169">En la aplicación DevTools, haga clic en el botón **Actualizar** del selector de destino de depuración local.</span><span class="sxs-lookup"><span data-stu-id="f3f62-169">In the DevTools app, click the **Refresh** button in the Local debug target chooser.</span></span>  <span data-ttu-id="f3f62-170">Ahora debe aparecer el sitio de PWA \ (EdgeHTML \).</span><span class="sxs-lookup"><span data-stu-id="f3f62-170">Your PWA \(EdgeHTML\) site should now be listed.</span></span>  <span data-ttu-id="f3f62-171">\ (Si también se ejecuta en una ventana del explorador, es la última instancia de ese sitio en la lista).</span><span class="sxs-lookup"><span data-stu-id="f3f62-171">\(If it is also running in a browser window, it is the last instance of that site in the list.\)</span></span>  
1.  <span data-ttu-id="f3f62-172">Haga clic en la lista de sitios de PWA \ (EdgeHTML \) para abrir una nueva ficha de instancias de DevTools y empezar a depurar.</span><span class="sxs-lookup"><span data-stu-id="f3f62-172">Click on your PWA \(EdgeHTML\) site listing to open a new DevTools instance tab and start debugging.</span></span>  
    
    ![Selección local de destinos de depuración en la aplicación Microsoft Edge DevTools](media/devtools-local.png)  
    
1.  <span data-ttu-id="f3f62-174">Puede comprobar que DevTools está adjunta a la aplicación PWA que se ejecuta como Windows.</span><span class="sxs-lookup"><span data-stu-id="f3f62-174">You are able to verify that DevTools is attached to your PWA-running-as-Windows-app.</span></span>  <span data-ttu-id="f3f62-175">En la **consola**de DevTools, escriba:</span><span class="sxs-lookup"><span data-stu-id="f3f62-175">In the DevTools **Console**, type:</span></span>  
    
    ```shell
    window.Windows
    ```  
    
    <span data-ttu-id="f3f62-176">De esta forma, se devuelve el `Windows Runtime` objeto global que contiene todos los [espacios de nombres WinRT de nivel superior](#find-windows-runtime-winrt-apis).</span><span class="sxs-lookup"><span data-stu-id="f3f62-176">This returns the global `Windows Runtime` object containing all of the [top-level WinRT namespaces](#find-windows-runtime-winrt-apis).</span></span>  <span data-ttu-id="f3f62-177">Este es tu punto de vista de PWA \ \ (EdgeHTML \) a la [plataforma universal de Windows][WindowsUWPIndex]y solo está expuesto a las aplicaciones web que se ejecutan como aplicaciones de Windows 10 (que se ejecutan fuera del explorador, en un `WWAHost.exe` proceso).</span><span class="sxs-lookup"><span data-stu-id="f3f62-177">This is your PWA \(EdgeHTML\) entrypoint to the [Universal Windows Platform][WindowsUWPIndex], and only exposed to web apps that run as Windows 10 apps (running outside the browser, in a `WWAHost.exe` process).</span></span>  
    
## <span data-ttu-id="f3f62-178">Buscar API de Windows Runtime \ (WinRT \)</span><span class="sxs-lookup"><span data-stu-id="f3f62-178">Find Windows Runtime \(WinRT\) APIs</span></span>  

<span data-ttu-id="f3f62-179">Como una aplicación de Windows instalada, tu [PWA \ (EdgeHTML \) tiene acceso completo a las API nativas de Windows Runtime][WindowsRuntime]; Identifique lo que necesita usar, obtenga los permisos necesarios y use la detección de características para enviar esa solicitud de API en entornos admitidos.</span><span class="sxs-lookup"><span data-stu-id="f3f62-179">As an installed Windows app, your [PWA \(EdgeHTML\) has full access to native Windows Runtime APIs][WindowsRuntime]; identify what you need to use, obtain the requisite permissions, and employ feature detection to send that API request on supported environments.</span></span>  <span data-ttu-id="f3f62-180">Recorra este proceso para agregar una mejora progresiva para los usuarios de escritorio de Windows de su PWA.</span><span class="sxs-lookup"><span data-stu-id="f3f62-180">Walk through this process to add a progressive enhancement for Windows desktop users of your PWA.</span></span>  

<span data-ttu-id="f3f62-181">Hay varias maneras de identificar las API de la plataforma universal de Windows que necesitas para tu PWA de Windows, como la búsqueda de contenido completo [documentos de UWP en el centro de desarrollo de Windows] [UWP/API/], descargar y ejecutar [muestras de código de UWP](#uwp-code-samples) con Visual Studio y examinar los fragmentos de código para las tareas comunes de PWAs en Windows.</span><span class="sxs-lookup"><span data-stu-id="f3f62-181">There are a number of ways to identify the Universal Windows Platform APIs you need for your Windows PWA, including searching the comprehensive [UWP docs on Windows Dev Center][uwp/api/], downloading and running [UWP code samples](#uwp-code-samples) with Visual Studio, and browsing code snippets for common tasks for PWAs on Windows.</span></span>

<span data-ttu-id="f3f62-182">Hay varias maneras de identificar las API de la plataforma universal de Windows que necesitas para tu Windows PWA, entre las que se incluyen la búsqueda de contenido completo [documentos de UWP en el centro de desarrollo de Windows] [UWP/API/], descargar y ejecutar [muestras de código de UWP](#uwp-code-samples) con Visual Studio y examinar los fragmentos de código de las tareas comunes de [PWAs en Windows 10 (EdgeHTML)][PwaIndexWindows10].</span><span class="sxs-lookup"><span data-stu-id="f3f62-182">There are a number of ways to identify the Universal Windows Platform APIs you need for your Windows PWA, including searching the comprehensive [UWP docs on Windows Dev Center][uwp/api/], downloading and running [UWP code samples](#uwp-code-samples) with Visual Studio, and browsing code snippets for common tasks for [PWAs on Windows 10 (EdgeHTML)][PwaIndexWindows10].</span></span>  

<span data-ttu-id="f3f62-183">En general, las API de WinRT funcionan en JavaScript de la misma forma que lo hacen en C#, por lo que puedes seguir la documentación general de la [plataforma universal de Windows][WindowsUWPIndex] y la referencia de la [API][UwpApiIndex] para su uso.</span><span class="sxs-lookup"><span data-stu-id="f3f62-183">Overall, WinRT APIs work in JavaScript the same way they do in C#, so you may follow the general [Universal Windows Platform documentation][WindowsUWPIndex] and [API Reference][UwpApiIndex] for usage.</span></span>  <span data-ttu-id="f3f62-184">Sin embargo, tenga en cuenta las siguientes diferencias:</span><span class="sxs-lookup"><span data-stu-id="f3f62-184">However, please note the following differences:</span></span>  

*   <span data-ttu-id="f3f62-185">Las características de WinRT en JavaScript usan [diferentes convenciones de mayúsculas y minúsculas][ScriptingJsinrtUsingWinRTCasingConventions]</span><span class="sxs-lookup"><span data-stu-id="f3f62-185">WinRT features in JavaScript use  [different casing conventions][ScriptingJsinrtUsingWinRTCasingConventions]</span></span>  
*   <span data-ttu-id="f3f62-186">[Los eventos se representan como identificadores de cadena][ScriptingJsinrtHandlingWinRTEvents] que se pasan a `addEventListener` / `removeEventListener` métodos de clase</span><span class="sxs-lookup"><span data-stu-id="f3f62-186">[Events are represented as string identifiers][ScriptingJsinrtHandlingWinRTEvents] passed to class `addEventListener`/`removeEventListener` methods</span></span>  
*   <span data-ttu-id="f3f62-187">Los [métodos asincrónicos][ScriptingJsinrtUsingWinRT] usan el modelo de promesas de JavaScript</span><span class="sxs-lookup"><span data-stu-id="f3f62-187">[Asynchronous methods][ScriptingJsinrtUsingWinRT] use the JavaScript Promise model</span></span>  
*   <span data-ttu-id="f3f62-188">Las aplicaciones de `Windows.UI.Xaml` JavaScript no admiten las API en el espacio de nombres, que usan la pila de procesamiento Web del motor de [EdgeHTML][DevGuideWhatsNew] \ (HTML, CSS \)</span><span class="sxs-lookup"><span data-stu-id="f3f62-188">APIs in the `Windows.UI.Xaml` namespace are not supported for JavaScript apps, which instead use the [EdgeHTML][DevGuideWhatsNew] engine web rendering stack \(HTML, CSS\)</span></span>  

<span data-ttu-id="f3f62-189">Para obtener más información, consulta [usar Windows Runtime en JavaScript][WindowRuntimeUsingJavascript].</span><span class="sxs-lookup"><span data-stu-id="f3f62-189">For more details, see [Using the Windows Runtime in JavaScript][WindowRuntimeUsingJavascript].</span></span>  

### <span data-ttu-id="f3f62-190">Muestras de código de UWP</span><span class="sxs-lookup"><span data-stu-id="f3f62-190">UWP code samples</span></span>  

<span data-ttu-id="f3f62-191">Consulta el repositorio de muestras de código de la [plataforma universal de Windows \ (UWP \)][MicrosoftDeveloperWindowsSamples] para examinar ejemplos de JavaScript para escenarios comunes de aplicaciones de Windows 10.</span><span class="sxs-lookup"><span data-stu-id="f3f62-191">Check out the [Universal Windows Platform \(UWP\) Code Samples][MicrosoftDeveloperWindowsSamples] repo to browse JavaScript examples for common Windows 10 app scenarios.</span></span>  <span data-ttu-id="f3f62-192">Aunque las versiones de JS de estos ejemplos usan la biblioteca [WinJS][GithubWinjsWinjs] para estructurar la plantilla de ejemplo, WinJS no es necesario para enviar las solicitudes de la API de WinRT mostradas en estos ejemplos.</span><span class="sxs-lookup"><span data-stu-id="f3f62-192">Although the JS versions of these samples use the [WinJS][GithubWinjsWinjs] library to structure the sample template, WinJS is not required for sending the WinRT API requests demonstrated in these samples.</span></span>  

> [!NOTE]
> <span data-ttu-id="f3f62-193">Si necesitas escuchar el [`activated`][UwpApiWindowsUiWebuiWebapplicationActivated] evento de la aplicación, puedes hacerlo usando la siguiente API de WinRT nativa:</span><span class="sxs-lookup"><span data-stu-id="f3f62-193">If you need to listen for the [`activated`][UwpApiWindowsUiWebuiWebapplicationActivated] event for the app, you are able to do this using the following native WinRT API:</span></span>  
> 
> **<span data-ttu-id="f3f62-194">Use este</span><span class="sxs-lookup"><span data-stu-id="f3f62-194">Use this</span></span>**  
> 
> ```javascript
> Windows.UI.WebUI.WebUIApplication.addEventListener("activated", function (activatedEventArgs) {
>     // Check activatedEventArgs.kind and respond as needed
> });
> ```  
> 
> <span data-ttu-id="f3f62-195">... por oposición, este tipo de solicitud de WinJS usada en las muestras:</span><span class="sxs-lookup"><span data-stu-id="f3f62-195">... as opposed this type of WinJS request used in the samples:</span></span>  
> 
> **<span data-ttu-id="f3f62-196">No esto</span><span class="sxs-lookup"><span data-stu-id="f3f62-196">Not this</span></span>**  
> 
> ```javascript
>     var page = WinJS.UI.Pages.define("/html/scenario1-launched.html", {
>         ready: function (element, options) {
>             // Check options.activationKind and respond as needed
>         }
>     });
> ```  

## <span data-ttu-id="f3f62-197">Enviar solicitudes de API de WinRT desde tu PWA (EdgeHTML)</span><span class="sxs-lookup"><span data-stu-id="f3f62-197">Send WinRT API requests from your PWA (EdgeHTML)</span></span>  

<span data-ttu-id="f3f62-198">En este punto, Imagine que desea agregar un menú contextual personalizado para los usuarios de Windows de nuestro PWA \ (EdgeHTML \) e identificar las API que necesita en el espacio de nombres [Windows. UI. popups][UwpApiWindowsUiPopups] .</span><span class="sxs-lookup"><span data-stu-id="f3f62-198">At this point, pretend you want to add a custom context menu for Windows users of our PWA \(EdgeHTML\) and have identified the APIs you need in the [Windows.UI.Popups][UwpApiWindowsUiPopups] namespace.</span></span>  

<span data-ttu-id="f3f62-199">Para poder enviar cualquier solicitud de API de WinRT de nuestro PWA \ (EdgeHTML \), primero debes [establecer los permisos necesarios](#set-application-content-uri-rules-acurs) \ (o las reglas de URI de contenido de la aplicación \) en el archivo \ (\) del manifiesto del paquete de la aplicación de Windows `.appxmanifest` .</span><span class="sxs-lookup"><span data-stu-id="f3f62-199">In order to send any WinRT APIs requests from our PWA \(EdgeHTML\), you first need to [establish the requisite permissions](#set-application-content-uri-rules-acurs) \(or, Application Content URI Rules\) in your Windows app package manifest \(`.appxmanifest`\) file.</span></span>  

<span data-ttu-id="f3f62-200">Si cualquiera de estas solicitudes de API implica el acceso a recursos de usuario, como imágenes o música, o a características como la cámara o el micrófono, también tendrá que agregar [declaraciones de funcionalidades de aplicación](#app-capability-declarations) al manifiesto del paquete de la aplicación para que Windows solicite permiso al usuario.</span><span class="sxs-lookup"><span data-stu-id="f3f62-200">If any of these API requests involve access to user resources like pictures or music, or to device features like the camera or microphone, you also need to add [app capability declarations](#app-capability-declarations) to the app package manifest in order for Windows to prompt the user for permission.</span></span>  <span data-ttu-id="f3f62-201">Si, posteriormente, publica su PWA \ (EdgeHTML \) en Microsoft Store, estos [permisos de aplicación][MicrosoftSupportWindowsAppPermissions] obligatorios también se indican en la descripción de la tienda.</span><span class="sxs-lookup"><span data-stu-id="f3f62-201">If you later publish your PWA \(EdgeHTML\) to the Microsoft Store, these required [App permissions][MicrosoftSupportWindowsAppPermissions] are also noted in your store listing.</span></span>  

#### <span data-ttu-id="f3f62-202">Establecer reglas de URI de contenido de la aplicación (Acur)</span><span class="sxs-lookup"><span data-stu-id="f3f62-202">Set Application Content URI Rules (ACURs)</span></span>  

<span data-ttu-id="f3f62-203">A través de las Acur, también conocidas como una lista de direcciones URL permitidas, podrás dar a las direcciones URL de tu nombre de PWA \ \ (EdgeHTML \) acceso directo a las API de Windows Runtime.</span><span class="sxs-lookup"><span data-stu-id="f3f62-203">Through ACURs, otherwise known as a URL allow list, you are able to give the URLs of your PWA \(EdgeHTML\) direct access to Windows Runtime APIs.</span></span>  <span data-ttu-id="f3f62-204">En el nivel del sistema operativo Windows, los límites de la Directiva adecuada se establecen para permitir el código hospedado en el servidor web para enviar directamente solicitudes de API de plataforma.</span><span class="sxs-lookup"><span data-stu-id="f3f62-204">At the Windows OS level, the right policy bounds are set to allow code hosted on your web server to directly send platform API requests.</span></span>  <span data-ttu-id="f3f62-205">Estos límites se definen en el archivo de manifiesto del paquete de la aplicación al especificar las direcciones URL de PWA como `ApplicationContentUriRules` .</span><span class="sxs-lookup"><span data-stu-id="f3f62-205">You define these bounds in the app package manifest file when you specify your PWA URLs as `ApplicationContentUriRules`.</span></span>  

<span data-ttu-id="f3f62-206">Las reglas deben incluir la página de inicio de la aplicación y cualquier otra página que desee incluir en las páginas de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="f3f62-206">Your rules should include the start page for your app and any other pages you want included as app pages.</span></span>  <span data-ttu-id="f3f62-207">Si el usuario se desplaza a una dirección URL que no esté incluida en las reglas, Windows abrirá la dirección URL de destino en el explorador Microsoft Edge en lugar de la ventana independiente PWA \ (EdgeHTML \) \ ( `WWAHost.exe` proceso \).</span><span class="sxs-lookup"><span data-stu-id="f3f62-207">If your user navigates to a URL that is not included in your rules, Windows opens the target URL in the Microsoft Edge browser rather than your standalone PWA \(EdgeHTML\) window \(`WWAHost.exe` process\).</span></span>  <span data-ttu-id="f3f62-208">También puede excluir direcciones URL específicas.</span><span class="sxs-lookup"><span data-stu-id="f3f62-208">You may also exclude specific URLs.</span></span>  

<span data-ttu-id="f3f62-209">Hay varias formas de especificar una dirección URL `Match` en las reglas:</span><span class="sxs-lookup"><span data-stu-id="f3f62-209">There are several ways to specify a URL `Match` in your rules:</span></span>  

*   <span data-ttu-id="f3f62-210">Un nombre de host exacto</span><span class="sxs-lookup"><span data-stu-id="f3f62-210">An exact hostname</span></span>  
*   <span data-ttu-id="f3f62-211">Se incluye un nombre de host para el que se incluya o excluya un URI con un subdominio cualquiera de ese nombre de host</span><span class="sxs-lookup"><span data-stu-id="f3f62-211">A hostname for which a URI with any subdomain of that hostname is included or excluded</span></span>  
*   <span data-ttu-id="f3f62-212">Un URI exacto</span><span class="sxs-lookup"><span data-stu-id="f3f62-212">An exact URI</span></span>  
*   <span data-ttu-id="f3f62-213">Un URI exacto que contiene una propiedad de consulta</span><span class="sxs-lookup"><span data-stu-id="f3f62-213">An exact URI containing a query property</span></span>  
*   <span data-ttu-id="f3f62-214">Una ruta de acceso parcial y un comodín para indicar una extensión de archivo concreta para una regla de inclusión.</span><span class="sxs-lookup"><span data-stu-id="f3f62-214">A partial path and a wildcard to indicate a particular file extension for an include rule</span></span>  
*   <span data-ttu-id="f3f62-215">Rutas de acceso relativas para reglas de exclusión</span><span class="sxs-lookup"><span data-stu-id="f3f62-215">Relative paths for exclude rules</span></span>  

<span data-ttu-id="f3f62-216">Estos son algunos ejemplos de Acur en un `.appxmanifest` archivo:</span><span class="sxs-lookup"><span data-stu-id="f3f62-216">Here are a few examples of ACURs in a `.appxmanifest` file:</span></span>  

```xml
<Application
Id="App"
StartPage="https://contoso.com/home">
<uap:ApplicationContentUriRules>
    <uap:Rule Type="include" Match="https://contoso.com/" WindowsRuntimeAccess="all" />
    <uap:Rule Type="include" Match="https://*.contoso.com/" WindowsRuntimeAccess="all" />
    <uap:Rule Type="exclude" Match="https://contoso.com/excludethispage.aspx" />
</uap:ApplicationContentUriRules>
```  

<span data-ttu-id="f3f62-217">Las direcciones URL definidas dentro de las Acur para la aplicación pueden conceder permisos a Windows en tiempo de ejecución a través del `WindowsRuntimeAccess` atributo, que acepta los siguientes valores:</span><span class="sxs-lookup"><span data-stu-id="f3f62-217">URLs defined within the ACURs for your app are able to be granted permission to the Windows Runtime through the `WindowsRuntimeAccess` attribute, which accepts the following values:</span></span>  

*   `all`<span data-ttu-id="f3f62-218">: El código de JavaScript remoto tiene acceso a todas las API de WinRT y a cualquier componente local empaquetado.</span><span class="sxs-lookup"><span data-stu-id="f3f62-218">: Remote JavaScript code has access to all WinRT APIs and any local packaged components.</span></span>  <span data-ttu-id="f3f62-219">El espacio de nombres [Windows \ (WinRT \))][UwpApiIndex] se ha insertado y está presente en el motor de secuencias de comandos.</span><span class="sxs-lookup"><span data-stu-id="f3f62-219">The [Windows \(WinRT\))][UwpApiIndex] namespace is injected and present in the script engine.</span></span>  
*   `allowForWeb`<span data-ttu-id="f3f62-220">: El acceso a código remoto de JavaScript se limita a componentes empaquetados locales, incluidos los componentes personalizados de la versión C++/C #.</span><span class="sxs-lookup"><span data-stu-id="f3f62-220">: Remote JavaScript code access is limited to local packaged components, including custom C++/C# components.</span></span>  
*   `none`<span data-ttu-id="f3f62-221">Programas.</span><span class="sxs-lookup"><span data-stu-id="f3f62-221">: Default.</span></span>  <span data-ttu-id="f3f62-222">La dirección URL especificada no tiene acceso a la plataforma.</span><span class="sxs-lookup"><span data-stu-id="f3f62-222">The specified URL has no platform access.</span></span>  

<span data-ttu-id="f3f62-223">En este tutorial, ya ha establecido la única ACUR que necesita \ (paso 6 de la configuración anterior [y ejecutar](#set-up-and-run-your-universal-windows-app) la sección \ App \) para su aplicación de una sola página.</span><span class="sxs-lookup"><span data-stu-id="f3f62-223">In this tutorial, you already set the only ACUR that you need \(Step 6 of the previous [Set up and run your app](#set-up-and-run-your-universal-windows-app) section\) for your single-page app.</span></span>  <span data-ttu-id="f3f62-224">Puede confirmarlo en el panel **URI de contenido** del diseñador de Visual Studio `package.appxmanifest` .</span><span class="sxs-lookup"><span data-stu-id="f3f62-224">You are able to confirm this from the **Content URIs** panel of the Visual Studio `package.appxmanifest` designer.</span></span>  

![Panel URI de contenido del diseñador de Visual Studio appxmanifest](media/vs-appxmanifest-editor-acurs.png)  

<span data-ttu-id="f3f62-226">También puede ver el XML sin formato de su manifiesto haciendo clic con el botón secundario `package.appxmanifest` en el archivo en el explorador de soluciones de Visual Studio y seleccionando **Ver código** \ ( `F7` \).</span><span class="sxs-lookup"><span data-stu-id="f3f62-226">You are also able to view the raw XML of your manifest by right-clicking your `package.appxmanifest` file in Visual Studio Solution Explorer and selecting **View Code** \(`F7`\).</span></span>  <span data-ttu-id="f3f62-227">Para volver a la vista de diseñador, seleccione **Diseñador de vistas** \ ( `Shift` + `F7` \).</span><span class="sxs-lookup"><span data-stu-id="f3f62-227">To toggle back to the Designer view, select **View Designer** \(`Shift`+`F7`\).</span></span>  

#### <span data-ttu-id="f3f62-228">Declaraciones de funcionalidades de las aplicaciones</span><span class="sxs-lookup"><span data-stu-id="f3f62-228">App capability declarations</span></span>  

<span data-ttu-id="f3f62-229">Si tu aplicación necesita acceso mediante programación a recursos de usuario, como imágenes o música, o a dispositivos como una cámara o un micrófono, debes incluir las [declaraciones de funcionalidad][WindowsUwpPackagingAppCapabilities] de la aplicación correspondientes en el archivo de manifiesto del paquete de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="f3f62-229">If your app needs programmatic access to user resources like pictures or music, or to devices like a camera or a microphone, you must include the corresponding [App capability declarations][WindowsUwpPackagingAppCapabilities] in your app package manifest file.</span></span>  <span data-ttu-id="f3f62-230">Existen 3 categorías de declaración de funcionalidad de aplicación:</span><span class="sxs-lookup"><span data-stu-id="f3f62-230">There are three app capability declaration categories:</span></span>  

*   <span data-ttu-id="f3f62-231">[Funcionalidades de uso general][WindowsUwpPackagingAppCapabilitiesGeneralUse] que se aplican a la los escenarios de aplicaciones más habituales.</span><span class="sxs-lookup"><span data-stu-id="f3f62-231">[General-use capabilities][WindowsUwpPackagingAppCapabilitiesGeneralUse] that apply to most common app scenarios.</span></span>  
*   <span data-ttu-id="f3f62-232">[Funcionalidades de dispositivo][WindowsUwpPackagingAppCapabilitiesDevice] que permiten a tu aplicación acceder a periféricos y dispositivos internos.</span><span class="sxs-lookup"><span data-stu-id="f3f62-232">[Device capabilities][WindowsUwpPackagingAppCapabilitiesDevice] that allow your app to access peripheral and internal devices.</span></span>  
*   <span data-ttu-id="f3f62-233">[Capacidades de uso especial][WindowsUwpPackagingAppCapabilitiesSpecialRestricted] que admiten escenarios empresariales y requieren una cuenta de Microsoft Store Company.</span><span class="sxs-lookup"><span data-stu-id="f3f62-233">[Special-use capabilities][WindowsUwpPackagingAppCapabilitiesSpecialRestricted] that support enterprise scenarios and require a Microsoft Store company account.</span></span>  <span data-ttu-id="f3f62-234">Para obtener más información sobre las cuentas de empresa, consulta [Tipos de cuenta, ubicaciones y precios][WindowsUwpPublishAccountTypesLocationsFees].</span><span class="sxs-lookup"><span data-stu-id="f3f62-234">For more info about company accounts, see [Account types, locations, and fees][WindowsUwpPublishAccountTypesLocationsFees].</span></span>

<span data-ttu-id="f3f62-235">La página de la aplicación Microsoft Store muestra todas las funciones que declares en el manifiesto del paquete de la aplicación, así que asegúrate de especificar solo las funcionalidades que tu aplicación realmente usa.</span><span class="sxs-lookup"><span data-stu-id="f3f62-235">Your Microsoft Store app page lists all the capabilities you declare in your app package manifest, so be sure to only specify the capabilities that your app actually uses.</span></span>

<span data-ttu-id="f3f62-236">Algunas funciones proporcionan a las aplicaciones acceso a recursos confidenciales.</span><span class="sxs-lookup"><span data-stu-id="f3f62-236">Some capabilities provide apps access to sensitive resources.</span></span>  <span data-ttu-id="f3f62-237">Estos recursos se consideran confidenciales porque cada uno de ellos puede acceder a los datos personales del usuario o costar dinero al usuario.</span><span class="sxs-lookup"><span data-stu-id="f3f62-237">These resources are considered sensitive because each is able to access the user's personal data or cost the user money.</span></span>  <span data-ttu-id="f3f62-238">La configuración de privacidad, administrada por la aplicación [configuración][BingResultsWindows10Settings] de Windows 10, permite que el usuario controle dinámicamente el acceso a los recursos confidenciales.</span><span class="sxs-lookup"><span data-stu-id="f3f62-238">Privacy settings, managed by the Windows 10 [Settings][BingResultsWindows10Settings] app, let the user dynamically control access to sensitive resources.</span></span>  <span data-ttu-id="f3f62-239">Por lo tanto, es importante que la aplicación no asuma que un recurso sensible siempre esté disponible.</span><span class="sxs-lookup"><span data-stu-id="f3f62-239">Thus, it is important that your app does not assume a sensitive resource is always available.</span></span>  <span data-ttu-id="f3f62-240">Para obtener más información sobre cómo acceder a recursos confidenciales, consulta las [Directrices para aplicaciones compatibles con la privacidad][WindowsUwp|::ref2::|Index].</span><span class="sxs-lookup"><span data-stu-id="f3f62-240">For more info about accessing sensitive resources, see [Guidelines for privacy-aware apps][WindowsUwp|::ref2::|Index].</span></span>  

<span data-ttu-id="f3f62-241">Para solicitar acceso, declara funcionalidades en el manifiesto del paquete de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="f3f62-241">You request access by declaring capabilities in the package manifest for your app.</span></span>  <span data-ttu-id="f3f62-242">En Visual Studio, puedes hacerlo desde el panel de **funciones** del diseñador package. appxmanifest.</span><span class="sxs-lookup"><span data-stu-id="f3f62-242">In Visual Studio, you are able to do this from the **Capabilities** panel of the package.appxmanifest designer.</span></span>  

![Panel capacidades del diseñador de Visual Studio appxmanifest](media/vs-appxmanifest-editor-capabilities.png)  

<span data-ttu-id="f3f62-244">En este tutorial, solo se necesita la funcionalidad predeterminada de Internet \ (cliente \), por lo que no es necesaria ninguna otra acción.</span><span class="sxs-lookup"><span data-stu-id="f3f62-244">In this tutorial, only the default Internet \(Client\) capability is required, so no further action is needed.</span></span>  

### <span data-ttu-id="f3f62-245">Usar la detección de características para invocar WinRT</span><span class="sxs-lookup"><span data-stu-id="f3f62-245">Use feature detection to invoke WinRT</span></span>  

<span data-ttu-id="f3f62-246">Para garantizar una experiencia de línea base de calidad para la audiencia de PWA en todas las plataformas, mejore progresivamente su experiencia de PWA en Windows usando la detección de características de WinRT.</span><span class="sxs-lookup"><span data-stu-id="f3f62-246">To ensure a quality baseline experience for your PWA audience across all platforms, you progressively enhance your PWA experience on Windows using WinRT feature detection.</span></span>  <span data-ttu-id="f3f62-247">De esta manera, podrás asegurarte de que el código específico de Windows solo se ejecuta en un contexto en el que las API de WinRT estén disponibles y sean aplicables.</span><span class="sxs-lookup"><span data-stu-id="f3f62-247">This way, you are able to be sure your Windows-specific code is only run in a context where WinRT APIs are available and applicable.</span></span>  

<span data-ttu-id="f3f62-248">La detección de características puede ser tan simple como buscar el `Windows` objeto \ (el punto de espera del [espacio de nombres WinRT][UwpApiIndex]\) como se indica a continuación:</span><span class="sxs-lookup"><span data-stu-id="f3f62-248">Feature detection may be as simple as looking for the `Windows` object \(the entrypoint to the [WinRT namespace][UwpApiIndex]\) as below:</span></span>  

```javascript
if(window.Windows){
    /*Run code that sends Windows API requests */
}
```  

<span data-ttu-id="f3f62-249">Sin embargo, dado que no todas las API de Windows están disponibles en todos los [tipos de dispositivos de Windows 10][UwpExtensionSdkDeviceFamiliesOverview], generalmente es útil usar una detección de características más específica para calificar aún más el espacio de nombres de la solicitud de API que se envía:</span><span class="sxs-lookup"><span data-stu-id="f3f62-249">However, given that not all Windows APIs are available on all [Windows 10 device types][UwpExtensionSdkDeviceFamiliesOverview], it is generally useful to use more specific feature detection to further qualify the namespace of the API request you are sending:</span></span>  

```javascript
if(window.Windows && Windows.Media.SpeechRecognition){
    /*Run code that sends Windows API requests */
}
```  

<span data-ttu-id="f3f62-250">Con ese fondo, estás listo para agregar código WinRT para implementar un menú contextual personalizado.</span><span class="sxs-lookup"><span data-stu-id="f3f62-250">With that background, you are ready to add some WinRT code to implement a custom context menu.</span></span>  <span data-ttu-id="f3f62-251">Si usa el ejemplo PWA de introducción [a las aplicaciones web progresivas][PwaGetStarted]:</span><span class="sxs-lookup"><span data-stu-id="f3f62-251">If you are using the sample PWA from [Get started with Progressive Web Apps][PwaGetStarted]:</span></span>

1.  <span data-ttu-id="f3f62-252">Abra Visual Studio en el proyecto de sitio de PWA.</span><span class="sxs-lookup"><span data-stu-id="f3f62-252">Open Visual Studio to your PWA site project.</span></span>

1.  <span data-ttu-id="f3f62-253">En el explorador de soluciones, abra el `views\layout.pug` archivo y agregue la línea siguiente, justo debajo de la `script` Referencia del trabajador del servicio:</span><span class="sxs-lookup"><span data-stu-id="f3f62-253">In Solution Explorer, open the `views\layout.pug` file and add the following line, right below the `script` reference for your service worker:</span></span>
    
    ```xml
    script(src='/javascripts/site.js')
    ```  

1.  <span data-ttu-id="f3f62-254">En el explorador de soluciones, haga clic con el botón derecho en la `javascripts` carpeta y **agregue**  >  **nuevo archivo...**</span><span class="sxs-lookup"><span data-stu-id="f3f62-254">In Solution Explorer, right-click on the `javascripts` folder and **Add** > **New File...**.</span></span>

1.  <span data-ttu-id="f3f62-255">Asigne un nombre al archivo `site.js` y cópielo en el siguiente código:</span><span class="sxs-lookup"><span data-stu-id="f3f62-255">Name your file: `site.js`, and copy in the following code:</span></span>
    
    ```javascript
    if (window.Windows && Windows.UI.Popups) {
        document.addEventListener('contextmenu', function (e) {

            // Build the context menu
            var menu = new Windows.UI.Popups.PopupMenu();
            menu.commands.append(new Windows.UI.Popups.UICommand("Option 1", null, 1));
            menu.commands.append(new Windows.UI.Popups.UICommandSeparator);
            menu.commands.append(new Windows.UI.Popups.UICommand("Option 2", null, 2));

            // Convert from webpage to WinRT coordinates
            function pageToWinRT(pageX, pageY) {
                var zoomFactor = document.documentElement.msContentZoomFactor;
                return {
                    x: (pageX - window.pageXOffset) * zoomFactor,
                    y: (pageY - window.pageYOffset) * zoomFactor
                };
            }

            // When the menu is invoked, execute the requested command
            menu.showAsync(pageToWinRT(e.pageX, e.pageY)).done(function (invokedCommand) {
                if (invokedCommand !== null) {
                    switch (invokedCommand.id) {
                        case 1:
                            console.log('Option 1 selected');
                            // Invoke code for option 1
                            break;
                        case 2:
                            console.log('Option 2 selected');
                            // Invoke code for option 2
                            break;
                        default:
                            break;
                    }
                } else {
                    // The command is null if no command was invoked.
                    console.log("Context menu dismissed");
                }
            });
        }, false);
    }
    ```

1.  <span data-ttu-id="f3f62-256">Compare el comportamiento del menú contextual cuando ejecute su PWA en el explorador \ ( `F5` desde el proyecto de sitio de PWA \) o desde dentro de la ventana de la aplicación de Windows \ ( `F5` desde el proyecto de aplicación universal de Windows \).</span><span class="sxs-lookup"><span data-stu-id="f3f62-256">Compare the context menu behavior when you run your PWA in the browser \(`F5` from your PWA site project\) versus from inside the Windows app window \(`F5` from your Universal Windows app project\).</span></span>  <span data-ttu-id="f3f62-257">En el explorador, al hacer clic con el botón secundario se le proporciona el menú contextual de Microsoft Edge predeterminado mientras que, en el `WWAHost.exe` proceso, aparece ahora el menú personalizado.</span><span class="sxs-lookup"><span data-stu-id="f3f62-257">In the browser, right-clicking gives you the Microsoft Edge default context menu, whereas in the `WWAHost.exe` process, your custom menu now appears.</span></span>  

    | <span data-ttu-id="f3f62-258">Microsoft Edge</span><span class="sxs-lookup"><span data-stu-id="f3f62-258">Microsoft Edge</span></span> | <span data-ttu-id="f3f62-259">Aplicación de Windows 10</span><span class="sxs-lookup"><span data-stu-id="f3f62-259">Windows 10 app</span></span> |  
    |:--- |:---- |  
    | ![Menú contextual predeterminado del explorador](media/browser-context-menu.png) | ![Menú contextual personalizado de la aplicación](media/app-context-menu.png) |  

<span data-ttu-id="f3f62-262">Afortunadamente, ahora tienes una base sólida para mejorar de manera progresiva tu PWAs en Windows.</span><span class="sxs-lookup"><span data-stu-id="f3f62-262">Hopefully you now have a solid foundation for progressively enhancing your PWAs on Windows.</span></span>  <span data-ttu-id="f3f62-263">Si tienes preguntas o algo no está claro, envía un comentario.</span><span class="sxs-lookup"><span data-stu-id="f3f62-263">If you run into questions or anything is unclear, please send a comment!</span></span>  

## <span data-ttu-id="f3f62-264">Ir más allá</span><span class="sxs-lookup"><span data-stu-id="f3f62-264">Going further</span></span>

<span data-ttu-id="f3f62-265">El [centro de desarrollo de Windows][MicrosoftDeveloperWindowsApps] es tu referencia completa para todas las fases de la creación de aplicaciones de Windows, desde [Introducción][MicrosoftDeveloperWindowsAppsGetStarted], hasta [diseñar][MicrosoftDeveloperWindowsAppsDesign], [desarrollar][MicrosoftDeveloperWindowsAppsDevelop]y [publicar][MicrosoftDeveloperStorePublishApps] en Microsoft Store.</span><span class="sxs-lookup"><span data-stu-id="f3f62-265">The [Windows Dev Center][MicrosoftDeveloperWindowsApps] is your complete reference for all stages of Windows app building, from [getting started][MicrosoftDeveloperWindowsAppsGetStarted], to [designing][MicrosoftDeveloperWindowsAppsDesign], [developing][MicrosoftDeveloperWindowsAppsDevelop], and [publishing][MicrosoftDeveloperStorePublishApps] to the Microsoft Store.</span></span>  

<span data-ttu-id="f3f62-266">Para obtener información general sobre la plataforma universal de Windows \ (UWP \) y sobre cómo dirigir distintas familias de dispositivos de Windows 10, consulta [Introducción a la plataforma universal de Windows][WindowsUWPGetStartedGuide].</span><span class="sxs-lookup"><span data-stu-id="f3f62-266">For a general overview on the Universal Windows Platform \(UWP\) and how to target different Windows 10 device families, see [Intro to the Universal Windows Platform][WindowsUWPGetStartedGuide].</span></span>  

<span data-ttu-id="f3f62-267">Y cuando esté listo, aquí se muestra cómo \ (y por qué! \) [enviar su PWA a Microsoft Store](./microsoft-store.md).</span><span class="sxs-lookup"><span data-stu-id="f3f62-267">And when you are ready, here is how \(and why!\) to [Submit your PWA to the Microsoft Store](./microsoft-store.md).</span></span>  

<!-- image links -->  

<!-- links -->  

[PwaGetStarted]: ./get-started.md "Introducción a las aplicaciones web progresivas"  
[PwaIndexWindows10]: ./index.md#pwas-on-windows-10-edgehtml "PWAs en Windows 10 (EdgeHTML): aplicaciones web progresivas en Windows"  
[DevToolsGuide]: ../devtools-guide.md "Herramientas para desarrolladores de Microsoft Edge (EdgeHTML)"  
[DevToolsGuideMicrosoftStoreApp]: ../devtools-guide.md#microsoft-store-app "Aplicación Microsoft Store: herramientas para desarrolladores de Microsoft Edge (EdgeHTML)"  
[DevToolsGuideServiceWorkers]: ../devtools-guide/service-workers.md "Trabajadores de servicio"  
[DevToolsProtocol01ClientsEdgePreview]: ../devtools-protocol/0.1/clients.md#microsoft-edge-devtools-preview "Microsoft Edge DevTools Preview-clientes de protocolo DevTools"  
[DevGuideWhatsNew]: ../dev-guide/whats-new.md "Novedades de EdgeHTML"  
[WindowsRuntime]: ../windows-runtime/index.md "Windows Runtime (WinRT) para JavaScript"  
[WindowRuntimeUsingJavascript]: ../windows-runtime/using-the-windows-runtime-in-javascript.md "Usar Windows Runtime en JavaScript"  

[ScriptingJsinrtHandlingWinRTEvents]: /scripting/jswinrt/handling-windows-runtime-events-in-javascript "Controlar eventos de Windows Runtime en JavaScript"  
[ScriptingJsinrtUsingWinRT]: /scripting/jswinrt/using-windows-runtime-asynchronous-methods "Uso de los métodos asincrónicos de Windows Runtime"  
[ScriptingJsinrtUsingWinRTCasingConventions]:  /scripting/jswinrt/using-the-windows-runtime-in-javascript#casing-conventions-with-windows-runtime-features "Convenciones de las mayúsculas y minúsculas con características de Windows Runtime: uso de Windows Runtime en JavaScript"  
[UwpApiIndex]: /uwp/api/index "Espacios de nombres de Windows para UWP"  
[UwpApiWindowsUiPopups]: /uwp/api/windows.ui.popups "Espacio de nombres Windows. UI. popups"  
[UwpApiWindowsUiWebuiWebapplicationActivated]: /uwp/api/windows.ui.webui.webuiapplication.activated "Evento WebUIApplication. Activated"  
[UwpExtensionSdkDeviceFamiliesOverview]: /uwp/extension-sdks/device-families-overview "Descripción general de las familias de dispositivos"  
[UwpSchemasAppxpackageUapmanifestschemaGeneratePackageManifest]: /uwp/schemas/appxpackage/uapmanifestschema/generate-package-manifest "Cómo genera Visual Studio un manifiesto del paquete de la aplicación"  
[WindowsUWPIndex]: /windows/uwp/index "Documentación de la plataforma universal de Windows"  
[WindowsUWPGetStartedGuide]: /windows/uwp/get-started/universal-application-platform-guide "¿Qué es una aplicación para la plataforma universal de Windows (UWP)?"  
[WindowsUWPGetStartedEnable]: /windows/uwp/get-started/enable-your-device-for-development "Habilitar el dispositivo para el desarrollo"  
[WindowsUwpSecurityIndex]: /windows/uwp/security/index "Seguridad"  
[WindowsUwpPublishAccountTypesLocationsFees]: /windows/uwp/publish/account-types-locations-and-fees "Tipos de cuenta, ubicaciones y cuotas"  
[WindowsUwpPackagingAppCapabilitiesSpecialRestricted]: /windows/uwp/packaging/app-capability-declarations#special-and-restricted-capabilities "Capacidades restringidas"  
[WindowsUwpPackagingAppCapabilitiesDevice]: /windows/uwp/packaging/app-capability-declarations#device-capabilities "Capacidades del dispositivo"  
[WindowsUwpPackagingAppCapabilitiesGeneralUse]: /windows/uwp/packaging/app-capability-declarations#general-use-capabilities "Capacidades de uso general"  
[WindowsUwpPackagingAppCapabilities]: /windows/uwp/packaging/app-capability-declarations "Declaraciones de funcionalidades de aplicaciones"  

[BingResultsWindows10Settings]: https://binged.it/2lOGSH0 "configuración de Windows 10: Bing"  
[GithubWinjsWinjs]: https://github.com/winjs/winjs "winjs/winjs | GitHub"  
[MicrosoftDeveloperStorePublishApps]: https://developer.microsoft.com/store/publish-apps/index "Publicar aplicaciones y juegos de Windows"  
[MicrosoftDeveloperWindowsApps]: https://developer.microsoft.com/windows/apps/index "Documentación de la plataforma universal de Windows"  
[MicrosoftDeveloperWindowsAppsDesign]: https://developer.microsoft.com/windows/apps/design/index "Diseñar y codificar aplicaciones de Windows"  
[MicrosoftDeveloperWindowsAppsDevelop]: https://developer.microsoft.com/windows/apps/develop/index "Desarrollar aplicaciones para UWP"  
[MicrosoftDeveloperWindowsAppsGetStarted]: https://developer.microsoft.com/windows/apps/getstarted/index "Introducción a las aplicaciones de Windows 10"  
[MicrosoftDeveloperWindowsSamples]: https://developer.microsoft.com/windows/samples "Ejemplos de código"  
[MicrosoftStoreEdgeDevtoolsPreview]: https://www.microsoft.com/store/p/microsoft-edge-devtools-preview/9mzbfrmz0mnj "Vista previa de Microsoft Edge DevTools"  
[MicrosoftSupportWindowsAppPermissions]: https://support.microsoft.com/help/10557/windows-10-app-permissions "Permisos de aplicación"  
[MicrosoftVisualStudioDownloads]: https://visualstudio.microsoft.com/downloads "Descargas"  
[MicrosoftVisualStudioPreview]: https://visualstudio.microsoft.com/vs/preview "Vista previa de Visual Studio"  