---
title: Classe de journalisation (System.Net)
ms.date: 06/12/2020
ms.technology: dotnet-networking
topic_type:
- apiref
api_name:
- System.Net.Logging
- System.Net.Logging.Associate
- System.Net.Logging.Enter
- System.Net.Logging.Exception
- System.Net.Logging.Exit
- System.Net.Logging.get_Http
- System.Net.Logging.get_On
api_location:
- System.dll
api_type:
- Assembly
ms.openlocfilehash: ad85fdd41252ed147eb5fe1a9db029db046d720c
ms.sourcegitcommit: 45c8eed045779b70a47b23169897459d0323dc89
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/18/2020
ms.locfileid: "84990389"
---
# <a name="logging-class"></a><span data-ttu-id="5cf36-102">Logging, classe</span><span class="sxs-lookup"><span data-stu-id="5cf36-102">Logging class</span></span>

<span data-ttu-id="5cf36-103">Fournit la fonctionnalité de journalisation de suivi.</span><span class="sxs-lookup"><span data-stu-id="5cf36-103">Provides trace logging functionality.</span></span>

```csharp
internal class Logging
```

> [!WARNING]
> <span data-ttu-id="5cf36-104">Cette classe est interne et n’est pas destinée à être utilisée directement dans votre code.</span><span class="sxs-lookup"><span data-stu-id="5cf36-104">This class is internal and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="5cf36-105">Microsoft ne prend pas en charge l’utilisation de cette classe dans une application de production en l’absence de toute circonstance.</span><span class="sxs-lookup"><span data-stu-id="5cf36-105">Microsoft does not support the use of this class in a production application under any circumstance.</span></span>

## <a name="associate-method"></a><span data-ttu-id="5cf36-106">Méthode Associate</span><span class="sxs-lookup"><span data-stu-id="5cf36-106">Associate method</span></span>

<span data-ttu-id="5cf36-107">Journalise les informations auxquelles deux objets sont associés.</span><span class="sxs-lookup"><span data-stu-id="5cf36-107">Logs information that two objects are associated with each other.</span></span>

```csharp
internal static void Associate(TraceSource traceSource, object objA, object objB)
```

### <a name="parameters"></a><span data-ttu-id="5cf36-108">Paramètres</span><span class="sxs-lookup"><span data-stu-id="5cf36-108">Parameters</span></span>

- <span data-ttu-id="5cf36-109">`traceSource` <xref:System.Diagnostics.TraceSource></span><span class="sxs-lookup"><span data-stu-id="5cf36-109">`traceSource` <xref:System.Diagnostics.TraceSource></span></span>

  <span data-ttu-id="5cf36-110">Source de suivi dans laquelle enregistrer l’événement.</span><span class="sxs-lookup"><span data-stu-id="5cf36-110">The trace source to log the event to.</span></span>

- <span data-ttu-id="5cf36-111">`objA` <xref:System.Object></span><span class="sxs-lookup"><span data-stu-id="5cf36-111">`objA` <xref:System.Object></span></span>

  <span data-ttu-id="5cf36-112">Objet à associer à `objB` .</span><span class="sxs-lookup"><span data-stu-id="5cf36-112">The object to associate with `objB`.</span></span>

- <span data-ttu-id="5cf36-113">`objB` <xref:System.Object></span><span class="sxs-lookup"><span data-stu-id="5cf36-113">`objB` <xref:System.Object></span></span>

  <span data-ttu-id="5cf36-114">Objet à associer à `objA` .</span><span class="sxs-lookup"><span data-stu-id="5cf36-114">The object to associate with `objA`.</span></span>

## <a name="entertracesource-object-string-string-method"></a><span data-ttu-id="5cf36-115">Enter (TraceSource, Object, String, String), méthode</span><span class="sxs-lookup"><span data-stu-id="5cf36-115">Enter(TraceSource, object, string, string) method</span></span>

<span data-ttu-id="5cf36-116">Journalise l’entrée dans une méthode.</span><span class="sxs-lookup"><span data-stu-id="5cf36-116">Logs entrance to a method.</span></span>

```csharp
internal static void Enter(TraceSource traceSource, object obj, string method, string param)
```

### <a name="parameters"></a><span data-ttu-id="5cf36-117">Paramètres</span><span class="sxs-lookup"><span data-stu-id="5cf36-117">Parameters</span></span>

- <span data-ttu-id="5cf36-118">`traceSource` <xref:System.Diagnostics.TraceSource></span><span class="sxs-lookup"><span data-stu-id="5cf36-118">`traceSource` <xref:System.Diagnostics.TraceSource></span></span>

  <span data-ttu-id="5cf36-119">Source de suivi dans laquelle enregistrer l’événement.</span><span class="sxs-lookup"><span data-stu-id="5cf36-119">The trace source to log the event to.</span></span>

- <span data-ttu-id="5cf36-120">`obj` <xref:System.Object></span><span class="sxs-lookup"><span data-stu-id="5cf36-120">`obj` <xref:System.Object></span></span>

  <span data-ttu-id="5cf36-121">Objet sur lequel la méthode a été appelée.</span><span class="sxs-lookup"><span data-stu-id="5cf36-121">The object that the method was called on.</span></span>

- <span data-ttu-id="5cf36-122">`method` <xref:System.String></span><span class="sxs-lookup"><span data-stu-id="5cf36-122">`method` <xref:System.String></span></span>

  <span data-ttu-id="5cf36-123">Méthode entrée.</span><span class="sxs-lookup"><span data-stu-id="5cf36-123">The method that is being entered.</span></span>

- <span data-ttu-id="5cf36-124">`param` <xref:System.String></span><span class="sxs-lookup"><span data-stu-id="5cf36-124">`param` <xref:System.String></span></span>

  <span data-ttu-id="5cf36-125">Paramètres passés à la méthode.</span><span class="sxs-lookup"><span data-stu-id="5cf36-125">The parameters that were passed to the method.</span></span>

## <a name="entertracesource-object-string-object-method"></a><span data-ttu-id="5cf36-126">Enter (TraceSource, Object, String, Object), méthode</span><span class="sxs-lookup"><span data-stu-id="5cf36-126">Enter(TraceSource, object, string, object) method</span></span>

<span data-ttu-id="5cf36-127">Journalise l’entrée dans une méthode.</span><span class="sxs-lookup"><span data-stu-id="5cf36-127">Logs entrance to a method.</span></span>

```csharp
internal static void Enter(TraceSource traceSource, object obj, string method, object paramObject)
```

### <a name="parameters"></a><span data-ttu-id="5cf36-128">Paramètres</span><span class="sxs-lookup"><span data-stu-id="5cf36-128">Parameters</span></span>

- <span data-ttu-id="5cf36-129">`traceSource` <xref:System.Diagnostics.TraceSource></span><span class="sxs-lookup"><span data-stu-id="5cf36-129">`traceSource` <xref:System.Diagnostics.TraceSource></span></span>

  <span data-ttu-id="5cf36-130">Source de suivi dans laquelle enregistrer l’événement.</span><span class="sxs-lookup"><span data-stu-id="5cf36-130">The trace source to log the event to.</span></span>

- <span data-ttu-id="5cf36-131">`obj` <xref:System.Object></span><span class="sxs-lookup"><span data-stu-id="5cf36-131">`obj` <xref:System.Object></span></span>

  <span data-ttu-id="5cf36-132">Objet sur lequel la méthode a été appelée.</span><span class="sxs-lookup"><span data-stu-id="5cf36-132">The object that the method was called on.</span></span>

- <span data-ttu-id="5cf36-133">`method` <xref:System.String></span><span class="sxs-lookup"><span data-stu-id="5cf36-133">`method` <xref:System.String></span></span>

  <span data-ttu-id="5cf36-134">Méthode entrée.</span><span class="sxs-lookup"><span data-stu-id="5cf36-134">The method that is being entered.</span></span>

- <span data-ttu-id="5cf36-135">`paramObject` <xref:System.Object></span><span class="sxs-lookup"><span data-stu-id="5cf36-135">`paramObject` <xref:System.Object></span></span>

  <span data-ttu-id="5cf36-136">Paramètres passés à la méthode.</span><span class="sxs-lookup"><span data-stu-id="5cf36-136">The parameters that were passed to the method.</span></span>

## <a name="entertracesource-string-string-string-method"></a><span data-ttu-id="5cf36-137">Enter (TraceSource, String, String, String), méthode</span><span class="sxs-lookup"><span data-stu-id="5cf36-137">Enter(TraceSource, string, string, string) method</span></span>

<span data-ttu-id="5cf36-138">Journalise l’entrée dans une méthode.</span><span class="sxs-lookup"><span data-stu-id="5cf36-138">Logs entrance to a method.</span></span>

```csharp
internal static void Enter(TraceSource traceSource, string obj, string method, string param)
```

### <a name="parameters"></a><span data-ttu-id="5cf36-139">Paramètres</span><span class="sxs-lookup"><span data-stu-id="5cf36-139">Parameters</span></span>

- <span data-ttu-id="5cf36-140">`traceSource` <xref:System.Diagnostics.TraceSource></span><span class="sxs-lookup"><span data-stu-id="5cf36-140">`traceSource` <xref:System.Diagnostics.TraceSource></span></span>

  <span data-ttu-id="5cf36-141">Source de suivi dans laquelle enregistrer l’événement.</span><span class="sxs-lookup"><span data-stu-id="5cf36-141">The trace source to log the event to.</span></span>

- <span data-ttu-id="5cf36-142">`obj` <xref:System.String></span><span class="sxs-lookup"><span data-stu-id="5cf36-142">`obj` <xref:System.String></span></span>

  <span data-ttu-id="5cf36-143">Objet sur lequel la méthode a été appelée.</span><span class="sxs-lookup"><span data-stu-id="5cf36-143">The object that the method was called on.</span></span>

- <span data-ttu-id="5cf36-144">`method` <xref:System.String></span><span class="sxs-lookup"><span data-stu-id="5cf36-144">`method` <xref:System.String></span></span>

  <span data-ttu-id="5cf36-145">Méthode entrée.</span><span class="sxs-lookup"><span data-stu-id="5cf36-145">The method that is being entered.</span></span>

- <span data-ttu-id="5cf36-146">`param` <xref:System.String></span><span class="sxs-lookup"><span data-stu-id="5cf36-146">`param` <xref:System.String></span></span>

  <span data-ttu-id="5cf36-147">Paramètres passés à la méthode.</span><span class="sxs-lookup"><span data-stu-id="5cf36-147">The parameters that were passed to the method.</span></span>

## <a name="entertracesource-string-string-object-method"></a><span data-ttu-id="5cf36-148">Enter (TraceSource, String, String, Object), méthode</span><span class="sxs-lookup"><span data-stu-id="5cf36-148">Enter(TraceSource, string, string, object) method</span></span>

<span data-ttu-id="5cf36-149">Journalise l’entrée dans une méthode.</span><span class="sxs-lookup"><span data-stu-id="5cf36-149">Logs entrance to a method.</span></span>

```csharp
internal static void Enter(TraceSource traceSource, string obj, string method, object paramObject)
```

### <a name="parameters"></a><span data-ttu-id="5cf36-150">Paramètres</span><span class="sxs-lookup"><span data-stu-id="5cf36-150">Parameters</span></span>

- <span data-ttu-id="5cf36-151">`traceSource` <xref:System.Diagnostics.TraceSource></span><span class="sxs-lookup"><span data-stu-id="5cf36-151">`traceSource` <xref:System.Diagnostics.TraceSource></span></span>

  <span data-ttu-id="5cf36-152">Source de suivi dans laquelle enregistrer l’événement.</span><span class="sxs-lookup"><span data-stu-id="5cf36-152">The trace source to log the event to.</span></span>

- <span data-ttu-id="5cf36-153">`obj` <xref:System.String></span><span class="sxs-lookup"><span data-stu-id="5cf36-153">`obj` <xref:System.String></span></span>

  <span data-ttu-id="5cf36-154">Objet sur lequel la méthode a été appelée.</span><span class="sxs-lookup"><span data-stu-id="5cf36-154">The object that the method was called on.</span></span>

- <span data-ttu-id="5cf36-155">`method` <xref:System.String></span><span class="sxs-lookup"><span data-stu-id="5cf36-155">`method` <xref:System.String></span></span>

  <span data-ttu-id="5cf36-156">Méthode entrée.</span><span class="sxs-lookup"><span data-stu-id="5cf36-156">The method that is being entered.</span></span>

- <span data-ttu-id="5cf36-157">`paramObject` <xref:System.Object></span><span class="sxs-lookup"><span data-stu-id="5cf36-157">`paramObject` <xref:System.Object></span></span>

  <span data-ttu-id="5cf36-158">Paramètres passés à la méthode.</span><span class="sxs-lookup"><span data-stu-id="5cf36-158">The parameters that were passed to the method.</span></span>

## <a name="entertracesource-string-string-method"></a><span data-ttu-id="5cf36-159">Méthode Enter (TraceSource, String, String)</span><span class="sxs-lookup"><span data-stu-id="5cf36-159">Enter(TraceSource, string, string) method</span></span>

<span data-ttu-id="5cf36-160">Journalise l’entrée dans une méthode.</span><span class="sxs-lookup"><span data-stu-id="5cf36-160">Logs entrance to a method.</span></span>

```csharp
internal static void Enter(TraceSource traceSource, string method, string parameters)
```

### <a name="parameters"></a><span data-ttu-id="5cf36-161">Paramètres</span><span class="sxs-lookup"><span data-stu-id="5cf36-161">Parameters</span></span>

- <span data-ttu-id="5cf36-162">`traceSource` <xref:System.Diagnostics.TraceSource></span><span class="sxs-lookup"><span data-stu-id="5cf36-162">`traceSource` <xref:System.Diagnostics.TraceSource></span></span>

  <span data-ttu-id="5cf36-163">Source de suivi dans laquelle enregistrer l’événement.</span><span class="sxs-lookup"><span data-stu-id="5cf36-163">The trace source to log the event to.</span></span>

- <span data-ttu-id="5cf36-164">`method` <xref:System.String></span><span class="sxs-lookup"><span data-stu-id="5cf36-164">`method` <xref:System.String></span></span>

  <span data-ttu-id="5cf36-165">Méthode entrée.</span><span class="sxs-lookup"><span data-stu-id="5cf36-165">The method that is being entered.</span></span>

- <span data-ttu-id="5cf36-166">`parameters` <xref:System.String></span><span class="sxs-lookup"><span data-stu-id="5cf36-166">`parameters` <xref:System.String></span></span>

  <span data-ttu-id="5cf36-167">Paramètres passés à la méthode.</span><span class="sxs-lookup"><span data-stu-id="5cf36-167">The parameters that were passed to the method.</span></span>

## <a name="entertracesource-string-method"></a><span data-ttu-id="5cf36-168">Enter (TraceSource, String), méthode</span><span class="sxs-lookup"><span data-stu-id="5cf36-168">Enter(TraceSource, string) method</span></span>

<span data-ttu-id="5cf36-169">Journalise l’entrée dans une méthode.</span><span class="sxs-lookup"><span data-stu-id="5cf36-169">Logs entrance to a method.</span></span>

```csharp
internal static void Enter(TraceSource traceSource, string msg)
```

### <a name="parameters"></a><span data-ttu-id="5cf36-170">Paramètres</span><span class="sxs-lookup"><span data-stu-id="5cf36-170">Parameters</span></span>

- <span data-ttu-id="5cf36-171">`traceSource` <xref:System.Diagnostics.TraceSource></span><span class="sxs-lookup"><span data-stu-id="5cf36-171">`traceSource` <xref:System.Diagnostics.TraceSource></span></span>

  <span data-ttu-id="5cf36-172">Source de suivi dans laquelle enregistrer l’événement.</span><span class="sxs-lookup"><span data-stu-id="5cf36-172">The trace source to log the event to.</span></span>

- <span data-ttu-id="5cf36-173">`msg` <xref:System.String></span><span class="sxs-lookup"><span data-stu-id="5cf36-173">`msg` <xref:System.String></span></span>

  <span data-ttu-id="5cf36-174">Message d’entrée à enregistrer dans la source de la trace.</span><span class="sxs-lookup"><span data-stu-id="5cf36-174">The entrance message to log to the trace source.</span></span>

## <a name="exception-method"></a><span data-ttu-id="5cf36-175">Exception (méthode)</span><span class="sxs-lookup"><span data-stu-id="5cf36-175">Exception method</span></span>

<span data-ttu-id="5cf36-176">Journalise une exception et restaure la mise en retrait.</span><span class="sxs-lookup"><span data-stu-id="5cf36-176">Logs an exception and restores indentation.</span></span>

```csharp
internal static void Exception(TraceSource traceSource, object obj, string method, Exception e)
```

### <a name="parameters"></a><span data-ttu-id="5cf36-177">Paramètres</span><span class="sxs-lookup"><span data-stu-id="5cf36-177">Parameters</span></span>

- <span data-ttu-id="5cf36-178">`traceSource` <xref:System.Diagnostics.TraceSource></span><span class="sxs-lookup"><span data-stu-id="5cf36-178">`traceSource` <xref:System.Diagnostics.TraceSource></span></span>

  <span data-ttu-id="5cf36-179">Source de suivi dans laquelle enregistrer l’événement.</span><span class="sxs-lookup"><span data-stu-id="5cf36-179">The trace source to log the event to.</span></span>

- <span data-ttu-id="5cf36-180">`obj` <xref:System.Object></span><span class="sxs-lookup"><span data-stu-id="5cf36-180">`obj` <xref:System.Object></span></span>

  <span data-ttu-id="5cf36-181">Objet sur lequel la méthode qui a levé une exception a été appelée.</span><span class="sxs-lookup"><span data-stu-id="5cf36-181">The object that the method that threw an exception was called on.</span></span>

- <span data-ttu-id="5cf36-182">`method` <xref:System.String></span><span class="sxs-lookup"><span data-stu-id="5cf36-182">`method` <xref:System.String></span></span>

  <span data-ttu-id="5cf36-183">Méthode qui a levé l’exception.</span><span class="sxs-lookup"><span data-stu-id="5cf36-183">The method that threw the exception.</span></span>

- <span data-ttu-id="5cf36-184">`e` <xref:System.Exception></span><span class="sxs-lookup"><span data-stu-id="5cf36-184">`e` <xref:System.Exception></span></span>

  <span data-ttu-id="5cf36-185">Exception qui a été levée.</span><span class="sxs-lookup"><span data-stu-id="5cf36-185">The exception that was thrown.</span></span>

## <a name="exittracesource-object-string-object-method"></a><span data-ttu-id="5cf36-186">Exit (TraceSource, Object, String, Object), méthode</span><span class="sxs-lookup"><span data-stu-id="5cf36-186">Exit(TraceSource, object, string, object) method</span></span>

<span data-ttu-id="5cf36-187">Les journaux quittent une fonction.</span><span class="sxs-lookup"><span data-stu-id="5cf36-187">Logs exit from a function.</span></span>

```csharp
internal static void Exit(TraceSource traceSource, object obj, string method, object retObject)
```

### <a name="parameters"></a><span data-ttu-id="5cf36-188">Paramètres</span><span class="sxs-lookup"><span data-stu-id="5cf36-188">Parameters</span></span>

- <span data-ttu-id="5cf36-189">`traceSource` <xref:System.Diagnostics.TraceSource></span><span class="sxs-lookup"><span data-stu-id="5cf36-189">`traceSource` <xref:System.Diagnostics.TraceSource></span></span>

  <span data-ttu-id="5cf36-190">Source de suivi dans laquelle enregistrer l’événement.</span><span class="sxs-lookup"><span data-stu-id="5cf36-190">The trace source to log the event to.</span></span>

- <span data-ttu-id="5cf36-191">`obj` <xref:System.Object></span><span class="sxs-lookup"><span data-stu-id="5cf36-191">`obj` <xref:System.Object></span></span>

  <span data-ttu-id="5cf36-192">Objet sur lequel la méthode a été appelée.</span><span class="sxs-lookup"><span data-stu-id="5cf36-192">The object that the method was called on.</span></span>

- <span data-ttu-id="5cf36-193">`method` <xref:System.String></span><span class="sxs-lookup"><span data-stu-id="5cf36-193">`method` <xref:System.String></span></span>

  <span data-ttu-id="5cf36-194">Méthode en cours de sortie.</span><span class="sxs-lookup"><span data-stu-id="5cf36-194">The method that is being exited.</span></span>

- <span data-ttu-id="5cf36-195">`retObject` <xref:System.Object></span><span class="sxs-lookup"><span data-stu-id="5cf36-195">`retObject` <xref:System.Object></span></span>

  <span data-ttu-id="5cf36-196">Valeur retournée par la méthode.</span><span class="sxs-lookup"><span data-stu-id="5cf36-196">The value that's being returned by the method.</span></span>

## <a name="exittracesource-string-string-object-method"></a><span data-ttu-id="5cf36-197">Exit (TraceSource, String, String, Object), méthode</span><span class="sxs-lookup"><span data-stu-id="5cf36-197">Exit(TraceSource, string, string, object) method</span></span>

<span data-ttu-id="5cf36-198">Les journaux quittent une fonction.</span><span class="sxs-lookup"><span data-stu-id="5cf36-198">Logs exit from a function.</span></span>

```csharp
internal static void Exit(TraceSource traceSource, string obj, string method, object retObject)
```

### <a name="parameters"></a><span data-ttu-id="5cf36-199">Paramètres</span><span class="sxs-lookup"><span data-stu-id="5cf36-199">Parameters</span></span>

- <span data-ttu-id="5cf36-200">`traceSource` <xref:System.Diagnostics.TraceSource></span><span class="sxs-lookup"><span data-stu-id="5cf36-200">`traceSource` <xref:System.Diagnostics.TraceSource></span></span>

  <span data-ttu-id="5cf36-201">Source de suivi dans laquelle enregistrer l’événement.</span><span class="sxs-lookup"><span data-stu-id="5cf36-201">The trace source to log the event to.</span></span>

- <span data-ttu-id="5cf36-202">`obj` <xref:System.String></span><span class="sxs-lookup"><span data-stu-id="5cf36-202">`obj` <xref:System.String></span></span>

  <span data-ttu-id="5cf36-203">Objet sur lequel la méthode a été appelée.</span><span class="sxs-lookup"><span data-stu-id="5cf36-203">The object that the method was called on.</span></span>

- <span data-ttu-id="5cf36-204">`method` <xref:System.String></span><span class="sxs-lookup"><span data-stu-id="5cf36-204">`method` <xref:System.String></span></span>

  <span data-ttu-id="5cf36-205">Méthode en cours de sortie.</span><span class="sxs-lookup"><span data-stu-id="5cf36-205">The method that is being exited.</span></span>

- <span data-ttu-id="5cf36-206">`retObject` <xref:System.Object></span><span class="sxs-lookup"><span data-stu-id="5cf36-206">`retObject` <xref:System.Object></span></span>

  <span data-ttu-id="5cf36-207">Valeur retournée par la méthode.</span><span class="sxs-lookup"><span data-stu-id="5cf36-207">The value that's being returned by the method.</span></span>

## <a name="exittracesource-object-string-string-method"></a><span data-ttu-id="5cf36-208">Exit (TraceSource, Object, String, String), méthode</span><span class="sxs-lookup"><span data-stu-id="5cf36-208">Exit(TraceSource, object, string, string) method</span></span>

<span data-ttu-id="5cf36-209">Les journaux quittent une fonction.</span><span class="sxs-lookup"><span data-stu-id="5cf36-209">Logs exit from a function.</span></span>

```csharp
internal static void Exit(TraceSource traceSource, object obj, string method, string retValue)
```

### <a name="parameters"></a><span data-ttu-id="5cf36-210">Paramètres</span><span class="sxs-lookup"><span data-stu-id="5cf36-210">Parameters</span></span>

- <span data-ttu-id="5cf36-211">`traceSource` <xref:System.Diagnostics.TraceSource></span><span class="sxs-lookup"><span data-stu-id="5cf36-211">`traceSource` <xref:System.Diagnostics.TraceSource></span></span>

  <span data-ttu-id="5cf36-212">Source de suivi dans laquelle enregistrer l’événement.</span><span class="sxs-lookup"><span data-stu-id="5cf36-212">The trace source to log the event to.</span></span>

- <span data-ttu-id="5cf36-213">`obj` <xref:System.Object></span><span class="sxs-lookup"><span data-stu-id="5cf36-213">`obj` <xref:System.Object></span></span>

  <span data-ttu-id="5cf36-214">Objet sur lequel la méthode a été appelée.</span><span class="sxs-lookup"><span data-stu-id="5cf36-214">The object that the method was called on.</span></span>

- <span data-ttu-id="5cf36-215">`method` <xref:System.String></span><span class="sxs-lookup"><span data-stu-id="5cf36-215">`method` <xref:System.String></span></span>

  <span data-ttu-id="5cf36-216">Méthode en cours de sortie.</span><span class="sxs-lookup"><span data-stu-id="5cf36-216">The method that is being exited.</span></span>

- <span data-ttu-id="5cf36-217">`retValue` <xref:System.String></span><span class="sxs-lookup"><span data-stu-id="5cf36-217">`retValue` <xref:System.String></span></span>

  <span data-ttu-id="5cf36-218">Valeur retournée par la méthode.</span><span class="sxs-lookup"><span data-stu-id="5cf36-218">The value that's being returned by the method.</span></span>

## <a name="exittracesource-string-string-string-method"></a><span data-ttu-id="5cf36-219">Exit (TraceSource, String, String, String), méthode</span><span class="sxs-lookup"><span data-stu-id="5cf36-219">Exit(TraceSource, string, string, string) method</span></span>

<span data-ttu-id="5cf36-220">Les journaux quittent une fonction.</span><span class="sxs-lookup"><span data-stu-id="5cf36-220">Logs exit from a function.</span></span>

```csharp
internal static void Exit(TraceSource traceSource, string obj, string method, string retValue)
```

### <a name="parameters"></a><span data-ttu-id="5cf36-221">Paramètres</span><span class="sxs-lookup"><span data-stu-id="5cf36-221">Parameters</span></span>

- <span data-ttu-id="5cf36-222">`traceSource` <xref:System.Diagnostics.TraceSource></span><span class="sxs-lookup"><span data-stu-id="5cf36-222">`traceSource` <xref:System.Diagnostics.TraceSource></span></span>

  <span data-ttu-id="5cf36-223">Source de suivi dans laquelle enregistrer l’événement.</span><span class="sxs-lookup"><span data-stu-id="5cf36-223">The trace source to log the event to.</span></span>

- <span data-ttu-id="5cf36-224">`obj` <xref:System.String></span><span class="sxs-lookup"><span data-stu-id="5cf36-224">`obj` <xref:System.String></span></span>

  <span data-ttu-id="5cf36-225">Objet sur lequel la méthode a été appelée.</span><span class="sxs-lookup"><span data-stu-id="5cf36-225">The object that the method was called on.</span></span>

- <span data-ttu-id="5cf36-226">`method` <xref:System.String></span><span class="sxs-lookup"><span data-stu-id="5cf36-226">`method` <xref:System.String></span></span>

  <span data-ttu-id="5cf36-227">Méthode en cours de sortie.</span><span class="sxs-lookup"><span data-stu-id="5cf36-227">The method that is being exited.</span></span>

- <span data-ttu-id="5cf36-228">`retValue` <xref:System.String></span><span class="sxs-lookup"><span data-stu-id="5cf36-228">`retValue` <xref:System.String></span></span>

  <span data-ttu-id="5cf36-229">Valeur retournée par la méthode.</span><span class="sxs-lookup"><span data-stu-id="5cf36-229">The value that's being returned by the method.</span></span>

## <a name="exittracesource-string-string-method"></a><span data-ttu-id="5cf36-230">Exit (TraceSource, String, String), méthode</span><span class="sxs-lookup"><span data-stu-id="5cf36-230">Exit(TraceSource, string, string) method</span></span>

<span data-ttu-id="5cf36-231">Les journaux quittent une fonction.</span><span class="sxs-lookup"><span data-stu-id="5cf36-231">Logs exit from a function.</span></span>

```csharp
internal static void Exit(TraceSource traceSource, string method, string parameters)
```

### <a name="parameters"></a><span data-ttu-id="5cf36-232">Paramètres</span><span class="sxs-lookup"><span data-stu-id="5cf36-232">Parameters</span></span>

- <span data-ttu-id="5cf36-233">`traceSource` <xref:System.Diagnostics.TraceSource></span><span class="sxs-lookup"><span data-stu-id="5cf36-233">`traceSource` <xref:System.Diagnostics.TraceSource></span></span>

  <span data-ttu-id="5cf36-234">Source de suivi dans laquelle enregistrer l’événement.</span><span class="sxs-lookup"><span data-stu-id="5cf36-234">The trace source to log the event to.</span></span>

- <span data-ttu-id="5cf36-235">`method` <xref:System.String></span><span class="sxs-lookup"><span data-stu-id="5cf36-235">`method` <xref:System.String></span></span>

  <span data-ttu-id="5cf36-236">Méthode en cours de sortie.</span><span class="sxs-lookup"><span data-stu-id="5cf36-236">The method that is being exited.</span></span>

- <span data-ttu-id="5cf36-237">`parameters` <xref:System.String></span><span class="sxs-lookup"><span data-stu-id="5cf36-237">`parameters` <xref:System.String></span></span>

  <span data-ttu-id="5cf36-238">Paramètres passés à la méthode en cours de sortie.</span><span class="sxs-lookup"><span data-stu-id="5cf36-238">The parameters that were passed to the method that's being exited.</span></span>

## <a name="exittracesource-string-method"></a><span data-ttu-id="5cf36-239">Exit (TraceSource, String), méthode</span><span class="sxs-lookup"><span data-stu-id="5cf36-239">Exit(TraceSource, string) method</span></span>

<span data-ttu-id="5cf36-240">Les journaux quittent une fonction.</span><span class="sxs-lookup"><span data-stu-id="5cf36-240">Logs exit from a function.</span></span>

```csharp
internal static void Exit(TraceSource traceSource, string msg)
```

### <a name="parameters"></a><span data-ttu-id="5cf36-241">Paramètres</span><span class="sxs-lookup"><span data-stu-id="5cf36-241">Parameters</span></span>

- <span data-ttu-id="5cf36-242">`traceSource` <xref:System.Diagnostics.TraceSource></span><span class="sxs-lookup"><span data-stu-id="5cf36-242">`traceSource` <xref:System.Diagnostics.TraceSource></span></span>

  <span data-ttu-id="5cf36-243">Source de suivi dans laquelle enregistrer l’événement.</span><span class="sxs-lookup"><span data-stu-id="5cf36-243">The trace source to log the event to.</span></span>

- <span data-ttu-id="5cf36-244">`msg` <xref:System.String></span><span class="sxs-lookup"><span data-stu-id="5cf36-244">`msg` <xref:System.String></span></span>

  <span data-ttu-id="5cf36-245">Message de sortie à enregistrer dans la source de la trace.</span><span class="sxs-lookup"><span data-stu-id="5cf36-245">The exit message to log to the trace source.</span></span>

## <a name="http-property"></a><span data-ttu-id="5cf36-246">Propriété http</span><span class="sxs-lookup"><span data-stu-id="5cf36-246">Http property</span></span>

<span data-ttu-id="5cf36-247">Obtient la source de suivi pour « System .net. http ».</span><span class="sxs-lookup"><span data-stu-id="5cf36-247">Gets the trace source for "System.Net.Http".</span></span>

```csharp
internal static TraceSource Http { get; }
```

### <a name="property-value"></a><span data-ttu-id="5cf36-248">Valeur de la propriété</span><span class="sxs-lookup"><span data-stu-id="5cf36-248">Property value</span></span>

<xref:System.Diagnostics.TraceSource>\
<span data-ttu-id="5cf36-249">Source de suivi pour « System .net. http », ou `null` si la journalisation n’est pas activée.</span><span class="sxs-lookup"><span data-stu-id="5cf36-249">The trace source for "System.Net.Http", or `null` if logging is not enabled.</span></span>

## <a name="on-property"></a><span data-ttu-id="5cf36-250">Sur la propriété</span><span class="sxs-lookup"><span data-stu-id="5cf36-250">On property</span></span>

<span data-ttu-id="5cf36-251">Obtient une valeur qui indique si la journalisation est activée.</span><span class="sxs-lookup"><span data-stu-id="5cf36-251">Gets a value that indicates whether logging is enabled.</span></span>

```csharp
internal static bool On { get; }
```

### <a name="property-value"></a><span data-ttu-id="5cf36-252">Valeur de la propriété</span><span class="sxs-lookup"><span data-stu-id="5cf36-252">Property value</span></span>

<xref:System.Boolean>\
<span data-ttu-id="5cf36-253">`true` si la journalisation est activée ; sinon `false`.</span><span class="sxs-lookup"><span data-stu-id="5cf36-253">`true` if logging is enabled; otherwise, `false`.</span></span>

## <a name="requirements"></a><span data-ttu-id="5cf36-254">Spécifications</span><span class="sxs-lookup"><span data-stu-id="5cf36-254">Requirements</span></span>

<span data-ttu-id="5cf36-255">**Espace de noms :** <xref:System.Net></span><span class="sxs-lookup"><span data-stu-id="5cf36-255">**Namespace:** <xref:System.Net></span></span>

<span data-ttu-id="5cf36-256">**Assembly :** Système (en System.dll)</span><span class="sxs-lookup"><span data-stu-id="5cf36-256">**Assembly:** System (in System.dll)</span></span>
