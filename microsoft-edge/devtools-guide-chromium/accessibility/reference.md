---
title: Referencia de accesibilidad
author: MSEdgeTeam
ms.author: msedgedevrel
ms.date: 03/18/2020
ms.topic: article
ms.prod: microsoft-edge
keywords: Microsoft Edge, desarrollo web, herramientas F12, DevTools
ms.openlocfilehash: 7417388023612b6e1ca651deba28e099e3c8e3d8
ms.sourcegitcommit: 8bfa239274e7a4856b961b9cf163b08d96463c10
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2020
ms.locfileid: "10581576"
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





# <span data-ttu-id="811ae-103">Referencia de accesibilidad</span><span class="sxs-lookup"><span data-stu-id="811ae-103">Accessibility Reference</span></span>   



<span data-ttu-id="811ae-104">Esta página es una referencia completa de las características de accesibilidad en Microsoft Edge DevTools.</span><span class="sxs-lookup"><span data-stu-id="811ae-104">This page is a comprehensive reference of accessibility features in Microsoft Edge DevTools.</span></span>  <span data-ttu-id="811ae-105">Está destinada a los programadores web que:</span><span class="sxs-lookup"><span data-stu-id="811ae-105">It is intended for web developers who:</span></span>  

*   <span data-ttu-id="811ae-106">Tener un conocimiento básico de DevTools, como, por ejemplo, cómo abrirlo.</span><span class="sxs-lookup"><span data-stu-id="811ae-106">Have a basic understanding of DevTools, such as how to open it.</span></span>  
*   <span data-ttu-id="811ae-107">Está familiarizado con los [principios de accesibilidad y los procedimientos recomendados][MDNAccessibility].</span><span class="sxs-lookup"><span data-stu-id="811ae-107">Are familiar with [accessibility principles and best practices][MDNAccessibility].</span></span>  

<span data-ttu-id="811ae-108">El propósito de esta referencia es ayudarle a descubrir todas las herramientas disponibles en DevTools que le ayudan a examinar la accesibilidad de una página.</span><span class="sxs-lookup"><span data-stu-id="811ae-108">The purpose of this reference is to help you discover all of the tools available in DevTools that help you examine the accessibility of a page.</span></span>  

<span data-ttu-id="811ae-109">Consulte [navegar por Microsoft Edge DevTools con tecnología de asistencia][DevtoolsAccessibilityNavigation] si necesita ayuda para navegar por DevTools con una tecnología de asistencia, como un lector de pantalla.</span><span class="sxs-lookup"><span data-stu-id="811ae-109">See [Navigating Microsoft Edge DevTools With Assistive Technology][DevtoolsAccessibilityNavigation] if you are looking for help on navigating DevTools with an assistive technology like a screen reader.</span></span>  

## <span data-ttu-id="811ae-110">Información general sobre las características de accesibilidad en Microsoft Edge DevTools</span><span class="sxs-lookup"><span data-stu-id="811ae-110">Overview of accessibility features in Microsoft Edge DevTools</span></span>   

<span data-ttu-id="811ae-111">En esta sección se explica cómo DevTools encaja en el conjunto de herramientas general de accesibilidad.</span><span class="sxs-lookup"><span data-stu-id="811ae-111">This section explains how DevTools fits into your overall accessibility toolkit.</span></span>  

<span data-ttu-id="811ae-112">Al determinar si una página es accesible, debe tener en cuenta dos preguntas generales:</span><span class="sxs-lookup"><span data-stu-id="811ae-112">When determining whether a page is accessible, you need to have 2 general questions in mind:</span></span>  

1.  <span data-ttu-id="811ae-113">¿Puede navegar por la página con un teclado o un [lector de pantalla][MDNScreenReader]?</span><span class="sxs-lookup"><span data-stu-id="811ae-113">Are you able to navigate the page with a keyboard or [screen reader][MDNScreenReader]?</span></span>  
1.  <span data-ttu-id="811ae-114">¿Están los elementos de la página correctamente marcados para los lectores de pantalla?</span><span class="sxs-lookup"><span data-stu-id="811ae-114">Are the elements of the page properly marked up for screen readers?</span></span>  

<span data-ttu-id="811ae-115">En general, DevTools debería ayudarle a corregir los errores relacionados con preguntas #2, porque estos errores son fáciles de detectar de forma automática.</span><span class="sxs-lookup"><span data-stu-id="811ae-115">In general, DevTools should help you fix errors related to question #2, because these errors are easy to detect in an automated fashion.</span></span>  <span data-ttu-id="811ae-116">La pregunta #1 es tan importante, pero lamentablemente DevTools no le ayuda a usted.</span><span class="sxs-lookup"><span data-stu-id="811ae-116">Question #1 is just as important, but unfortunately DevTools does not help you there.</span></span>  <span data-ttu-id="811ae-117">La única forma de buscar errores relacionados con la pregunta #1 es intentar usar una página con un teclado o lector de pantalla.</span><span class="sxs-lookup"><span data-stu-id="811ae-117">The only way to find errors related to question #1 is to try using a page with a keyboard or screen reader yourself.</span></span>  <!--See [How To Do An Accessibility Review][AccessibilityReview] to learn more.  -->  

<!--[AccessibilityReview]: /web/fundamentals/accessibility/how-to-review  -->  

## <span data-ttu-id="811ae-118">Auditar la accesibilidad de una página</span><span class="sxs-lookup"><span data-stu-id="811ae-118">Audit the accessibility of a page</span></span>   

> [!NOTE]
> <span data-ttu-id="811ae-119">El panel **Auditoría** proporciona vínculos a contenido hospedado en sitios web de terceros.</span><span class="sxs-lookup"><span data-stu-id="811ae-119">The **Audits** panel provides links to content hosted on third-party websites.</span></span>  <span data-ttu-id="811ae-120">Microsoft no se responsabiliza y no tiene ningún control sobre el contenido de estos sitios y los datos que se pueden recopilar.</span><span class="sxs-lookup"><span data-stu-id="811ae-120">Microsoft is not responsible for and has no control over the content of these sites and any data that may be collected.</span></span>  

<span data-ttu-id="811ae-121">En general, use el panel auditorías para determinar si:</span><span class="sxs-lookup"><span data-stu-id="811ae-121">In general, use the Audits panel to determine if:</span></span>  

*   <span data-ttu-id="811ae-122">Una página se marcó correctamente para los lectores de pantalla.</span><span class="sxs-lookup"><span data-stu-id="811ae-122">A page is properly marked up for screen readers.</span></span>  
*   <span data-ttu-id="811ae-123">Los elementos de texto de una página tienen relaciones de contraste suficientes.</span><span class="sxs-lookup"><span data-stu-id="811ae-123">The text elements on a page have sufficient contrast ratios.</span></span> <span data-ttu-id="811ae-124">Consulte también [ver la relación de contraste de un elemento de texto en el selector de colores](#view-the-contrast-ratio-of-a-text-element-in-the-color-picker).</span><span class="sxs-lookup"><span data-stu-id="811ae-124">See also [View the contrast ratio of a text element in the Color Picker](#view-the-contrast-ratio-of-a-text-element-in-the-color-picker).</span></span>  

<span data-ttu-id="811ae-125">Para auditar una página:</span><span class="sxs-lookup"><span data-stu-id="811ae-125">To audit a page:</span></span>  

1.  <span data-ttu-id="811ae-126">Vaya a la dirección URL que desea auditar.</span><span class="sxs-lookup"><span data-stu-id="811ae-126">Go to the URL that you want to audit.</span></span>  
1.  <span data-ttu-id="811ae-127">En DevTools, haga clic en la pestaña **auditorías** .  En DevTools se muestran varias opciones de configuración.</span><span class="sxs-lookup"><span data-stu-id="811ae-127">In DevTools, click the **Audits** tab.  DevTools shows you various configuration options.</span></span>  
    
    > ##### <span data-ttu-id="811ae-128">Figura 1</span><span class="sxs-lookup"><span data-stu-id="811ae-128">Figure 1</span></span>  
    > <span data-ttu-id="811ae-129">Configuración de auditorías</span><span class="sxs-lookup"><span data-stu-id="811ae-129">Configuring audits</span></span>  
    > ![Configuración de auditorías][ImageConfiguringAudits]  
    
    > [!NOTE]
    > <span data-ttu-id="811ae-131">Las capturas de pantallas de esta sección se han tomado con la versión 79 de Microsoft Edge.</span><span class="sxs-lookup"><span data-stu-id="811ae-131">The screenshots in this section were taken with version 79 of Microsoft Edge.</span></span>  <span data-ttu-id="811ae-132">Puede consultar qué versión está ejecutando `edge://version` .</span><span class="sxs-lookup"><span data-stu-id="811ae-132">You may check what version you are running at `edge://version`.</span></span>  <span data-ttu-id="811ae-133">La interfaz de usuario del panel **auditorías** tiene un aspecto diferente en versiones anteriores de Microsoft Edge, pero el flujo de trabajo general es el mismo.</span><span class="sxs-lookup"><span data-stu-id="811ae-133">The **Audits** panel UI looks different in earlier versions of Microsoft Edge, but the general workflow is the same.</span></span>  
    
1.  <span data-ttu-id="811ae-134">En **dispositivo**, seleccione **móvil** si desea simular un dispositivo móvil.</span><span class="sxs-lookup"><span data-stu-id="811ae-134">For **Device**, select **Mobile** if you want to simulate a mobile device.</span></span>  <span data-ttu-id="811ae-135">Esta opción cambia la cadena de agente de usuario y cambia el tamaño de la ventanilla.</span><span class="sxs-lookup"><span data-stu-id="811ae-135">This option changes your user agent string and resizes the viewport.</span></span>  <span data-ttu-id="811ae-136">Si la versión móvil de la página se muestra de forma diferente a la de la versión de escritorio, esta opción podría tener un efecto significativo en los resultados de la auditoría.</span><span class="sxs-lookup"><span data-stu-id="811ae-136">If the mobile version of the page displays differently than the desktop version, this option could have a significant effect on the results of your audit.</span></span>  
1.  <span data-ttu-id="811ae-137">En la sección **auditorías** , asegúrese de que **accesibilidad** está habilitada.</span><span class="sxs-lookup"><span data-stu-id="811ae-137">In the **Audits** section, make sure that **Accessibility** is enabled.</span></span>  <span data-ttu-id="811ae-138">Deshabilite las otras categorías si desea excluirlas de su informe.</span><span class="sxs-lookup"><span data-stu-id="811ae-138">Disable the other categories if you want to exclude them from your report.</span></span>  <span data-ttu-id="811ae-139">Déjelas habilitadas si deseas descubrir otras formas de mejorar la calidad de la página.</span><span class="sxs-lookup"><span data-stu-id="811ae-139">Leave them enabled if you want to discover other ways to improve the quality of your page.</span></span>  
1.  <span data-ttu-id="811ae-140">La sección de **limitación** le permite limitar la red y la CPU, lo cual es útil al analizar el rendimiento de la carga.</span><span class="sxs-lookup"><span data-stu-id="811ae-140">The **Throttling** section lets you throttle the network and CPU, which is useful when analyzing load performance.</span></span>  <span data-ttu-id="811ae-141">Esta opción no debe ser relevante para la puntuación de accesibilidad, por lo que puede usar lo que prefiera.</span><span class="sxs-lookup"><span data-stu-id="811ae-141">This option should be irrelevant to your accessibility score, so you may use whatever you prefer.</span></span>  
1.  <span data-ttu-id="811ae-142">La casilla **Borrar almacenamiento** le permite borrar todo el almacenamiento antes de cargar la página o conservar el almacenamiento entre cargas de páginas.</span><span class="sxs-lookup"><span data-stu-id="811ae-142">The **Clear Storage** checkbox lets you clear all storage before loading the page, or preserve storage between page loads.</span></span>  <span data-ttu-id="811ae-143">Esta opción también probablemente es irrelevante para la puntuación de accesibilidad, por lo que puede usar lo que prefiera.</span><span class="sxs-lookup"><span data-stu-id="811ae-143">This option is also probably irrelevant to your accessibility score, so you may use whatever you prefer.</span></span>  
1.  <span data-ttu-id="811ae-144">Haga clic en **Ejecutar Auditorías**.</span><span class="sxs-lookup"><span data-stu-id="811ae-144">Click **Run Audits**.</span></span> <span data-ttu-id="811ae-145">Después de 10 a 30 segundos, DevTools proporciona un informe.</span><span class="sxs-lookup"><span data-stu-id="811ae-145">After 10 to 30 seconds, DevTools provides a report.</span></span>  <span data-ttu-id="811ae-146">El informe le ofrece varias sugerencias para mejorar la accesibilidad de la página.</span><span class="sxs-lookup"><span data-stu-id="811ae-146">Your report gives you various tips on how to improve the accessibility of the page.</span></span>  
    
    > ##### <span data-ttu-id="811ae-147">Figura 2</span><span class="sxs-lookup"><span data-stu-id="811ae-147">Figure 2</span></span>  
    > <span data-ttu-id="811ae-148">Un informe</span><span class="sxs-lookup"><span data-stu-id="811ae-148">A report</span></span>  
    > ![Un informe][ImageReport]  
    
1.  <span data-ttu-id="811ae-150">Haga clic en una auditoría para obtener más información sobre ella.</span><span class="sxs-lookup"><span data-stu-id="811ae-150">Click an audit to learn more about it.</span></span>  
    
    > ##### <span data-ttu-id="811ae-151">Imagen 3</span><span class="sxs-lookup"><span data-stu-id="811ae-151">Figure 3</span></span>  
    > <span data-ttu-id="811ae-152">Más información sobre una auditoría</span><span class="sxs-lookup"><span data-stu-id="811ae-152">More information about an audit</span></span>  
    > ![Más información sobre una auditoría][ImageAttributes]  
    
1.  <span data-ttu-id="811ae-154">Haga clic en más **información** para ver la documentación de esa auditoría.</span><span class="sxs-lookup"><span data-stu-id="811ae-154">Click **Learn More** to view the documentation of that audit.</span></span>
    
    > ##### <span data-ttu-id="811ae-155">Imagen 4</span><span class="sxs-lookup"><span data-stu-id="811ae-155">Figure 4</span></span>  
    > <span data-ttu-id="811ae-156">Ver la documentación de una auditoría</span><span class="sxs-lookup"><span data-stu-id="811ae-156">Viewing the documentation of an audit</span></span>  
    > ![Ver la documentación de una auditoría][ImageAuditDocumentation]  
    
### <span data-ttu-id="811ae-158">Vea también: extensión aXe</span><span class="sxs-lookup"><span data-stu-id="811ae-158">See also: aXe extension</span></span>   

<span data-ttu-id="811ae-159">Es posible que prefiera usar la [extensión de aXe][ChromeWebStoreAxe] en lugar del panel **auditorías** .</span><span class="sxs-lookup"><span data-stu-id="811ae-159">You may prefer to use the [aXe extension][ChromeWebStoreAxe] rather than the **Audits** panel.</span></span>  
<span data-ttu-id="811ae-160">La extensión aXe generalmente proporciona la misma información, ya que es el motor subyacente que alimenta el panel auditorías.</span><span class="sxs-lookup"><span data-stu-id="811ae-160">The aXe extension generally provides the same information, since it is the underlying engine that powers the Audits panel.</span></span>  <span data-ttu-id="811ae-161">La extensión de aXe tiene una interfaz de usuario diferente y describe las auditorías de forma ligeramente distinta.</span><span class="sxs-lookup"><span data-stu-id="811ae-161">The aXe extension has a different UI and describes audits slightly differently.</span></span>  
<span data-ttu-id="811ae-162">Una de las ventajas de que la extensión aXe está en el panel **Auditoría** es que le permite inspeccionar y resaltar los nodos con errores.</span><span class="sxs-lookup"><span data-stu-id="811ae-162">One advantage that the aXe extension has over the **Audits** panel is that it enables you to inspect and highlight failing nodes.</span></span>  

> ##### <span data-ttu-id="811ae-163">Imagen 5</span><span class="sxs-lookup"><span data-stu-id="811ae-163">Figure 5</span></span>  
> <span data-ttu-id="811ae-164">La extensión de aXe</span><span class="sxs-lookup"><span data-stu-id="811ae-164">The aXe extension</span></span>  
> ![La extensión de aXe][ImageAxeExtension]  

## <span data-ttu-id="811ae-166">El panel Accesibilidad</span><span class="sxs-lookup"><span data-stu-id="811ae-166">The Accessibility pane</span></span>   

<span data-ttu-id="811ae-167">El panel de **accesibilidad** es el lugar donde se ve el árbol de accesibilidad, los atributos de Aria y las propiedades de accesibilidad calculadas de los nodos DOM.</span><span class="sxs-lookup"><span data-stu-id="811ae-167">The **Accessibility** pane is where you view the accessibility tree, ARIA attributes, and computed accessibility properties of DOM nodes.</span></span>  

<span data-ttu-id="811ae-168">Para abrir el panel **accesibilidad** :</span><span class="sxs-lookup"><span data-stu-id="811ae-168">To open the **Accessibility** pane:</span></span>  

1.  <span data-ttu-id="811ae-169">Haga clic en la pestaña **elementos** .</span><span class="sxs-lookup"><span data-stu-id="811ae-169">Click the **Elements** tab.</span></span>  
1.  <span data-ttu-id="811ae-170">En el **árbol DOM**, seleccione el elemento que desea inspeccionar.</span><span class="sxs-lookup"><span data-stu-id="811ae-170">In the **DOM Tree**, select the element which you want to inspect.</span></span>  
1.  <span data-ttu-id="811ae-171">Haga clic en la pestaña **accesibilidad** .  Es posible que esta pestaña esté oculta **detrás del** botón más pestañas más pestañas ![ ][ImageMoreTabsIcon] .</span><span class="sxs-lookup"><span data-stu-id="811ae-171">Click the **Accessibility** tab.  This tab may be hidden behind the **More Tabs** ![More Tabs][ImageMoreTabsIcon] button.</span></span>  

> ##### <span data-ttu-id="811ae-172">Imagen 6</span><span class="sxs-lookup"><span data-stu-id="811ae-172">Figure 6</span></span>  
> <span data-ttu-id="811ae-173">Inspeccionar el `h1` elemento de la Página principal de DevTools en el panel **accesibilidad**</span><span class="sxs-lookup"><span data-stu-id="811ae-173">Inspecting the `h1` element of the DevTools homepage in the **Accessibility** pane</span></span>  
> ![Inspeccionar el elemento H1 de la Página principal de DevTools en el panel Accesibilidad][ImageA11yPane]  

### <span data-ttu-id="811ae-175">Ver la posición de un elemento en el árbol de accesibilidad</span><span class="sxs-lookup"><span data-stu-id="811ae-175">View the position of an element in the accessibility tree</span></span>   

<span data-ttu-id="811ae-176">El [árbol de accesibilidad][MDNAccessibilityTree] es un subconjunto del árbol DOM.</span><span class="sxs-lookup"><span data-stu-id="811ae-176">The [accessibility tree][MDNAccessibilityTree] is a subset of the DOM tree.</span></span>  <span data-ttu-id="811ae-177">Solo contiene elementos del árbol DOM que son relevantes y útiles para mostrar el contenido de una página en un lector de pantalla.</span><span class="sxs-lookup"><span data-stu-id="811ae-177">It only contains elements from the DOM tree that are relevant and useful for displaying the contents of a page in a screen reader.</span></span>  

<span data-ttu-id="811ae-178">Inspeccione la posición de un elemento en el árbol de accesibilidad en el [panel Accesibilidad](#the-accessibility-pane).</span><span class="sxs-lookup"><span data-stu-id="811ae-178">Inspect the position of an element in the accessibility tree from the [Accessibility pane](#the-accessibility-pane).</span></span>  

> ##### <span data-ttu-id="811ae-179">Imagen 7</span><span class="sxs-lookup"><span data-stu-id="811ae-179">Figure 7</span></span>  
> <span data-ttu-id="811ae-180">Sección de árbol de accesibilidad</span><span class="sxs-lookup"><span data-stu-id="811ae-180">The Accessibility Tree section</span></span>  
> ![Sección de árbol de accesibilidad][ImageAllyTree]  

### <span data-ttu-id="811ae-182">Ver los atributos de ARIA de un elemento</span><span class="sxs-lookup"><span data-stu-id="811ae-182">View the ARIA attributes of an element</span></span>   

<span data-ttu-id="811ae-183">Los atributos de ARIA garantizan que los lectores de pantalla tengan toda la información que necesitan para representar correctamente el contenido de una página.</span><span class="sxs-lookup"><span data-stu-id="811ae-183">ARIA attributes ensure that screen readers have all of the information that they need in order to properly represent the contents of a page.</span></span>  

<span data-ttu-id="811ae-184">Ver los atributos de ARIA de un elemento en el [Panel de accesibilidad](#the-accessibility-pane).</span><span class="sxs-lookup"><span data-stu-id="811ae-184">View the ARIA attributes of an element in the [Accessibility pane](#the-accessibility-pane).</span></span>  

> ##### <span data-ttu-id="811ae-185">Imagen 8</span><span class="sxs-lookup"><span data-stu-id="811ae-185">Figure 8</span></span>  
> <span data-ttu-id="811ae-186">La sección de atributos de ARIA</span><span class="sxs-lookup"><span data-stu-id="811ae-186">The ARIA Attributes section</span></span>  
> ![La sección de atributos de ARIA][ImageAriaAttributesSection]  

### <span data-ttu-id="811ae-188">Ver las propiedades de accesibilidad calculadas de un elemento</span><span class="sxs-lookup"><span data-stu-id="811ae-188">View the computed accessibility properties of an element</span></span>   

> [!NOTE]
> <span data-ttu-id="811ae-189">Si está buscando propiedades calculadas de CSS, consulte la [pestaña calculada][DevtoolsCssReferenceViewActuallyAppliedElements].</span><span class="sxs-lookup"><span data-stu-id="811ae-189">If you are looking for computed CSS properties, see the [Computed tab][DevtoolsCssReferenceViewActuallyAppliedElements].</span></span>  

<span data-ttu-id="811ae-190">El explorador calcula dinámicamente algunas propiedades de accesibilidad.</span><span class="sxs-lookup"><span data-stu-id="811ae-190">Some accessibility properties are dynamically calculated by the browser.</span></span>  <span data-ttu-id="811ae-191">Estas propiedades se muestran en la sección **propiedades calculadas** del panel **accesibilidad** .</span><span class="sxs-lookup"><span data-stu-id="811ae-191">These properties are displayed in the **Computed Properties** section of the **Accessibility** pane.</span></span>  

<span data-ttu-id="811ae-192">Ver las propiedades de accesibilidad calculadas de un elemento en el [Panel de accesibilidad](#the-accessibility-pane).</span><span class="sxs-lookup"><span data-stu-id="811ae-192">View the computed accessibility properties of an element in the [Accessibility pane](#the-accessibility-pane).</span></span>  

> ##### <span data-ttu-id="811ae-193">Imagen 9</span><span class="sxs-lookup"><span data-stu-id="811ae-193">Figure 9</span></span>  
> <span data-ttu-id="811ae-194">Sección de propiedades calculadas (accesibilidad)</span><span class="sxs-lookup"><span data-stu-id="811ae-194">The Computed (Accessibility) Properties section</span></span>  
> ![Sección de propiedades calculadas (accesibilidad)][ImageComputedA11yPropertiesSection]  

## <span data-ttu-id="811ae-196">Ver la relación de contraste de un elemento de texto en el selector de colores</span><span class="sxs-lookup"><span data-stu-id="811ae-196">View the contrast ratio of a text element in the Color Picker</span></span>   

<span data-ttu-id="811ae-197">Algunas personas con deficiencias visuales no ven las áreas muy claras o muy oscuras.</span><span class="sxs-lookup"><span data-stu-id="811ae-197">Some people with low vision do not see areas as very bright or very dark.</span></span>  <span data-ttu-id="811ae-198">Todo tiende a aparecer sobre el mismo brillo, lo que hace que sea difícil distinguir los esquemas y los bordes.</span><span class="sxs-lookup"><span data-stu-id="811ae-198">Everything tends to appear at about the same brightness, which makes it hard to distinguish outlines and edges.</span></span>  
<span data-ttu-id="811ae-199">La relación de contraste mide la diferencia de brillo entre el primer plano y el fondo del texto.</span><span class="sxs-lookup"><span data-stu-id="811ae-199">Contrast ratio measures the difference in brightness between the foreground and background of text.</span></span>  <span data-ttu-id="811ae-200">Si el texto tiene una relación de contraste baja, es posible que los usuarios de estas deficiencias experimenten literalmente su sitio como pantalla en blanco.</span><span class="sxs-lookup"><span data-stu-id="811ae-200">If your text has a low contrast ratio, then these low vision users may literally experience your site as a blank screen.</span></span>  

<span data-ttu-id="811ae-201">El selector de colores le ayuda a comprobar que el texto cumple los niveles de proporción de contraste recomendados:</span><span class="sxs-lookup"><span data-stu-id="811ae-201">The Color Picker helps you verify that your text meets recommended contrast ratio levels:</span></span>  

1.  <span data-ttu-id="811ae-202">Haga clic en la pestaña **elementos** .</span><span class="sxs-lookup"><span data-stu-id="811ae-202">Click the **Elements** tab.</span></span>  
1.  <span data-ttu-id="811ae-203">En el **árbol DOM**, seleccione el elemento de texto que desea inspeccionar.</span><span class="sxs-lookup"><span data-stu-id="811ae-203">In the **DOM Tree**, select the text element that you want to inspect.</span></span>  
    
    > ##### <span data-ttu-id="811ae-204">Imagen 10</span><span class="sxs-lookup"><span data-stu-id="811ae-204">Figure 10</span></span>  
    > <span data-ttu-id="811ae-205">Inspeccionar un párrafo en el árbol DOM</span><span class="sxs-lookup"><span data-stu-id="811ae-205">Inspecting a paragraph in the DOM Tree</span></span>  
    > ![Inspeccionar un párrafo en el árbol DOM][ImageInspectDomTree]  
    
1.  <span data-ttu-id="811ae-207">En el panel **estilos** , haga clic en el cuadrado de color situado junto al `color` valor del elemento.</span><span class="sxs-lookup"><span data-stu-id="811ae-207">In the **Styles** pane, click the color square next to the `color` value of the element.</span></span>  
    
    > ##### <span data-ttu-id="811ae-208">Imagen 11</span><span class="sxs-lookup"><span data-stu-id="811ae-208">Figure 11</span></span>  
    > <span data-ttu-id="811ae-209">La `color` propiedad del elemento</span><span class="sxs-lookup"><span data-stu-id="811ae-209">The `color` property of the element</span></span>  
    > ![Propiedad color del elemento][ImageColorElement]  
    
1.  <span data-ttu-id="811ae-211">Compruebe la sección **relación de contraste** del selector de colores.</span><span class="sxs-lookup"><span data-stu-id="811ae-211">Check the **Contrast Ratio** section of the Color Picker.</span></span>  <span data-ttu-id="811ae-212">Una marca de verificación significa que el elemento cumple con la [recomendación mínima][W3CContrastMinimum].</span><span class="sxs-lookup"><span data-stu-id="811ae-212">One checkmark means that the element meets the [minimum recommendation][W3CContrastMinimum].</span></span>  <span data-ttu-id="811ae-213">Dos marcas de verificación significa que cumple con la [Recomendación mejorada][W3CContrastEnhanced].</span><span class="sxs-lookup"><span data-stu-id="811ae-213">Two checkmarks means that it meets the [enhanced recommendation][W3CContrastEnhanced].</span></span>
    
    > ##### <span data-ttu-id="811ae-214">Imagen 12</span><span class="sxs-lookup"><span data-stu-id="811ae-214">Figure 12</span></span>  
    > <span data-ttu-id="811ae-215">La sección de relación de contraste del selector de color muestra 2 marcas de verificación y un valor de</span><span class="sxs-lookup"><span data-stu-id="811ae-215">The Contrast Ratio section of the Color Picker shows 2 checkmarks and a value of</span></span> `13.97`  
    > ![La sección relación de contraste del selector de color muestra 2 marcas de verificación y un valor de 13,97][ImageColorPickerContrastRatio]  
    
1.  <span data-ttu-id="811ae-217">Haga clic en la sección **relación de contraste** para ver más información.</span><span class="sxs-lookup"><span data-stu-id="811ae-217">Click the **Contrast Ratio** section to see more information.</span></span>  <span data-ttu-id="811ae-218">Aparece una línea en el selector visual en la parte superior del selector de colores.</span><span class="sxs-lookup"><span data-stu-id="811ae-218">A line appears in the visual picker at the top of the Color Picker.</span></span>  <span data-ttu-id="811ae-219">Si el color actual cumple con las recomendaciones, cualquier cosa en el mismo lado de la línea también se ajusta a las recomendaciones.</span><span class="sxs-lookup"><span data-stu-id="811ae-219">If the current color meets recommendations, then anything on the same side of the line also meets recommendations.</span></span>  <span data-ttu-id="811ae-220">Si el color actual no cumple con las recomendaciones, entonces cualquier cosa en el mismo lado no cumple con las recomendaciones.</span><span class="sxs-lookup"><span data-stu-id="811ae-220">If the current color does not meet recommendations, then anything on the same side also does not meet recommendations.</span></span>  
    
    > ##### <span data-ttu-id="811ae-221">Imagen 13</span><span class="sxs-lookup"><span data-stu-id="811ae-221">Figure 13</span></span>  
    > <span data-ttu-id="811ae-222">La línea de proporción de contraste en el selector visual</span><span class="sxs-lookup"><span data-stu-id="811ae-222">The Contrast Ratio Line in the visual picker</span></span>  
    > ![La línea de proporción de contraste en el selector visual][ImageContrastRatioLine]  

<!--## Feedback   -->  



<!-- image links -->  

[ImageMoreTabsIcon]: /microsoft-edge/devtools-guide-chromium/media/more-tabs-icon.msft.png  

[ImageConfiguringAudits]: /microsoft-edge/devtools-guide-chromium/media/accessibility-audits-pane.msft.png "Ilustración 1: configuración de auditorías"  
[ImageReport]: /microsoft-edge/devtools-guide-chromium/media/accessibility-audits-run-audits-result.msft.png "Ilustración 2: una figura"  
[ImageAttributes]: /microsoft-edge/devtools-guide-chromium/media/accessibility-audits-run-audits-result-issues-expanded.msft.png "Ilustración 3: más información sobre una auditoría"  
[ImageAuditDocumentation]: /microsoft-edge/devtools-guide-chromium/media/accessibility-web-dev-accessibility-audits-learn-more.msft.png "Figura 4: visualización de la documentación de una auditoría"  
[ImageAxeExtension]: /microsoft-edge/devtools-guide-chromium/media/accessibility-devtools-extension-axe-panel.msft.png "Ilustración 5: la extensión aXe"  
[ImageA11yPane]: /microsoft-edge/devtools-guide-chromium/media/accessibility-elements-accessibility.msft.png "Ilustración 6: inspeccionar el elemento H1 de la Página principal de DevTools en el panel Accesibilidad"  
[ImageAllyTree]: /microsoft-edge/devtools-guide-chromium/media/accessibility-elements-accessibility-tree.msft.png "Ilustración 7: sección de árbol de accesibilidad"  
[ImageAriaAttributesSection]: /microsoft-edge/devtools-guide-chromium/media/accessibility-elements-accessibility-aria-attributes.msft.png "Ilustración 8: la sección de atributos de ARIA"  
[ImageComputedA11yPropertiesSection]: /microsoft-edge/devtools-guide-chromium/media/accessibility-elements-accessibility-computed-properties.msft.png "Ilustración 9: la sección de propiedades calculadas (accesibilidad)"  
[ImageInspectDomTree]: /microsoft-edge/devtools-guide-chromium/media/accessibility-elements-paragraph-highlight.msft.png "Ilustración 10: inspección de un párrafo en el árbol DOM"  
[ImageColorElement]: /microsoft-edge/devtools-guide-chromium/media/accessibility-elements-styles-paragraph-highlight-color.msft.png "Ilustración 11: la propiedad color del elemento"  
[ImageColorPickerContrastRatio]: /microsoft-edge/devtools-guide-chromium/media/accessibility-elements-styles-paragraph-highlight-color-picker.msft.png "Ilustración 12: la sección de relación de contraste del selector de colores muestra 2 marcas de verificación y un valor de 13,97"  
[ImageContrastRatioLine]: /microsoft-edge/devtools-guide-chromium/media/accessibility-elements-styles-paragraph-highlight-color-picker-contrast-ratio-details.msft.png "Ilustración 13: línea de proporción de contraste en el selector visual"  
<!-- links -->  

[DevtoolsAccessibilityNavigation]: navigation.md "Navegar por Microsoft Edge DevTools con tecnología de asistencia"  
[DevtoolsCssReferenceViewActuallyAppliedElements]: ../css/reference.md#view-only-the-css-that-is-actually-applied-to-an-element "Ver solo la CSS que se aplica realmente a una referencia CSS de elemento"  

[ChromeWebStoreAxe]: https://chrome.google.com/webstore/detail/axe/lhdoppojpmngadmnindnejefpokejbdd?hl=en-US "Axe-pruebas de accesibilidad web-tienda web de Chrome"  

[MDNAccessibilityTree]: https://developer.mozilla.org/docs/Glossary/AOM "Árbol de accesibilidad (AOM) | MDN"  
[MDNAccessibility]: https://developer.mozilla.org/docs/Web/Accessibility "Accesibilidad | MDN"  
[MDNScreenReader]: https://developer.mozilla.org/docs/Glossary/Screen_reader "Lector de pantalla | MDN"  

[W3CContrastEnhanced]: https://www.w3.org/WAI/WCAG21/quickref/#contrast-enhanced "Nivel de contraste (mejorado) AAA AAA | RELATIVA"  
[W3CContrastMinimum]: https://www.w3.org/WAI/WCAG21/quickref/#contrast-minimum "Contraste (mínimo) nivel AA | RELATIVA"  

> [!NOTE]
> <span data-ttu-id="811ae-245">Algunas partes de esta página son modificaciones basadas en el trabajo creado y [compartido por Google][GoogleSitePolicies] y se usan según las condiciones descritas en la [licencia internacional de Creative Commons Atribution 4,0][CCA4IL].</span><span class="sxs-lookup"><span data-stu-id="811ae-245">Portions of this page are modifications based on work created and [shared by Google][GoogleSitePolicies] and used according to terms described in the [Creative Commons Attribution 4.0 International License][CCA4IL].</span></span>  
> <span data-ttu-id="811ae-246">La página original se encuentra [aquí](https://developers.google.com/web/tools/chrome-devtools/accessibility/reference) y está modificada por [Kayce vascos][KayceBasques] \ (redactor técnico, Chrome DevTools \ & Lighthouse \).</span><span class="sxs-lookup"><span data-stu-id="811ae-246">The original page is found [here](https://developers.google.com/web/tools/chrome-devtools/accessibility/reference) and is authored by [Kayce Basques][KayceBasques] \(Technical Writer, Chrome DevTools \& Lighthouse\).</span></span>  

[![Licencia de Creative Commons][CCby4Image]][CCA4IL]  
<span data-ttu-id="811ae-248">Este trabajo dispone de licencia conforme a [Licencia internacional de Creative Commons Attribution 4.0][CCA4IL].</span><span class="sxs-lookup"><span data-stu-id="811ae-248">This work is licensed under a [Creative Commons Attribution 4.0 International License][CCA4IL].</span></span>  

[CCA4IL]: https://creativecommons.org/licenses/by/4.0  
[CCby4Image]: https://i.creativecommons.org/l/by/4.0/88x31.png  
[GoogleSitePolicies]: https://developers.google.com/terms/site-policies  
[KayceBasques]: https://developers.google.com/web/resources/contributors/kaycebasques  