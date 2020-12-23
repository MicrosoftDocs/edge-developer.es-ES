---
ms.assetid: c4544a19-de78-4c69-a042-c0415726548f
description: Para asegurarse de que el icono de extensión esté visible mientras se encuentra en modo Light y Dark, siga la guía de accesibilidad.
title: 'Accesibilidad: extensiones (EdgeHTML)'
author: MSEdgeTeam
ms.author: msedgedevrel
ms.topic: article
ms.prod: microsoft-edge
keywords: Edge, desarrollo web, HTML, CSS, JavaScript, desarrollador
ms.date: 11/19/2020
ROBOTS: NOINDEX,NOFOLLOW
ms.openlocfilehash: e6e7dbd2ee66ac785be31eec7189b87e6a6bd91f
ms.sourcegitcommit: a35a6b5bbc21b7df61d08cbc6b074b5325ad4fef
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/17/2020
ms.locfileid: "11236534"
---
# Accesibilidad: extensiones (EdgeHTML)  

[!INCLUDE [deprecation-note](../includes/deprecation-note.md)]  

## Crear iconos de extensión accesibles para Microsoft Edge

Se recomienda a los desarrolladores de extensiones de terceros que usen recursos de imagen que cumplan con los requisitos de accesibilidad estrictos de Microsoft, de modo que los iconos estén claramente visibles para los temas Light y Dark. Recomendamos que todos los iconos de extensión tengan una relación de 14:1 entre el color de fondo del icono y el color dominante del propio icono.


Las extensiones de origen desarrolladas por Microsoft aplican un tratamiento visual "adhesivo" para cumplir con estos requisitos.

### Ejemplos de la "pegatina"

El principal objetivo de "etiquetar" es hacer que el icono sea visualmente accesible en cualquier color de fondo. La relación de color recomendada entre el trazo exterior blanco y el icono debe ser de 14:1 para admitir los requisitos de alto contraste.

#### Icono de buena
Con las pegatinas, un icono oscuro principalmente permanecerá visible en cualquier color de fondo.


![imagen del icono visible en cualquier color de fondo](./../media/accessibility-light-to-dark-good.png)

#### Icono incorrecto
Sin etiquetar, un icono se puede fusionar con el fondo y resulta imposible de ver.


![imagen de la combinación de iconos en el fondo negro](./../media/accessibility-light-to-dark-bad.png)

### Icono de extensión

Los siguientes cinco pasos describen el método sugerido para crear un icono de extensión que cumpla con los requisitos de accesibilidad de Microsoft:


| Paso 1                                       | Paso 2                                       | Paso 3                                                                                 | Paso 4                                                                          | Paso 5                                                       |
|:---------------------------------------------|:---------------------------------------------|:---------------------------------------------------------------------------------------|:--------------------------------------------------------------------------------|:-------------------------------------------------------------|
| Establezca el icono en la cuadrícula especificada.    | Reduzca el tamaño del icono en 2 píxeles.           | Copie el icono y péguelo en su sitio. Crear un trazo exterior de 2 píxeles con esquinas redondeadas. | Esquematizar el trazo, soltar el trazado compuesto y combinar las formas restantes. | Colorea el trazo exterior blanco y el icono interno como desee. |
| ![step1](./../media/accessibility-step1.png) | ![step2](./../media/accessibility-step2.png) | ![step3](./../media/accessibility-step3.png)                                           | ![step4](./../media/accessibility-step4.png)                                    | ![step5](./../media/accessibility-step5.png)                 |
