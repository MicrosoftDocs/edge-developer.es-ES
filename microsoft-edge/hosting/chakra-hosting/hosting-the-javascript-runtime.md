---
description: Use el motor de JavaScript de Chakra basado en estándares para agregar capacidades de scripting a su aplicación para Windows.
title: Hospedar el Runtime de JavaScript | Microsoft docs
ms.custom: ''
ms.date: 01/15/2020
ms.prod: microsoft-edge
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 30ec744e-57cc-4ef5-8fe1-d2c27b946548
caps.latest.revision: 14
author: MSEdgeTeam
ms.author: msedgedevrel
manager: ''
ms.openlocfilehash: 9077284d96ff0d9ae22e152329efe9304081ae39
ms.sourcegitcommit: 6860234c25a8be863b7f29a54838e78e120dbb62
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/09/2020
ms.locfileid: "10573550"
---
# <span data-ttu-id="feb38-103">Hospedaje de JavaScript en tiempo de ejecución</span><span class="sxs-lookup"><span data-stu-id="feb38-103">Hosting the JavaScript Runtime</span></span>
<span data-ttu-id="feb38-104">Las API de JavaScript Runtime (JsRT) proporcionan una manera de usar aplicaciones de escritorio, de la tienda Windows y del servidor que se ejecutan en el sistema operativo Windows para agregar capacidades de scripting a la aplicación con el motor de JavaScript de Chakra basado en estándares que también usa Microsoft Edge e Internet Explorer.</span><span class="sxs-lookup"><span data-stu-id="feb38-104">The JavaScript Runtime (JsRT) APIs provide a way for desktop, Windows Store, and server-side applications running on the Windows operating system to add scripting capabilities to the application by using the standards-based Chakra JavaScript engine that is also utilized by Microsoft Edge and Internet Explorer.</span></span> <span data-ttu-id="feb38-105">Estas API están disponibles en Windows 10 y cualquier versión del sistema operativo Windows que tenga Internet Explorer versión 11,0 instalado en el equipo.</span><span class="sxs-lookup"><span data-stu-id="feb38-105">These APIs are available on Windows 10 and any version of the Windows operating system that has Internet Explorer version 11.0 installed on the machine.</span></span> <span data-ttu-id="feb38-106">Para obtener más información, consulta [referencia (tiempo de ejecución de JavaScript)](../chakra-hosting/reference-javascript-runtime.md).</span><span class="sxs-lookup"><span data-stu-id="feb38-106">For more info, see [Reference (JavaScript Runtime)](../chakra-hosting/reference-javascript-runtime.md).</span></span> <span data-ttu-id="feb38-107">Para obtener información sobre el uso de JsRT en aplicaciones de la tienda Windows, consulta [JsRT y la plataforma universal de Windows](#Windows).</span><span class="sxs-lookup"><span data-stu-id="feb38-107">For info on using the JsRT in Windows Store apps, see [JsRT and the Universal Windows Platform](#Windows).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="feb38-108">En esta documentación se supone que está trabajando general con el lenguaje JavaScript.</span><span class="sxs-lookup"><span data-stu-id="feb38-108">This documentation assumes a general working familiarity with the JavaScript language.</span></span>  
  
## <span data-ttu-id="feb38-109">Conceptos</span><span class="sxs-lookup"><span data-stu-id="feb38-109">Concepts</span></span>  
 <span data-ttu-id="feb38-110">Comprender cómo hospedar el motor de JavaScript con las API de JsRT depende de dos conceptos clave: runtimes y contextos de ejecución.</span><span class="sxs-lookup"><span data-stu-id="feb38-110">Understanding how to host the JavaScript engine using the JsRT APIs depends on two key concepts: runtimes and execution contexts.</span></span>  
  
 <span data-ttu-id="feb38-111">Un *Runtime* representa un entorno de ejecución de JavaScript completo.</span><span class="sxs-lookup"><span data-stu-id="feb38-111">A *runtime* represents a complete JavaScript execution environment.</span></span> <span data-ttu-id="feb38-112">Cada Runtime que se crea tiene su propia pila aislada de recolección de elementos no utilizados y, de forma predeterminada, su propio subproceso del compilador Just-in-Time (JIT) y subproceso de recopilación de elementos no utilizados (GC).</span><span class="sxs-lookup"><span data-stu-id="feb38-112">Each runtime that is created has its own isolated garbage collected heap and, by default, its own just-in-time (JIT) compiler thread and garbage collector (GC) thread.</span></span> <span data-ttu-id="feb38-113">Un *contexto de ejecución* representa un entorno de JavaScript que tiene su propio objeto global de JavaScript distinto del resto de contextos de ejecución.</span><span class="sxs-lookup"><span data-stu-id="feb38-113">An *execution context* represents a JavaScript environment that has its own JavaScript global object distinct from all other execution contexts.</span></span> <span data-ttu-id="feb38-114">Un tiempo de ejecución puede contener varios contextos de ejecución y, en esos casos, todos los contextos de ejecución comparten el compilador JIT y el subproceso GC asociados con el motor en tiempo de ejecución.</span><span class="sxs-lookup"><span data-stu-id="feb38-114">One runtime may contain multiple execution contexts, and in such cases, all the execution contexts share the JIT compiler and GC thread associated with the runtime.</span></span>  
  
 <span data-ttu-id="feb38-115">Los Runtime representan un único subproceso de ejecución.</span><span class="sxs-lookup"><span data-stu-id="feb38-115">Runtimes represent a single thread of execution.</span></span> <span data-ttu-id="feb38-116">Solo puede haber un Runtime activo en un subproceso determinado a la vez, y un tiempo de ejecución solo puede estar activo en un subproceso a la vez.</span><span class="sxs-lookup"><span data-stu-id="feb38-116">Only one runtime can be active on a particular thread at a time, and a runtime can only be active on one thread at a time.</span></span> <span data-ttu-id="feb38-117">Los Runtimes tienen un subproceso de alquiler, por lo que un Runtime que no está activo en ese momento en un subproceso (es decir, no se ejecuta ningún código de JavaScript o responde a las llamadas del host) se puede usar en cualquier subproceso que aún no tenga un Runtime activo en él.</span><span class="sxs-lookup"><span data-stu-id="feb38-117">Runtimes are rental threaded, so a runtime that is not currently active on a thread (i.e. isn't running any JavaScript code or responding to any calls from the host) can be used on any thread that doesn't already have an active runtime on it.</span></span>  
  
 <span data-ttu-id="feb38-118">Los contextos de ejecución están vinculados a un Runtime en particular y ejecutan código dentro de ese Runtime.</span><span class="sxs-lookup"><span data-stu-id="feb38-118">Execution contexts are tied to a particular runtime and execute code within that runtime.</span></span> <span data-ttu-id="feb38-119">A diferencia de los motores de tiempo de ejecución, los contextos de ejecución múltiple pueden activarse en un subproceso al mismo tiempo.</span><span class="sxs-lookup"><span data-stu-id="feb38-119">Unlike runtimes, multiple execution contexts can be active on a thread at the same time.</span></span> <span data-ttu-id="feb38-120">Por lo tanto, un host puede hacer una llamada en un contexto de ejecución, ese contexto de ejecución puede devolver la llamada al host y el anfitrión puede hacer una llamada en un contexto de ejecución diferente.</span><span class="sxs-lookup"><span data-stu-id="feb38-120">So a host can make a call into an execution context, that execution context can call back to the host, and the host can make a call into a different execution context.</span></span>  
  
 ![Varios contextos de ejecución](../chakra-hosting/media/js-chakra-hosting.png "JS_Chakra_Hosting")  
  
 <span data-ttu-id="feb38-122">En la práctica, a menos que un host necesite ejecutar código en entornos separados, se puede usar un solo contexto de ejecución.</span><span class="sxs-lookup"><span data-stu-id="feb38-122">In practice, unless a host needs to run code in separated environments, a single execution context can be used.</span></span> <span data-ttu-id="feb38-123">De forma similar, a menos que un host necesite ejecutar varios fragmentos de código de forma simultánea, un único tiempo de ejecución es suficiente.</span><span class="sxs-lookup"><span data-stu-id="feb38-123">Similarly, unless a host needs to run multiple pieces of code concurrently, a single runtime is sufficient.</span></span>  
  
## <span data-ttu-id="feb38-124">Administración de memoria</span><span class="sxs-lookup"><span data-stu-id="feb38-124">Memory management</span></span>  
 <span data-ttu-id="feb38-125">JavaScript es un lenguaje recolectado de elementos no usados y, por lo tanto, hay varias consideraciones que deben tenerse en cuenta al trabajar con las API de JsRT desde otro idioma.</span><span class="sxs-lookup"><span data-stu-id="feb38-125">JavaScript is a garbage collected language, and thus there are several considerations that must be kept in mind when working with the JsRT APIs from another language.</span></span>  
  
 <span data-ttu-id="feb38-126">La principal consideración es que el recolector de elementos no utilizados de JavaScript solo puede ver referencias a valores en dos lugares: el montón de su tiempo de ejecución y la pila.</span><span class="sxs-lookup"><span data-stu-id="feb38-126">The main consideration is that the JavaScript garbage collector can only see references to values in two places: its runtime's heap, and the stack.</span></span> <span data-ttu-id="feb38-127">Por lo tanto, el recolector de elementos no utilizados siempre verá una referencia a un valor de JavaScript que se almacena dentro de otro valor de JavaScript o en una variable local de la pila.</span><span class="sxs-lookup"><span data-stu-id="feb38-127">Thus, a reference to a JavaScript value that is stored inside of another JavaScript value or in a local variable on the stack will always be seen by the garbage collector.</span></span> <span data-ttu-id="feb38-128">Pero las referencias almacenadas en otras ubicaciones, como montones administradas por el host o el sistema, no se verán en el recolector de elementos no utilizados y pueden provocar una recolección prematura de valores que el host aún usa.</span><span class="sxs-lookup"><span data-stu-id="feb38-128">But references stored in other locations, such as heaps managed by the host or the system, will not be seen by the garbage collector and may result in premature collection of values that are still in use by the host.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="feb38-129">Algunos compiladores de lenguaje (como el compilador C++ de Visual Studio) optimizarán las variables locales siempre que sea posible.</span><span class="sxs-lookup"><span data-stu-id="feb38-129">Some language compilers (such as the Visual Studio C++ compiler) will optimize away local variables where possible.</span></span> <span data-ttu-id="feb38-130">Se debe tener cuidado para asegurarse de que las variables locales que hacen referencia a valores de JavaScript estén en la pila si se espera que mantengan esos valores activos.</span><span class="sxs-lookup"><span data-stu-id="feb38-130">Care must be taken to ensure that local variables that reference JavaScript values are on the stack if they are expected to keep those values alive.</span></span>  
  
 <span data-ttu-id="feb38-131">Si una referencia a un valor de JavaScript se va a almacenar en una ubicación que no es visible para el recolector de elementos no utilizados, el host debe agregar y quitar las referencias de forma manual con las API de JsRT.</span><span class="sxs-lookup"><span data-stu-id="feb38-131">If a reference to a JavaScript value will be stored in a location not visible to the garbage collector, the host must manually add and remove references using the JsRT APIs.</span></span>  
  
## <span data-ttu-id="feb38-132">Control de excepciones</span><span class="sxs-lookup"><span data-stu-id="feb38-132">Exception handling</span></span>  
 <span data-ttu-id="feb38-133">Cuando se produce una excepción de JavaScript durante la ejecución del script, el Runtime que lo contiene se coloca en un estado de excepción.</span><span class="sxs-lookup"><span data-stu-id="feb38-133">When a JavaScript exception occurs during script execution, the containing runtime is put into an exception state.</span></span> <span data-ttu-id="feb38-134">Mientras se encuentra en estado de excepción, no se puede ejecutar ningún código y todas las llamadas a través de la API generarán un error con el código de error `JsErrorInExceptionState` hasta que el host recupere y borre la excepción con la `JsGetAndClearException` API.</span><span class="sxs-lookup"><span data-stu-id="feb38-134">While in an exception state, no code can run and all API calls will fail with the error code `JsErrorInExceptionState` until the host retrieves and clears the exception using the `JsGetAndClearException` API.</span></span> <span data-ttu-id="feb38-135">Si el host devuelve una devolución de llamada de JavaScript sin borrar el motor en tiempo de ejecución de un estado de excepción, la excepción de JavaScript se volverá a iniciar tan pronto como el control vuelva al motor de JavaScript.</span><span class="sxs-lookup"><span data-stu-id="feb38-135">If the host returns from a JavaScript callback without clearing the runtime from an exception state, then the JavaScript exception will be re-thrown as soon as control passes back to the JavaScript engine.</span></span> <span data-ttu-id="feb38-136">Esto también permite que las devoluciones de llamada de hospedaje "inicien" una excepción de JavaScript al establecer el Runtime en un estado de excepción y, a continuación, devolver desde una devolución de llamada de host.</span><span class="sxs-lookup"><span data-stu-id="feb38-136">This also enables host callbacks to "throw" a JavaScript exception by setting the runtime into an exception state and then returning from a host callback.</span></span>  
  
 <span data-ttu-id="feb38-137">Un host no puede permitir que sus propias excepciones internas se propaguen a través de una devolución de llamada de host: cualquier método de devolución de llamada debe detectar todas las excepciones de host antes de devolver el control al motor en tiempo de ejecución.</span><span class="sxs-lookup"><span data-stu-id="feb38-137">A host is not allowed to let its own internal exceptions to propagate across a host callback—any callback methods must catch all host exceptions before returning control to the runtime.</span></span>  
  
## <span data-ttu-id="feb38-138">Uso de recursos en tiempo de ejecución</span><span class="sxs-lookup"><span data-stu-id="feb38-138">Runtime resource usage</span></span>  
 <span data-ttu-id="feb38-139">Las API de JsRT exponen una serie de maneras de supervisar y modificar la manera en que los Runtime usan los recursos.</span><span class="sxs-lookup"><span data-stu-id="feb38-139">The JsRT APIs expose a number of way to monitor and modify the way runtimes use resources.</span></span> <span data-ttu-id="feb38-140">Por lo general, se dividen en las siguientes categorías:</span><span class="sxs-lookup"><span data-stu-id="feb38-140">They generally break down into the following categories:</span></span>  
  
-   <span data-ttu-id="feb38-141">**Uso de subprocesos**.</span><span class="sxs-lookup"><span data-stu-id="feb38-141">**Thread Usage**.</span></span> <span data-ttu-id="feb38-142">De forma predeterminada, cada Runtime creará un subproceso de compilador JIT dedicado y un subproceso GC dedicado que prestan servicio a ese motor en tiempo de ejecución.</span><span class="sxs-lookup"><span data-stu-id="feb38-142">By default, each runtime will create a dedicated JIT compiler thread and a dedicated GC thread that service that runtime.</span></span> <span data-ttu-id="feb38-143">Si se crea un Runtime con la `JsRuntimeAttributeDisableBackgroundWork` marca, el trabajo JIT y el GC se realizará en el propio subproceso en tiempo de ejecución en lugar de subprocesos de fondo independientes para cada uno de ellos.</span><span class="sxs-lookup"><span data-stu-id="feb38-143">If a runtime is created with the `JsRuntimeAttributeDisableBackgroundWork` flag, then the JIT and GC work will be performed on the runtime thread itself instead of separate background threads for each one of them.</span></span> <span data-ttu-id="feb38-144">Un host puede proporcionar también una devolución de llamada del servicio de subprocesos a la `JsCreateRuntime` llamada, lo que permitirá al host programar el trabajo JIT y el catálogo global de la manera más adecuada.</span><span class="sxs-lookup"><span data-stu-id="feb38-144">A host can also supply a thread service callback to the `JsCreateRuntime` call, which will allow the host to schedule JIT and GC work in any way it sees fit.</span></span>  
  
-   <span data-ttu-id="feb38-145">**Uso**de la memoria.</span><span class="sxs-lookup"><span data-stu-id="feb38-145">**Memory Usage**.</span></span> <span data-ttu-id="feb38-146">Hay varias maneras de supervisar y modificar el uso de memoria de un motor en tiempo de ejecución.</span><span class="sxs-lookup"><span data-stu-id="feb38-146">There are several ways to monitor and modify the memory usage of a runtime.</span></span> <span data-ttu-id="feb38-147">Si el tiempo de ejecución se va a ejecutar durante mucho tiempo, el host puede especificar la `JsRuntimeAttributeEnableIdleProcessing` marca al crear el Runtime y, después, llamar `JsIdle` cuando el host se encuentra en estado de inactividad.</span><span class="sxs-lookup"><span data-stu-id="feb38-147">If the runtime will be running for a long time, the host can specify the `JsRuntimeAttributeEnableIdleProcessing` flag when creating the runtime and then call `JsIdle` when the host is in an idle state.</span></span> <span data-ttu-id="feb38-148">Esto permite que el motor postergue la limpieza de la memoria y el trabajo de contabilidad hasta el tiempo de inactividad.</span><span class="sxs-lookup"><span data-stu-id="feb38-148">This allows the engine to defer some memory cleanup and bookkeeping work until idle time.</span></span>  
  
     <span data-ttu-id="feb38-149">El host puede supervisar las recolecciones de elementos no utilizados llamando a `JsSetRuntimeBeforeCollectCallback` .</span><span class="sxs-lookup"><span data-stu-id="feb38-149">The host can monitor garbage collections by calling `JsSetRuntimeBeforeCollectCallback`.</span></span> <span data-ttu-id="feb38-150">También puede supervisar las asignaciones realizadas por el montón llamando a `JsSetRuntimeMemoryAllocationCallback` .</span><span class="sxs-lookup"><span data-stu-id="feb38-150">It can also monitor allocations made by the heap by calling `JsSetRuntimeMemoryAllocationCallback`.</span></span> <span data-ttu-id="feb38-151">Ten en cuenta que esta API no vuelve a llamar en todas las asignaciones de JavaScript, solo cuando el montón del Runtime necesita más espacio del que asignar.</span><span class="sxs-lookup"><span data-stu-id="feb38-151">Note that this API does not call back on every JavaScript allocation, just when the runtime's heap needs more space from which to allocate.</span></span> <span data-ttu-id="feb38-152">La devolución de llamada de asignación de memoria puede denegar la solicitud, lo que desencadenará una recolección de elementos no utilizados y, si no hay memoria disponible, se producirá un error de memoria insuficiente en el tiempo de ejecución.</span><span class="sxs-lookup"><span data-stu-id="feb38-152">The memory allocation callback is allowed to deny the request, which will trigger a garbage collection and, if no memory is available, an out of memory error in the runtime.</span></span>  
  
     <span data-ttu-id="feb38-153">El anfitrión también puede llamar `JsSetRuntimeMemoryLimit` para establecer un límite para la cantidad de memoria que puede usar un tiempo de ejecución.</span><span class="sxs-lookup"><span data-stu-id="feb38-153">The host can also call `JsSetRuntimeMemoryLimit` to set a limit for how much memory a runtime can use.</span></span> <span data-ttu-id="feb38-154">Cuando un tiempo de ejecución alcanza un límite, desencadena una recolección de elementos no utilizados y, si no hay memoria disponible, el motor en tiempo de ejecución generará un error de memoria insuficiente.</span><span class="sxs-lookup"><span data-stu-id="feb38-154">When a runtime hits a limit, it will trigger a garbage collection and, if no memory is available, an out of memory error will be thrown by the runtime.</span></span>  
  
-   <span data-ttu-id="feb38-155">**Interrupción y evaluación de la secuencia de comandos**.</span><span class="sxs-lookup"><span data-stu-id="feb38-155">**Script Interruption and Evaluation**.</span></span> <span data-ttu-id="feb38-156">El anfitrión puede llamar `JsDisableRuntimeExecution` para finalizar la ejecución en un tiempo de ejecución.</span><span class="sxs-lookup"><span data-stu-id="feb38-156">The host can call `JsDisableRuntimeExecution` to terminate execution within a runtime.</span></span> <span data-ttu-id="feb38-157">Esta llamada se puede realizar en cualquier momento y desde cualquier conversación.</span><span class="sxs-lookup"><span data-stu-id="feb38-157">This call can be made at any time and from any thread.</span></span> <span data-ttu-id="feb38-158">Debido a que la terminación del script depende de alcanzar puntos de protección insertados en el código, es posible que un script no finalice en el momento exacto, pero lo hará muy pronto.</span><span class="sxs-lookup"><span data-stu-id="feb38-158">Because script termination depends on reaching guard points inserted into the code, a script may not terminate at the exact moment, but will do so very shortly afterwards.</span></span> <span data-ttu-id="feb38-159">De forma predeterminada, los puntos de protección de terminación se colocan con cautela en el código generado y es posible que no cubran todas las situaciones, como un bucle infinito.</span><span class="sxs-lookup"><span data-stu-id="feb38-159">By default, termination guard points are placed in the generated code conservatively and may not cover every situation, such as an infinite loop.</span></span> <span data-ttu-id="feb38-160">Crear el motor en tiempo de ejecución con la `JsRuntimeAttributeAllowScriptInterrupt` marca hace que el motor en tiempo de ejecución Inserte comprobaciones adicionales para los bucles infinitos, a menudo a costa de una pequeña sobrecarga de rendimiento.</span><span class="sxs-lookup"><span data-stu-id="feb38-160">Creating the runtime with the `JsRuntimeAttributeAllowScriptInterrupt` flag causes the runtime to insert additional checks for infinite loops, often at the cost of a small performance overhead.</span></span>  
  
     <span data-ttu-id="feb38-161">Si un host desea impedir la generación de código nativo mediante el compilador JIT, puede especificar la `JsRuntimeAttributeDisableNativeCodeGeneration` marca.</span><span class="sxs-lookup"><span data-stu-id="feb38-161">If a host wishes to disallow generation of native code by the JIT compiler, it can specify the `JsRuntimeAttributeDisableNativeCodeGeneration` flag.</span></span> <span data-ttu-id="feb38-162">Un host también puede impedir que se ejecuten los scripts de forma dinámica al especificar la `JsRuntimeAttributeDisableEval` marca.</span><span class="sxs-lookup"><span data-stu-id="feb38-162">A host can also disallow scripts from dynamically running scripts itself by specifying the `JsRuntimeAttributeDisableEval` flag.</span></span>  
  
## <span data-ttu-id="feb38-163">Depuración y generación de perfiles</span><span class="sxs-lookup"><span data-stu-id="feb38-163">Debugging and Profiling</span></span>  
 <span data-ttu-id="feb38-164">Las API de JsRT admiten la depuración y la generación de perfiles mediante la tecnología Active Scripting.</span><span class="sxs-lookup"><span data-stu-id="feb38-164">JsRT APIs supports debugging and profiling via the Active Scripting technology.</span></span>  
  
 <span data-ttu-id="feb38-165">A partir de Windows 10, el motor de JavaScript de Chakra es compatible con el motor heredado de Internet Explorer (MSHTML) y el nuevo motor de Microsoft Edge (EdgeHTML) y puede dirigirse en JsRT (vea [dirigirse a Microsoft Edge frente a motores heredados](../chakra-hosting/targeting-edge-vs-legacy-engines-in-jsrt-apis.md) para obtener más información).</span><span class="sxs-lookup"><span data-stu-id="feb38-165">Starting in Windows 10, the Chakra JavaScript Engine supports the legacy Internet Explorer (MSHTML) engine and new Microsoft Edge (EdgeHTML) engine, and you can target either in JsRT (see [Targeting Microsoft Edge vs. Legacy Engines](../chakra-hosting/targeting-edge-vs-legacy-engines-in-jsrt-apis.md) for details).</span></span> <span data-ttu-id="feb38-166">La depuración de un script en Visual Studio funciona de manera diferente entre el motor heredado y el motor de Microsoft Edge.</span><span class="sxs-lookup"><span data-stu-id="feb38-166">Debugging a script in Visual Studio works differently between the legacy engine and Microsoft Edge engine.</span></span> <span data-ttu-id="feb38-167">Con el motor heredado, el hospedador debe proporcionar un puntero de [interfaz IDebugApplication](/scripting/winscript/reference/idebugapplication-interface) , que se puede obtener desde una instancia de la [interfaz IProcessDebugManager](/scripting/winscript/reference/iprocessdebugmanager-interface) .</span><span class="sxs-lookup"><span data-stu-id="feb38-167">With the legacy engine, the host needs to provide an [IDebugApplication Interface](/scripting/winscript/reference/idebugapplication-interface) pointer, which can be obtained from an [IProcessDebugManager Interface](/scripting/winscript/reference/iprocessdebugmanager-interface) instance.</span></span> <span data-ttu-id="feb38-168">Con el motor Microsoft Edge, `IDebugApplication` está obsoleto y el motor de Chakra habilita las capacidades de depuración nativa y de script a través del depurador de Visual Studio sin requerir una implementación del `IDebugApplication` usuario.</span><span class="sxs-lookup"><span data-stu-id="feb38-168">With the Microsoft Edge engine, `IDebugApplication` is deprecated, and the Chakra engine enables native and script debugging capabilities through the Visual Studio debugger without requiring an implementation of `IDebugApplication` from the user.</span></span>  
  
 <span data-ttu-id="feb38-169">Para que los scripts en un contexto de ejecución se depuren, el motor de Chakra debe cambiar al uso de métodos de ejecución de código menos eficientes.</span><span class="sxs-lookup"><span data-stu-id="feb38-169">To make scripts in an execution context debuggable, the Chakra engine has to switch to using less efficient code execution methods.</span></span> <span data-ttu-id="feb38-170">Por lo tanto, el código depurable se ejecuta más lentamente que el código no depurable.</span><span class="sxs-lookup"><span data-stu-id="feb38-170">As such, debuggable code typically runs slower than non-debuggable code.</span></span> <span data-ttu-id="feb38-171">Como resultado, con el motor heredado, un host puede elegir iniciar la depuración en un contexto de ejecución desde el principio proporcionando el `IDebugApplication` puntero hacia arriba `JsCreateContext` o puede esperar hasta que se necesite la depuración y, a continuación, llamar `JsStartDebugging` .</span><span class="sxs-lookup"><span data-stu-id="feb38-171">As a result, with the legacy engine, a host can choose to either start debugging in an execution context from the beginning by providing the `IDebugApplication` pointer up front through `JsCreateContext`, or it can wait until debugging is needed and then call `JsStartDebugging`.</span></span> <span data-ttu-id="feb38-172">Con el motor de Microsoft Edge, `JsCreateContext` ya no se usa un `IDebugApplication` parámetro y, como resultado, solo se podrá depurar el script después de la `JsStartDebugging` llamada.</span><span class="sxs-lookup"><span data-stu-id="feb38-172">With the Microsoft Edge engine, `JsCreateContext` no longer takes an `IDebugApplication` parameter, and as a result the script is debuggable only after `JsStartDebugging` is called.</span></span> <span data-ttu-id="feb38-173">Al depurar con Visual Studio, la opción de depurador "script" debe estar habilitada.</span><span class="sxs-lookup"><span data-stu-id="feb38-173">When debugging using Visual Studio, the "Script" debugger option must be enabled.</span></span>  
  
 <span data-ttu-id="feb38-174">El código de JavaScript en un contexto de ejecución se puede mostrar de una de dos maneras.</span><span class="sxs-lookup"><span data-stu-id="feb38-174">The JavaScript code in an execution context can be profiled in one of two ways.</span></span> <span data-ttu-id="feb38-175">El generador de perfiles de la línea de comandos de Visual Studio (VSPerf. exe) se puede usar en Windows 8,1 y versiones posteriores con el modificador/JS para generar un informe destinado al código de JavaScript que se ejecuta en la aplicación.</span><span class="sxs-lookup"><span data-stu-id="feb38-175">The command line Visual Studio Profiler (vsperf.exe) can be used in Windows 8.1 and later versions with the /js switch to produce a report that targets the JavaScript code run in the application.</span></span> <span data-ttu-id="feb38-176">O bien, el anfitrión puede llamar directamente `JsStartProfiling` y `JsStopProfiling` proporcionar una devolución de llamada para realizar la generación de perfiles.</span><span class="sxs-lookup"><span data-stu-id="feb38-176">Or the host can directly call `JsStartProfiling` and `JsStopProfiling` and provide a callback to do profiling itself.</span></span> <span data-ttu-id="feb38-177">El host también puede examinar el estado de la pila de recolección de elementos no utilizados mediante una llamada `JsEnumerateHeap` .</span><span class="sxs-lookup"><span data-stu-id="feb38-177">The host can also examine the state of the garbage collected heap by calling `JsEnumerateHeap`.</span></span> <span data-ttu-id="feb38-178">La generación de perfiles en JsRT funciona de la misma manera entre el motor heredado y el motor Microsoft Edge.</span><span class="sxs-lookup"><span data-stu-id="feb38-178">Profiling in JsRT works in the same manner between the legacy and the Microsoft Edge engine.</span></span> <span data-ttu-id="feb38-179">Sin embargo, las API de generación `JsStartProfiling` de perfiles de JsRT (,, `JsStopProfiling` `JsEnumerateHeap` , y `JsIsEnumeratingHeap` ) no están disponibles para las aplicaciones universales de Windows.</span><span class="sxs-lookup"><span data-stu-id="feb38-179">However, JsRT profiling APIs (`JsStartProfiling`, `JsStopProfiling`, `JsEnumerateHeap`, and `JsIsEnumeratingHeap`) are not available for Universal Windows Apps.</span></span>  
  
<a name="Windows"></a>   
## <span data-ttu-id="feb38-180">JsRT y la plataforma universal de Windows</span><span class="sxs-lookup"><span data-stu-id="feb38-180">JsRT and the Universal Windows Platform</span></span>  

<span data-ttu-id="feb38-181">Puedes usar las API de JsRT para agregar capacidades de scripting a una aplicación universal de Windows.</span><span class="sxs-lookup"><span data-stu-id="feb38-181">You can use JsRT APIs to add scripting capabilities to a Universal Windows app.</span></span> <span data-ttu-id="feb38-182">Una aplicación universal de Windows que use las API de JsRT necesitará dirigirse a las API de Microsoft Edge JSRT, que a su vez tienen como destino el motor de Chakra perimetral.</span><span class="sxs-lookup"><span data-stu-id="feb38-182">A Universal Windows app that uses the JsRT APIs will need to target the Microsoft Edge JSRT APIs, which in turn target the Edge Chakra engine.</span></span> <span data-ttu-id="feb38-183">Para obtener más información, consulta [apuntar a Microsoft Edge frente a motores heredados](../chakra-hosting/targeting-edge-vs-legacy-engines-in-jsrt-apis.md).</span><span class="sxs-lookup"><span data-stu-id="feb38-183">For more information, see [Targeting Microsoft Edge vs. Legacy Engines](../chakra-hosting/targeting-edge-vs-legacy-engines-in-jsrt-apis.md).</span></span> <span data-ttu-id="feb38-184">La API completa de JsRT está disponible para las aplicaciones universales de Windows, excepto para la generación de perfiles y la compatibilidad de la enumeración de montones ( `JsStartProfiling` ,, `JsStopProfiling` `JsEnumerateHeap` y `JsIsEnumeratingHeap` no son compatibles).</span><span class="sxs-lookup"><span data-stu-id="feb38-184">The complete JsRT API is available for Universal Windows apps, except for profiling and heap enumeration support (`JsStartProfiling`, `JsStopProfiling`, `JsEnumerateHeap`, and `JsIsEnumeratingHeap` are not supported).</span></span>  
  
<span data-ttu-id="feb38-185">JsRT también permite que los scripts accedan de forma nativa a cualquier API de la [plataforma universal de Windows (UWP)](https://msdn.microsoft.com/library/windows/apps/br211377.aspx) después de exponer el espacio de nombres de la API a través de la API de Microsoft Edge JsRT `JsProjectWinRTNamespace` .</span><span class="sxs-lookup"><span data-stu-id="feb38-185">JsRT also allows scripts to natively access any [Universal Windows Platform (UWP) APIs](https://msdn.microsoft.com/library/windows/apps/br211377.aspx) after exposing the API namespace through Microsoft Edge JsRT API `JsProjectWinRTNamespace`.</span></span> <span data-ttu-id="feb38-186">Aunque las aplicaciones universales para Windows no necesitan ninguna configuración, además de proyectar espacios de nombres necesarios, en una aplicación de Windows clásica (Win32), debe habilitarse un mecanismo de bombeo delegado inicializado por COM `JsSetProjectionEnqueueCallback` para habilitar eventos y API asincrónicas.</span><span class="sxs-lookup"><span data-stu-id="feb38-186">While Universal Windows Applications require no setup in addition to projecting necessary namespaces, in a Classic (Win32) Windows Application, a COM-initialized delegated pumping mechanism needs to be enabled through `JsSetProjectionEnqueueCallback` to enable events and asynchronous APIs.</span></span> <span data-ttu-id="feb38-187">En el siguiente ejemplo de Win32 se usan las API asincrónicas de UWP para crear un cliente http y obtener el contenido de un URI:</span><span class="sxs-lookup"><span data-stu-id="feb38-187">The following Win32 sample utilizes asynchronous UWP APIs to create an http client to get content from a Uri:</span></span>  
  
```cpp  
typedef struct _jsCall {  
    JsProjectionCallback jsCallback;  
    JsProjectionCallbackContext jsContext;  
    HANDLE event;  
} jsCall;  
  
// Set up delegated pumping mechanism; not necessary in UWP applications.  
jsCall outstandingCall = {};  
CoInitializeEx(nullptr, COINIT_MULTITHREADED);  
JsSetProjectionEnqueueCallback([](JsProjectionCallback jsCallback,   
JsProjectionCallbackContext jsContext, void *callbackState) {  
    jsCall* call = (jsCall*)callbackState;  
    call->jsCallback = jsCallback;  
    call->jsContext = jsContext;  
    SetEvent(call->event);  
    },  
&outstandingCall);  
HANDLE event = CreateEventEx(NULL, NULL, CREATE_EVENT_MANUAL_RESET, EVENT_ALL_ACCESS);  
outstandingCall.event = event;  
  
// Project necessary namespaces.  
JsProjectWinRTNamespace(L"Windows.Foundation");  
JsProjectWinRTNamespace(L"Windows.Web");  
  
// Get content from an Uri.  
JsRunScript(L"var uri = new Windows.Foundation.Uri(\"http://somedatasource.com\"); " \  
    L"var httpClient = new Windows.Web.Http.HttpClient();" \  
    L"httpClient.getStringAsync(uri).done(function (content) { " \  
    L"    // do something with the string content " \    
    L"}, onError); " \  
    L"function onError(reason) { " \  
    L"    // error handling " \        
    L"}",   
    currentSourceContext, L"", &result);  
  
// Wait for async call to come in and then execute; not necessary in UWP applications.  
WaitForSingleObjectEx(outstandingCall.event, 10000, FALSE) == WAIT_OBJECT_0;  
outstandingCall.jsCallback(outstandingCall.jsContext);  
  
```  
  
## <span data-ttu-id="feb38-188">Consulta también</span><span class="sxs-lookup"><span data-stu-id="feb38-188">See Also</span></span>  
 [<span data-ttu-id="feb38-189">Aplicación de ejemplo en tiempo de ejecución de JavaScript</span><span class="sxs-lookup"><span data-stu-id="feb38-189">JavaScript Runtime Sample App</span></span>](https://go.microsoft.com/fwlink/p/?LinkID=306674&clcid=0x409)   
 [<span data-ttu-id="feb38-190">Referencia (tiempo de ejecución de JavaScript)</span><span class="sxs-lookup"><span data-stu-id="feb38-190">Reference (JavaScript Runtime)</span></span>](../chakra-hosting/reference-javascript-runtime.md)   
 [<span data-ttu-id="feb38-191">Hospedaje en tiempo de ejecución de JavaScript</span><span class="sxs-lookup"><span data-stu-id="feb38-191">JavaScript Runtime Hosting</span></span>](../javascript-runtime-hosting.md)  
 