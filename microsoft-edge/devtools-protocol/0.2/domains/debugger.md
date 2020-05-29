---
description: Referencia del dominio de depuración. El dominio del depurador expone capacidades de depuración de JavaScript. Permite establecer y quitar puntos de interrupción, avanzar por la ejecución, explorar los seguimientos de la pila, etc.
title: Dominio de depuración-DevTools Protocol versión 0,2
author: pelavall
ms.author: pelavall
ms.date: 03/05/2020
ms.topic: reference
ms.prod: microsoft-edge
ms.custom: seodec18
ms.openlocfilehash: de967b0e067bf43ea07f8975eac7ee7c5a4dfd83
ms.sourcegitcommit: 6860234c25a8be863b7f29a54838e78e120dbb62
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/09/2020
ms.locfileid: "10573745"
---
# <span data-ttu-id="4edb7-105">Depurador</span><span class="sxs-lookup"><span data-stu-id="4edb7-105">Debugger</span></span>
<span data-ttu-id="4edb7-106">El dominio del depurador expone capacidades de depuración de JavaScript.</span><span class="sxs-lookup"><span data-stu-id="4edb7-106">Debugger domain exposes JavaScript debugging capabilities.</span></span> <span data-ttu-id="4edb7-107">Permite establecer y quitar puntos de interrupción, avanzar por la ejecución, explorar los seguimientos de la pila, etc.</span><span class="sxs-lookup"><span data-stu-id="4edb7-107">It allows setting and removing breakpoints, stepping through execution, exploring stack traces, etc.</span></span>

| | |
|-|-|
| [**<span data-ttu-id="4edb7-108">Métodos</span><span class="sxs-lookup"><span data-stu-id="4edb7-108">Methods</span></span>**](#methods) | <span data-ttu-id="4edb7-109">[enable](#enable), [Disable](#disable), [getPossibleBreakpoints](#getpossiblebreakpoints), [setBreakpointsActive](#setbreakpointsactive), [setBreakpointByUrl](#setbreakpointbyurl), [setBreakpoint](#setbreakpoint), [removeBreakpoint](#removebreakpoint), [ancho](#stepover) [de es, stepInto](#stepinto) [, stepOut](#stepout), [PAUSE](#pause), [resume](#resume) [, getScriptSource, setPauseOnExceptions](#getscriptsource) [, evaluateOnCallFrame](#setpauseonexceptions) [,](#evaluateoncallframe) [setVariableValue](#setvariablevalue), [setBlackboxPatterns](#setblackboxpatterns) [, msSetDebuggerPropertyValue](#mssetdebuggerpropertyvalue)</span><span class="sxs-lookup"><span data-stu-id="4edb7-109">[enable](#enable), [disable](#disable), [getPossibleBreakpoints](#getpossiblebreakpoints), [setBreakpointsActive](#setbreakpointsactive), [setBreakpointByUrl](#setbreakpointbyurl), [setBreakpoint](#setbreakpoint), [removeBreakpoint](#removebreakpoint), [stepOver](#stepover), [stepInto](#stepinto), [stepOut](#stepout), [pause](#pause), [resume](#resume), [getScriptSource](#getscriptsource), [setPauseOnExceptions](#setpauseonexceptions), [evaluateOnCallFrame](#evaluateoncallframe), [setVariableValue](#setvariablevalue), [setBlackboxPatterns](#setblackboxpatterns), [msSetDebuggerPropertyValue](#mssetdebuggerpropertyvalue)</span></span> |
| [**<span data-ttu-id="4edb7-110">Eventos</span><span class="sxs-lookup"><span data-stu-id="4edb7-110">Events</span></span>**](#events) | <span data-ttu-id="4edb7-111">[scriptParsed](#scriptparsed), [breakpointResolved](#breakpointresolved), [pausado](#paused), [reanudado](#resumed)</span><span class="sxs-lookup"><span data-stu-id="4edb7-111">[scriptParsed](#scriptparsed), [breakpointResolved](#breakpointresolved), [paused](#paused), [resumed](#resumed)</span></span> |
| [**<span data-ttu-id="4edb7-112">Tipos</span><span class="sxs-lookup"><span data-stu-id="4edb7-112">Types</span></span>**](#types) | <span data-ttu-id="4edb7-113">[BreakpointId](#breakpointid), [CallFrameId](#callframeid), [Ubicación](#location), [BreakLocation](#breaklocation), [CallFrame](#callframe), [ámbito](#scope)</span><span class="sxs-lookup"><span data-stu-id="4edb7-113">[BreakpointId](#breakpointid), [CallFrameId](#callframeid), [Location](#location), [BreakLocation](#breaklocation), [CallFrame](#callframe), [Scope](#scope)</span></span> |
| [**<span data-ttu-id="4edb7-114">Dependencias</span><span class="sxs-lookup"><span data-stu-id="4edb7-114">Dependencies</span></span>**](#dependencies) | [<span data-ttu-id="4edb7-115">Motores</span><span class="sxs-lookup"><span data-stu-id="4edb7-115">Runtime</span></span>](runtime.md) |
## <span data-ttu-id="4edb7-116">Métodos</span><span class="sxs-lookup"><span data-stu-id="4edb7-116">Methods</span></span>

### <span data-ttu-id="4edb7-117">habilitar</span><span class="sxs-lookup"><span data-stu-id="4edb7-117">enable</span></span>
<span data-ttu-id="4edb7-118">Habilita el depurador para la página dada.</span><span class="sxs-lookup"><span data-stu-id="4edb7-118">Enables debugger for the given page.</span></span> <span data-ttu-id="4edb7-119">Los clientes no deben suponer que la depuración se ha habilitado hasta que se reciba el resultado de este comando.</span><span class="sxs-lookup"><span data-stu-id="4edb7-119">Clients should not assume that the debugging has been enabled until the result for this command is received.</span></span>

</p>

---

### <span data-ttu-id="4edb7-120">deshabilitar </span><span class="sxs-lookup"><span data-stu-id="4edb7-120">disable</span></span>
<span data-ttu-id="4edb7-121">Deshabilita el depurador para la página dada.</span><span class="sxs-lookup"><span data-stu-id="4edb7-121">Disables debugger for given page.</span></span>

</p>

---

### <span data-ttu-id="4edb7-122">getPossibleBreakpoints</span><span class="sxs-lookup"><span data-stu-id="4edb7-122">getPossibleBreakpoints</span></span>
<span data-ttu-id="4edb7-123">Devuelve posibles ubicaciones para el punto de interrupción.</span><span class="sxs-lookup"><span data-stu-id="4edb7-123">Returns possible locations for breakpoint.</span></span> <span data-ttu-id="4edb7-124">scriptId en las ubicaciones de intervalo de inicio y de finalización deben ser iguales.</span><span class="sxs-lookup"><span data-stu-id="4edb7-124">scriptId in start and end range locations should be the same.</span></span>

<table>
    <thead>
        <tr>
            <th><span data-ttu-id="4edb7-125">Parameters</span><span class="sxs-lookup"><span data-stu-id="4edb7-125">Parameters</span></span></th>
            <th></th>
            <th></th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td><span data-ttu-id="4edb7-126">start</span><span class="sxs-lookup"><span data-stu-id="4edb7-126">start</span></span></td>
            <td><a href="#location"><code class="flyout">Location</code></a></td>
            <td><span data-ttu-id="4edb7-127">Inicio del rango para buscar posibles ubicaciones de puntos de interrupción en.</span><span class="sxs-lookup"><span data-stu-id="4edb7-127">Start of range to search possible breakpoint locations in.</span></span></td>
        </tr>
        <tr>
            <td><span data-ttu-id="4edb7-128">terminar</span><span class="sxs-lookup"><span data-stu-id="4edb7-128">end</span></span></td>
            <td><a href="#location"><code class="flyout">Location</code></a></td>
            <td><span data-ttu-id="4edb7-129">Fin del rango para buscar posibles ubicaciones de puntos de interrupción en (excepto).</span><span class="sxs-lookup"><span data-stu-id="4edb7-129">End of range to search possible breakpoint locations in (excluding).</span></span> <span data-ttu-id="4edb7-130">Cuando no se especifica, el final de las secuencias de comandos se usa como fin del rango.</span><span class="sxs-lookup"><span data-stu-id="4edb7-130">When not specified, end of scripts is used as end of range.</span></span></td>
        </tr>
    </tbody>
</table>
<table>
    <thead>
        <tr>
            <th><span data-ttu-id="4edb7-131">Devuelve</span><span class="sxs-lookup"><span data-stu-id="4edb7-131">Returns</span></span></th>
            <th></th>
            <th></th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td><span data-ttu-id="4edb7-132">sitios</span><span class="sxs-lookup"><span data-stu-id="4edb7-132">locations</span></span></td>
            <td><a href="#breaklocation"><code class="flyout">BreakLocation</code></a></td>
            <td><span data-ttu-id="4edb7-133">Lista de posibles ubicaciones de los puntos de interrupción.</span><span class="sxs-lookup"><span data-stu-id="4edb7-133">List of the possible breakpoint locations.</span></span></td>
        </tr>
    </tbody>
</table>
</p>

---

### <span data-ttu-id="4edb7-134">setBreakpointsActive</span><span class="sxs-lookup"><span data-stu-id="4edb7-134">setBreakpointsActive</span></span>
<span data-ttu-id="4edb7-135">Activa o desactiva todos los puntos de interrupción de la página.</span><span class="sxs-lookup"><span data-stu-id="4edb7-135">Activates / deactivates all breakpoints on the page.</span></span>

<table>
    <thead>
        <tr>
            <th><span data-ttu-id="4edb7-136">Parameters</span><span class="sxs-lookup"><span data-stu-id="4edb7-136">Parameters</span></span></th>
            <th></th>
            <th></th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td><span data-ttu-id="4edb7-137">activa</span><span class="sxs-lookup"><span data-stu-id="4edb7-137">active</span></span></td>
            <td><code class="flyout">boolean</code></td>
            <td><span data-ttu-id="4edb7-138">Nuevo valor para puntos de interrupción activo estado.</span><span class="sxs-lookup"><span data-stu-id="4edb7-138">New value for breakpoints active state.</span></span></td>
        </tr>
    </tbody>
</table>
</p>

---

### <span data-ttu-id="4edb7-139">setBreakpointByUrl</span><span class="sxs-lookup"><span data-stu-id="4edb7-139">setBreakpointByUrl</span></span>
<span data-ttu-id="4edb7-140">Establece un punto de interrupción de JavaScript en la ubicación especificada, por dirección URL o dirección URL Regex.</span><span class="sxs-lookup"><span data-stu-id="4edb7-140">Sets JavaScript breakpoint at given location specified either by URL or URL regex.</span></span> <span data-ttu-id="4edb7-141">Una vez que se haya emitido este comando, todos los scripts analizados existentes tendrán los puntos de interrupción resueltos y devueltos en la <code>locations</code> propiedad.</span><span class="sxs-lookup"><span data-stu-id="4edb7-141">Once this command is issued, all existing parsed scripts will have breakpoints resolved and returned in <code>locations</code> property.</span></span> <span data-ttu-id="4edb7-142">Además, el análisis de scripts más parecido dará como resultado <code>breakpointResolved</code> eventos posteriores.</span><span class="sxs-lookup"><span data-stu-id="4edb7-142">Further matching script parsing will result in subsequent <code>breakpointResolved</code> events issued.</span></span> <span data-ttu-id="4edb7-143">Este punto de interrupción lógico afectará a las recargas de páginas.</span><span class="sxs-lookup"><span data-stu-id="4edb7-143">This logical breakpoint will survive page reloads.</span></span>

<table>
    <thead>
        <tr>
            <th><span data-ttu-id="4edb7-144">Parameters</span><span class="sxs-lookup"><span data-stu-id="4edb7-144">Parameters</span></span></th>
            <th></th>
            <th></th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td><span data-ttu-id="4edb7-145">lineNumber</span><span class="sxs-lookup"><span data-stu-id="4edb7-145">lineNumber</span></span></td>
            <td><code class="flyout">integer</code></td>
            <td><span data-ttu-id="4edb7-146">Número de línea para establecer el punto de interrupción en.</span><span class="sxs-lookup"><span data-stu-id="4edb7-146">Line number to set breakpoint at.</span></span></td>
        </tr>
        <tr>
            <td><span data-ttu-id="4edb7-147">url</span><span class="sxs-lookup"><span data-stu-id="4edb7-147">url</span></span> <br/> <i><span data-ttu-id="4edb7-148">opcional</span><span class="sxs-lookup"><span data-stu-id="4edb7-148">optional</span></span></i></td>
            <td><code class="flyout">string</code></td>
            <td><span data-ttu-id="4edb7-149">Dirección URL de los recursos para establecer el punto de interrupción.</span><span class="sxs-lookup"><span data-stu-id="4edb7-149">URL of the resources to set breakpoint on.</span></span></td>
        </tr>
        <tr>
            <td><span data-ttu-id="4edb7-150">urlRegex</span><span class="sxs-lookup"><span data-stu-id="4edb7-150">urlRegex</span></span> <br/> <i><span data-ttu-id="4edb7-151">opcional</span><span class="sxs-lookup"><span data-stu-id="4edb7-151">optional</span></span></i></td>
            <td><code class="flyout">string</code></td>
            <td><span data-ttu-id="4edb7-152">Patrón de Regex para las direcciones URL de los recursos para establecer puntos de interrupción.</span><span class="sxs-lookup"><span data-stu-id="4edb7-152">Regex pattern for the URLs of the resources to set breakpoints on.</span></span> <span data-ttu-id="4edb7-153"><code>url</code>O <code>urlRegex</code> debe especificarse.</span><span class="sxs-lookup"><span data-stu-id="4edb7-153">Either <code>url</code> or <code>urlRegex</code> must be specified.</span></span></td>
        </tr>
        <tr>
            <td><span data-ttu-id="4edb7-154">columnNumber</span><span class="sxs-lookup"><span data-stu-id="4edb7-154">columnNumber</span></span> <br/> <i><span data-ttu-id="4edb7-155">opcional</span><span class="sxs-lookup"><span data-stu-id="4edb7-155">optional</span></span></i></td>
            <td><code class="flyout">integer</code></td>
            <td><span data-ttu-id="4edb7-156">Desplazamiento en la línea para establecer el punto de interrupción en.</span><span class="sxs-lookup"><span data-stu-id="4edb7-156">Offset in the line to set breakpoint at.</span></span></td>
        </tr>
        <tr>
            <td><span data-ttu-id="4edb7-157">requisito</span><span class="sxs-lookup"><span data-stu-id="4edb7-157">condition</span></span> <br/> <i><span data-ttu-id="4edb7-158">opcional</span><span class="sxs-lookup"><span data-stu-id="4edb7-158">optional</span></span></i></td>
            <td><code class="flyout">string</code></td>
            <td><span data-ttu-id="4edb7-159">Expresión que se va a usar como condición de punto de interrupción.</span><span class="sxs-lookup"><span data-stu-id="4edb7-159">Expression to use as a breakpoint condition.</span></span> <span data-ttu-id="4edb7-160">Cuando se especifica, Debugger solo se detendrá en el punto de interrupción si esta expresión se evalúa como true.</span><span class="sxs-lookup"><span data-stu-id="4edb7-160">When specified, debugger will only stop on the breakpoint if this expression evaluates to true.</span></span></td>
        </tr>
    </tbody>
</table>
<table>
    <thead>
        <tr>
            <th><span data-ttu-id="4edb7-161">Devuelve</span><span class="sxs-lookup"><span data-stu-id="4edb7-161">Returns</span></span></th>
            <th></th>
            <th></th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td><span data-ttu-id="4edb7-162">breakpointId</span><span class="sxs-lookup"><span data-stu-id="4edb7-162">breakpointId</span></span></td>
            <td><a href="#breakpointid"><code class="flyout">BreakpointId</code></a></td>
            <td><span data-ttu-id="4edb7-163">Identificador del punto de interrupción creado para referencia adicional.</span><span class="sxs-lookup"><span data-stu-id="4edb7-163">Id of the created breakpoint for further reference.</span></span></td>
        </tr>
        <tr>
            <td><span data-ttu-id="4edb7-164">sitios</span><span class="sxs-lookup"><span data-stu-id="4edb7-164">locations</span></span></td>
            <td><a href="#location"><code class="flyout">Location[]</code></a></td>
            <td><span data-ttu-id="4edb7-165">Lista de las ubicaciones en las que se ha resuelto este punto de interrupción.</span><span class="sxs-lookup"><span data-stu-id="4edb7-165">List of the locations this breakpoint resolved into upon addition.</span></span></td>
        </tr>
    </tbody>
</table>
</p>

---

### <span data-ttu-id="4edb7-166">setBreakpoint</span><span class="sxs-lookup"><span data-stu-id="4edb7-166">setBreakpoint</span></span>
<span data-ttu-id="4edb7-167">Establece un punto de interrupción de JavaScript en una ubicación determinada.</span><span class="sxs-lookup"><span data-stu-id="4edb7-167">Sets JavaScript breakpoint at a given location.</span></span>

<table>
    <thead>
        <tr>
            <th><span data-ttu-id="4edb7-168">Parameters</span><span class="sxs-lookup"><span data-stu-id="4edb7-168">Parameters</span></span></th>
            <th></th>
            <th></th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td><span data-ttu-id="4edb7-169">Ubicación</span><span class="sxs-lookup"><span data-stu-id="4edb7-169">location</span></span></td>
            <td><a href="#location"><code class="flyout">Location</code></a></td>
            <td><span data-ttu-id="4edb7-170">Ubicación en la que se establecerá el punto de interrupción.</span><span class="sxs-lookup"><span data-stu-id="4edb7-170">Location to set breakpoint in.</span></span></td>
        </tr>
        <tr>
            <td><span data-ttu-id="4edb7-171">requisito</span><span class="sxs-lookup"><span data-stu-id="4edb7-171">condition</span></span> <br/> <i><span data-ttu-id="4edb7-172">opcional</span><span class="sxs-lookup"><span data-stu-id="4edb7-172">optional</span></span></i></td>
            <td><code class="flyout">string</code></td>
            <td><span data-ttu-id="4edb7-173">Expresión que se va a usar como condición de punto de interrupción.</span><span class="sxs-lookup"><span data-stu-id="4edb7-173">Expression to use as a breakpoint condition.</span></span> <span data-ttu-id="4edb7-174">Cuando se especifica, Debugger solo se detendrá en el punto de interrupción si esta expresión se evalúa como true.</span><span class="sxs-lookup"><span data-stu-id="4edb7-174">When specified, debugger will only stop on the breakpoint if this expression evaluates to true.</span></span></td>
        </tr>
    </tbody>
</table>
<table>
    <thead>
        <tr>
            <th><span data-ttu-id="4edb7-175">Devuelve</span><span class="sxs-lookup"><span data-stu-id="4edb7-175">Returns</span></span></th>
            <th></th>
            <th></th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td><span data-ttu-id="4edb7-176">breakpointId</span><span class="sxs-lookup"><span data-stu-id="4edb7-176">breakpointId</span></span></td>
            <td><a href="#breakpointid"><code class="flyout">BreakpointId</code></a></td>
            <td><span data-ttu-id="4edb7-177">Identificador del punto de interrupción creado para referencia adicional.</span><span class="sxs-lookup"><span data-stu-id="4edb7-177">Id of the created breakpoint for further reference.</span></span></td>
        </tr>
        <tr>
            <td><span data-ttu-id="4edb7-178">actualLocation</span><span class="sxs-lookup"><span data-stu-id="4edb7-178">actualLocation</span></span></td>
            <td><a href="#location"><code class="flyout">Location</code></a></td>
            <td><span data-ttu-id="4edb7-179">Ubicación en la que se resuelve este punto de interrupción.</span><span class="sxs-lookup"><span data-stu-id="4edb7-179">Location this breakpoint resolved into.</span></span></td>
        </tr>
    </tbody>
</table>
</p>

---

### <span data-ttu-id="4edb7-180">removeBreakpoint</span><span class="sxs-lookup"><span data-stu-id="4edb7-180">removeBreakpoint</span></span>
<span data-ttu-id="4edb7-181">Quita el punto de interrupción de JavaScript.</span><span class="sxs-lookup"><span data-stu-id="4edb7-181">Removes JavaScript breakpoint.</span></span>

<table>
    <thead>
        <tr>
            <th><span data-ttu-id="4edb7-182">Parameters</span><span class="sxs-lookup"><span data-stu-id="4edb7-182">Parameters</span></span></th>
            <th></th>
            <th></th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td><span data-ttu-id="4edb7-183">breakpointId</span><span class="sxs-lookup"><span data-stu-id="4edb7-183">breakpointId</span></span></td>
            <td><a href="#breakpointid"><code class="flyout">BreakpointId</code></a></td>
            <td></td>
        </tr>
    </tbody>
</table>
</p>

---

### <span data-ttu-id="4edb7-184">Pasadas</span><span class="sxs-lookup"><span data-stu-id="4edb7-184">stepOver</span></span>
<span data-ttu-id="4edb7-185">Pasos sobre la instrucción.</span><span class="sxs-lookup"><span data-stu-id="4edb7-185">Steps over the statement.</span></span>

</p>

---

### <span data-ttu-id="4edb7-186">stepInto</span><span class="sxs-lookup"><span data-stu-id="4edb7-186">stepInto</span></span>
<span data-ttu-id="4edb7-187">Recorre los pasos de la llamada de función.</span><span class="sxs-lookup"><span data-stu-id="4edb7-187">Steps into the function call.</span></span>

</p>

---

### <span data-ttu-id="4edb7-188">stepOut</span><span class="sxs-lookup"><span data-stu-id="4edb7-188">stepOut</span></span>
<span data-ttu-id="4edb7-189">Recorre los pasos de la llamada de función.</span><span class="sxs-lookup"><span data-stu-id="4edb7-189">Steps out of the function call.</span></span>

</p>

---

### <span data-ttu-id="4edb7-190">pause</span><span class="sxs-lookup"><span data-stu-id="4edb7-190">pause</span></span>
<span data-ttu-id="4edb7-191">Se detiene en la siguiente instrucción de JavaScript.</span><span class="sxs-lookup"><span data-stu-id="4edb7-191">Stops on the next JavaScript statement.</span></span>

</p>

---

### <span data-ttu-id="4edb7-192">resume</span><span class="sxs-lookup"><span data-stu-id="4edb7-192">resume</span></span>
<span data-ttu-id="4edb7-193">Reanuda la ejecución de JavaScript.</span><span class="sxs-lookup"><span data-stu-id="4edb7-193">Resumes JavaScript execution.</span></span>

</p>

---

### <span data-ttu-id="4edb7-194">getScriptSource</span><span class="sxs-lookup"><span data-stu-id="4edb7-194">getScriptSource</span></span>
<span data-ttu-id="4edb7-195">Devuelve el origen del script con el identificador especificado.</span><span class="sxs-lookup"><span data-stu-id="4edb7-195">Returns source for the script with given id.</span></span>

<table>
    <thead>
        <tr>
            <th><span data-ttu-id="4edb7-196">Parameters</span><span class="sxs-lookup"><span data-stu-id="4edb7-196">Parameters</span></span></th>
            <th></th>
            <th></th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td><span data-ttu-id="4edb7-197">scriptId</span><span class="sxs-lookup"><span data-stu-id="4edb7-197">scriptId</span></span></td>
            <td><a href="runtime.md#scriptid"><code class="flyout">Runtime.ScriptId</code></a></td>
            <td><span data-ttu-id="4edb7-198">Identificador del script para el que se va a obtener el origen.</span><span class="sxs-lookup"><span data-stu-id="4edb7-198">Id of the script to get source for.</span></span></td>
        </tr>
    </tbody>
</table>
<table>
    <thead>
        <tr>
            <th><span data-ttu-id="4edb7-199">Devuelve</span><span class="sxs-lookup"><span data-stu-id="4edb7-199">Returns</span></span></th>
            <th></th>
            <th></th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td><span data-ttu-id="4edb7-200">scriptSource</span><span class="sxs-lookup"><span data-stu-id="4edb7-200">scriptSource</span></span></td>
            <td><code class="flyout">string</code></td>
            <td><span data-ttu-id="4edb7-201">Origen de script.</span><span class="sxs-lookup"><span data-stu-id="4edb7-201">Script source.</span></span></td>
        </tr>
    </tbody>
</table>
</p>

---

### <span data-ttu-id="4edb7-202">setPauseOnExceptions</span><span class="sxs-lookup"><span data-stu-id="4edb7-202">setPauseOnExceptions</span></span>
<span data-ttu-id="4edb7-203">Define la pausa en el estado de las excepciones.</span><span class="sxs-lookup"><span data-stu-id="4edb7-203">Defines pause on exceptions state.</span></span> <span data-ttu-id="4edb7-204">Puede establecerse en detener en todas las excepciones, excepciones no detectadas o sin excepciones.</span><span class="sxs-lookup"><span data-stu-id="4edb7-204">Can be set to stop on all exceptions, uncaught exceptions or no exceptions.</span></span> <span data-ttu-id="4edb7-205">El estado de pausa inicial en excepciones es de <code>none</code> .</span><span class="sxs-lookup"><span data-stu-id="4edb7-205">Initial pause on exceptions state is <code>none</code>.</span></span>

<table>
    <thead>
        <tr>
            <th><span data-ttu-id="4edb7-206">Parameters</span><span class="sxs-lookup"><span data-stu-id="4edb7-206">Parameters</span></span></th>
            <th></th>
            <th></th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td><span data-ttu-id="4edb7-207">situación</span><span class="sxs-lookup"><span data-stu-id="4edb7-207">state</span></span></td>
            <td><code class="flyout">string</code> <br/> <i><span data-ttu-id="4edb7-208">Valores permitidos: ninguno, no detectados, todos</span><span class="sxs-lookup"><span data-stu-id="4edb7-208">Allowed values: none, uncaught, all</span></span></i></td>
            <td><span data-ttu-id="4edb7-209">Pausar en el modo de excepciones.</span><span class="sxs-lookup"><span data-stu-id="4edb7-209">Pause on exceptions mode.</span></span></td>
        </tr>
    </tbody>
</table>
</p>

---

### <span data-ttu-id="4edb7-210">evaluateOnCallFrame</span><span class="sxs-lookup"><span data-stu-id="4edb7-210">evaluateOnCallFrame</span></span>
<span data-ttu-id="4edb7-211">Evalúa Expression en un marco de llamada dado.</span><span class="sxs-lookup"><span data-stu-id="4edb7-211">Evaluates expression on a given call frame.</span></span>

<table>
    <thead>
        <tr>
            <th><span data-ttu-id="4edb7-212">Parameters</span><span class="sxs-lookup"><span data-stu-id="4edb7-212">Parameters</span></span></th>
            <th></th>
            <th></th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td><span data-ttu-id="4edb7-213">callFrameId</span><span class="sxs-lookup"><span data-stu-id="4edb7-213">callFrameId</span></span></td>
            <td><a href="#callframeid"><code class="flyout">CallFrameId</code></a></td>
            <td><span data-ttu-id="4edb7-214">Identificador de marco de llamada que se va a evaluar.</span><span class="sxs-lookup"><span data-stu-id="4edb7-214">Call frame identifier to evaluate on.</span></span></td>
        </tr>
        <tr>
            <td><span data-ttu-id="4edb7-215">Expression</span><span class="sxs-lookup"><span data-stu-id="4edb7-215">expression</span></span></td>
            <td><code class="flyout">string</code></td>
            <td><span data-ttu-id="4edb7-216">Expresión que se va a evaluar.</span><span class="sxs-lookup"><span data-stu-id="4edb7-216">Expression to evaluate.</span></span></td>
        </tr>
    </tbody>
</table>
<table>
    <thead>
        <tr>
            <th><span data-ttu-id="4edb7-217">Devuelve</span><span class="sxs-lookup"><span data-stu-id="4edb7-217">Returns</span></span></th>
            <th></th>
            <th></th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td><span data-ttu-id="4edb7-218">resultado</span><span class="sxs-lookup"><span data-stu-id="4edb7-218">result</span></span></td>
            <td><a href="runtime.md#remoteobject"><code class="flyout">Runtime.RemoteObject</code></a></td>
            <td><span data-ttu-id="4edb7-219">Contenedor de objetos para el resultado de evaluación.</span><span class="sxs-lookup"><span data-stu-id="4edb7-219">Object wrapper for the evaluation result.</span></span></td>
        </tr>
    </tbody>
</table>
</p>

---

### <span data-ttu-id="4edb7-220">setVariableValue</span><span class="sxs-lookup"><span data-stu-id="4edb7-220">setVariableValue</span></span>
<span data-ttu-id="4edb7-221">Cambia el valor de la variable en un callframe.</span><span class="sxs-lookup"><span data-stu-id="4edb7-221">Changes value of variable in a callframe.</span></span> <span data-ttu-id="4edb7-222">Los ámbitos basados en objetos no son compatibles y se deben mutar manualmente.</span><span class="sxs-lookup"><span data-stu-id="4edb7-222">Object-based scopes are not supported and must be mutated manually.</span></span>

<table>
    <thead>
        <tr>
            <th><span data-ttu-id="4edb7-223">Parameters</span><span class="sxs-lookup"><span data-stu-id="4edb7-223">Parameters</span></span></th>
            <th></th>
            <th></th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td><span data-ttu-id="4edb7-224">scopeNumber</span><span class="sxs-lookup"><span data-stu-id="4edb7-224">scopeNumber</span></span></td>
            <td><code class="flyout">integer</code></td>
            <td><span data-ttu-id="4edb7-225">número de base cero de ámbito que se mostraba en la cadena de ámbitos.</span><span class="sxs-lookup"><span data-stu-id="4edb7-225">0-based number of scope as was listed in scope chain.</span></span> <span data-ttu-id="4edb7-226">Solo se permiten los tipos de ámbito ' local ', ' cierre ' y ' Catch '.</span><span class="sxs-lookup"><span data-stu-id="4edb7-226">Only 'local', 'closure' and 'catch' scope types are allowed.</span></span> <span data-ttu-id="4edb7-227">Es posible manipular otros ámbitos de forma manual.</span><span class="sxs-lookup"><span data-stu-id="4edb7-227">Other scopes could be manipulated manually.</span></span></td>
        </tr>
        <tr>
            <td><span data-ttu-id="4edb7-228">variableName</span><span class="sxs-lookup"><span data-stu-id="4edb7-228">variableName</span></span></td>
            <td><code class="flyout">string</code></td>
            <td><span data-ttu-id="4edb7-229">Nombre de la variable.</span><span class="sxs-lookup"><span data-stu-id="4edb7-229">Variable name.</span></span></td>
        </tr>
        <tr>
            <td><span data-ttu-id="4edb7-230">Nuevovalor</span><span class="sxs-lookup"><span data-stu-id="4edb7-230">newValue</span></span></td>
            <td><a href="runtime.md#callargument"><code class="flyout">Runtime.CallArgument</code></a></td>
            <td><span data-ttu-id="4edb7-231">Nuevo valor de variable.</span><span class="sxs-lookup"><span data-stu-id="4edb7-231">New variable value.</span></span></td>
        </tr>
        <tr>
            <td><span data-ttu-id="4edb7-232">callFrameId</span><span class="sxs-lookup"><span data-stu-id="4edb7-232">callFrameId</span></span></td>
            <td><a href="#callframeid"><code class="flyout">CallFrameId</code></a></td>
            <td><span data-ttu-id="4edb7-233">Identificador de callframe que contiene la variable.</span><span class="sxs-lookup"><span data-stu-id="4edb7-233">Id of callframe that holds variable.</span></span></td>
        </tr>
    </tbody>
</table>
</p>

---

### <span data-ttu-id="4edb7-234">setBlackboxPatterns</span><span class="sxs-lookup"><span data-stu-id="4edb7-234">setBlackboxPatterns</span></span>
<span><b><span data-ttu-id="4edb7-235">Montaje.</span><span class="sxs-lookup"><span data-stu-id="4edb7-235">Experimental.</span></span> </b></span><span data-ttu-id="4edb7-236">Reemplazar patrones de Blackbox anteriores por los que se hayan pasado.</span><span class="sxs-lookup"><span data-stu-id="4edb7-236">Replace previous blackbox patterns with passed ones.</span></span> <span data-ttu-id="4edb7-237">Fuerza que el back-end omita la ejecución paso a paso en scripts con una dirección URL que coincide con uno de los patrones.</span><span class="sxs-lookup"><span data-stu-id="4edb7-237">Forces backend to skip stepping/pausing in scripts with url matching one of the patterns.</span></span> <span data-ttu-id="4edb7-238">El depurador intentará dejar la secuencia de comandos de blackboxed realizando ' paso a paso ' varias veces, por último, recurriendo a ' paso hacia fuera ' si no se ha realizado correctamente.</span><span class="sxs-lookup"><span data-stu-id="4edb7-238">The debugger will try to leave blackboxed script by performing 'step in' several times, finally resorting to 'step out' if unsuccessful.</span></span>

<table>
    <thead>
        <tr>
            <th><span data-ttu-id="4edb7-239">Parameters</span><span class="sxs-lookup"><span data-stu-id="4edb7-239">Parameters</span></span></th>
            <th></th>
            <th></th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td><span data-ttu-id="4edb7-240">modos</span><span class="sxs-lookup"><span data-stu-id="4edb7-240">patterns</span></span></td>
            <td><code class="flyout">string[]</code></td>
            <td><span data-ttu-id="4edb7-241">Matriz de RegExpS que se usará para comprobar la dirección URL del script para el estado de Blackbox.</span><span class="sxs-lookup"><span data-stu-id="4edb7-241">Array of regexps that will be used to check script url for blackbox state.</span></span></td>
        </tr>
    </tbody>
</table>
</p>

---

### <span data-ttu-id="4edb7-242">msSetDebuggerPropertyValue</span><span class="sxs-lookup"><span data-stu-id="4edb7-242">msSetDebuggerPropertyValue</span></span>
<span><b><span data-ttu-id="4edb7-243">Montaje.</span><span class="sxs-lookup"><span data-stu-id="4edb7-243">Experimental.</span></span> </b></span><span data-ttu-id="4edb7-244">Microsoft: establece la propiedad de depurador especificada en el valor especificado.</span><span class="sxs-lookup"><span data-stu-id="4edb7-244">Microsoft: Sets the specified debugger property to the specified value.</span></span>

<table>
    <thead>
        <tr>
            <th><span data-ttu-id="4edb7-245">Parameters</span><span class="sxs-lookup"><span data-stu-id="4edb7-245">Parameters</span></span></th>
            <th></th>
            <th></th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td><span data-ttu-id="4edb7-246">debuggerPropertyId</span><span class="sxs-lookup"><span data-stu-id="4edb7-246">debuggerPropertyId</span></span></td>
            <td><code class="flyout">string</code></td>
            <td><span data-ttu-id="4edb7-247">Microsoft: el identificador de propiedad (es decir, msDebuggerPropertyId) que se va a establecer.</span><span class="sxs-lookup"><span data-stu-id="4edb7-247">Microsoft: The property id (i.e. msDebuggerPropertyId) to set.</span></span></td>
        </tr>
        <tr>
            <td><span data-ttu-id="4edb7-248">Nuevovalor</span><span class="sxs-lookup"><span data-stu-id="4edb7-248">newValue</span></span></td>
            <td><code class="flyout">string</code></td>
            <td></td>
        </tr>
    </tbody>
</table>
</p>

---

## <span data-ttu-id="4edb7-249">Eventos</span><span class="sxs-lookup"><span data-stu-id="4edb7-249">Events</span></span>

### <span data-ttu-id="4edb7-250">scriptParsed</span><span class="sxs-lookup"><span data-stu-id="4edb7-250">scriptParsed</span></span>
<span data-ttu-id="4edb7-251">Se desencadena cuando se analiza el script.</span><span class="sxs-lookup"><span data-stu-id="4edb7-251">Fired when the script is parsed.</span></span> <span data-ttu-id="4edb7-252">Este evento también se desencadena para todos los scripts conocidos y no recopilados al habilitar el depurador.</span><span class="sxs-lookup"><span data-stu-id="4edb7-252">This event is also fired for all known and uncollected scripts upon enabling debugger.</span></span>

<table>
    <thead>
        <tr>
            <th><span data-ttu-id="4edb7-253">Parameters</span><span class="sxs-lookup"><span data-stu-id="4edb7-253">Parameters</span></span></th>
            <th></th>
            <th></th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td><span data-ttu-id="4edb7-254">scriptId</span><span class="sxs-lookup"><span data-stu-id="4edb7-254">scriptId</span></span></td>
            <td><a href="runtime.md#scriptid"><code class="flyout">Runtime.ScriptId</code></a></td>
            <td><span data-ttu-id="4edb7-255">Identificador de la secuencia de comandos analizada.</span><span class="sxs-lookup"><span data-stu-id="4edb7-255">Identifier of the script parsed.</span></span></td>
        </tr>
        <tr>
            <td><span data-ttu-id="4edb7-256">url</span><span class="sxs-lookup"><span data-stu-id="4edb7-256">url</span></span></td>
            <td><code class="flyout">string</code></td>
            <td><span data-ttu-id="4edb7-257">Dirección URL o nombre de la secuencia de comandos analizada (si hay alguna).</span><span class="sxs-lookup"><span data-stu-id="4edb7-257">URL or name of the script parsed (if any).</span></span></td>
        </tr>
        <tr>
            <td><span data-ttu-id="4edb7-258">startLine</span><span class="sxs-lookup"><span data-stu-id="4edb7-258">startLine</span></span></td>
            <td><code class="flyout">integer</code></td>
            <td><span data-ttu-id="4edb7-259">Desplazamiento de línea del script en el recurso con la dirección URL dada (para etiquetas de script).</span><span class="sxs-lookup"><span data-stu-id="4edb7-259">Line offset of the script within the resource with given URL (for script tags).</span></span></td>
        </tr>
        <tr>
            <td><span data-ttu-id="4edb7-260">Columnainicio</span><span class="sxs-lookup"><span data-stu-id="4edb7-260">startColumn</span></span></td>
            <td><code class="flyout">integer</code></td>
            <td><span data-ttu-id="4edb7-261">Desplazamiento de columna de la secuencia de comandos en el recurso con la dirección URL proporcionada.</span><span class="sxs-lookup"><span data-stu-id="4edb7-261">Column offset of the script within the resource with given URL.</span></span></td>
        </tr>
        <tr>
            <td><span data-ttu-id="4edb7-262">Fin</span><span class="sxs-lookup"><span data-stu-id="4edb7-262">endLine</span></span></td>
            <td><code class="flyout">integer</code></td>
            <td><span data-ttu-id="4edb7-263">Última línea de la secuencia de comandos.</span><span class="sxs-lookup"><span data-stu-id="4edb7-263">Last line of the script.</span></span></td>
        </tr>
        <tr>
            <td><span data-ttu-id="4edb7-264">Columnafin</span><span class="sxs-lookup"><span data-stu-id="4edb7-264">endColumn</span></span></td>
            <td><code class="flyout">integer</code></td>
            <td><span data-ttu-id="4edb7-265">Longitud de la última línea de la secuencia de comandos.</span><span class="sxs-lookup"><span data-stu-id="4edb7-265">Length of the last line of the script.</span></span></td>
        </tr>
        <tr>
            <td><span data-ttu-id="4edb7-266">executionContextId</span><span class="sxs-lookup"><span data-stu-id="4edb7-266">executionContextId</span></span></td>
            <td><a href="runtime.md#executioncontextid"><code class="flyout">Runtime.ExecutionContextId</code></a></td>
            <td><span data-ttu-id="4edb7-267">Especifica el contexto de creación de script.</span><span class="sxs-lookup"><span data-stu-id="4edb7-267">Specifies script creation context.</span></span></td>
        </tr>
        <tr>
            <td><span data-ttu-id="4edb7-268">sourceMapURL</span><span class="sxs-lookup"><span data-stu-id="4edb7-268">sourceMapURL</span></span> <br/> <i><span data-ttu-id="4edb7-269">opcional</span><span class="sxs-lookup"><span data-stu-id="4edb7-269">optional</span></span></i></td>
            <td><code class="flyout">string</code></td>
            <td><span data-ttu-id="4edb7-270">Dirección URL de la asignación de origen asociada con el script (si existe).</span><span class="sxs-lookup"><span data-stu-id="4edb7-270">URL of source map associated with script (if any).</span></span></td>
        </tr>
        <tr>
            <td><span data-ttu-id="4edb7-271">longitud</span><span class="sxs-lookup"><span data-stu-id="4edb7-271">length</span></span> <br/> <i><span data-ttu-id="4edb7-272">opcional</span><span class="sxs-lookup"><span data-stu-id="4edb7-272">optional</span></span></i></td>
            <td><code class="flyout">integer</code></td>
            <td><span><b><span data-ttu-id="4edb7-273">Montaje.</span><span class="sxs-lookup"><span data-stu-id="4edb7-273">Experimental.</span></span> </b></span><span data-ttu-id="4edb7-274">Esta longitud de script.</span><span class="sxs-lookup"><span data-stu-id="4edb7-274">This script length.</span></span></td>
        </tr>
        <tr>
            <td><span data-ttu-id="4edb7-275">msParentId</span><span class="sxs-lookup"><span data-stu-id="4edb7-275">msParentId</span></span> <br/> <i><span data-ttu-id="4edb7-276">opcional</span><span class="sxs-lookup"><span data-stu-id="4edb7-276">optional</span></span></i></td>
            <td><code class="flyout">string</code></td>
            <td><span><b><span data-ttu-id="4edb7-277">Montaje.</span><span class="sxs-lookup"><span data-stu-id="4edb7-277">Experimental.</span></span> </b></span><span data-ttu-id="4edb7-278">Este es el identificador de documento principal.</span><span class="sxs-lookup"><span data-stu-id="4edb7-278">This is the parent document ID.</span></span></td>
        </tr>
        <tr>
            <td><span data-ttu-id="4edb7-279">msMimeType</span><span class="sxs-lookup"><span data-stu-id="4edb7-279">msMimeType</span></span> <br/> <i><span data-ttu-id="4edb7-280">opcional</span><span class="sxs-lookup"><span data-stu-id="4edb7-280">optional</span></span></i></td>
            <td><code class="flyout">string</code></td>
            <td><span><b><span data-ttu-id="4edb7-281">Montaje.</span><span class="sxs-lookup"><span data-stu-id="4edb7-281">Experimental.</span></span> </b></span><span data-ttu-id="4edb7-282">Este es el tipo MIME.</span><span class="sxs-lookup"><span data-stu-id="4edb7-282">This is the mime type.</span></span></td>
        </tr>
        <tr>
            <td><span data-ttu-id="4edb7-283">msIsDynamicCode</span><span class="sxs-lookup"><span data-stu-id="4edb7-283">msIsDynamicCode</span></span> <br/> <i><span data-ttu-id="4edb7-284">opcional</span><span class="sxs-lookup"><span data-stu-id="4edb7-284">optional</span></span></i></td>
            <td><code class="flyout">boolean</code></td>
            <td><span><b><span data-ttu-id="4edb7-285">Montaje.</span><span class="sxs-lookup"><span data-stu-id="4edb7-285">Experimental.</span></span> </b></span><span data-ttu-id="4edb7-286">Indica si se trata de código dinámico.</span><span class="sxs-lookup"><span data-stu-id="4edb7-286">This indicates whether it is dynamic code.</span></span></td>
        </tr>
        <tr>
            <td><span data-ttu-id="4edb7-287">msLongDocumentId</span><span class="sxs-lookup"><span data-stu-id="4edb7-287">msLongDocumentId</span></span> <br/> <i><span data-ttu-id="4edb7-288">opcional</span><span class="sxs-lookup"><span data-stu-id="4edb7-288">optional</span></span></i></td>
            <td><code class="flyout">integer</code></td>
            <td><span><b><span data-ttu-id="4edb7-289">Montaje.</span><span class="sxs-lookup"><span data-stu-id="4edb7-289">Experimental.</span></span> </b></span><span data-ttu-id="4edb7-290">Este es el identificador de documento largo.</span><span class="sxs-lookup"><span data-stu-id="4edb7-290">This is the long document ID.</span></span></td>
        </tr>
    </tbody>
</table>
</p>

---

### <span data-ttu-id="4edb7-291">breakpointResolved</span><span class="sxs-lookup"><span data-stu-id="4edb7-291">breakpointResolved</span></span>
<span data-ttu-id="4edb7-292">Se desencadena cuando el punto de interrupción se resuelve como una secuencia de comandos y una ubicación reales.</span><span class="sxs-lookup"><span data-stu-id="4edb7-292">Fired when breakpoint is resolved to an actual script and location.</span></span>

<table>
    <thead>
        <tr>
            <th><span data-ttu-id="4edb7-293">Parameters</span><span class="sxs-lookup"><span data-stu-id="4edb7-293">Parameters</span></span></th>
            <th></th>
            <th></th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td><span data-ttu-id="4edb7-294">breakpointId</span><span class="sxs-lookup"><span data-stu-id="4edb7-294">breakpointId</span></span></td>
            <td><a href="#breakpointid"><code class="flyout">BreakpointId</code></a></td>
            <td><span data-ttu-id="4edb7-295">Identificador único de punto de interrupción.</span><span class="sxs-lookup"><span data-stu-id="4edb7-295">Breakpoint unique identifier.</span></span></td>
        </tr>
        <tr>
            <td><span data-ttu-id="4edb7-296">Ubicación</span><span class="sxs-lookup"><span data-stu-id="4edb7-296">location</span></span></td>
            <td><a href="#location"><code class="flyout">Location</code></a></td>
            <td><span data-ttu-id="4edb7-297">Ubicación real del punto de interrupción.</span><span class="sxs-lookup"><span data-stu-id="4edb7-297">Actual breakpoint location.</span></span></td>
        </tr>
        <tr>
            <td><span data-ttu-id="4edb7-298">msLength</span><span class="sxs-lookup"><span data-stu-id="4edb7-298">msLength</span></span> <br/> <i><span data-ttu-id="4edb7-299">opcional</span><span class="sxs-lookup"><span data-stu-id="4edb7-299">optional</span></span></i></td>
            <td><code class="flyout">integer</code></td>
            <td><span><b><span data-ttu-id="4edb7-300">Montaje.</span><span class="sxs-lookup"><span data-stu-id="4edb7-300">Experimental.</span></span> </b></span><span data-ttu-id="4edb7-301">Microsoft: longitud del código (es decir, número de caracteres) en la ubicación del punto de interrupción.</span><span class="sxs-lookup"><span data-stu-id="4edb7-301">Microsoft: Length of code (i.e. number of characters) at the breakpoint location.</span></span></td>
        </tr>
    </tbody>
</table>
</p>

---

### <span data-ttu-id="4edb7-302">en pausa</span><span class="sxs-lookup"><span data-stu-id="4edb7-302">paused</span></span>
<span data-ttu-id="4edb7-303">Se desencadena cuando los depuradores se interrumpen por un punto de interrupción o una excepción.</span><span class="sxs-lookup"><span data-stu-id="4edb7-303">Fired when the debuggers breaks for a breakpoint or exception.</span></span>

<table>
    <thead>
        <tr>
            <th><span data-ttu-id="4edb7-304">Parameters</span><span class="sxs-lookup"><span data-stu-id="4edb7-304">Parameters</span></span></th>
            <th></th>
            <th></th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td><span data-ttu-id="4edb7-305">callFrames</span><span class="sxs-lookup"><span data-stu-id="4edb7-305">callFrames</span></span></td>
            <td><a href="#callframe"><code class="flyout">CallFrame[]</code></a></td>
            <td><span data-ttu-id="4edb7-306">Pila de llamadas: el depurador ha dejado de hacerlo.</span><span class="sxs-lookup"><span data-stu-id="4edb7-306">Call stack the debugger stopped on.</span></span></td>
        </tr>
        <tr>
            <td><span data-ttu-id="4edb7-307">tanto</span><span class="sxs-lookup"><span data-stu-id="4edb7-307">reason</span></span></td>
            <td><code class="flyout">string</code> <br/> <i><span data-ttu-id="4edb7-308">Valores permitidos: punto de interrupción, paso, excepción, otro, EventListener</span><span class="sxs-lookup"><span data-stu-id="4edb7-308">Allowed values: breakpoint, step, exception, other, EventListener</span></span></i></td>
            <td><span data-ttu-id="4edb7-309">Motivo de la pausa.</span><span class="sxs-lookup"><span data-stu-id="4edb7-309">Pause reason.</span></span></td>
        </tr>
        <tr>
            <td><span data-ttu-id="4edb7-310">data</span><span class="sxs-lookup"><span data-stu-id="4edb7-310">data</span></span> <br/> <i><span data-ttu-id="4edb7-311">opcional</span><span class="sxs-lookup"><span data-stu-id="4edb7-311">optional</span></span></i></td>
            <td><code class="flyout">object</code></td>
            <td><span data-ttu-id="4edb7-312">Objeto que contiene propiedades auxiliares específicas de ruptura.</span><span class="sxs-lookup"><span data-stu-id="4edb7-312">Object containing break-specific auxiliary properties.</span></span></td>
        </tr>
        <tr>
            <td><span data-ttu-id="4edb7-313">hitBreakpoints</span><span class="sxs-lookup"><span data-stu-id="4edb7-313">hitBreakpoints</span></span> <br/> <i><span data-ttu-id="4edb7-314">opcional</span><span class="sxs-lookup"><span data-stu-id="4edb7-314">optional</span></span></i></td>
            <td><code class="flyout">string[]</code></td>
            <td><span data-ttu-id="4edb7-315">Identificadores de puntos de interrupción del posicionamiento</span><span class="sxs-lookup"><span data-stu-id="4edb7-315">Hit breakpoints IDs</span></span></td>
        </tr>
        <tr>
            <td><span data-ttu-id="4edb7-316">asyncStackTrace</span><span class="sxs-lookup"><span data-stu-id="4edb7-316">asyncStackTrace</span></span> <br/> <i><span data-ttu-id="4edb7-317">opcional</span><span class="sxs-lookup"><span data-stu-id="4edb7-317">optional</span></span></i></td>
            <td><!--  <a href="#stacktrace">  --><code class="flyout">StackTrace</code><!--  </a>  --></td>
            <td><span data-ttu-id="4edb7-318">Seguimiento de pila asincrónica de JavaScript.</span><span class="sxs-lookup"><span data-stu-id="4edb7-318">JavaScript async stack trace.</span></span></td>
        </tr>
    </tbody>
</table>
</p>

---

### <span data-ttu-id="4edb7-319">retomada</span><span class="sxs-lookup"><span data-stu-id="4edb7-319">resumed</span></span>
<span data-ttu-id="4edb7-320">Se desencadena cuando el depurador reanuda la ejecución.</span><span class="sxs-lookup"><span data-stu-id="4edb7-320">Fired when the debugger resumes execution.</span></span>

</p>

---

## <span data-ttu-id="4edb7-321">Tipos</span><span class="sxs-lookup"><span data-stu-id="4edb7-321">Types</span></span>

### <a name="breakpointid"></a> <span data-ttu-id="4edb7-322">BreakpointId</span><span class="sxs-lookup"><span data-stu-id="4edb7-322">BreakpointId</span></span> `string`

<span data-ttu-id="4edb7-323">Identificador de punto de interrupción.</span><span class="sxs-lookup"><span data-stu-id="4edb7-323">Breakpoint identifier.</span></span>

</p>

---

### <a name="callframeid"></a> <span data-ttu-id="4edb7-324">CallFrameId</span><span class="sxs-lookup"><span data-stu-id="4edb7-324">CallFrameId</span></span> `string`

<span data-ttu-id="4edb7-325">Identificador del marco de la llamada.</span><span class="sxs-lookup"><span data-stu-id="4edb7-325">Call frame identifier.</span></span>

</p>

---

### <a name="location"></a> <span data-ttu-id="4edb7-326">Ubicación</span><span class="sxs-lookup"><span data-stu-id="4edb7-326">Location</span></span> `object`

<span data-ttu-id="4edb7-327">Ubicación en el código fuente.</span><span class="sxs-lookup"><span data-stu-id="4edb7-327">Location in the source code.</span></span>

<table>
    <thead>
        <tr>
            <th><span data-ttu-id="4edb7-328">Propiedades</span><span class="sxs-lookup"><span data-stu-id="4edb7-328">Properties</span></span></th>
            <th></th>
            <th></th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td><span data-ttu-id="4edb7-329">scriptId</span><span class="sxs-lookup"><span data-stu-id="4edb7-329">scriptId</span></span></td>
            <td><a href="runtime.md#scriptid"><code class="flyout">Runtime.ScriptId</code></a></td>
            <td><span data-ttu-id="4edb7-330">Identificador de script tal y como se indica en el <code>Debugger.scriptParsed</code> .</span><span class="sxs-lookup"><span data-stu-id="4edb7-330">Script identifier as reported in the <code>Debugger.scriptParsed</code>.</span></span></td>
        </tr>
        <tr>
            <td><span data-ttu-id="4edb7-331">lineNumber</span><span class="sxs-lookup"><span data-stu-id="4edb7-331">lineNumber</span></span></td>
            <td><code class="flyout">integer</code></td>
            <td><span data-ttu-id="4edb7-332">Número de línea en el script (basado en 0).</span><span class="sxs-lookup"><span data-stu-id="4edb7-332">Line number in the script (0-based).</span></span></td>
        </tr>
        <tr>
            <td><span data-ttu-id="4edb7-333">columnNumber</span><span class="sxs-lookup"><span data-stu-id="4edb7-333">columnNumber</span></span> <br/> <i><span data-ttu-id="4edb7-334">opcional</span><span class="sxs-lookup"><span data-stu-id="4edb7-334">optional</span></span></i></td>
            <td><code class="flyout">integer</code></td>
            <td><span data-ttu-id="4edb7-335">Número de columna en el script (basado en 0).</span><span class="sxs-lookup"><span data-stu-id="4edb7-335">Column number in the script (0-based).</span></span></td>
        </tr>
        <tr>
            <td><span data-ttu-id="4edb7-336">msLength</span><span class="sxs-lookup"><span data-stu-id="4edb7-336">msLength</span></span></td>
            <td><code class="flyout">integer</code></td>
            <td><span data-ttu-id="4edb7-337">Microsoft: longitud del código (es decir, número de caracteres) en este marco de llamada.</span><span class="sxs-lookup"><span data-stu-id="4edb7-337">Microsoft: Length of code (i.e. number of characters) at this call frame.</span></span></td>
        </tr>
    </tbody>
</table>
</p>

---

### <a name="breaklocation"></a> <span data-ttu-id="4edb7-338">BreakLocation</span><span class="sxs-lookup"><span data-stu-id="4edb7-338">BreakLocation</span></span> `object`

<span data-ttu-id="4edb7-339">Interrumpir la ubicación en el código fuente.</span><span class="sxs-lookup"><span data-stu-id="4edb7-339">Break location in the source code.</span></span>

<table>
    <thead>
        <tr>
            <th><span data-ttu-id="4edb7-340">Propiedades</span><span class="sxs-lookup"><span data-stu-id="4edb7-340">Properties</span></span></th>
            <th></th>
            <th></th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td><span data-ttu-id="4edb7-341">scriptId</span><span class="sxs-lookup"><span data-stu-id="4edb7-341">scriptId</span></span></td>
            <td><a href="runtime.md#scriptid"><code class="flyout">Runtime.ScriptId</code></a></td>
            <td><span data-ttu-id="4edb7-342">Identificador de script tal y como se indica en el <code>Debugger.scriptParsed</code> .</span><span class="sxs-lookup"><span data-stu-id="4edb7-342">Script identifier as reported in the <code>Debugger.scriptParsed</code>.</span></span></td>
        </tr>
        <tr>
            <td><span data-ttu-id="4edb7-343">lineNumber</span><span class="sxs-lookup"><span data-stu-id="4edb7-343">lineNumber</span></span></td>
            <td><code class="flyout">integer</code></td>
            <td><span data-ttu-id="4edb7-344">Número de línea en el script (basado en 0).</span><span class="sxs-lookup"><span data-stu-id="4edb7-344">Line number in the script (0-based).</span></span></td>
        </tr>
        <tr>
            <td><span data-ttu-id="4edb7-345">columnNumber</span><span class="sxs-lookup"><span data-stu-id="4edb7-345">columnNumber</span></span> <br/> <i><span data-ttu-id="4edb7-346">opcional</span><span class="sxs-lookup"><span data-stu-id="4edb7-346">optional</span></span></i></td>
            <td><code class="flyout">integer</code></td>
            <td><span data-ttu-id="4edb7-347">Número de columna en el script (basado en 0).</span><span class="sxs-lookup"><span data-stu-id="4edb7-347">Column number in the script (0-based).</span></span></td>
        </tr>
        <tr>
            <td><span data-ttu-id="4edb7-348">msLength</span><span class="sxs-lookup"><span data-stu-id="4edb7-348">msLength</span></span></td>
            <td><code class="flyout">integer</code></td>
            <td><span data-ttu-id="4edb7-349">Microsoft: longitud del código (es decir, número de caracteres) en este marco de llamada.</span><span class="sxs-lookup"><span data-stu-id="4edb7-349">Microsoft: Length of code (i.e. number of characters) at this call frame.</span></span></td>
        </tr>
        <tr>
            <td><span data-ttu-id="4edb7-350">tipo</span><span class="sxs-lookup"><span data-stu-id="4edb7-350">type</span></span> <br/> <i><span data-ttu-id="4edb7-351">opcional</span><span class="sxs-lookup"><span data-stu-id="4edb7-351">optional</span></span></i></td>
            <td><code class="flyout">string</code></td>
            <td><span data-ttu-id="4edb7-352">Valores permitidos: debuggerStatement, Call, Return.</span><span class="sxs-lookup"><span data-stu-id="4edb7-352">Allowed values: debuggerStatement, call, return.</span></span></td>
        </tr>
    </tbody>
</table>
</p>

---

### <a name="callframe"></a> <span data-ttu-id="4edb7-353">CallFrame</span><span class="sxs-lookup"><span data-stu-id="4edb7-353">CallFrame</span></span> `object`

<span data-ttu-id="4edb7-354">Marco de llamada de JavaScript.</span><span class="sxs-lookup"><span data-stu-id="4edb7-354">JavaScript call frame.</span></span> <span data-ttu-id="4edb7-355">Matriz de marcos de llamadas que forman la pila de llamadas.</span><span class="sxs-lookup"><span data-stu-id="4edb7-355">Array of call frames form the call stack.</span></span>

<table>
    <thead>
        <tr>
            <th><span data-ttu-id="4edb7-356">Propiedades</span><span class="sxs-lookup"><span data-stu-id="4edb7-356">Properties</span></span></th>
            <th></th>
            <th></th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td><span data-ttu-id="4edb7-357">callFrameId</span><span class="sxs-lookup"><span data-stu-id="4edb7-357">callFrameId</span></span></td>
            <td><a href="#callframeid"><code class="flyout">CallFrameId</code></a></td>
            <td><span data-ttu-id="4edb7-358">Identificador del marco de la llamada.</span><span class="sxs-lookup"><span data-stu-id="4edb7-358">Call frame identifier.</span></span> <span data-ttu-id="4edb7-359">Este identificador solo es válido cuando el depurador está en pausa.</span><span class="sxs-lookup"><span data-stu-id="4edb7-359">This identifier is only valid while the debugger is paused.</span></span></td>
        </tr>
        <tr>
            <td><span data-ttu-id="4edb7-360">functionName</span><span class="sxs-lookup"><span data-stu-id="4edb7-360">functionName</span></span></td>
            <td><code class="flyout">string</code></td>
            <td><span data-ttu-id="4edb7-361">Nombre de la función de JavaScript a la que se llama en este marco de llamada.</span><span class="sxs-lookup"><span data-stu-id="4edb7-361">Name of the JavaScript function called on this call frame.</span></span></td>
        </tr>
        <tr>
            <td><span data-ttu-id="4edb7-362">functionLocation</span><span class="sxs-lookup"><span data-stu-id="4edb7-362">functionLocation</span></span> <br/> <i><span data-ttu-id="4edb7-363">opcional</span><span class="sxs-lookup"><span data-stu-id="4edb7-363">optional</span></span></i></td>
            <td><a href="#location"><code class="flyout">Location</code></a></td>
            <td><span><b><span data-ttu-id="4edb7-364">Montaje.</span><span class="sxs-lookup"><span data-stu-id="4edb7-364">Experimental.</span></span> </b></span><span data-ttu-id="4edb7-365">Ubicación en el código fuente.</span><span class="sxs-lookup"><span data-stu-id="4edb7-365">Location in the source code.</span></span></td>
        </tr>
        <tr>
            <td><span data-ttu-id="4edb7-366">Ubicación</span><span class="sxs-lookup"><span data-stu-id="4edb7-366">location</span></span></td>
            <td><a href="#location"><code class="flyout">Location</code></a></td>
            <td><span data-ttu-id="4edb7-367">Ubicación en el código fuente.</span><span class="sxs-lookup"><span data-stu-id="4edb7-367">Location in the source code.</span></span></td>
        </tr>
        <tr>
            <td><span data-ttu-id="4edb7-368">url</span><span class="sxs-lookup"><span data-stu-id="4edb7-368">url</span></span></td>
            <td><code class="flyout">string</code></td>
            <td><span data-ttu-id="4edb7-369">Nombre de script o URL de JavaScript.</span><span class="sxs-lookup"><span data-stu-id="4edb7-369">JavaScript script name or url.</span></span></td>
        </tr>
        <tr>
            <td><span data-ttu-id="4edb7-370">scopeChain</span><span class="sxs-lookup"><span data-stu-id="4edb7-370">scopeChain</span></span></td>
            <td><a href="#scope"><code class="flyout">Scope[]</code></a></td>
            <td><span data-ttu-id="4edb7-371">Cadena de ámbitos para este marco de llamada.</span><span class="sxs-lookup"><span data-stu-id="4edb7-371">Scope chain for this call frame.</span></span></td>
        </tr>
        <tr>
            <td><span data-ttu-id="4edb7-372">el</span><span class="sxs-lookup"><span data-stu-id="4edb7-372">this</span></span></td>
            <td><a href="runtime.md#remoteobject"><code class="flyout">Runtime.RemoteObject</code></a></td>
            <td><code>this</code> <span data-ttu-id="4edb7-373">objeto para este marco de llamada.</span><span class="sxs-lookup"><span data-stu-id="4edb7-373">object for this call frame.</span></span></td>
        </tr>
        <tr>
            <td><span data-ttu-id="4edb7-374">Vuelto</span><span class="sxs-lookup"><span data-stu-id="4edb7-374">returnValue</span></span> <br/> <i><span data-ttu-id="4edb7-375">opcional</span><span class="sxs-lookup"><span data-stu-id="4edb7-375">optional</span></span></i></td>
            <td><a href="runtime.md#remoteobject"><code class="flyout">Runtime.RemoteObject</code></a></td>
            <td><span data-ttu-id="4edb7-376">Valor que se devuelve, si la función está en el punto devuelto.</span><span class="sxs-lookup"><span data-stu-id="4edb7-376">The value being returned, if the function is at return point.</span></span></td>
        </tr>
    </tbody>
</table>
</p>

---

### <a name="scope"></a> <span data-ttu-id="4edb7-377">Ámbito</span><span class="sxs-lookup"><span data-stu-id="4edb7-377">Scope</span></span> `object`

<span data-ttu-id="4edb7-378">Descripción del ámbito.</span><span class="sxs-lookup"><span data-stu-id="4edb7-378">Scope description.</span></span>

<table>
    <thead>
        <tr>
            <th><span data-ttu-id="4edb7-379">Propiedades</span><span class="sxs-lookup"><span data-stu-id="4edb7-379">Properties</span></span></th>
            <th></th>
            <th></th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td><span data-ttu-id="4edb7-380">tipo</span><span class="sxs-lookup"><span data-stu-id="4edb7-380">type</span></span></td>
            <td><code class="flyout">string</code> <br/> <i><span data-ttu-id="4edb7-381">Valores permitidos: global, local, con, cierre, Catch, Block, script, eval, Module, Return</span><span class="sxs-lookup"><span data-stu-id="4edb7-381">Allowed values: global, local, with, closure, catch, block, script, eval, module, return</span></span></i></td>
            <td><span data-ttu-id="4edb7-382">Tipo de ámbito.</span><span class="sxs-lookup"><span data-stu-id="4edb7-382">Scope type.</span></span></td>
        </tr>
        <tr>
            <td><span data-ttu-id="4edb7-383">objeto</span><span class="sxs-lookup"><span data-stu-id="4edb7-383">object</span></span></td>
            <td><a href="runtime.md#remoteobject"><code class="flyout">Runtime.RemoteObject</code></a></td>
            <td><span data-ttu-id="4edb7-384">Objeto que representa el ámbito.</span><span class="sxs-lookup"><span data-stu-id="4edb7-384">Object representing the scope.</span></span> <span data-ttu-id="4edb7-385">Para <code>global</code> y <code>with</code> ámbitos, representa el objeto real; para el resto de los ámbitos, se trata de las variables de ámbito de la enumeración de objetos transitorias artificiales como sus propiedades.</span><span class="sxs-lookup"><span data-stu-id="4edb7-385">For <code>global</code> and <code>with</code> scopes it represents the actual object; for the rest of the scopes, it is artificial transient object enumerating scope variables as its properties.</span></span></td>
        </tr>
        <tr>
            <td><span data-ttu-id="4edb7-386">name</span><span class="sxs-lookup"><span data-stu-id="4edb7-386">name</span></span> <br/> <i><span data-ttu-id="4edb7-387">opcional</span><span class="sxs-lookup"><span data-stu-id="4edb7-387">optional</span></span></i></td>
            <td><code class="flyout">string</code></td>
            <td></td>
        </tr>
        <tr>
            <td><span data-ttu-id="4edb7-388">startLocation</span><span class="sxs-lookup"><span data-stu-id="4edb7-388">startLocation</span></span> <br/> <i><span data-ttu-id="4edb7-389">opcional</span><span class="sxs-lookup"><span data-stu-id="4edb7-389">optional</span></span></i></td>
            <td><a href="#location"><code class="flyout">Location</code></a></td>
            <td><span data-ttu-id="4edb7-390">Ubicación en el código fuente donde comienza el ámbito</span><span class="sxs-lookup"><span data-stu-id="4edb7-390">Location in the source code where scope starts</span></span></td>
        </tr>
        <tr>
            <td><span data-ttu-id="4edb7-391">endLocation</span><span class="sxs-lookup"><span data-stu-id="4edb7-391">endLocation</span></span> <br/> <i><span data-ttu-id="4edb7-392">opcional</span><span class="sxs-lookup"><span data-stu-id="4edb7-392">optional</span></span></i></td>
            <td><a href="#location"><code class="flyout">Location</code></a></td>
            <td><span data-ttu-id="4edb7-393">Ubicación en el código fuente donde el ámbito finaliza</span><span class="sxs-lookup"><span data-stu-id="4edb7-393">Location in the source code where scope ends</span></span></td>
        </tr>
    </tbody>
</table>
</p>

---

## <span data-ttu-id="4edb7-394">Dependencias</span><span class="sxs-lookup"><span data-stu-id="4edb7-394">Dependencies</span></span>

[<span data-ttu-id="4edb7-395">Motores</span><span class="sxs-lookup"><span data-stu-id="4edb7-395">Runtime</span></span>](runtime.md)