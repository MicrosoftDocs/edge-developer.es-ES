---
description: Aprende a cambiar la configuración y los estilos de fuente CSS mediante el panel Estilos de Microsoft Edge DevTools.
title: Editar los estilos y la configuración de fuentes CSS en el panel Estilos de DevTools
author: MSEdgeTeam
ms.author: msedgedevrel
ms.date: 02/03/2021
ms.topic: article
ms.prod: microsoft-edge
keywords: Microsoft Edge, desarrollo web, herramientas F12, DevTools
ms.openlocfilehash: 928f7abb0f74839708cbe5c904ad321109ae33f0
ms.sourcegitcommit: 12c30ad4ab2664d17c9b7e9d59d7a3cda60ff65c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/04/2021
ms.locfileid: "11313349"
---
# <span data-ttu-id="d85e1-104">Editar la configuración y los estilos de fuente CSS en el panel Estilos</span><span class="sxs-lookup"><span data-stu-id="d85e1-104">Edit CSS font styles and settings in the Styles pane</span></span>  

:::image type="icon" source="../media/experimental-tag-14px.msft.png":::

<span data-ttu-id="d85e1-105">La tipografía en la web es una parte importante de la experiencia del usuario.</span><span class="sxs-lookup"><span data-stu-id="d85e1-105">Typography on the web is an important part of the user experience.</span></span>  <span data-ttu-id="d85e1-106">Quieres asegurarte de que cumples las directrices de marca corporativa y que el contenido se muestra según lo esperado en varios dispositivos.</span><span class="sxs-lookup"><span data-stu-id="d85e1-106">You want to ensure you meet corporate brand guidelines, and your content displays as expected on various devices.</span></span>  <span data-ttu-id="d85e1-107">El texto debe ser fácil de leer con el tamaño y el alto de línea.</span><span class="sxs-lookup"><span data-stu-id="d85e1-107">Text must be easy to read using size and line-height.</span></span>  <span data-ttu-id="d85e1-108">Los usuarios pueden cambiar el tamaño de las fuentes para satisfacer necesidades individuales.</span><span class="sxs-lookup"><span data-stu-id="d85e1-108">Users may resize fonts to meet individual needs.</span></span>  <span data-ttu-id="d85e1-109">En situaciones en las que fuentes específicas no están disponibles en un dispositivo de usuario, debes proporcionar opciones de fuente de reserva.</span><span class="sxs-lookup"><span data-stu-id="d85e1-109">For situations when specific fonts are not available on a user device, you should provide fallback font options.</span></span>  

<span data-ttu-id="d85e1-110">CSS proporciona una mejor compatibilidad con la tipografía en los últimos años.</span><span class="sxs-lookup"><span data-stu-id="d85e1-110">CSS provides better support for typography in recent years.</span></span>  <span data-ttu-id="d85e1-111">Hay decenas de unidades CSS diferentes disponibles para definir el tamaño del texto.</span><span class="sxs-lookup"><span data-stu-id="d85e1-111">There are dozens of different CSS units available to define the size of text.</span></span>  <span data-ttu-id="d85e1-112">También tiene varias propiedades CSS que afectan al tamaño de fuente, el espaciado, el alto de línea y otras características tipográficas.</span><span class="sxs-lookup"><span data-stu-id="d85e1-112">You also have several CSS properties that affect font-size, spacing, line height, and other typographic features.</span></span>  

<span data-ttu-id="d85e1-113">Para facilitar el trabajo con tipografía, ahora hay un Editor de **fuentes** visual en el **panel** Estilos.</span><span class="sxs-lookup"><span data-stu-id="d85e1-113">To make it easier when working with typography, a visual **Font Editor** is now in the **Styles** pane.</span></span>  <span data-ttu-id="d85e1-114">Puede cambiar la configuración de fuente y los cambios se representan inmediatamente en el explorador.</span><span class="sxs-lookup"><span data-stu-id="d85e1-114">You may change your font settings, and the changes are rendered immediately in the browser.</span></span>  <span data-ttu-id="d85e1-115">Todo sin conocimientos exhaustivos de CSS.</span><span class="sxs-lookup"><span data-stu-id="d85e1-115">All without in-depth knowledge of CSS.</span></span>  

<span data-ttu-id="d85e1-116">Actualmente, **la herramienta Habilitar nueva herramienta de editor** de fuentes dentro de la característica del panel Estilos es experimental y debe activarla para Microsoft Edge Developer [Tools.][DevtoolsExperimentalFeaturesIndexTurnOnExperimentalFeatures]</span><span class="sxs-lookup"><span data-stu-id="d85e1-116">Currently the **Enable new font editor tool within the Styles pane** feature is experimental and you need to [turn it on for Microsoft Edge Developer Tools][DevtoolsExperimentalFeaturesIndexTurnOnExperimentalFeatures].</span></span>  

<span data-ttu-id="d85e1-117">Cualquier CSS del panel **Estilos,** ya sea definiciones de fuente o estilos en línea, muestra automáticamente un icono que abre el **Editor de fuentes visual.**</span><span class="sxs-lookup"><span data-stu-id="d85e1-117">Any CSS in the **Styles** pane, either font definitions or inline styles, automatically displays an icon that opens the visual **Font Editor**.</span></span>  <span data-ttu-id="d85e1-118">Para abrir el **Editor**de fuentes visual, elija el **icono del Editor de** fuentes.</span><span class="sxs-lookup"><span data-stu-id="d85e1-118">To open the visual **Font Editor**, choose the **Font Editor** icon.</span></span>  

:::row:::
   :::column span="":::
      :::image type="complex" source="../media/font-editor-icon.msft.png" alt-text="Icono del panel Estilos para editar la configuración de fuentes" lightbox="../media/font-editor-icon.msft.png":::
         <span data-ttu-id="d85e1-120">Icono del panel Estilos **para** editar la configuración de fuentes</span><span class="sxs-lookup"><span data-stu-id="d85e1-120">The icon in the **Styles** pane to edit font settings</span></span>  
      :::image-end:::  
   :::column-end:::
   :::column span="":::
      :::image type="complex" source="../media/font-editor-open.msft.png" alt-text="El Editor de fuentes se abre en la parte superior del panel Estilos" lightbox="../media/font-editor-open.msft.png":::
         <span data-ttu-id="d85e1-122">El **Editor de fuentes** se abre en la parte superior del panel **Estilos**</span><span class="sxs-lookup"><span data-stu-id="d85e1-122">The **Font Editor** open on top of the **Styles** pane</span></span>  
      :::image-end:::  
   :::column-end:::
:::row-end:::  

<span data-ttu-id="d85e1-123">Todos los campos del **Editor de fuentes** visual se rellenan a partir de los valores de CSS en el **panel** Estilos.</span><span class="sxs-lookup"><span data-stu-id="d85e1-123">All fields in the visual **Font Editor** are populated from the values in the CSS in the **Styles** pane.</span></span>  <span data-ttu-id="d85e1-124">Por ejemplo, la definición se establece en el panel Estilos, por lo que se muestra el campo de texto de alto de línea y el `line-height` `160%` desplegable de \*\*\*\* `160` `%` unidades.</span><span class="sxs-lookup"><span data-stu-id="d85e1-124">For example, the `line-height` definition is set to `160%` in the **Styles** pane, so the line height text field displays `160`, and the unit dropdown displays `%`.</span></span>  <span data-ttu-id="d85e1-125">Además, el control deslizante se establece automáticamente para que coincida con los valores del campo de texto.</span><span class="sxs-lookup"><span data-stu-id="d85e1-125">Also, the slider is automatically set to match the values of the text field.</span></span>  

<span data-ttu-id="d85e1-126">El **Editor de** fuentes consta de dos partes: el selector de familia de fuentes y el editor de propiedades CSS.</span><span class="sxs-lookup"><span data-stu-id="d85e1-126">The **Font Editor** consists of two parts:  the Font Family selector, and the CSS Properties editor.</span></span>  

## <span data-ttu-id="d85e1-127">Selector de familia de fuentes</span><span class="sxs-lookup"><span data-stu-id="d85e1-127">The Font Family selector</span></span>  

<span data-ttu-id="d85e1-128">El selector de familia de fuentes es la parte superior del **Editor de fuentes visual.**</span><span class="sxs-lookup"><span data-stu-id="d85e1-128">The Font Family selector is the upper part of the visual **Font Editor**.</span></span>  <span data-ttu-id="d85e1-129">Para elegir las fuentes de la regla CSS, en el editor CSS, use el selector **de familia de** fuentes.</span><span class="sxs-lookup"><span data-stu-id="d85e1-129">To choose the fonts of the CSS rule, in the CSS editor, use the **Font Family** selector.</span></span>  <span data-ttu-id="d85e1-130">Puede elegir fuentes principales y de reserva para cada regla CSS.</span><span class="sxs-lookup"><span data-stu-id="d85e1-130">You may choose main and fallback fonts for each CSS rule.</span></span>  

:::image type="complex" source="../media/font-editor-font-family.msft.png" alt-text="El Editor de fuentes se abre en la parte superior del panel Estilos con el selector de familia de fuentes resaltado" lightbox="../media/font-editor-font-family.msft.png":::
   <span data-ttu-id="d85e1-132">El **Editor de** fuentes se abre en la parte superior del panel **Estilos** con el selector de **familia** de fuentes resaltado</span><span class="sxs-lookup"><span data-stu-id="d85e1-132">The **Font Editor** open on top of the **Styles** pane with the **Font Family** selector highlighted</span></span>  
:::image-end:::  

<span data-ttu-id="d85e1-133">Usa la **lista desplegable Familia de** fuentes para elegir entre una lista de fuentes.</span><span class="sxs-lookup"><span data-stu-id="d85e1-133">Use the **Font Family** dropdown to choose from a list of fonts.</span></span>  <span data-ttu-id="d85e1-134">Las fuentes se organizan en cuatro grupos.</span><span class="sxs-lookup"><span data-stu-id="d85e1-134">Fonts are organized into four groups.</span></span>  

1.  <span data-ttu-id="d85e1-135">Fuentes calculadas, que son las fuentes disponibles en la hoja de estilos en el **panel** Estilos.</span><span class="sxs-lookup"><span data-stu-id="d85e1-135">Computed fonts, which are the fonts available in the stylesheet in the **Styles** pane.</span></span>  
1.  <span data-ttu-id="d85e1-136">Fuentes del sistema, que son las fuentes que están disponibles en el sistema operativo actual.</span><span class="sxs-lookup"><span data-stu-id="d85e1-136">System fonts, which are the fonts that are available on the current operating system.</span></span>  
1.  <span data-ttu-id="d85e1-137">Familias de fuentes genéricas, como `serif` o `sans-serif` .</span><span class="sxs-lookup"><span data-stu-id="d85e1-137">Generic font families, such as `serif` or `sans-serif`.</span></span>  
1.  <span data-ttu-id="d85e1-138">Valores globales, como `inherit` , `initial` y `unset` .</span><span class="sxs-lookup"><span data-stu-id="d85e1-138">Global values, such as `inherit`, `initial`, and `unset`.</span></span>  
    
:::image type="complex" source="../media/font-editor-font-family-list.msft.png" alt-text="El editor de fuentes se abre en la parte superior del panel Estilos con el selector de familia de fuentes resaltado" lightbox="../media/font-editor-font-family-list.msft.png":::
   <span data-ttu-id="d85e1-140">El **Editor de** fuentes se abre en la parte superior del panel **Estilos** con el selector de **familia** de fuentes resaltado</span><span class="sxs-lookup"><span data-stu-id="d85e1-140">The **Font Editor** open on top of the **Styles** pane with the **Font Family** selector highlighted</span></span>  
:::image-end:::  

<span data-ttu-id="d85e1-141">Después de elegir una fuente, se muestra otro menú desplegable para que elija fuentes de reserva.</span><span class="sxs-lookup"><span data-stu-id="d85e1-141">After you choose a font, another dropdown menu is displayed for you to choose fallback fonts.</span></span>  <span data-ttu-id="d85e1-142">Puedes elegir hasta ocho fuentes de reserva.</span><span class="sxs-lookup"><span data-stu-id="d85e1-142">You may choose up to eight fallback fonts.</span></span>  <span data-ttu-id="d85e1-143">Para quitar una fuente, elija el **icono Eliminar familia de** fuentes.</span><span class="sxs-lookup"><span data-stu-id="d85e1-143">To remove a font, choose the **Delete Font Family** icon.</span></span>  

<!--:::image type="complex" source="../media/font-editor-defining-fonts.msft.png" alt-text="The font editor with a defined list of fonts and fallback fonts" lightbox="../media/font-editor-defining-fonts.msft.png":::
   The **Font Editor** with a defined list of fonts and fallback fonts highlighted
:::image-end:::  -->

> [!NOTE]
> <span data-ttu-id="d85e1-144">Si elige un valor global para la familia de fuentes, no obtiene otro desplegable, ya que no hay reserva para él en CSS.</span><span class="sxs-lookup"><span data-stu-id="d85e1-144">If you choose a global value for font family, you do not get another dropdown since there is no fallback for it in CSS.</span></span>  

## <span data-ttu-id="d85e1-145">Editor de propiedades CSS</span><span class="sxs-lookup"><span data-stu-id="d85e1-145">The CSS Properties editor</span></span>  

<span data-ttu-id="d85e1-146">Puede cambiar las propiedades de fuente CSS en la parte inferior del **Editor de fuentes visual.**</span><span class="sxs-lookup"><span data-stu-id="d85e1-146">You may change CSS font properties in the lower part of the visual **Font Editor**.</span></span>  <span data-ttu-id="d85e1-147">Puedes cambiar el tamaño de fuente, el alto de línea, el grosor de fuente y el espaciado entre letras mediante cualquiera de los controles de la interfaz de usuario.</span><span class="sxs-lookup"><span data-stu-id="d85e1-147">You may change the font size, line height, font weight, and letter spacing using any of the UI controls.</span></span>  <span data-ttu-id="d85e1-148">Los cambios se aplican inmediatamente en el explorador.</span><span class="sxs-lookup"><span data-stu-id="d85e1-148">Your changes are applied immediately in the browser.</span></span>  

:::image type="complex" source="../media/font-editor-css-properties.msft.png" alt-text="El editor de fuentes abierto en la parte superior del panel Estilos con las propiedades CSS resaltadas" lightbox="../media/font-editor-css-properties.msft.png":::
   <span data-ttu-id="d85e1-150">El **Editor de** fuentes se abre en la parte superior del panel **Estilos** con las propiedades CSS resaltadas</span><span class="sxs-lookup"><span data-stu-id="d85e1-150">The **Font Editor** open on top of the **Styles** pane with the CSS properties highlighted</span></span>  
:::image-end:::  

<span data-ttu-id="d85e1-151">También puede convertir unidades CSS mediante el **Editor de fuentes visual.**</span><span class="sxs-lookup"><span data-stu-id="d85e1-151">You may also convert CSS units using the visual **Font Editor**.</span></span>  <span data-ttu-id="d85e1-152">Por ejemplo, puede usar la herramienta en \*\*\*\* una regla CSS donde el control deslizante tamaño de fuente se establece inicialmente en `16 pixels` .</span><span class="sxs-lookup"><span data-stu-id="d85e1-152">For example, you may use the tool on a CSS rule where the **Font Size** slider is initially set to `16 pixels`.</span></span>  <span data-ttu-id="d85e1-153">Ahora, use el desplegable de unidades y elija el `em` valor.</span><span class="sxs-lookup"><span data-stu-id="d85e1-153">Now, use the unit dropdown and choose the value `em`.</span></span>  <span data-ttu-id="d85e1-154">El `1 em` valor mostrado es igual a `16 pixels` .</span><span class="sxs-lookup"><span data-stu-id="d85e1-154">The `1 em` displayed is equal to `16 pixels`.</span></span>  

:::row:::
   :::column span="":::
      :::image type="complex" source="../media/font-editor-setting-to-16px.msft.png" alt-text="Cambiar el tamaño de fuente a 16 píxeles" lightbox="../media/font-editor-setting-to-16px.msft.png":::
         <span data-ttu-id="d85e1-156">Cambiar el tamaño de fuente a</span><span class="sxs-lookup"><span data-stu-id="d85e1-156">Change the font size to</span></span> `16 pixels`  
      :::image-end:::  
   :::column-end:::
   :::column span="":::
      :::image type="complex" source="../media/font-editor-converted-to-em.msft.png" alt-text="Abrir el desplegable de unidades para convertir en em" lightbox="../media/font-editor-converted-to-em.msft.png":::
         <span data-ttu-id="d85e1-158">Abrir la lista desplegable de unidades a la que convertir</span><span class="sxs-lookup"><span data-stu-id="d85e1-158">Open the unit dropdown to convert to</span></span> `em`  
      :::image-end:::  
   :::column-end:::
:::row-end:::  

<span data-ttu-id="d85e1-159">El desplegable de unidades proporciona todas las unidades CSS numéricas que están disponibles.</span><span class="sxs-lookup"><span data-stu-id="d85e1-159">The unit dropdown provides all the numeric CSS units that are available.</span></span>  <span data-ttu-id="d85e1-160">El tamaño de fuente, el alto de línea, el grosor de fuente y el espaciado usan unidades diferentes.</span><span class="sxs-lookup"><span data-stu-id="d85e1-160">Font size, line height, font weight, and spacing all use different units.</span></span>  <span data-ttu-id="d85e1-161">Cuando los cuadros de texto tienen el foco, puede seleccionar las `arrow up` teclas y para ajustar la `arrow down` configuración.</span><span class="sxs-lookup"><span data-stu-id="d85e1-161">When the text boxes have focus, you may select the `arrow up` and `arrow down` keys to fine-tune your settings.</span></span>  <span data-ttu-id="d85e1-162">Para usar los controles deslizantes con un teclado, selecciona `arrow left` las teclas `arrow down` y.</span><span class="sxs-lookup"><span data-stu-id="d85e1-162">To use the sliders with a keyboard, select the `arrow left` and `arrow down` keys.</span></span>  

<span data-ttu-id="d85e1-163">El editor de propiedades CSS también incluye palabras clave preestablecidas.</span><span class="sxs-lookup"><span data-stu-id="d85e1-163">The CSS Properties editor also includes preset keywords.</span></span>  <span data-ttu-id="d85e1-164">Para usar las palabras clave preestablecidas, en el lado derecho, elija el `Toggle Input Type` icono.</span><span class="sxs-lookup"><span data-stu-id="d85e1-164">To use the preset keywords, on the right-hand side, choose the `Toggle Input Type` icon.</span></span>  <span data-ttu-id="d85e1-165">La interfaz de usuario cambia y se muestra un desplegable de palabras clave preestablecidas.</span><span class="sxs-lookup"><span data-stu-id="d85e1-165">The UI changes, and a dropdown of preset keywords are displayed.</span></span>  <span data-ttu-id="d85e1-166">Para volver a la interfaz de usuario con el control deslizante y otros controles de la interfaz de usuario, vuelve a `Toggle Input Type` elegir el icono.</span><span class="sxs-lookup"><span data-stu-id="d85e1-166">To return to the UI with the slider and other UI controls, choose the `Toggle Input Type` icon again.</span></span>  

:::image type="complex" source="../media/font-editor-preset-font-sizes.msft.png" alt-text="Abrir la interfaz de palabras clave preestablecidas" lightbox="../media/font-editor-preset-font-sizes.msft.png":::
   <span data-ttu-id="d85e1-168">Abrir la interfaz de palabras clave preestablecidas</span><span class="sxs-lookup"><span data-stu-id="d85e1-168">Open the preset keyword interface</span></span>  
:::image-end:::  

## <span data-ttu-id="d85e1-169">Contactar al equipo de Microsoft Edge DevTools</span><span class="sxs-lookup"><span data-stu-id="d85e1-169">Getting in touch with the Microsoft Edge DevTools team</span></span>  

[!INCLUDE [contact DevTools team note](../includes/contact-devtools-team-note.md)]  

<!-- links -->  

[DevtoolsIndex]: ../index.md "Herramientas de desarrollo de Microsoft Edge (Chromium) | Microsoft Docs"  
[DevtoolsExperimentalFeaturesIndex]: ../experimental-features/index.md "Características experimentales | Microsoft Docs"  
[DevtoolsExperimentalFeaturesIndexTurnOnExperimentalFeatures]: ../experimental-features/index.md#turn-on-experimental-features "Activar características experimentales: características experimentales | Microsoft Docs"  