---
description: Conozca las Herramientas de desarrollo de Microsoft Edge (EdgeHTML)
title: Herramientas de desarrollo de Microsoft Edge (EdgeHTML)
author: MSEdgeTeam
ms.author: msedgedevrel
ms.date: 09/01/2020
ms.topic: article
ms.prod: microsoft-edge
ms.technology: devtools
keywords: microsoft edge, web development, f12 tools, devtools 
experimental: true 
experiment_id: "51fe4b97-3e55-41"
ms.localizationpriority: high
---

# Herramientas de desarrollo de Microsoft Edge (EdgeHTML)  

[!INCLUDE [new-devtools-version-note](includes/new-devtools-version-note.md)]  

Las Herramientas de desarrollo de Microsoft Edge \(EdgeHTML\) se han creado con [TypeScript][TypeScriptIndex], con tecnología de [código abierto][GithubMicrosoftChakracore]. Están optimizadas para los flujos de trabajo front-end modernos y ahora disponibles como una [aplicación independiente de Windows 10][MicrosoftStoreEdgeDevtoolsPreview] en la Microsoft Store.  

Para obtener más información sobre las características más recientes, vea las [Herramientas de desarrollo de la actualización más reciente de Windows 10 (EdgeHTML 18)][DevtoolsGuideEdgehtmlWhatsnew].  

## Herramientas básicas  

:::image type="complex" source="./devtools-guide/media/devtools.png" alt-text="Herramientas de desarrollo de Microsoft Edge (EdgeHTML)":::
   Herramientas de desarrollo de Microsoft Edge (EdgeHTML)
:::image-end:::

<!--![Microsoft Edge \(EdgeHTML\) DevTools][ImageDevtoolsEdgehtml]  -->  

Las Herramientas de desarrollo de Microsoft Edge \(EdgeHTML\) incluyen:  

*   Un panel [Elementos][DevtoolsGuideEdgehtmlElements] para editar HTML y CSS, inspeccionar propiedades de accesibilidad, ver escuchas de eventos y definir puntos de interrupción de mutación de DOM.  
*   Una [Consola][DevtoolsGuideEdgehtmlConsole] para ver y filtrar los mensajes de registro, inspeccionar objetos de JavaScript y nodos DOM y ejecutar JavaScript en el contexto de la ventana o marco seleccionados.  
*   Un [Depurador][DevtoolsGuideEdgehtmlDebugger] para revisar el código, establecer relojes y puntos de interrupción, editar en vivo el código y revisar el almacenamiento web y las cachés de cookies.  
*   Un panel de [Red][DevtoolsGuideEdgehtmlNetwork] para supervisar e inspeccionar las solicitudes y respuestas desde la memoria caché del explorador y la red.  
*   Un panel de [Rendimiento][DevtoolsGuideEdgehtmlPerformance] para perfilar los recursos de tiempo y de sistema necesarios para el sitio.  
*   Un panel de [Memoria][DevtoolsGuideEdgehtmlMemory] para medir el uso de los recursos de memoria y comparar las instantáneas de montón en diferentes estados del tiempo de ejecución de código.  
*   Un panel de [Almacenamiento][DevtoolsGuideEdgehtmlStorage] para inspeccionar y administrar el almacenamiento Web, IndexedDB, cookies y datos de la caché.  
*   Un panel [Service Workers][DevtoolsGuideEdgehtmlServiceworkers] para administrar y depurar los trabajos de los service workers.  
*   Un panel [Emulación][DevtoolsGuideEdgehtmlEmulation] para probar el sitio con diferentes perfiles de explorador, resoluciones de pantalla y coordenadas de ubicación de GPS.  

Siga enviándonos sus [comentarios y solicitudes de características](#getting-in-touch-with-the-microsoft-edge-devtools-team).  

> [!TIP]
> [Haga pruebas en Microsoft Edge \(EdgeHTML\) gratis desde cualquier explorador][BrowserstackEdgehtml].  
> El equipo de Microsoft Edge se ha asociado con [BrowserStack][BrowserstackEdgehtml] para ofrecer pruebas gratuitas en tiempo real y automatizadas en Microsoft Edge \(EdgeHTML\).  

## App de Microsoft Store  

Las **Herramientas de desarrollo** de Microsoft Edge \(EdgeHTML\) están [ahora disponibles][DevtoolsGuideEdgehtmlWhatsnew] como una aplicación de [Windows 10 para Microsoft Store][MicrosoftStoreEdgeDevtoolsPreview] llamada Microsoft Edge DevTools, además de las Herramientas del explorador (`F12`). En la versión para Microsoft Store viene un panel **selector** de adjuntar para abrir destinos de página locales y remotos, y un diseño con pestañas para facilitar el cambio entre las instancias de DevTools.  

### Depuración local  

Para depurar una página localmente, solo tiene que iniciar la aplicación Microsoft Edge DevTools. El panel Local del selector muestra todos los procesos de contenido de EdgeHTML activos, incluidas las pestañas del explorador abiertas, las [PWA][PwasEdgehtmlIndex] (procesos WWAHost.exe) y los controles [webview][HostingWebview]. Seleccione el destino que quiera adjuntar y abra una nueva instancia de la pestaña de la DevTools.  

:::image type="complex" source="./devtools-guide/media/chooser_local.png" alt-text="Panel local de la app DevTools":::
   Panel local de la app DevTools 
:::image-end:::

<!--![DevTools app Local panel][ImageDevtoolsGuideEdgehtmlChooselocal]  -->  

### Depuración remota  

La aplicación Microsoft Edge DevTools introduce la compatibilidad básica para la depuración de páginas en un equipo remoto a través de nuestro [protocolo de DevTools][DevtoolsProtocolEdgehtmlIndex] recientemente publicado. Con la versión más reciente, se obtiene acceso remoto a la funcionalidad principal de los paneles Depurador, Elementos (para las operaciones de solo lectura) y [Consola][DevtoolsGuideEdgehtmlConsole]. La depuración remota está limitada a los hosts de escritorio que ejecuten Microsoft Edge \(EdgeHTML\). En futuras versiones, ofreceremos compatibilidad con otros hosts de EdgeHTML y dispositivos Windows 10.  

Para empezar, consulte la sección Microsoft Edge DevTools de los documentos del [Protocolo de DevTools][DevtoolsProtocolEdgehtmlIndex].  

:::image type="complex" source="./devtools-guide/media/chooser_remote.png" alt-text="Panel remoto de DevTools app":::
   Panel remoto de DevTools app 
:::image-end:::

<!--![DevTools app Remote panel][ImageDevtoolsGuideEdgehtmlRemote]  -->  

## Métodos abreviados generales  

> [!IMPORTANT]
> Todos los métodos abreviados se han comprobado en la versión más reciente de Windows.  
> Si no puede usar un método abreviado de teclado, debe actualizar su copia de Windows.  

Estos métodos abreviados controlan la ventana de DevTools principal y deberían funcionar en todas las herramientas.  

| Acción | Acceso directo |  
|:--- |:--- |  
| Mostrar u ocultar DevTools (se abre en el último panel visto) | `F12`, `Ctrl`+`Mayus`+`I` |  
| Activar o desactivar el acoplamiento (desacoplar, inferior/derecho) | `Ctrl`+`Mayus`+`D` |  
| Abrir archivo | `Ctrl`+`P`, `Ctrl`+`O` |  
| Mostrar el código fuente HTML no modificable en el Depurador | `Ctrl`+`U` |  
| Mostrar u ocultar Consola en la parte inferior de cualquier otra herramienta | `Ctrl`+`` ` `` |  
| Cambiar a elementos (Explorador de DOM) | `Ctrl`+`1` |  
| Cambiar a Consola | `Ctrl`+`2` |  
| Cambiar a Depurador | `Ctrl`+`3` |  
| Cambiar a Red | `Ctrl`+`4` |  
| Cambiar a Rendimiento | `Ctrl`+`5` |  
| Cambiar a Memoria | `Ctrl`+`6` |  
| Cambiar a Emulación | `Ctrl`+`7` |  
| Documento de ayuda | `F1` |  
| Herramienta siguiente | `Ctrl`+`F6` |  
| Herramienta anterior | `Ctrl`+`Mayus`+`F6` |  
| Herramienta anterior (del historial) | `Ctrl`+`Mayús`+`[` |  
| Herramienta siguiente (del historial) | `Ctrl`+`Mayús`+`]` |  
| Submarco siguiente | `F6` |  
| Submarco anterior | `Mayús`+`F6` |  
| Coincidencia siguiente en el Cuadro de búsqueda | `F3` |  
| Coincidencia anterior en el cuadro de búsqueda | `Mayús`+`F3` |  
| Buscar en el cuadro de búsqueda | `Ctrl`+`F` |  
| Dar el enfoque a la consola en la parte inferior | `Alt`+`Mayus`+`I` |  
| Iniciar DevTools en la consola | `Ctrl`+`Mayus`+`J` |  
| Actualizar la página | `Ctrl`+`Mayus`+`F5`, `Ctrl`+`R` |  

> [!NOTE]
> Si está depurando y pausa en un punto de ruptura, la acción **Actualizar la página** reanuda primero el tiempo de ejecución.  

## Cómo ponerse en contacto con el equipo de Herramientas de desarrollo de Microsoft Edge  

Envíenos sus comentarios para ayudar a mejorar las Herramientas de desarrollo de Microsoft Edge \(EdgeHTML\). Simplemente, abra las herramientas (`F12`) y seleccione el botón [Enviar comentarios](#microsoft-edge-edgehtml-developer-tools).  

Conviértase en un [Windows Insider][WindowsInsiderProgram] para previsualizar [las características más recientes de las Herramientas de desarrollo][DevtoolsGuideEdgehtmlWhatsnew]. Use la aplicación del Centro de opiniones sobre Windows para publicar, votar, seguir y obtener soporte técnico sobre distintas sugerencias y problemas generales de Windows.  

<!-- image links  -->  

<!--[ImageDevtoolsEdgehtml]: /microsoft-edge/devtools-guide/media/devtools.png "Microsoft Edge (EdgeHTML) DevTools"  -->  
<!--[ImageDevtoolsGuideEdgehtmlChooselocal]: /microsoft-edge/devtools-guide/media/chooser_local.png "DevTools app Local panel"  -->  
<!--[ImageDevtoolsGuideEdgehtmlRemote]: /microsoft-edge/devtools-guide/media/chooser_remote.png "DevTools app Remote panel"  -->  

<!-- links  -->  

[DevtoolsGuideEdgehtmlConsole]: /microsoft-edge/devtools-guide/console "Consola"  
[DevtoolsGuideEdgehtmlDebugger]: /microsoft-edge/devtools-guide/debugger "Depurador"  
[DevtoolsGuideEdgehtmlElements]: /microsoft-edge/devtools-guide/elements "Elementos"  
[DevtoolsGuideEdgehtmlEmulation]: /microsoft-edge/devtools-guide/emulation "Emulación"  
[DevtoolsGuideEdgehtmlMemory]: /microsoft-edge/devtools-guide/memory "Memoria"  
[DevtoolsGuideEdgehtmlNetwork]: /microsoft-edge/devtools-guide/network "Red"  
[DevtoolsGuideEdgehtmlPerformance]: /microsoft-edge/devtools-guide/performance "Rendimiento"  
[DevtoolsGuideEdgehtmlServiceworkers]: /microsoft-edge/devtools-guide/service-workers "Service Workers"  
[DevtoolsGuideEdgehtmlStorage]: /microsoft-edge/devtools-guide/storage "Almacenamiento"  
[DevtoolsGuideEdgehtmlWhatsnew]: /microsoft-edge/devtools-guide/whats-new "Las Herramientas de desarrollo en la actualización más reciente de Windows 10 (EdgeHTML 18)"  
[DevtoolsProtocolEdgehtmlIndex]: /microsoft-edge/devtools-protocol/index "Protocolo de las Herramientas de desarrollo de Microsoft Edge (EdgeHTML)"  
[DevtoolsProtocolEdgehtmlClientsEdgePreview]: /microsoft-edge/devtools-protocol/0.1/clients.md#microsoft-edge-devtools-preview "Versión preliminar de las Herramientas de desarrollo de Microsoft Edge: Clientes de protocolo de las Herramientas de desarrollo"  
[HostingWebview]: /microsoft-edge/hosting/webview "WebView (EdgeHTML) para las aplicaciones de Windows 10"  
[PwasEdgehtmlIndex]: /microsoft-edge/progressive-web-apps-edgehtml/index "Aplicaciones web progresivas (EdgeHTML) en Windows"  

[MicrosoftStoreEdgeDevtoolsPreview]: https://www.microsoft.com/store/p/microsoft-edge-devtools-preview/9mzbfrmz0mnj "Versión preliminar de las Herramientas de desarrollo de Microsoft Edge"  

[WindowsInsiderProgram]: https://insider.windows.com "Programa Windows Insider"  

[BrowserstackEdgehtml]: https://www.browserstack.com/test-on-microsoft-edge-browser "Pruebas de explorador en Microsoft Edge gratis | BrowserStack"  

[GithubMicrosoftChakracore]: https://github.com/Microsoft/ChakraCore "microsoft/ChakraCore | GitHub"  

[TypeScriptIndex]: https://www.typescriptlang.org "TypeScript"  
