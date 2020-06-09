---
description: Hospedar contenido web en la aplicación Win32 con el control Microsoft Edge WebView2
title: Microsoft Edge WebView2 para aplicaciones Win32
author: MSEdgeTeam
ms.author: msedgedevrel
ms.date: 06/05/2020
ms.topic: reference
ms.prod: microsoft-edge
ms.technology: webview
keywords: IWebView2, IWebView2WebView, webview2, WebView, aplicaciones Win32, Win32, Edge, ICoreWebView2, ICoreWebView2Controller, control de explorador, HTML Edge
ms.openlocfilehash: 7072a25636efb638fcb42c593aa6cc77e990965a
ms.sourcegitcommit: 8dca1c1367853e45a0a975bc89b1818adb117bd4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/08/2020
ms.locfileid: "10699393"
---
# <span data-ttu-id="e7032-104">interfaz ICoreWebView2WebResourceResponse</span><span class="sxs-lookup"><span data-stu-id="e7032-104">interface ICoreWebView2WebResourceResponse</span></span> 

```
interface ICoreWebView2WebResourceResponse
  : public IUnknown
```

<span data-ttu-id="e7032-105">Una respuesta HTTP usada con el evento WebResourceRequested.</span><span class="sxs-lookup"><span data-stu-id="e7032-105">An HTTP response used with the WebResourceRequested event.</span></span>

## <span data-ttu-id="e7032-106">Resumen</span><span class="sxs-lookup"><span data-stu-id="e7032-106">Summary</span></span>

 <span data-ttu-id="e7032-107">Miembros</span><span class="sxs-lookup"><span data-stu-id="e7032-107">Members</span></span>                        | <span data-ttu-id="e7032-108">Descripciones</span><span class="sxs-lookup"><span data-stu-id="e7032-108">Descriptions</span></span>
--------------------------------|---------------------------------------------
[<span data-ttu-id="e7032-109">get_Content</span><span class="sxs-lookup"><span data-stu-id="e7032-109">get_Content</span></span>](#get_content) | <span data-ttu-id="e7032-110">Contenido de la respuesta HTTP como una secuencia.</span><span class="sxs-lookup"><span data-stu-id="e7032-110">HTTP response content as stream.</span></span>
[<span data-ttu-id="e7032-111">get_Headers</span><span class="sxs-lookup"><span data-stu-id="e7032-111">get_Headers</span></span>](#get_headers) | <span data-ttu-id="e7032-112">Encabezados de respuesta HTTP invalidados.</span><span class="sxs-lookup"><span data-stu-id="e7032-112">Overridden HTTP response headers.</span></span>
[<span data-ttu-id="e7032-113">get_ReasonPhrase</span><span class="sxs-lookup"><span data-stu-id="e7032-113">get_ReasonPhrase</span></span>](#get_reasonphrase) | <span data-ttu-id="e7032-114">La frase de razón de respuesta HTTP.</span><span class="sxs-lookup"><span data-stu-id="e7032-114">The HTTP response reason phrase.</span></span>
[<span data-ttu-id="e7032-115">get_StatusCode</span><span class="sxs-lookup"><span data-stu-id="e7032-115">get_StatusCode</span></span>](#get_statuscode) | <span data-ttu-id="e7032-116">El código de estado de respuesta HTTP.</span><span class="sxs-lookup"><span data-stu-id="e7032-116">The HTTP response status code.</span></span>
[<span data-ttu-id="e7032-117">put_Content</span><span class="sxs-lookup"><span data-stu-id="e7032-117">put_Content</span></span>](#put_content) | <span data-ttu-id="e7032-118">Establezca la propiedad de contenido.</span><span class="sxs-lookup"><span data-stu-id="e7032-118">Set the Content property.</span></span>
[<span data-ttu-id="e7032-119">put_ReasonPhrase</span><span class="sxs-lookup"><span data-stu-id="e7032-119">put_ReasonPhrase</span></span>](#put_reasonphrase) | <span data-ttu-id="e7032-120">Establezca la propiedad ReasonPhrase.</span><span class="sxs-lookup"><span data-stu-id="e7032-120">Set the ReasonPhrase property.</span></span>
[<span data-ttu-id="e7032-121">put_StatusCode</span><span class="sxs-lookup"><span data-stu-id="e7032-121">put_StatusCode</span></span>](#put_statuscode) | <span data-ttu-id="e7032-122">Establezca la propiedad StatusCode.</span><span class="sxs-lookup"><span data-stu-id="e7032-122">Set the StatusCode property.</span></span>

## <span data-ttu-id="e7032-123">Miembros</span><span class="sxs-lookup"><span data-stu-id="e7032-123">Members</span></span>

#### <span data-ttu-id="e7032-124">get_Content</span><span class="sxs-lookup"><span data-stu-id="e7032-124">get_Content</span></span> 

<span data-ttu-id="e7032-125">Contenido de la respuesta HTTP como una secuencia.</span><span class="sxs-lookup"><span data-stu-id="e7032-125">HTTP response content as stream.</span></span>

> <span data-ttu-id="e7032-126">[get_Content](#get_content)(HRESULT) público (contenido de IStream \* \*)</span><span class="sxs-lookup"><span data-stu-id="e7032-126">public HRESULT [get_Content](#get_content)(IStream \*\* content)</span></span>

<span data-ttu-id="e7032-127">La secuencia debe tener todos los datos de contenido disponibles por el momento en que se completa este aplazamiento de eventos de WebResourceRequested de respuesta.</span><span class="sxs-lookup"><span data-stu-id="e7032-127">Stream must have all the content data available by the time this response's WebResourceRequested event deferral is completed.</span></span> <span data-ttu-id="e7032-128">La secuencia debe ser ágil o crearse a partir de un subproceso en segundo plano para evitar el impacto en el rendimiento del subproceso de interfaz de usuario.</span><span class="sxs-lookup"><span data-stu-id="e7032-128">Stream should be agile or be created from a background thread to prevent performance impact to the UI thread.</span></span> <span data-ttu-id="e7032-129">Null significa que no hay datos de contenido.</span><span class="sxs-lookup"><span data-stu-id="e7032-129">Null means no content data.</span></span> <span data-ttu-id="e7032-130">Se aplican las semánticas de IStream (Return S_OK para leer las llamadas hasta que se agoten todos los datos)</span><span class="sxs-lookup"><span data-stu-id="e7032-130">IStream semantics apply (return S_OK to Read calls until all data is exhausted)</span></span>

#### <span data-ttu-id="e7032-131">get_Headers</span><span class="sxs-lookup"><span data-stu-id="e7032-131">get_Headers</span></span> 

<span data-ttu-id="e7032-132">Encabezados de respuesta HTTP invalidados.</span><span class="sxs-lookup"><span data-stu-id="e7032-132">Overridden HTTP response headers.</span></span>

> <span data-ttu-id="e7032-133">[get_Headers](#get_headers)de HRESULT público (encabezados[ICoreWebView2HttpResponseHeaders](icorewebview2httpresponseheaders.md) \* \*)</span><span class="sxs-lookup"><span data-stu-id="e7032-133">public HRESULT [get_Headers](#get_headers)([ICoreWebView2HttpResponseHeaders](icorewebview2httpresponseheaders.md) \*\* headers)</span></span>

#### <span data-ttu-id="e7032-134">get_ReasonPhrase</span><span class="sxs-lookup"><span data-stu-id="e7032-134">get_ReasonPhrase</span></span> 

<span data-ttu-id="e7032-135">La frase de razón de respuesta HTTP.</span><span class="sxs-lookup"><span data-stu-id="e7032-135">The HTTP response reason phrase.</span></span>

> <span data-ttu-id="e7032-136">[get_ReasonPhrase](#get_reasonphrase)de HRESULT público (LPWStr \* ReasonPhrase)</span><span class="sxs-lookup"><span data-stu-id="e7032-136">public HRESULT [get_ReasonPhrase](#get_reasonphrase)(LPWSTR \* reasonPhrase)</span></span>

#### <span data-ttu-id="e7032-137">get_StatusCode</span><span class="sxs-lookup"><span data-stu-id="e7032-137">get_StatusCode</span></span> 

<span data-ttu-id="e7032-138">El código de estado de respuesta HTTP.</span><span class="sxs-lookup"><span data-stu-id="e7032-138">The HTTP response status code.</span></span>

> <span data-ttu-id="e7032-139">[get_StatusCode](#get_statuscode)de HRESULT público (int \* StatusCode)</span><span class="sxs-lookup"><span data-stu-id="e7032-139">public HRESULT [get_StatusCode](#get_statuscode)(int \* statusCode)</span></span>

#### <span data-ttu-id="e7032-140">put_Content</span><span class="sxs-lookup"><span data-stu-id="e7032-140">put_Content</span></span> 

<span data-ttu-id="e7032-141">Establezca la propiedad de contenido.</span><span class="sxs-lookup"><span data-stu-id="e7032-141">Set the Content property.</span></span>

> <span data-ttu-id="e7032-142">[put_Content](#put_content)(HRESULT) público (contenido de IStream \*)</span><span class="sxs-lookup"><span data-stu-id="e7032-142">public HRESULT [put_Content](#put_content)(IStream \* content)</span></span>

#### <span data-ttu-id="e7032-143">put_ReasonPhrase</span><span class="sxs-lookup"><span data-stu-id="e7032-143">put_ReasonPhrase</span></span> 

<span data-ttu-id="e7032-144">Establezca la propiedad ReasonPhrase.</span><span class="sxs-lookup"><span data-stu-id="e7032-144">Set the ReasonPhrase property.</span></span>

> <span data-ttu-id="e7032-145">[put_ReasonPhrase](#put_reasonphrase)pública HRESULT (LPCWSTR ReasonPhrase)</span><span class="sxs-lookup"><span data-stu-id="e7032-145">public HRESULT [put_ReasonPhrase](#put_reasonphrase)(LPCWSTR reasonPhrase)</span></span>

#### <span data-ttu-id="e7032-146">put_StatusCode</span><span class="sxs-lookup"><span data-stu-id="e7032-146">put_StatusCode</span></span> 

<span data-ttu-id="e7032-147">Establezca la propiedad StatusCode.</span><span class="sxs-lookup"><span data-stu-id="e7032-147">Set the StatusCode property.</span></span>

> <span data-ttu-id="e7032-148">[put_StatusCode](#put_statuscode)de HRESULT público (int StatusCode)</span><span class="sxs-lookup"><span data-stu-id="e7032-148">public HRESULT [put_StatusCode](#put_statuscode)(int statusCode)</span></span>
