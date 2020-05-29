---
title: Invalidar geolocalización con Microsoft Edge DevTools
author: MSEdgeTeam
ms.author: msedgedevrel
ms.date: 03/26/2020
ms.topic: article
ms.prod: microsoft-edge
keywords: Microsoft Edge, desarrollo web, herramientas F12, DevTools
ms.openlocfilehash: 307064bedf992e528b6d79eed3a2ade3367830d4
ms.sourcegitcommit: 531ec8aa1f89b28bc4d271e8e995f846f2392bc3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/29/2020
ms.locfileid: "10607443"
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





# <span data-ttu-id="08bbc-103">Invalidar geolocalización con Microsoft Edge DevTools</span><span class="sxs-lookup"><span data-stu-id="08bbc-103">Override Geolocation With Microsoft Edge DevTools</span></span>   



<span data-ttu-id="08bbc-104">Muchos sitios web aprovechan la ubicación del usuario para proporcionar una experiencia más relevante a los usuarios.</span><span class="sxs-lookup"><span data-stu-id="08bbc-104">Many websites take advantage of user location in order to provide a more relevant experience for the users.</span></span>  <span data-ttu-id="08bbc-105">Por ejemplo, un sitio web de Meteorología puede mostrar la previsión local en el área de un usuario, después de que el usuario haya concedido permiso al sitio web para acceder a la ubicación del usuario actual.</span><span class="sxs-lookup"><span data-stu-id="08bbc-105">For example, a weather website may show the local forecast in a user's area, after the user has granted the website permission to access the current user location.</span></span>  

<!--todo: add link to user location section when available -->  

<span data-ttu-id="08bbc-106">Si estás creando una interfaz de usuario que varía según el lugar donde se encuentre el usuario, probablemente quieras asegurarte de que el sitio se comparará correctamente en diferentes lugares de todo el mundo.</span><span class="sxs-lookup"><span data-stu-id="08bbc-106">If you are building a UI that changes depending on where the user is located, you probably want to make sure that the site behaves correctly in different places around the world.</span></span>  <span data-ttu-id="08bbc-107">Para invalidar su ubicación geográfica en Microsoft Edge DevTools:</span><span class="sxs-lookup"><span data-stu-id="08bbc-107">To override your geolocation in Microsoft Edge DevTools:</span></span>  

1.  <span data-ttu-id="08bbc-108">Pulse `Control` + `Shift` + `P` \ (Windows \) o `Command` + `Shift` + `P` \ (MacOS \) para abrir el **menú de comandos**.</span><span class="sxs-lookup"><span data-stu-id="08bbc-108">Press `Control`+`Shift`+`P` \(Windows\) or `Command`+`Shift`+`P` \(macOS\) to open the **Command Menu**.</span></span>  
    
    > ##### <span data-ttu-id="08bbc-109">Figura 1</span><span class="sxs-lookup"><span data-stu-id="08bbc-109">Figure 1</span></span>  
    > <span data-ttu-id="08bbc-110">El menú de comandos</span><span class="sxs-lookup"><span data-stu-id="08bbc-110">The Command Menu</span></span>  
    > ![El menú de comandos][ImageCommandMenu]  
    
1.  <span data-ttu-id="08bbc-112">Escriba `sensors` , seleccione **Mostrar sensores**y, a continuación, pulse `Enter` .</span><span class="sxs-lookup"><span data-stu-id="08bbc-112">Type `sensors`, select **Show Sensors**, and press `Enter`.</span></span>  <span data-ttu-id="08bbc-113">La ficha **sensores** se abre en la parte inferior de la ventana de DevTools.</span><span class="sxs-lookup"><span data-stu-id="08bbc-113">The **Sensors** tab opens at the bottom of your DevTools window.</span></span>  
1.  <span data-ttu-id="08bbc-114">En la lista **geolocation** , seleccione una de las ciudades preconfiguradas, `Tokyo` o seleccione **ubicación personalizada** para especificar las coordenadas de longitud y latitud personalizadas, o seleccione **ubicación no disponible** para ver cómo se comporta su sitio cuando la ubicación del usuario no está disponible.</span><span class="sxs-lookup"><span data-stu-id="08bbc-114">From the **Geolocation** list select one of the preset cities, like `Tokyo`, or select **Custom location** to enter custom longitude and latitude coordinates, or select **Location unavailable** to see how your site behaves when the user's location is not available.</span></span>  
    
    > ##### <span data-ttu-id="08bbc-115">Figura 2</span><span class="sxs-lookup"><span data-stu-id="08bbc-115">Figure 2</span></span>  
    > <span data-ttu-id="08bbc-116">Selección `Tokyo` de la lista de **ubicación geográfica**</span><span class="sxs-lookup"><span data-stu-id="08bbc-116">Selecting `Tokyo` from the **Geolocation** list</span></span>  
    > ![Selección de Tokyo desde la lista de geolocalización][ImageGeolocationTokyo]  
    
<!--## Feedback   

  -->  

<!-- image links -->  

[ImageCommandMenu]: /microsoft-edge/devtools-guide-chromium/media/device-mode-console-command-menu.msft.png "Ilustración 1: el menú de comandos"  
[ImageGeolocationTokyo]: /microsoft-edge/devtools-guide-chromium/media/device-mode-console-sensors-geolocation-tokyo.msft.png "Ilustración 2: selección de Tokio de la lista de ubicación geográfica"  

<!-- links -->  

<!--[WebFundamentalsNativeHardwareUserLocationIndex]: /web/fundamentals/native-hardware/user-location/index "User Location"  -->  

> [!NOTE]
> <span data-ttu-id="08bbc-120">Algunas partes de esta página son modificaciones basadas en el trabajo creado y [compartido por Google][GoogleSitePolicies] y se usan según las condiciones descritas en la [licencia internacional de Creative Commons Atribution 4,0][CCA4IL].</span><span class="sxs-lookup"><span data-stu-id="08bbc-120">Portions of this page are modifications based on work created and [shared by Google][GoogleSitePolicies] and used according to terms described in the [Creative Commons Attribution 4.0 International License][CCA4IL].</span></span>  
> <span data-ttu-id="08bbc-121">La página original se encuentra [aquí](https://developers.google.com/web/tools/chrome-devtools/device-mode/geolocation) y está modificada por [Kayce vascos][KayceBasques] \ (redactor técnico, Chrome DevTools \ & Lighthouse \).</span><span class="sxs-lookup"><span data-stu-id="08bbc-121">The original page is found [here](https://developers.google.com/web/tools/chrome-devtools/device-mode/geolocation) and is authored by [Kayce Basques][KayceBasques] \(Technical Writer, Chrome DevTools \& Lighthouse\).</span></span>  

[![Licencia de Creative Commons][CCby4Image]][CCA4IL]  
<span data-ttu-id="08bbc-123">Este trabajo dispone de licencia conforme a [Licencia internacional de Creative Commons Attribution 4.0][CCA4IL].</span><span class="sxs-lookup"><span data-stu-id="08bbc-123">This work is licensed under a [Creative Commons Attribution 4.0 International License][CCA4IL].</span></span>  

[CCA4IL]: https://creativecommons.org/licenses/by/4.0  
[CCby4Image]: https://i.creativecommons.org/l/by/4.0/88x31.png  
[GoogleSitePolicies]: https://developers.google.com/terms/site-policies  
[KayceBasques]: https://developers.google.com/web/resources/contributors/kaycebasques  