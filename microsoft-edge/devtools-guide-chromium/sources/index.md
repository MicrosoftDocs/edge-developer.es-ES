---
description: Visualice y edite archivos, cree fragmentos, depure JavaScript y configure áreas de trabajo en el panel orígenes de Microsoft Edge DevTools.
title: Información general del panel orígenes
author: MSEdgeTeam
ms.author: msedgedevrel
ms.date: 12/17/2020
ms.topic: article
ms.prod: microsoft-edge
keywords: Microsoft Edge, desarrollo web, herramientas F12, DevTools
ms.openlocfilehash: b90f927670146c004a335256ace28203219442eb
ms.sourcegitcommit: a35a6b5bbc21b7df61d08cbc6b074b5325ad4fef
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/17/2020
ms.locfileid: "11236048"
---
<!-- Copyright Kayce Basques 

   Licensed under the Apache License, Version 2.0 (the "License");
   you may not use this file except in compliance with the License.
   You may obtain a copy of the License at

       https://www.apache.org/licenses/LICENSE-2.0

   Unless required by applicable law or agreed to in writing, software
   distributed under the License is distributed on an "AS IS" BASIS,
   WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
   See the License for the specific language governing permissions and
   limitations under the License.  -->

# <span data-ttu-id="e74a0-104">Información general del panel orígenes</span><span class="sxs-lookup"><span data-stu-id="e74a0-104">Sources panel overview</span></span>  

<span data-ttu-id="e74a0-105">Use el panel de **orígenes** de Microsoft Edge DevTools para realizar las siguientes acciones.</span><span class="sxs-lookup"><span data-stu-id="e74a0-105">Use the Microsoft Edge DevTools **Sources** panel to perform the following actions.</span></span>  

*   <span data-ttu-id="e74a0-106">[Archivos de visualización](#display-files).</span><span class="sxs-lookup"><span data-stu-id="e74a0-106">[Display files](#display-files).</span></span>  
*   <span data-ttu-id="e74a0-107">[Edite CSS y JavaScript](#edit-css-and-javascript).</span><span class="sxs-lookup"><span data-stu-id="e74a0-107">[Edit CSS and JavaScript](#edit-css-and-javascript).</span></span>  
*   <span data-ttu-id="e74a0-108">[Cree y guarde **fragmentos** de código de JavaScript](#create-save-and-run-snippets), que puede ejecutar en cualquier página web.</span><span class="sxs-lookup"><span data-stu-id="e74a0-108">[Create and save **Snippets** of JavaScript](#create-save-and-run-snippets), which you may run on any webpage.</span></span>  <span data-ttu-id="e74a0-109">Los **fragmentos de código** son similares a bookmarklets.</span><span class="sxs-lookup"><span data-stu-id="e74a0-109">**Snippets** are similar to bookmarklets.</span></span>  
*   <span data-ttu-id="e74a0-110">[Depure JavaScript](#debug-javascript).</span><span class="sxs-lookup"><span data-stu-id="e74a0-110">[Debug JavaScript](#debug-javascript).</span></span>  
*   <span data-ttu-id="e74a0-111">[Configure un área de trabajo](#set-up-a-workspace)para que los cambios que realice en DevTools se guarden en el código de su sistema de archivos.</span><span class="sxs-lookup"><span data-stu-id="e74a0-111">[Set up a Workspace](#set-up-a-workspace), so that changes you make in DevTools get saved to the code on your file system.</span></span>  
    
## <span data-ttu-id="e74a0-112">Archivos de visualización</span><span class="sxs-lookup"><span data-stu-id="e74a0-112">Display files</span></span>  

<span data-ttu-id="e74a0-113">Use el panel de **páginas** para mostrar todos los recursos que la página ha cargado.</span><span class="sxs-lookup"><span data-stu-id="e74a0-113">Use the **Page** pane to display all of the resources that the page has loaded.</span></span>

:::image type="complex" source="../media/sources-page-pane.msft.png" alt-text="El panel de páginas" lightbox="../media/sources-page-pane.msft.png":::
   <span data-ttu-id="e74a0-115">El panel de **páginas**</span><span class="sxs-lookup"><span data-stu-id="e74a0-115">The **Page** pane</span></span>  
:::image-end:::  

<span data-ttu-id="e74a0-116">Organización del panel de **páginas** :</span><span class="sxs-lookup"><span data-stu-id="e74a0-116">How the **Page** pane is organized:</span></span>  
*   <span data-ttu-id="e74a0-117">El nivel superior, como `top` en la figura anterior, representa un [marco html][W3CHtml4Frames].</span><span class="sxs-lookup"><span data-stu-id="e74a0-117">The top-level, such as `top` in the previous figure, represents an [HTML frame][W3CHtml4Frames].</span></span>  <span data-ttu-id="e74a0-118">Buscar `top` en cada página que visite.</span><span class="sxs-lookup"><span data-stu-id="e74a0-118">Find `top` on every page that you visit.</span></span>  `top` <span data-ttu-id="e74a0-119">representa el marco del documento principal.</span><span class="sxs-lookup"><span data-stu-id="e74a0-119">represents the main document frame.</span></span>  
*   <span data-ttu-id="e74a0-120">El segundo nivel, como `docs.microsoft.com` en la figura anterior, representa un [origen][HtmlstandardOrigin].</span><span class="sxs-lookup"><span data-stu-id="e74a0-120">The second-level, such as `docs.microsoft.com` in the previous figure, represents an [origin][HtmlstandardOrigin].</span></span>  
*   <span data-ttu-id="e74a0-121">El tercer nivel, el cuarto nivel, etc., representan los directorios y recursos que se cargaron desde ese origen.</span><span class="sxs-lookup"><span data-stu-id="e74a0-121">The third-level, fourth-level, and so on, represent directories and resources that were loaded from that origin.</span></span>  <span data-ttu-id="e74a0-122">Por ejemplo, en la ilustración anterior, la ruta de acceso completa al recurso `devtools-guide-chromium` es</span><span class="sxs-lookup"><span data-stu-id="e74a0-122">For example, in the previous figure the full path to the resource `devtools-guide-chromium` is</span></span> `docs.microsoft.com/en-us/microsoft-edge/devtools-guide-chromium`  
    
<span data-ttu-id="e74a0-123">Elija un archivo en el panel de **páginas** para mostrar el contenido en el panel del **Editor** .</span><span class="sxs-lookup"><span data-stu-id="e74a0-123">Choose a file in the **Page** pane to display the contents in the **Editor** pane.</span></span>  <span data-ttu-id="e74a0-124">Puede mostrar cualquier tipo de archivo.</span><span class="sxs-lookup"><span data-stu-id="e74a0-124">You may display any type of file.</span></span>  <span data-ttu-id="e74a0-125">Para las imágenes, se muestra una vista previa de la imagen.</span><span class="sxs-lookup"><span data-stu-id="e74a0-125">For images, a preview of the image is displayed.</span></span>  

:::image type="complex" source="../media/sources-editor-pane.msft.png" alt-text="Mostrar el contenido de a4d10f71.index-docs.js en el panel Editor" lightbox="../media/sources-editor-pane.msft.png":::
   <span data-ttu-id="e74a0-127">Mostrar el contenido de `a4d10f71.index-docs.js` en el panel **Editor**</span><span class="sxs-lookup"><span data-stu-id="e74a0-127">Display the contents of `a4d10f71.index-docs.js` in the **Editor** pane</span></span>  
:::image-end:::  

## <span data-ttu-id="e74a0-128">Editar CSS y JavaScript</span><span class="sxs-lookup"><span data-stu-id="e74a0-128">Edit CSS and JavaScript</span></span>  

<span data-ttu-id="e74a0-129">Use el panel **Editor** para editar CSS y JavaScript.</span><span class="sxs-lookup"><span data-stu-id="e74a0-129">Use the **Editor** pane to edit CSS and JavaScript.</span></span>  <span data-ttu-id="e74a0-130">DevTools actualiza la página para ejecutar el nuevo código.</span><span class="sxs-lookup"><span data-stu-id="e74a0-130">DevTools updates the page to run your new code.</span></span>  <span data-ttu-id="e74a0-131">Por ejemplo, Si edita un archivo CSS agregando la regla de estilo a continuación:</span><span class="sxs-lookup"><span data-stu-id="e74a0-131">For example, if you edit a CSS file by adding the style rule below:</span></span>

```css
.metadata.page-metadata {
    color: red;
}
```

<span data-ttu-id="e74a0-132">Ese cambio debe surtir efecto inmediatamente.</span><span class="sxs-lookup"><span data-stu-id="e74a0-132">That change should take effect immediately.</span></span>

:::image type="complex" source="../media/edit-css.msft.png" alt-text="Editar CSS en el panel del editor para cambiar el color del texto del subtítulo a rojo" lightbox="../media/edit-css.msft.png":::
   <span data-ttu-id="e74a0-134">Editar CSS en el panel del **Editor** para cambiar el color del texto del subtítulo a rojo</span><span class="sxs-lookup"><span data-stu-id="e74a0-134">Edit CSS in the **Editor** pane to change the text color of the subtitle to red</span></span>  
:::image-end:::  

<span data-ttu-id="e74a0-135">Los cambios de CSS se aplican inmediatamente, no es necesario guardar.</span><span class="sxs-lookup"><span data-stu-id="e74a0-135">CSS changes take effect immediately, no save needed.</span></span>  <span data-ttu-id="e74a0-136">Para que los cambios de JavaScript surtan efecto, seleccione `Control` + `S` \ (Windows, Linux \) o `Command` + `S` \ (MacOS \).</span><span class="sxs-lookup"><span data-stu-id="e74a0-136">For JavaScript changes to take effect, select `Control`+`S` \(Windows, Linux\) or `Command`+`S` \(macOS\).</span></span>  <span data-ttu-id="e74a0-137">DevTools no vuelve a ejecutar un script, por lo que los únicos cambios de JavaScript que se aplican son los que realiza dentro de las funciones.</span><span class="sxs-lookup"><span data-stu-id="e74a0-137">DevTools does not re-run a script, so the only JavaScript changes that take effect are those that you make inside of functions.</span></span>  <span data-ttu-id="e74a0-138">Por ejemplo, en la siguiente ilustración, observe cómo `console.log('A')` no se ejecuta, pero `console.log('B')` sí.</span><span class="sxs-lookup"><span data-stu-id="e74a0-138">For example, in the following figure, notice how `console.log('A')` does not run, whereas `console.log('B')` does.</span></span>  <span data-ttu-id="e74a0-139">Si DevTools vuelve a ejecutar la secuencia de comandos completa después de realizar el cambio, el texto `A` se habría grabado en la **consola**.</span><span class="sxs-lookup"><span data-stu-id="e74a0-139">If DevTools re-runs the entire script after making the change, then the text `A` would have been logged to the **Console**.</span></span>  

:::image type="complex" source="../media/edit-js.msft.png" alt-text="Edición de JavaScript en el panel Editor" lightbox="../media/edit-js.msft.png":::
   <span data-ttu-id="e74a0-141">Edición de JavaScript en el panel **Editor**</span><span class="sxs-lookup"><span data-stu-id="e74a0-141">Editing JavaScript in the **Editor** pane</span></span>  
:::image-end:::  

<span data-ttu-id="e74a0-142">DevTools borra los cambios de CSS y JavaScript al volver a cargar la página.</span><span class="sxs-lookup"><span data-stu-id="e74a0-142">DevTools erases your CSS and JavaScript changes when you reload the page.</span></span>  <span data-ttu-id="e74a0-143">Vaya a [configurar un área de trabajo](#set-up-a-workspace) para obtener información sobre cómo guardar los cambios en el sistema de archivos.</span><span class="sxs-lookup"><span data-stu-id="e74a0-143">Navigate to [Set up a Workspace](#set-up-a-workspace) to learn how to save the changes to your file system.</span></span>  

## <span data-ttu-id="e74a0-144">Crear, guardar y ejecutar fragmentos de código</span><span class="sxs-lookup"><span data-stu-id="e74a0-144">Create, save, and run Snippets</span></span>  

<span data-ttu-id="e74a0-145">Los fragmentos de código son scripts que se pueden ejecutar en cualquier página.</span><span class="sxs-lookup"><span data-stu-id="e74a0-145">Snippets are scripts which you may run on any page.</span></span>  <span data-ttu-id="e74a0-146">Suponga que escribe repetidamente el siguiente código en la **consola**, para insertar la biblioteca de jQuery en una página, de modo que pueda ejecutar comandos de jQuery desde la **consola**.</span><span class="sxs-lookup"><span data-stu-id="e74a0-146">Imagine that you repeatedly type out the following code in the **Console**, in order to insert the jQuery library into a page, so that you may run jQuery commands from the **Console**.</span></span>  

```javascript
let script = document.createElement('script');
script.src = 'https://code.jquery.com/jquery-3.2.1.min.js';
script.crossOrigin = 'anonymous';
script.integrity = 'sha256-hwg4gsxgFZhOsEEamdOYGBf13FyQuiTwlAQgxVSNgt4=';
document.head.appendChild(script);
```  

<span data-ttu-id="e74a0-147">En su lugar, puede guardar este código en un **fragmento** de código y ejecutarlo con un par de clics de botón, cada vez que lo necesite.</span><span class="sxs-lookup"><span data-stu-id="e74a0-147">Instead, you may save this code in a **Snippet** and run it with a couple of button clicks, any time you need it.</span></span>  <span data-ttu-id="e74a0-148">DevTools guarda el **fragmento de código** en el sistema de archivos.</span><span class="sxs-lookup"><span data-stu-id="e74a0-148">DevTools saves the **Snippet** to your file system.</span></span>  

:::image type="complex" source="../media/snippet.msft.png" alt-text="Un fragmento de código que inserta la biblioteca jQuery en una página" lightbox="../media/snippet.msft.png":::
   <span data-ttu-id="e74a0-150">Un **fragmento de código** que inserta la biblioteca jQuery en una página</span><span class="sxs-lookup"><span data-stu-id="e74a0-150">A **Snippet** that inserts the jQuery library into a page</span></span>  
:::image-end:::  

<span data-ttu-id="e74a0-151">Para ejecutar un **fragmento de código**:</span><span class="sxs-lookup"><span data-stu-id="e74a0-151">To run a **Snippet**:</span></span>

*   <span data-ttu-id="e74a0-152">Abra el archivo con el panel **fragmentos de código** y elija **Ejecutar** \ ( ![ el botón ejecutar ][ImageRunIcon] \).</span><span class="sxs-lookup"><span data-stu-id="e74a0-152">Open the file using the **Snippets** pane, and choose **Run** \(![The Run button][ImageRunIcon]\).</span></span>  
*   <span data-ttu-id="e74a0-153">Abra el [menú de comandos][DevtoolsGuideChromiumCommandMenuIndex], elimine el `>` carácter, escriba `!` , escriba el nombre del **fragmento de código**y, a continuación, seleccione `Enter` .</span><span class="sxs-lookup"><span data-stu-id="e74a0-153">Open the [Command Menu][DevtoolsGuideChromiumCommandMenuIndex], delete the `>` character, type `!`, type the name of your **Snippet**, and then select `Enter`.</span></span>  
    
<span data-ttu-id="e74a0-154">Navegue para [Ejecutar fragmentos de código desde cualquier página][DevtoolsGuideChromiumJavascriptSnippets] para obtener más información.</span><span class="sxs-lookup"><span data-stu-id="e74a0-154">Navigate to [Run Snippets Of Code From Any Page][DevtoolsGuideChromiumJavascriptSnippets] to learn more.</span></span>

## <span data-ttu-id="e74a0-155">Depurar JavaScript</span><span class="sxs-lookup"><span data-stu-id="e74a0-155">Debug JavaScript</span></span>  

<span data-ttu-id="e74a0-156">En lugar de usar `console.log()` para inferir Dónde está el error de JavaScript, considere la posibilidad de usar las herramientas de depuración de Microsoft Edge DevTools en su lugar.</span><span class="sxs-lookup"><span data-stu-id="e74a0-156">Rather than using `console.log()` to infer where your JavaScript is going wrong, consider using the Microsoft Edge DevTools debugging tools, instead.</span></span>  <span data-ttu-id="e74a0-157">La idea general es establecer un punto de interrupción, que es un lugar de detención intencionado en el código, y, a continuación, pasar por el tiempo de ejecución del código, de línea en línea.</span><span class="sxs-lookup"><span data-stu-id="e74a0-157">The general idea is to set a breakpoint, which is an intentional stopping place in your code, and then step through the runtime of your code, one line at a time.</span></span>  <span data-ttu-id="e74a0-158">Mientras recorres el código, puedes mostrar y cambiar los valores de todas las propiedades y variables definidas actualmente, ejecutar JavaScript en la **consola**y mucho más.</span><span class="sxs-lookup"><span data-stu-id="e74a0-158">As you step through the code, you may display and change the values of all currently-defined properties and variables, run JavaScript in the **Console**, and more.</span></span>

<span data-ttu-id="e74a0-159">Vaya a introducción a la [depuración de JavaScript][DevtoolsGuideChromiumJavascriptIndex] para conocer los conceptos básicos de la depuración en DevTools.</span><span class="sxs-lookup"><span data-stu-id="e74a0-159">Navigate to [Get Started With Debugging JavaScript][DevtoolsGuideChromiumJavascriptIndex] to learn the basics of debugging in DevTools.</span></span>

:::image type="complex" source="../media/debugging.msft.png" alt-text="Depurar JavaScript" lightbox="../media/debugging.msft.png":::
   <span data-ttu-id="e74a0-161">Depurar JavaScript</span><span class="sxs-lookup"><span data-stu-id="e74a0-161">Debug JavaScript</span></span>  
:::image-end:::  

## <span data-ttu-id="e74a0-162">Configurar un área de trabajo</span><span class="sxs-lookup"><span data-stu-id="e74a0-162">Set up a Workspace</span></span>  

<span data-ttu-id="e74a0-163">De forma predeterminada, al editar un archivo en la herramienta **orígenes** , esos cambios se pierden al volver a cargar la página.</span><span class="sxs-lookup"><span data-stu-id="e74a0-163">By default, when you edit a file in the **Sources** tool, those changes are lost when you reload the page.</span></span>  <span data-ttu-id="e74a0-164">Las **áreas de trabajo** le permiten guardar los cambios que realice en DevTools en el sistema de archivos.</span><span class="sxs-lookup"><span data-stu-id="e74a0-164">**Workspaces** enable you to save the changes that you make in DevTools to your file system.</span></span>  <span data-ttu-id="e74a0-165">Esencialmente, DevTools puede usarse como editor de código.</span><span class="sxs-lookup"><span data-stu-id="e74a0-165">Essentially, DevTools is able to be used as your code editor.</span></span>

<span data-ttu-id="e74a0-166">Desplácese hasta [editar archivos con áreas de trabajo][DevtoolsGuideChromiumWorkspacesIndex] para comenzar.</span><span class="sxs-lookup"><span data-stu-id="e74a0-166">Navigate to [Edit Files With Workspaces][DevtoolsGuideChromiumWorkspacesIndex] to get started.</span></span>

## <span data-ttu-id="e74a0-167">Contactar al equipo de Microsoft Edge DevTools</span><span class="sxs-lookup"><span data-stu-id="e74a0-167">Getting in touch with the Microsoft Edge DevTools team</span></span>  

[!INCLUDE [contact DevTools team note](../includes/contact-devtools-team-note.md)]  

<!-- image links -->  

[ImageRunIcon]: ../media/run-snippet-icon.msft.png  

<!-- links -->  

[DevtoolsGuideChromiumCommandMenuIndex]: ../command-menu/index.md "Ejecutar comandos con el menú de comandos de Microsoft Edge DevTools | Microsoft docs"  
[DevtoolsGuideChromiumJavascriptIndex]: ../javascript/index.md "Introducción a la depuración de JavaScript en Microsoft Edge DevTools | Microsoft docs"  
[DevtoolsGuideChromiumJavascriptSnippets]: ../javascript/snippets.md "Ejecutar fragmentos de código de JavaScript en cualquier página con Microsoft Edge DevTools | Microsoft docs"  
[DevtoolsGuideChromiumWorkspacesIndex]: ../workspaces/index.md "Editar archivos con áreas de trabajo | Microsoft docs"  

[HtmlstandardOrigin]: https://html.spec.whatwg.org/multipage/origin.html#origin "Origen | Estándar HTML"  

[W3CHtml4Frames]: https://w3.org/TR/html401/present/frames.html "Marcos | RELATIVA"  

> [!NOTE]
> <span data-ttu-id="e74a0-174">Algunas partes de esta página son modificaciones basadas en el trabajo creado y [compartido por Google][GoogleSitePolicies] y se usan según los términos descritos en la [Licencia internacional de Creative Commons Attribution 4.0][CCA4IL].</span><span class="sxs-lookup"><span data-stu-id="e74a0-174">Portions of this page are modifications based on work created and [shared by Google][GoogleSitePolicies] and used according to terms described in the [Creative Commons Attribution 4.0 International License][CCA4IL].</span></span>  
> <span data-ttu-id="e74a0-175">La página original se encuentra [aquí](https://developers.google.com/web/tools/chrome-devtools/sources) y está modificada por [Kayce vascos][KayceBasques] \ (redactor técnico, Chrome DevTools \ & Lighthouse \).</span><span class="sxs-lookup"><span data-stu-id="e74a0-175">The original page is found [here](https://developers.google.com/web/tools/chrome-devtools/sources) and is authored by [Kayce Basques][KayceBasques] \(Technical Writer, Chrome DevTools \& Lighthouse\).</span></span>  

[![Licencia de Creative Commons][CCby4Image]][CCA4IL]  
<span data-ttu-id="e74a0-177">Este trabajo dispone de licencia conforme a [Licencia internacional de Creative Commons Attribution 4.0][CCA4IL].</span><span class="sxs-lookup"><span data-stu-id="e74a0-177">This work is licensed under a [Creative Commons Attribution 4.0 International License][CCA4IL].</span></span>  

[CCA4IL]: https://creativecommons.org/licenses/by/4.0  
[CCby4Image]: https://i.creativecommons.org/l/by/4.0/88x31.png  
[GoogleSitePolicies]: https://developers.google.com/terms/site-policies  
[KayceBasques]: https://developers.google.com/web/resources/contributors/kaycebasques  
