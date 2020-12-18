---
description: Obtiene el valor de `null` en el contexto de script actual.
title: Función JsGetNullValue | Microsoft docs
ms.prod: microsoft-edge
ms.topic: reference
f1_keywords:
- jsrt/JsGetNullValue
helpviewer_keywords:
- JsGetNullValue function
ms.assetid: 132a1496-8dfe-4d3c-a8f8-389f5b0b50d2
caps.latest.revision: 12
author: MSEdgeTeam
ms.author: msedgedevrel
ms.date: 11/19/2020
ROBOTS: NOINDEX,NOFOLLOW
ms.openlocfilehash: 31e1ba19f9f27e75f0166238d98390e2c4a26c24
ms.sourcegitcommit: a35a6b5bbc21b7df61d08cbc6b074b5325ad4fef
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/17/2020
ms.locfileid: "11235907"
---
# Función JsGetNullValue

Obtiene el valor de `null` en el contexto de script actual.  
  
## Sintaxis  
  
```cpp  
STDAPI_(JsErrorCode) JsGetNullValue(  
   _Out_ JsValueRef *nullValue  
);  
```  
  
#### Parámetros  
 `nullValue`  
 El `null` valor.  
  
## Valor devuelto  
 El código `JsNoError` si la operación se realizó correctamente; de lo contrario, un código de error.  
  
## Observaciones  
 Requiere un contexto de script activo.  
  
## Requisitos  
 **Encabezado:** jsrt. h  
  
## Consulta también  
 [Referencia (tiempo de ejecución de JavaScript)](../chakra-hosting/reference-javascript-runtime.md)
