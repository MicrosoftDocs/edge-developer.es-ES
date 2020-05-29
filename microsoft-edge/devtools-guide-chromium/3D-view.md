---
description: Todo sobre la vista 3D y cómo usarla.
title: Vista 3D
author: erdraud
ms.author: erdraud
ms.date: 11/27/2019
ms.topic: article
ms.prod: microsoft-edge
keywords: Microsoft Edge, desarrollo web, herramientas F12, DevTools
ms.openlocfilehash: f2ae80426da71797d4bee4060d33965f04047e19
ms.sourcegitcommit: 6860234c25a8be863b7f29a54838e78e120dbb62
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/09/2020
ms.locfileid: "10573275"
---
# <span data-ttu-id="0bfa4-104">Vista 3D</span><span class="sxs-lookup"><span data-stu-id="0bfa4-104">3D View</span></span>

<span data-ttu-id="0bfa4-105">Use la **vista 3D** para depurar la aplicación web desplazándose por el [modelo de objetos de documento](https://developer.mozilla.org/en-US/docs/Web/API/Document_Object_Model) (dom) o el contexto de apilamiento [de índice z](https://developer.mozilla.org/en-US/docs/Web/CSS/z-index) .</span><span class="sxs-lookup"><span data-stu-id="0bfa4-105">Use the **3D View** to debug your web application by navigating through the [Document Object Model](https://developer.mozilla.org/en-US/docs/Web/API/Document_Object_Model) (DOM) or the [z-index](https://developer.mozilla.org/en-US/docs/Web/CSS/z-index) stacking context.</span></span> <span data-ttu-id="0bfa4-106">Con ella, puedes hacer lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="0bfa4-106">With it you can:</span></span> 

- [<span data-ttu-id="0bfa4-107">Explorar la Página Web traducida a un 3D perspevtive</span><span class="sxs-lookup"><span data-stu-id="0bfa4-107">Explore the web page translated into a 3D perspevtive</span></span>](#3d-dom)
- [<span data-ttu-id="0bfa4-108">Depuración basada en el contexto de apilamiento de índice z</span><span class="sxs-lookup"><span data-stu-id="0bfa4-108">Debug based on z-index stacking context</span></span>](#z-index)
- <span data-ttu-id="0bfa4-109">[Borrar parte del desorden en el panel Dom o en](#changing-your-view) el [Panel de índice z](#change-the-scope-of-your-exploration)</span><span class="sxs-lookup"><span data-stu-id="0bfa4-109">[Clear some of the clutter in the DOM pane](#changing-your-view) or the [z-index pane](#change-the-scope-of-your-exploration)</span></span>
- <span data-ttu-id="0bfa4-110">[Elegir la combinación de colores para la mejor depuración de problemas de Dom](#dom-color-type) o [de índice z](#z-index-color-type)</span><span class="sxs-lookup"><span data-stu-id="0bfa4-110">[Pick the color scheme to best debug your DOM problems](#dom-color-type) or [z-index problems](#z-index-color-type)</span></span>

<span data-ttu-id="0bfa4-111">Hay dos paneles que puede usar para su experiencia de depuración.</span><span class="sxs-lookup"><span data-stu-id="0bfa4-111">There are two panes that you can use for your debugging experience.</span></span>

1. <span data-ttu-id="0bfa4-112">**Índice Z** Desplácese por los distintos elementos de la aplicación web con el contexto de índice z en mente.</span><span class="sxs-lookup"><span data-stu-id="0bfa4-112">**Z-index** Navigate through the different elements in the web application with the z-index context in mind.</span></span> <span data-ttu-id="0bfa4-113">Este es el panel predeterminado.</span><span class="sxs-lookup"><span data-stu-id="0bfa4-113">This is the default pane.</span></span>
2. <span data-ttu-id="0bfa4-114">**Dom 3D** Explore el DOM como un todo con todos los elementos a su alcance.</span><span class="sxs-lookup"><span data-stu-id="0bfa4-114">**3D DOM** Explore the DOM as a whole with all the elements at your fingertips.</span></span> <span data-ttu-id="0bfa4-115">Para obtener acceso a este panel, haga clic en el panel "DOM" junto al panel "índice Z".</span><span class="sxs-lookup"><span data-stu-id="0bfa4-115">To access this pane, click on the "DOM" pane next to the "Z-index" pane.</span></span>

![lienzo de vista 3D](./media/canvas.png)

## <span data-ttu-id="0bfa4-117">Navegar por el lienzo</span><span class="sxs-lookup"><span data-stu-id="0bfa4-117">Navigating the canvas</span></span>

### <span data-ttu-id="0bfa4-118">Métodos abreviados de teclado</span><span class="sxs-lookup"><span data-stu-id="0bfa4-118">Keyboard shortcuts</span></span>
- <span data-ttu-id="0bfa4-119">Girar el DOM: Use las teclas de flecha izquierda y derecha para girar horizontalmente y use las teclas de flecha arriba y abajo para girar verticalmente.</span><span class="sxs-lookup"><span data-stu-id="0bfa4-119">Rotate the DOM: use the left and right arrow keys to rotate horizontally and use the up and down arrow keys to rotate vertically.</span></span>
- <span data-ttu-id="0bfa4-120">Navegar por el DOM: si se selecciona un elemento, puede usar las teclas de flecha arriba y abajo para desplazarse por los elementos adyacentes</span><span class="sxs-lookup"><span data-stu-id="0bfa4-120">Navigate the DOM: if an element is selected, you can use the up and down arrow keys to move through the elements adjacent</span></span>

### <span data-ttu-id="0bfa4-121">Controles del ratón</span><span class="sxs-lookup"><span data-stu-id="0bfa4-121">Mouse controls</span></span>
- <span data-ttu-id="0bfa4-122">Girar el DOM: haga clic con el botón izquierdo y arrastre alrededor del espacio del lienzo.</span><span class="sxs-lookup"><span data-stu-id="0bfa4-122">Rotate the DOM: left click and drag around the canvas space.</span></span>
- <span data-ttu-id="0bfa4-123">Desplácese por el DOM: haga clic con el botón secundario y arrastre en la dirección en la que desea mover el DOM.</span><span class="sxs-lookup"><span data-stu-id="0bfa4-123">Pan around the DOM: right click and drag in the direction you want the DOM to move.</span></span>
- <span data-ttu-id="0bfa4-124">Zoom: arrastre dos dedos por el panel táctil o use la rueda de desplazamiento del mouse.</span><span class="sxs-lookup"><span data-stu-id="0bfa4-124">Zoom: drag two fingers across the touchpad or use the scroll wheel on your mouse.</span></span>

![controles en pantalla](./media/controls-small.png)
### <span data-ttu-id="0bfa4-126">Controles en pantalla</span><span class="sxs-lookup"><span data-stu-id="0bfa4-126">On-screen controls</span></span>
- <span data-ttu-id="0bfa4-127">Restablezca la vista de lienzo a la vista original: haga clic en el botón con la etiqueta "restablecer cámara" o haga clic en el icono que se parezca a un botón de actualización de un lado y tendrá "restablecer elementos en la vista y volver a centrar la cámara".</span><span class="sxs-lookup"><span data-stu-id="0bfa4-127">Reset the canvas view to the original view: click the button labeled "Reset camera," or click on the icon that looks like a sideways refresh button and has "Reset elements in view and re-center camera"</span></span>
- <span data-ttu-id="0bfa4-128">Actualice el lienzo (por ejemplo, si el explorador cambió o ha cambiado a la vista emulador de dispositivos): haga clic en el botón que dice "volver a tomar instantánea" o haga clic en el botón que tiene el aspecto de un icono de actualización y tiene "tomar instantánea nueva" como el texto activable.</span><span class="sxs-lookup"><span data-stu-id="0bfa4-128">Refresh the canvas (e.g. if the browser changed or you switched to a device emulator view): click on the button that says "Retake snapshot," or click on the button that looks like a refresh icon and has "Take new snapshot" as the hover text.</span></span>

![Vista de índice Z](./media/z-index-view-box.png)

## <span data-ttu-id="0bfa4-130">Índice Z</span><span class="sxs-lookup"><span data-stu-id="0bfa4-130">Z-index</span></span>

<span data-ttu-id="0bfa4-131">Aunque el panel Índice Z tiene características compartidas con el panel DOM, aún tienen elementos que son únicos para el panel.</span><span class="sxs-lookup"><span data-stu-id="0bfa4-131">While the Z-index pane has shared features with the DOM pane, they still have elements that are unique to the pane.</span></span>

### <span data-ttu-id="0bfa4-132">Resaltar elementos con contexto de apilamiento</span><span class="sxs-lookup"><span data-stu-id="0bfa4-132">Highlight elements with stacking context</span></span>

<span data-ttu-id="0bfa4-133">Esta configuración le permite activar y desactivar las etiquetas de índice z de los elementos del lienzo.</span><span class="sxs-lookup"><span data-stu-id="0bfa4-133">This setting allows you to toggle the z-index tags on and off for the elements in the canvas.</span></span> <span data-ttu-id="0bfa4-134">La casilla de verificación estará seleccionada de forma predeterminada.</span><span class="sxs-lookup"><span data-stu-id="0bfa4-134">The checkbox will be selected by default.</span></span>

### <span data-ttu-id="0bfa4-135">Cambiar el ámbito de exploración</span><span class="sxs-lookup"><span data-stu-id="0bfa4-135">Change the scope of your exploration</span></span>

<span data-ttu-id="0bfa4-136">El botón **Mostrar todos los elementos** es la manera más rápida de Mostrar todos los elementos del DOM después de cambiar la configuración a continuación.</span><span class="sxs-lookup"><span data-stu-id="0bfa4-136">The **Show all elements** button is the quickest way to display all the DOM's elements after changing the settings below.</span></span>

<span data-ttu-id="0bfa4-137">**Mostrar solo los elementos con el contexto de apilamiento** quita los elementos sin contexto de apilamiento y alisa el Dom para facilitar la navegación.</span><span class="sxs-lookup"><span data-stu-id="0bfa4-137">**Show only elements with stacking context** removes elements without stacking context and flattens the DOM for easier navigation.</span></span>

<span data-ttu-id="0bfa4-138">El filtro de **elemento seleccionado aislar** es esencialmente tres botones en uno.</span><span class="sxs-lookup"><span data-stu-id="0bfa4-138">The **Isolate selected element** filter is essentially three buttons in one.</span></span> <span data-ttu-id="0bfa4-139">Hay dos casillas debajo de este botón: una es "Mostrar todos los padres" y "mantener solo los padres con el nuevo contexto de apilamiento".</span><span class="sxs-lookup"><span data-stu-id="0bfa4-139">There are two checkboxes below this button: one is "Show all parents" and "Keep only parents with new stacking context."</span></span> 

<span data-ttu-id="0bfa4-140">La casilla "Mostrar todos los padres" se activará de forma predeterminada.</span><span class="sxs-lookup"><span data-stu-id="0bfa4-140">The "Show all parents" checkbox will be checked by default.</span></span> <span data-ttu-id="0bfa4-141">Si selecciona un elemento en el panel de lienzo y hace clic en **aislar elemento seleccionado**, el lienzo solo mostrará el elemento y sus elementos primarios.</span><span class="sxs-lookup"><span data-stu-id="0bfa4-141">If you select an element in the canvas pane and click on **Isolate selected element**, the canvas will only display the element and its parents.</span></span>

<span data-ttu-id="0bfa4-142">Si selecciona la "conservar solo los padres con el nuevo contexto de apilamiento" y hace clic en **aislar elemento seleccionado**, el lienzo solo mostrará el elemento y los elementos primarios que tienen un nuevo contexto de apilamiento.</span><span class="sxs-lookup"><span data-stu-id="0bfa4-142">If you select the "Keep only parents with new stacking context," and click on **Isolate selected element**, the canvas will only display the element and the parents that have a new stacking context.</span></span>

<span data-ttu-id="0bfa4-143">Si anula la selección de las casillas de verificación y hace clic en **aislar elemento seleccionado**, el lienzo solo mostrará el elemento que haya elegido en primer lugar.</span><span class="sxs-lookup"><span data-stu-id="0bfa4-143">If you deselect both of the checkboxes and click on **Isolate selected element**, the canvas will only display the element you chose in the first place.</span></span>

<span data-ttu-id="0bfa4-144">En la parte inferior del panel controles, hay **elementos ocultos con el mismo orden de pintura que su control parental** .</span><span class="sxs-lookup"><span data-stu-id="0bfa4-144">At the very bottom of the controls panel, there is the **Hide elements with the same paint order as their parent** toggle.</span></span> <span data-ttu-id="0bfa4-145">Al seleccionar y anular la selección de la casilla, se volverán a cargar los elementos en función de la selección.</span><span class="sxs-lookup"><span data-stu-id="0bfa4-145">Selecting and deselecting the checkbox will reload the elements based on your selection.</span></span> <span data-ttu-id="0bfa4-146">Si está seleccionado, los elementos que compartan el orden de pintura se acoplarán al elemento primario.</span><span class="sxs-lookup"><span data-stu-id="0bfa4-146">If selected, elements that share paint order will be flattened to the parent.</span></span>

<span data-ttu-id="0bfa4-147">Estas opciones pretenden borrar algunos de los desordens que crean páginas web más complejas en el lienzo.</span><span class="sxs-lookup"><span data-stu-id="0bfa4-147">These options are meant to clear up some of the clutter that more complex web pages create in your canvas.</span></span>

### <span data-ttu-id="0bfa4-148">Tipo de color de índice Z</span><span class="sxs-lookup"><span data-stu-id="0bfa4-148">Z-index color type</span></span>

<span data-ttu-id="0bfa4-149">Estas son las diferentes visualizaciones que puede usar para el DOM en el lienzo.</span><span class="sxs-lookup"><span data-stu-id="0bfa4-149">These are the different visualizations you can use for the DOM in your canvas.</span></span> <span data-ttu-id="0bfa4-150">Tanto si lo usas por diversión como si te ayudan a visualizar mejor el DOM, tenemos tres colorways diferentes, así como una configuración de "color de fondo".</span><span class="sxs-lookup"><span data-stu-id="0bfa4-150">Whether you use it for fun or because they help you visualize the DOM better, we have three different colorways as well as a "background color" setting.</span></span> <span data-ttu-id="0bfa4-151">Los botones de radio le permiten alternar entre las opciones y seleccionar el tipo de color más adecuado para el proyecto (o que le gusten).</span><span class="sxs-lookup"><span data-stu-id="0bfa4-151">The radio buttons allow you to toggle through the options and pick the color type most appropriate for your project (or that you like the most).</span></span>

![Vista DOM](./media/dom-purple-box.png)

## <span data-ttu-id="0bfa4-153">DOM 3D</span><span class="sxs-lookup"><span data-stu-id="0bfa4-153">3D DOM</span></span>

<span data-ttu-id="0bfa4-154">Si desea tomar más de una vista de depuración general, en lugar de la experiencia de índice z, el DOM 3D ofrece un aspecto general del DOM.</span><span class="sxs-lookup"><span data-stu-id="0bfa4-154">If you want to take more of a general debugging view, rather than the z-index experience, the 3D DOM gives an overall look of the DOM.</span></span> <span data-ttu-id="0bfa4-155">Dado que el contexto de índice z se elimina, DOM se apila de forma más estrecha y clara.</span><span class="sxs-lookup"><span data-stu-id="0bfa4-155">Since the z-index context is removed, the DOM is stacked more closely and cleanly.</span></span> <span data-ttu-id="0bfa4-156">Este panel tiene una funcionalidad similar, pero hay algunos matices.</span><span class="sxs-lookup"><span data-stu-id="0bfa4-156">This pane has similar functionality, but there are a few nuances.</span></span>

### <span data-ttu-id="0bfa4-157">Cambiar la vista</span><span class="sxs-lookup"><span data-stu-id="0bfa4-157">Changing your view</span></span>

<span data-ttu-id="0bfa4-158">En el panel **3D Dom** , el filtro del **elemento seleccionado aislar** tiene "incluir hijos" y "incluir padres".</span><span class="sxs-lookup"><span data-stu-id="0bfa4-158">In the **3D DOM** pane, the **Isolate selected element** filter has "Include children" and "Include parents."</span></span> <span data-ttu-id="0bfa4-159">De forma predeterminada, se seleccionan las dos casillas, lo que significa que al hacer clic en el botón **aislar elemento seleccionado** después de seleccionar un elemento en el lienzo, se muestra el elemento elegido, los elementos primarios del elemento y los elementos secundarios del elemento.</span><span class="sxs-lookup"><span data-stu-id="0bfa4-159">By default both checkboxes are selected, which means that clicking on the **Isolate selected element** button after selecting an element in the canvas would display the element chosen, the element's parents, and the element's children.</span></span> <span data-ttu-id="0bfa4-160">Si anula la selección de la casilla "incluir hijos" y hace clic de nuevo en el botón **aislar elemento seleccionado** , se mostrará el elemento seleccionado y los elementos primarios del elemento.</span><span class="sxs-lookup"><span data-stu-id="0bfa4-160">Deselecting the "Include children" checkbox and clicking the **Isolate selected element** button again would display the selected element and the element's parents.</span></span> <span data-ttu-id="0bfa4-161">Si selecciona la casilla "incluir hijos" y anula la selección de la casilla "incluir padres" antes de hacer clic en **aislar elemento seleccionado**, el lienzo mostrará el elemento y sus elementos secundarios.</span><span class="sxs-lookup"><span data-stu-id="0bfa4-161">If you select the "Include children" checkbox and deselect the "Include parents" checkbox before clicking on **Isolate selected element**, the canvas will then display the element and its children.</span></span> <span data-ttu-id="0bfa4-162">Si anula la selección de ambas casillas y hace clic en **aislar elemento seleccionado**, el lienzo solo mostrará el elemento que seleccionó previamente.</span><span class="sxs-lookup"><span data-stu-id="0bfa4-162">If you deselect both checkboxes and click on **Isolate selected element**, the canvas will only display the element you previously selected.</span></span>

<span data-ttu-id="0bfa4-163">Verá un control deslizante en el panel de control titulado **nivel de anidamiento** con un número al lado.</span><span class="sxs-lookup"><span data-stu-id="0bfa4-163">You'll notice a slider in the control pane titled **Nesting level** with a number next to it.</span></span> <span data-ttu-id="0bfa4-164">El número indica el número de capas en el documento.</span><span class="sxs-lookup"><span data-stu-id="0bfa4-164">The number indicates the number of layers in the document.</span></span> <span data-ttu-id="0bfa4-165">Si arrastra el control deslizante hacia la izquierda, las capas exteriores desaparecerán hasta que se quede con un nivel de anidamiento de 1, lo que muestra únicamente el elemento posterior más lejano del DOM.</span><span class="sxs-lookup"><span data-stu-id="0bfa4-165">Dragging the slider to the left will cause the outermost layers to peel away until you are left with a nesting level of 1, displaying only the furthest back element in the DOM.</span></span> <span data-ttu-id="0bfa4-166">Esto le permite quitar algunos de los desorden si está intentando obtener más información sobre lo que sucede en los niveles inferiores.</span><span class="sxs-lookup"><span data-stu-id="0bfa4-166">This allows you to remove some of the clutter if you are trying to get a closer look at what is going on in the lower levels.</span></span>

### <span data-ttu-id="0bfa4-167">Tipo de color DOM</span><span class="sxs-lookup"><span data-stu-id="0bfa4-167">DOM color type</span></span>

<span data-ttu-id="0bfa4-168">Verá que, además de las opciones de color de fondo *a blanco*, *azul a amarillo*, *arco iris*y *usar color de fondo* , se *usa la textura*de la pantalla.</span><span class="sxs-lookup"><span data-stu-id="0bfa4-168">You'll notice that, in addition to the *Purple to White*, *Blue to Yellow*, *Rainbow*, and *Use background color* options, there is *Use screen texture*.</span></span> <span data-ttu-id="0bfa4-169">La textura de la pantalla agrega el contexto a la experiencia de depuración mostrando el contenido de la página web directamente en los elementos.</span><span class="sxs-lookup"><span data-stu-id="0bfa4-169">The screen texture adds context to your debugging experience by displaying the content from the web page directly onto the elements.</span></span> <span data-ttu-id="0bfa4-170">Esto sigue siendo un trabajo en curso, ya que algunos sitios web tienen un tiempo más difícil que representa la textura de la pantalla en la vista 3D.</span><span class="sxs-lookup"><span data-stu-id="0bfa4-170">This is still a work in progress, as some websites have a harder time rendering their screen texture in the 3D View.</span></span> 

## <span data-ttu-id="0bfa4-171">Pasos siguientes</span><span class="sxs-lookup"><span data-stu-id="0bfa4-171">Next steps</span></span>

<span data-ttu-id="0bfa4-172">Trabajamos en la interfaz de usuario y agregamos más funcionalidad a la vista 3D según las preguntas de los usuarios como usted.</span><span class="sxs-lookup"><span data-stu-id="0bfa4-172">We are working on the UI and adding more functionality to the 3D View based on asks from users like you.</span></span> <span data-ttu-id="0bfa4-173">Envíanos tus comentarios para que podamos seguir mejorando el DevTools de Microsoft Edge para ti.</span><span class="sxs-lookup"><span data-stu-id="0bfa4-173">Please send us your feedback so we can continue improving the Microsoft Edge DevTools for you!</span></span> <span data-ttu-id="0bfa4-174">Simplemente haz clic en el icono de comentarios de la DevTools o pulsa `Alt`  +  `Shift`  +  `I` en Windows ( `Option`  +  `Shift`  +  `I` en Mac) y escribe las solicitudes de comentarios o características de la DevTools.</span><span class="sxs-lookup"><span data-stu-id="0bfa4-174">Simply click the feedback icon in the DevTools or press `Alt` + `Shift` + `I` on Windows (`Option` + `Shift` + `I` on Mac) and enter any feedback or feature requests you have for the DevTools.</span></span>