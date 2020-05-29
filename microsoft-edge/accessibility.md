---
ms.assetid: 1e5c42a7-4604-46ac-ad7b-a65390e5b36a
description: Aprenda a crear, diseñar y probar sitios web accesibles en Microsoft Edge.
title: Accesibilidad
author: MSEdgeTeam
ms.author: msedgedevrel
ms.date: 04/16/2020
ms.topic: article
ms.prod: microsoft-edge
keywords: accesibilidad, accesibilidad para desarrolladores, sitios web accesibles, Edge, desarrollo web, ARIA, desarrollador, UIA, automatización de la interfaz de usuario
ms.openlocfilehash: 6ad95e9c250aa6a4a61ca09470cea86efd715427
ms.sourcegitcommit: 9169d784485e3cb0b1987a8f395c4bb688bd9b2e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/21/2020
ms.locfileid: "10583108"
---
# <span data-ttu-id="364f1-104">Accesibilidad</span><span class="sxs-lookup"><span data-stu-id="364f1-104">Accessibility</span></span>  

> <span data-ttu-id="364f1-105">"\ [T \] el impacto de la incapacidad se modifica radicalmente en la web, ya que la web elimina las barreras de comunicación e interacción que muchas personas se enfrentan en el mundo físico."</span><span class="sxs-lookup"><span data-stu-id="364f1-105">"\[T\]he impact of disability is radically changed on the Web because the Web removes barriers to communication and interaction that many people face in the physical world."</span></span> [<span data-ttu-id="364f1-106">(Accesibilidad | RELATIVA</span><span class="sxs-lookup"><span data-stu-id="364f1-106">(Accessibility | W3C)</span></span>][W3CAccessibility]  

<span data-ttu-id="364f1-107">La [Organización Mundial][WHODisabilities] de la salud define la incapacidad como "no coincidencia en la interacción entre las características del cuerpo de una persona y las características del entorno en el que viven".</span><span class="sxs-lookup"><span data-stu-id="364f1-107">The [World Health Organization][WHODisabilities] defines disability as "a mismatch in interaction between the features of a person's body and the features of the environment in which they live".</span></span>  <span data-ttu-id="364f1-108">Las discapacidades van desde discapacidades por situaciones, como una movilidad limitada mientras mantienen un bebé o una luz solar en un teléfono, a otras deficiencias físicas, auditivas, visuales o de edad.</span><span class="sxs-lookup"><span data-stu-id="364f1-108">Disabilities range from situational disabilities, like limited mobility while holding a baby or bright sunlight on a phone, to other physical, auditory, visual, or age-related impairments.</span></span>  

<span data-ttu-id="364f1-109">El diseño de sitios web y otras tecnologías para la inclusión crea una experiencia divertida por parte de cada usuario.</span><span class="sxs-lookup"><span data-stu-id="364f1-109">Designing websites and other technologies for inclusion creates an experience enjoyable by every person.</span></span>  <span data-ttu-id="364f1-110">El diseño inclusivo y la accesibilidad web facultan y ayudan a todo el mundo a usar la Web.</span><span class="sxs-lookup"><span data-stu-id="364f1-110">Inclusive design and web accessibility empowers and assists everyone to use the web.</span></span>  

<span data-ttu-id="364f1-111">Estos son algunos procedimientos recomendados, ejemplos de código y otros recursos para obtener más información sobre cómo [diseñar][AccessibilityDesign], [crear][AccessibilityBuild]y [probar][AccessibilityTest] sitios web accesibles en Microsoft Edge.</span><span class="sxs-lookup"><span data-stu-id="364f1-111">Here are some best practices, code samples, and further resources for you to learn more about [Designing][AccessibilityDesign], [Building][AccessibilityBuild], and [Testing][AccessibilityTest] accessible websites in Microsoft Edge.</span></span>  

## <span data-ttu-id="364f1-112">Accesibilidad en Microsoft Edge</span><span class="sxs-lookup"><span data-stu-id="364f1-112">Accessibility in Microsoft Edge</span></span>  

<span data-ttu-id="364f1-113">En Microsoft Edge, hemos introducido la moderna API de automatización de la [interfaz de usuario][WindowsWin32AutoEntryui] (UIA API \).</span><span class="sxs-lookup"><span data-stu-id="364f1-113">In Microsoft Edge, we introduced modern [UI Automation API][WindowsWin32AutoEntryui] \(UIA API\).</span></span>  <span data-ttu-id="364f1-114">El cambio a UIA era una gran inversión en la accesibilidad del explorador y constituye la base para una experiencia web más inclusiva para los usuarios que dependen de la tecnología de asistencia en Windows 10.</span><span class="sxs-lookup"><span data-stu-id="364f1-114">The change to UIA was a major investment in browser accessibility, and it lays the foundation for a more inclusive web experience for users who depend on assistive technology in Windows 10.</span></span>  <span data-ttu-id="364f1-115">Los usuarios también se benefician de la naturaleza de la perenne del motor de cromo.</span><span class="sxs-lookup"><span data-stu-id="364f1-115">Users also benefit from the evergreen nature of the Chromium engine.</span></span>  

<span data-ttu-id="364f1-116">El sistema de accesibilidad de Microsoft Edge es compatible de forma inherente con los estándares web modernos, incluidos ARIA, HTML5 y CSS3.</span><span class="sxs-lookup"><span data-stu-id="364f1-116">The accessibility system in Microsoft Edge inherently supports modern web standards including ARIA, HTML5, and CSS3.</span></span>  <span data-ttu-id="364f1-117">El siguiente diagrama de la canalización de explorador simplificada sigue el contenido de las páginas web a una capa de presentación accesible.</span><span class="sxs-lookup"><span data-stu-id="364f1-117">The following diagram of the simplified browser pipeline follows webpage content into an accessible presentation layer.</span></span>  

:::image type="complex" source="./media/accessibilityarchitecture.png" alt-text="El contenido transformado en el modelo de motor se proyecta en vistas visuales y de accesibilidad que se presentan como una presentación visual o accesible.":::
   <span data-ttu-id="364f1-119">Figura 1.</span><span class="sxs-lookup"><span data-stu-id="364f1-119">Figure 1.</span></span>  <span data-ttu-id="364f1-120">El contenido transformado en el modelo de motor se proyecta en vistas visuales y de accesibilidad que se presentan como una presentación visual o accesible.</span><span class="sxs-lookup"><span data-stu-id="364f1-120">Content transformed to the engine model is projected into visual and accessibility views that are presented either as visual or accessible presentation</span></span>
:::image-end:::

<!--![Figure 1.  Content transformed to the engine model is projected into visual and accessibility views that are presented either as visual or accessible presentation][ImageAccessibilityArchitecture]  -->  

<span data-ttu-id="364f1-121">El equipo de Microsoft Edge funciona con el W3C y otros proveedores de exploradores de manera continua para garantizar que las nuevas características de plataforma web tengan la accesibilidad integrada suficiente.</span><span class="sxs-lookup"><span data-stu-id="364f1-121">The Microsoft Edge team works with the W3C and other browser vendors on an ongoing basis to ensure that new web platform features have sufficient built-in accessibility.</span></span>  

<span data-ttu-id="364f1-122">Para obtener información sobre las nuevas características de HTML5 compatibles con Microsoft Edge, visite [HTML5Accessibility][HTML5Accessibility].</span><span class="sxs-lookup"><span data-stu-id="364f1-122">For information on which new HTML5 features are accessibly supported by Microsoft Edge, visit [HTML5Accessibility][HTML5Accessibility].</span></span>  

## <span data-ttu-id="364f1-123">Recursos</span><span class="sxs-lookup"><span data-stu-id="364f1-123">Resources</span></span>  

#### <span data-ttu-id="364f1-124">Blog de automatización de la interfaz de usuario de Microsoft Windows</span><span class="sxs-lookup"><span data-stu-id="364f1-124">Microsoft Windows UI Automation Blog</span></span>  

<span data-ttu-id="364f1-125">El [blog de automatización de la interfaz de usuario de Microsoft Windows][ArchiveBlogsWinuiautomation] incluye temas relacionados con la API de automatización de Windows.</span><span class="sxs-lookup"><span data-stu-id="364f1-125">The [Microsoft Windows UI Automation blog][ArchiveBlogsWinuiautomation] covers topics related to the Windows Automation API.</span></span>  

#### <span data-ttu-id="364f1-126">Iniciativa de accesibilidad para web (WAI)</span><span class="sxs-lookup"><span data-stu-id="364f1-126">Web Accessibility Initiative (WAI)</span></span>  

<span data-ttu-id="364f1-127">La [iniciativa de accesibilidad web (WAI)][W3CWaiHome] proporcionó BT el W3C es un esfuerzo para ayudarle a mejorar la accesibilidad de la Web.</span><span class="sxs-lookup"><span data-stu-id="364f1-127">The [Web Accessibility Initiative (WAI)][W3CWaiHome] provided bt the W3C is an effort to help improve the accessibility of the web.</span></span>  <span data-ttu-id="364f1-128">El sitio proporciona una variedad de recursos para [empezar a usar la accesibilidad web][W3CWaiGettingstartedOverview], [diseñar la inclusión][W3CWaiFundamentals], [tutoriales y presentaciones][W3CWaiTeachAdvocate], entre otras.</span><span class="sxs-lookup"><span data-stu-id="364f1-128">The site provides a variety of resources for [Getting Started with Web Accessibility][W3CWaiGettingstartedOverview], [Designing for Inclusion][W3CWaiFundamentals], [tutorials and presentations][W3CWaiTeachAdvocate], and more.</span></span>  


<!-- image links -->  

<!--[ImageAccessibilityArchitecture]: ./media/accessibilityarchitecture.png "Figure 1: Content transformed to the engine model is projected into visual and accessibility views that are presented either as visual or accessible presentation"  -->  

<!-- links -->  

[AccessibilityBuild]: ./accessibility/build.md "Creación de sitios web accesibles"  
[AccessibilityDesign]: ./accessibility/design.md "Diseñar sitios web accesibles"  
[AccessibilityTest]: ./accessibility/test.md "Pruebas de accesibilidad"  

[WindowsWin32AutoEntryui]: /windows/win32/winauto/entry-uiauto-win32 "Automatización de la interfaz de usuario"  

[ArchiveBlogsWinuiautomation]: /archive/blogs/winuiautomation/ "Blog de automatización de la interfaz de usuario de Microsoft Windows"  

[HTML5Accessibility]: https://html5accessibility.com "Accesibilidad de HTML5"  

[W3CAccessibility]: https://w3.org/standards/webdesign/accessibility "Accesibilidad | RELATIVA"  
[W3CWaiFundamentals]: https://w3.org/wai/fundamentals/accessibility-intro "Introducción a la accesibilidad web | Iniciativa de accesibilidad web (WAI) | RELATIVA"  
[W3CWaiGettingstartedOverview]: https://w3.org/wai/gettingstarted/Overview "Introducción: hacer que un sitio web sea accesible | Iniciativa de accesibilidad web (WAI) | RELATIVA"  
[W3CWaiHome]: https://w3.org/wai "Iniciativa de accesibilidad web (WAI) | RELATIVA"  
[W3CWaiTeachAdvocate]: https://w3.org/wai/teach-advocate "Información general de enseñar y abogar | Iniciativa de accesibilidad web (WAI) | RELATIVA"  

[WHODisabilities]: https://who.int/topics/disabilities "Discapacidades | CON"  
