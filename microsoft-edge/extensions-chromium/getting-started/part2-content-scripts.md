---
description: Extensiones Introducción a la parte 1
title: Insertar dinámicamente la imagen de la NASA debajo de la etiqueta cuerpo de página con scripts de contenido
author: MSEdgeTeam
ms.author: msedgedevrel
ms.date: 05/08/2020
ms.topic: article
ms.prod: microsoft-edge-chromium
keywords: Edge-cromo, desarrollo web, HTML, CSS, JavaScript, desarrollador, extensiones
ms.openlocfilehash: b37184f0188b72ec868ab3de3f2341c0694ee42c
ms.sourcegitcommit: 0bc1312a1e6a0ac37cf385201db4361fc05184fc
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/28/2020
ms.locfileid: "10683647"
---
# <span data-ttu-id="c6d06-104">Insertar dinámicamente la imagen de la NASA debajo de la etiqueta cuerpo de página con scripts de contenido</span><span class="sxs-lookup"><span data-stu-id="c6d06-104">Dynamically Insert NASA Picture Below The Page Body Tag Using Content Scripts</span></span>  
  
[<span data-ttu-id="c6d06-105">Origen del paquete de extensión completado para este elemento</span><span class="sxs-lookup"><span data-stu-id="c6d06-105">Completed Extension Package Source for This Part</span></span>][ArchiveExtensionGettingStartedPart2]  

## <span data-ttu-id="c6d06-106">Introducción</span><span class="sxs-lookup"><span data-stu-id="c6d06-106">Overview</span></span>  

<span data-ttu-id="c6d06-107">En la parte 2, aprenderá a actualizar el menú emergente para no mostrar la imagen de los estrellas estáticos que tenía antes, pero para reemplazar la imagen con un título y un botón HTML estándar.</span><span class="sxs-lookup"><span data-stu-id="c6d06-107">In part 2, you learn to update your pop-up menu to not show the static stars image you had before, but to replace that image with a title and a standard HTML button.</span></span>  <span data-ttu-id="c6d06-108">Este botón, cuando está seleccionado, pasa a la página de contenido la imagen de las estrellas, que está insertada en la extensión.</span><span class="sxs-lookup"><span data-stu-id="c6d06-108">That button, when selected, passes that stars image, which is embedded in the Extension, to the content page.</span></span>  <span data-ttu-id="c6d06-109">Esta imagen se inserta en la ficha del explorador activo.</span><span class="sxs-lookup"><span data-stu-id="c6d06-109">That image, is inserted into the active browser tab.</span></span>  

*   <span data-ttu-id="c6d06-110">Tecnologías de extensión descritas en esta guía</span><span class="sxs-lookup"><span data-stu-id="c6d06-110">Extension technologies covered in this guide</span></span>  
    *   <span data-ttu-id="c6d06-111">Inyectar bibliotecas de JavaScript en la extensión</span><span class="sxs-lookup"><span data-stu-id="c6d06-111">Injecting JavaScript libraries into Extension</span></span>  
    *   <span data-ttu-id="c6d06-112">Exponer los recursos de extensión a las pestañas del explorador</span><span class="sxs-lookup"><span data-stu-id="c6d06-112">Exposing Extension assets to browser tabs</span></span>  
    *   <span data-ttu-id="c6d06-113">Incluir páginas de contenido en pestañas del explorador existentes</span><span class="sxs-lookup"><span data-stu-id="c6d06-113">Including content pages in existing browser tabs</span></span>  
    *   <span data-ttu-id="c6d06-114">Hacer que las páginas de contenido escuchen los mensajes de las ventanas emergentes y respondan</span><span class="sxs-lookup"><span data-stu-id="c6d06-114">Having content pages listen for messages from pop-ups and respond</span></span>  

## <span data-ttu-id="c6d06-115">Quitar la imagen de la ventana emergente y reemplazarla por un botón</span><span class="sxs-lookup"><span data-stu-id="c6d06-115">Remove the image from the pop-up and replace it with a button</span></span>  

<span data-ttu-id="c6d06-116">En primer lugar, actualice el `popup.html` archivo con una marca hacia adelante recta que muestre un título y un botón.</span><span class="sxs-lookup"><span data-stu-id="c6d06-116">First, update your `popup.html` file with some straight forward markup that displays a title and a button.</span></span>  <span data-ttu-id="c6d06-117">En breve puedes programar ese botón, pero por ahora solo tienes que incluir una referencia a un archivo de JavaScript vacío `popup.js` .</span><span class="sxs-lookup"><span data-stu-id="c6d06-117">You program that button shortly, but for now, just include a reference to an empty JavaScript file `popup.js`.</span></span>  <span data-ttu-id="c6d06-118">Aquí es Update HTML.</span><span class="sxs-lookup"><span data-stu-id="c6d06-118">Here is update HTML.</span></span>  

```html
<html>
    <head>
        <meta charset="utf-8" />
        <style>
            body {
                width: 500px;
            }
            button {
                background-color: #336dab;
                border: none;
                color: white;
                padding: 15px 32px;
                text-align: center;
                font-size: 16px;
            }
        </style>
    </head>
    <body>
        <h1>Show the NASA Picture of the Day</h1>
        <h2>(select the image to remove)</h2>
        <button id="sendmessageid">Display</button>
        <script src="popup.js"></script>
    </body>
</html>
```  

<span data-ttu-id="c6d06-119">Después de actualizar la extensión y seleccionar el icono de inicio de la extensión, el tiene la siguiente ventana emergente incluye un botón Mostrar.</span><span class="sxs-lookup"><span data-stu-id="c6d06-119">After updating your Extension and selecting the Extension launch icon, the have the following pop-up includes a display button.</span></span>  

:::image type="complex" source="./media/part2-popupdialog.png" alt-text="visualización de Popup. html después de presionar el icono de extensión":::
   <span data-ttu-id="c6d06-121">visualización de Popup. html después de presionar el icono de extensión</span><span class="sxs-lookup"><span data-stu-id="c6d06-121">popup.html display after pressing the Extension icon</span></span>
:::image-end:::

<!--![popup.html display after pressing the Extension icon][ImagePart2Popupdialog]  -->  

## <span data-ttu-id="c6d06-122">Estrategia actualizada para mostrar la imagen en la parte superior de la pestaña del explorador</span><span class="sxs-lookup"><span data-stu-id="c6d06-122">Updated strategy to display image at the top of the browser tab</span></span>  

<span data-ttu-id="c6d06-123">Después de agregar el botón, la siguiente tarea es hacer que muestre el `images/stars.jpeg` archivo de imagen en la parte superior de la página de la pestaña activa.</span><span class="sxs-lookup"><span data-stu-id="c6d06-123">After adding the button, the next task is to make it bring up the `images/stars.jpeg` image file at the top of the active tab page.</span></span>  

<span data-ttu-id="c6d06-124">Recuerde que cada página de pestaña tiene un subproceso único y la extensión tiene un subproceso independiente.</span><span class="sxs-lookup"><span data-stu-id="c6d06-124">Remember, each tab page has a unique own thread and the Extension has a separate thread.</span></span>  <span data-ttu-id="c6d06-125">Por lo tanto, primero debe crear un script de contenido y inyectar ese script de contenido en la página de pestañas.</span><span class="sxs-lookup"><span data-stu-id="c6d06-125">So, you must first create a content script and inject that content script into the tab page.</span></span>  <span data-ttu-id="c6d06-126">Una vez que lo haya hecho, debe enviar un mensaje desde el elemento emergente a la secuencia de comandos de contenido que se ejecuta en la página de la ficha que indica el contenido, la imagen que se muestra y cómo mostrarlo.</span><span class="sxs-lookup"><span data-stu-id="c6d06-126">Once you do that, you must send a message from your pop-up to that content script running on the tab page telling that content script what image to show, and how to show it.</span></span>  

## <span data-ttu-id="c6d06-127">Crear el JavaScript emergente para enviar un mensaje</span><span class="sxs-lookup"><span data-stu-id="c6d06-127">Creating the pop-up JavaScript to send a message</span></span>  

<span data-ttu-id="c6d06-128">En primer lugar, cree `popup/popup.js` y agregue código para enviar un mensaje a su script de contenido que no haya creado, que debe crear momentáneamente e inyectar en la pestaña del explorador.  Para ello, el siguiente código agrega un `onclick` evento al botón Mostrar emergente.</span><span class="sxs-lookup"><span data-stu-id="c6d06-128">First, create `popup/popup.js` and add code to send a message to your not-yet-created content script that you must momentarily create and inject into your browser tab.  To do that, the following code adds an `onclick` event to your pop-up display button.</span></span>  

```javascript
const sendMessageId = document.getElementById("sendmessageid");
if (sendMessageId) {
  sendMessageId.onclick = function() {
    // do something
  };
}
```  

<span data-ttu-id="c6d06-129">En el `onclick` evento, lo que debe hacer es encontrar la pestaña del explorador actual \ (si solo hay una abierta, se trata de un \).</span><span class="sxs-lookup"><span data-stu-id="c6d06-129">In the `onclick` event, what you must do is find the current browser tab \(if there is only one open it is that one\).</span></span>  <span data-ttu-id="c6d06-130">Después, una vez que encuentre esa pestaña, use la `chrome.tabs.sendmessage` API de extensión para enviar un mensaje a esa pestaña.</span><span class="sxs-lookup"><span data-stu-id="c6d06-130">Then, once you find that tab, use the `chrome.tabs.sendmessage` Extension API to send a message to that tab.</span></span>  

<span data-ttu-id="c6d06-131">En ese mensaje, debe incluir la dirección URL de la imagen que desea mostrar y desea enviar un identificador único que se debe asignar a la imagen insertada.</span><span class="sxs-lookup"><span data-stu-id="c6d06-131">In that message you must include the URL to the image you want to display, and you want to send a unique ID that should be assigned to that inserted image.</span></span>  <span data-ttu-id="c6d06-132">Puede optar por permitir que el JavaScript de inserción de contenido genere eso, pero por razones que se hacen evidentes más adelante, genera ese identificador único aquí `popup.js` y lo pasa al script de contenido que aún no se ha creado.</span><span class="sxs-lookup"><span data-stu-id="c6d06-132">You may choose to let the content insertion JavaScript generate that, but for reasons that become apparent later, generate that unique ID here in `popup.js` and pass it to the not-yet-created content script.</span></span>  

<span data-ttu-id="c6d06-133">Este es tu `popup/popup.js` archivo actualizado.</span><span class="sxs-lookup"><span data-stu-id="c6d06-133">Here is your updated `popup/popup.js` file.</span></span>  <span data-ttu-id="c6d06-134">Además, pase el identificador de pestaña actual que necesita en una sección posterior, pero por ahora, no se usa.</span><span class="sxs-lookup"><span data-stu-id="c6d06-134">Also, pass in the current tab ID which you should need in a later section but for now, is not be used.</span></span>  

```javascript
const sendMessageId = document.getElementById("sendmessageid");
if (sendMessageId) {
    sendMessageId.onclick = function() {
        chrome.tabs.query({ active: true, currentWindow: true }, function(tabs) {
            chrome.tabs.sendMessage(
                tabs[0].id,
                {
                    url: chrome.extension.getURL("images/stars.jpeg"),
                    imageDivId: `${guidGenerator()}`,
                    tabId: tabs[0].id
                },
                function(response) {
                    window.close();
                }
            );
            function guidGenerator() {
                const S4 = function () {
                    return (((1 + Math.random()) * 0x10000) | 0).toString(16).substring(1);
                };
                return (S4() + S4() + "-" + S4() + "-" + S4() + "-" + S4() + "-" + S4() + S4() + S4());
            }
        });
    };
}
```  

## <span data-ttu-id="c6d06-135">Cómo conseguir que las cintas. JPEG estén disponibles desde cualquier pestaña del explorador</span><span class="sxs-lookup"><span data-stu-id="c6d06-135">Making your stars.jpeg available from any browser tab</span></span>  

<span data-ttu-id="c6d06-136">Probablemente se pregunte por qué, cuando pase el, `images/stars.jpeg` debe usar la `chrome.extension.getURL` API de extensión Chrome en lugar de simplemente pasar la dirección URL relativa sin el prefijo adicional como en la sección anterior.</span><span class="sxs-lookup"><span data-stu-id="c6d06-136">You are probably wondering why, when you pass the `images/stars.jpeg` must you use the `chrome.extension.getURL` chrome Extension API instead of just passing in the relative URL without the extra prefix like in the previous section.</span></span>  <span data-ttu-id="c6d06-137">Por cierto, ese prefijo adicional, devuelto por `getUrl` la imagen adjunta, tiene un aspecto similar al siguiente.</span><span class="sxs-lookup"><span data-stu-id="c6d06-137">By the way, that extra prefix, returned by `getUrl` with the image attached looks something like the following.</span></span>  

```http
extension://inigobacliaghocjiapeaaoemkjifjhp/images/stars.jpeg
```  

<span data-ttu-id="c6d06-138">El motivo es que se inserta la imagen con el `src` atributo del `img` elemento en la página de contenido.</span><span class="sxs-lookup"><span data-stu-id="c6d06-138">The reason is that you are injecting the image using the `src` attribute of the `img` element into the content page.</span></span>  <span data-ttu-id="c6d06-139">La página de contenido se está ejecutando en un subproceso único que no es el mismo que el subproceso que ejecuta la extensión.</span><span class="sxs-lookup"><span data-stu-id="c6d06-139">The content page is running on a unique thread that is not the same as the thread running the Extension.</span></span>  <span data-ttu-id="c6d06-140">Debe exponer el archivo de imagen estática como un recurso Web para que funcione correctamente.</span><span class="sxs-lookup"><span data-stu-id="c6d06-140">You must expose the static image file as a web asset for it to work correctly.</span></span>  

<span data-ttu-id="c6d06-141">Para ello, debe agregar otra entrada en el `manifest.json` archivo.</span><span class="sxs-lookup"><span data-stu-id="c6d06-141">To do that, you must add another entry in the `manifest.json` file.</span></span>  <span data-ttu-id="c6d06-142">Debe declarar la imagen para que sea accesible desde cualquier pestaña del explorador.  Esa entrada es la siguiente \ (debería verla en el `manifest.json` archivo completo a continuación al agregar la declaración de script de contenido).</span><span class="sxs-lookup"><span data-stu-id="c6d06-142">You must declare the image to be accessible from any browser tab.  That entry is as follows \(you should see it in the full `manifest.json` file below when you add the content script declaration coming up\).</span></span>  

```json
"web_accessible_resources": [
    "images/*.jpeg"
]
```  

<span data-ttu-id="c6d06-143">Ya ha escrito el código en el `popup.js` archivo para enviar un mensaje a la página de contenido que está insertada en la página de la pestaña activa actual, pero no ha creado e insertado esa página de contenido.</span><span class="sxs-lookup"><span data-stu-id="c6d06-143">You have now written the code in your `popup.js` file to send a message to the content page that is embedded on the current active tab page, but you have not created and injected that content page.</span></span>  <span data-ttu-id="c6d06-144">Hágalo ahora.</span><span class="sxs-lookup"><span data-stu-id="c6d06-144">Do that now.</span></span>  

## <span data-ttu-id="c6d06-145">Actualización del manifiesto. JSON para contenido y acceso web</span><span class="sxs-lookup"><span data-stu-id="c6d06-145">Updating your manifest.json for content and web access</span></span>  

<span data-ttu-id="c6d06-146">La actualización `manifest.json` que incluye el `content-scripts` y `web_accessible_resources` es la siguiente.</span><span class="sxs-lookup"><span data-stu-id="c6d06-146">The updated `manifest.json` that includes the `content-scripts` and `web_accessible_resources` is as follows.</span></span>  

```json
{
    "name": "NASA Picture of the day viewer",
    "version": "0.0.0.1",
    "manifest_version": 2,
    "description": "A Chromium Extension to show the NASA Picture of the Day.",
    "icons": {
        "16": "icons/nasapod16x16.png",
        "32": "icons/nasapod32x32.png",
        "48": "icons/nasapod48x48.png",
        "128": "icons/nasapod128x128.png"
    },
    "browser_action": {
        "default_popup": "popup/popup.html"
    },
    "content_scripts": [
        {
            "matches": [
              "<all_urls>"
            ],
            "js": ["lib/jquery.min.js","content-scripts/content.js"]
        }
    ],
    "web_accessible_resources": [
        "images/*.jpeg"
    ]
}
```  

<span data-ttu-id="c6d06-147">La sección que has agregado es `content_scripts` .</span><span class="sxs-lookup"><span data-stu-id="c6d06-147">The section you added is `content_scripts`.</span></span>  <span data-ttu-id="c6d06-148">El atributo `matches` establecido `<all_urls>` significa que todos los archivos que se mencionan en la sección **content_scripts** se insertan en todas las páginas de la pestaña del explorador cuando se cargan.</span><span class="sxs-lookup"><span data-stu-id="c6d06-148">The attribute `matches` set to `<all_urls>` means that all the files mention in the **content_scripts** section is injected into all browser tab pages when each are loaded.</span></span>  <span data-ttu-id="c6d06-149">Los tipos permitidos de archivos que se pueden insertar aquí son JavaScript y CSS.</span><span class="sxs-lookup"><span data-stu-id="c6d06-149">The allowable types of files that are able to be injected here are javascript and css.</span></span>  <span data-ttu-id="c6d06-150">También has añadido `libjquery.min.js` .</span><span class="sxs-lookup"><span data-stu-id="c6d06-150">You also added `libjquery.min.js`.</span></span>  <span data-ttu-id="c6d06-151">Podrás incluirlo en la descarga mencionada en la parte superior de la sección.</span><span class="sxs-lookup"><span data-stu-id="c6d06-151">You are able to include that from the download mentioned at the top of the section.</span></span>  

## <span data-ttu-id="c6d06-152">Agregar jQuery y comprender el subproceso asociado</span><span class="sxs-lookup"><span data-stu-id="c6d06-152">Adding jQuery and understanding the associated thread</span></span>  

<span data-ttu-id="c6d06-153">En los scripts de contenido que está inyectando, planee el uso de jQuery \ ( `$` \).</span><span class="sxs-lookup"><span data-stu-id="c6d06-153">In the content scripts you are injecting, plan on using jQuery \(`$`\).</span></span>  <span data-ttu-id="c6d06-154">Agregó una versión de minified de jQuery y la puso en el paquete de extensión como `lib\jquery.min.js` .</span><span class="sxs-lookup"><span data-stu-id="c6d06-154">You added a minified version of jQuery and put it in your Extension package as `lib\jquery.min.js`.</span></span>  <span data-ttu-id="c6d06-155">Estos scripts de contenido se ejecutan en un espacio aislado individual de ordenaciones, lo que significa que jQuery inyectado en la `popup.js` Página no se comparte con el contenido.</span><span class="sxs-lookup"><span data-stu-id="c6d06-155">These content scripts run in an individual sandbox of sorts, which means that the jQuery injected into the `popup.js` page does not share with the content.</span></span>  

<span data-ttu-id="c6d06-156">Tenga en cuenta que incluso si la pestaña del explorador tiene JavaScript ejecutándose en la página web cargada, el contenido insertado no tendrá acceso a él.</span><span class="sxs-lookup"><span data-stu-id="c6d06-156">Keep in mind that even if the browser tab has JavaScript running on it on the loaded web page, any content injected does not have access to that.</span></span>  <span data-ttu-id="c6d06-157">Los JavaScript insertados solo tienen acceso al DOM real cargado en la pestaña del explorador.</span><span class="sxs-lookup"><span data-stu-id="c6d06-157">That injected JavaScript just has access to the actual DOM loaded in that browser tab.</span></span>  

## <span data-ttu-id="c6d06-158">Agregar el agente de escucha de mensajes de script de contenido</span><span class="sxs-lookup"><span data-stu-id="c6d06-158">Adding the content script message listener</span></span>  

<span data-ttu-id="c6d06-159">Este es `content-scripts\content.js` el archivo que se inyecta en todas las páginas de la pestaña del explorador en función de la `manifest.json` `content-scripts` sección.</span><span class="sxs-lookup"><span data-stu-id="c6d06-159">Here is that `content-scripts\content.js` file that gets injected into every browser tab page based on your `manifest.json` `content-scripts` section.</span></span>  

```javascript
chrome.runtime.onMessage.addListener(function(request, sender, sendResponse) {
    $("body").prepend(
        `<img  src="${request.url}" id="${request.imageDivId}"
               class="slide-image" /> `
    );
    $("head").prepend(
        `<style>
          .slide-image {
              height: auto;
              width: 100vw;
          }
        </style>`
    );
    $(`#${request.imageDivId}`).click(function() {
        $(`#${request.imageDivId}`).remove(`#${request.imageDivId}`);
    });
    sendResponse({ fromcontent: "This message is from content.js" });
});
```  

<span data-ttu-id="c6d06-160">Ten en cuenta que todo lo mencionado anteriormente es registrar un `listener` con el `chrome.runtime.onMessage.addListener` método API de extensión.</span><span class="sxs-lookup"><span data-stu-id="c6d06-160">Notice that all the above JavaScript does is to register a `listener` using the `chrome.runtime.onMessage.addListener` Extension API method.</span></span>  <span data-ttu-id="c6d06-161">Este agente de escucha espera mensajes como el que envió desde la `popup.js` Descripción anterior con el `chrome.tabs.sendMessage` método API de extensión.</span><span class="sxs-lookup"><span data-stu-id="c6d06-161">This listener waits for messages like the one you sent from the `popup.js` described earlier with the `chrome.tabs.sendMessage` Extension API method.</span></span>  

<span data-ttu-id="c6d06-162">El primer parámetro del `addListener` método es una función cuyo primer parámetro, Request, son los detalles del mensaje que se pasa.</span><span class="sxs-lookup"><span data-stu-id="c6d06-162">The first parameter of the `addListener` method is a function whose first parameter, request, is the details of the message being passed in.</span></span>  <span data-ttu-id="c6d06-163">Recuerde, de `popup.js` , cuando usó el `sendMessage` método, los atributos del primer parámetro son `url` y `imageDivId` .</span><span class="sxs-lookup"><span data-stu-id="c6d06-163">Remember, from `popup.js`, when you used the `sendMessage` method, those attributes of the first parameter are `url` and `imageDivId`.</span></span>  

<span data-ttu-id="c6d06-164">Cuando el agente de escucha procesa un evento, se ejecuta la función que es el primer parámetro.</span><span class="sxs-lookup"><span data-stu-id="c6d06-164">When an event is processed by the listener, the function that is the first parameter is run.</span></span>  <span data-ttu-id="c6d06-165">El primer parámetro de esa función es un objeto que tiene atributos asignados por `sendMessage` .</span><span class="sxs-lookup"><span data-stu-id="c6d06-165">The first parameter of that function is an object that has attributes as assigned by `sendMessage`.</span></span>  <span data-ttu-id="c6d06-166">Esa función simplemente procesa las tres líneas de script jQuery.</span><span class="sxs-lookup"><span data-stu-id="c6d06-166">That function simply processes the three jQuery script lines.</span></span>  

*   <span data-ttu-id="c6d06-167">El primero inserta dinámicamente en el encabezado DOM una **\<style\>** sección que debes asignar como una `slide-image` clase al `img` elemento.</span><span class="sxs-lookup"><span data-stu-id="c6d06-167">The first dynamically inserts into the DOM header a **\<style\>** section that you must assign as a `slide-image` class to your `img` element.</span></span>  
*   <span data-ttu-id="c6d06-168">La segunda anexa un `img` elemento a la parte inferior `body` de la pestaña del explorador que tiene la `slide-image` clase asignada, así como el `imageDivId` identificador del elemento de imagen.</span><span class="sxs-lookup"><span data-stu-id="c6d06-168">The second, appends an `img` element right below the `body` of your browser tab that has the `slide-image` class assigned as well as the `imageDivId` as the ID of that image element.</span></span>  
*   <span data-ttu-id="c6d06-169">El tercero agrega un `click` evento que cubre toda la imagen, lo que permite al usuario seleccionar cualquier lugar de la imagen y esa imagen se elimina de la página \ (junto con la escucha de eventos \).</span><span class="sxs-lookup"><span data-stu-id="c6d06-169">The third adds a `click` event that covers the entire image allowing the user to select any place on the image and that image is be removed from the page \(along with it is event listener\).</span></span>  

## <span data-ttu-id="c6d06-170">Agregar funcionalidad para quitar la imagen mostrada al seleccionarla</span><span class="sxs-lookup"><span data-stu-id="c6d06-170">Adding functionality to remove the displayed image when selected</span></span>  

<span data-ttu-id="c6d06-171">Ahora, cuando vaya a cualquier página y seleccione el icono de **extensión** , el menú emergente aparecerá de la siguiente manera.</span><span class="sxs-lookup"><span data-stu-id="c6d06-171">Now, when you browse to any page and select your **Extension** icon, the pop-up menu is displayed as follows.</span></span>  

:::image type="complex" source="./media/part2-popupdialog.png" alt-text="visualización de Popup. html después de presionar el icono de extensión":::
   <span data-ttu-id="c6d06-173">visualización de Popup. html después de presionar el icono de extensión</span><span class="sxs-lookup"><span data-stu-id="c6d06-173">popup.html display after pressing the Extension icon</span></span>
:::image-end:::

<!--![popup.html display after pressing the Extension icon][ImagePart2Popupdialog]  -->  

<span data-ttu-id="c6d06-174">Al seleccionar el `Display` botón, obtienes lo que aparece a continuación.</span><span class="sxs-lookup"><span data-stu-id="c6d06-174">When you select the `Display` button, you get what is below.</span></span>  <span data-ttu-id="c6d06-175">Si selecciona cualquier lugar de la `stars.jpeg` imagen, este elemento de imagen se quita y las páginas de pestañas se vuelven a las que se mostraban originalmente.</span><span class="sxs-lookup"><span data-stu-id="c6d06-175">If you select anywhere on the `stars.jpeg` image, that image element is removed and tab pages collapses back to what was originally displayed.</span></span>  

:::image type="complex" source="./media/part2-showingimage.png" alt-text="Imagen que se muestra en el explorador":::
   <span data-ttu-id="c6d06-177">Imagen que se muestra en el explorador</span><span class="sxs-lookup"><span data-stu-id="c6d06-177">The image showing in browser</span></span>
:::image-end:::

<!--![The image showing in browser][ImagePart2Showingimage]  -->  

<span data-ttu-id="c6d06-178">Ya ha creado una extensión que ha enviado correctamente un mensaje desde el icono emergente de extensión, al contenido de JavaScript que se ha insertado dinámicamente en la pestaña del explorador.  Ese contenido insertado estableció el elemento de imagen para mostrar tus estrellas estáticas JPEG.</span><span class="sxs-lookup"><span data-stu-id="c6d06-178">You have now created an Extension that successfully sends a message from the Extension icon pop-up, to the dynamically inserted JavaScript running as content on the browser tab.  That injected content set the image element to display your static stars jpeg.</span></span>  

<!-- image links -->  

<!--[ImagePart2Popupdialog]: ./media/part2-popupdialog.png "popup.html display after pressing the Extension icon"  -->  
<!--[ImagePart2Showingimage]: ./media/part2-showingimage.png "The image showing in browser"  -->

<!-- links -->  

[ArchiveExtensionGettingStartedPart2]: ./extension-source/extension-getting-started-part2.zip "Origen del paquete de extensión completado para esta parte | Microsoft docs"  