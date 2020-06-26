---
title: Assistant Débogage managé gcUnmanagedToManaged
description: Passez en revue l’Assistant Débogage managé gcManagedToUnmanaged dans .NET. Cet Assistant Débogage managé peut s’activer en raison d’une altération du tas de mémoire pendant la transition vers du code managé.
ms.date: 03/30/2017
helpviewer_keywords:
- MDAs (managed debugging assistants), garbage collection
- GC unmanaged to managed
- transitioning threads unmanaged to managed code
- GcUnmanagedToManaged MDA
- threading [.NET Framework], garbage collection
- managed debugging assistants (MDAs), garbage collection
- threading [.NET Framework], managed debugging assistants
- garbage collection, run-time errors
- unmanaged to managed garbage collection
ms.assetid: 103eb3a3-1cf0-4406-8a9a-a7798fdc22d1
ms.openlocfilehash: 320d55224e6a204d330447d6c68eabe0fa6cf892
ms.sourcegitcommit: a2c8b19e813a52b91facbb5d7e3c062c7188b457
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/26/2020
ms.locfileid: "85415899"
---
# <a name="gcunmanagedtomanaged-mda"></a><span data-ttu-id="6d2c3-104">Assistant Débogage managé gcUnmanagedToManaged</span><span class="sxs-lookup"><span data-stu-id="6d2c3-104">gcUnmanagedToManaged MDA</span></span>
<span data-ttu-id="6d2c3-105">L'Assistant Débogage managé (MDA) `gcUnmanagedToManaged` déclenche une opération garbage collection chaque fois qu'un thread effectue la transition du code non managé au code managé.</span><span class="sxs-lookup"><span data-stu-id="6d2c3-105">The `gcUnmanagedToManaged` managed debugging assistant (MDA) causes a garbage collection whenever a thread transitions from unmanaged to managed code.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="6d2c3-106">Symptômes</span><span class="sxs-lookup"><span data-stu-id="6d2c3-106">Symptoms</span></span>  
 <span data-ttu-id="6d2c3-107">Une application exécutant des composants utilisateur non managés à l'aide de COM et d'appels de code non managé provoque une violation d'accès non déterministe dans le CLR.</span><span class="sxs-lookup"><span data-stu-id="6d2c3-107">An application running unmanaged user components using COM and platform invoke is causing a nondeterministic access violation in the CLR.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="6d2c3-108">Cause</span><span class="sxs-lookup"><span data-stu-id="6d2c3-108">Cause</span></span>  
 <span data-ttu-id="6d2c3-109">Si une application exécute des composants utilisateur non managés, il se peut que ces composants aient endommagé le tas obtenu à l'issue d'une opération garbage collection.</span><span class="sxs-lookup"><span data-stu-id="6d2c3-109">If an application is running unmanaged user components, then those components might have corrupted the garbage-collected heap.</span></span> <span data-ttu-id="6d2c3-110">Cela provoque une violation d'accès dans le CLR quand le garbage collector tente de parcourir le graphique d'objet.</span><span class="sxs-lookup"><span data-stu-id="6d2c3-110">This causes an access violation in the CLR when the garbage collector tries to walk the object graph.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="6d2c3-111">Résolution</span><span class="sxs-lookup"><span data-stu-id="6d2c3-111">Resolution</span></span>  
 <span data-ttu-id="6d2c3-112">L'activation de cet assistant réduit la durée entre le moment où le composant non managé endommage le tas obtenu à l'issue d'une opération garbage collection et le moment de la violation d'accès en obligeant l'exécution d'une opération garbage collection avant chaque transition managée.</span><span class="sxs-lookup"><span data-stu-id="6d2c3-112">Enabling this assistant reduces the time between when the unmanaged component corrupts the garbage-collected heap and when the access violation happens by forcing a garbage collection to occur before every managed transition.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="6d2c3-113">Effet sur le runtime</span><span class="sxs-lookup"><span data-stu-id="6d2c3-113">Effect on the Runtime</span></span>  
 <span data-ttu-id="6d2c3-114">Provoque une opération garbage collection chaque fois qu’un thread effectue la transition du code non managé au code managé.</span><span class="sxs-lookup"><span data-stu-id="6d2c3-114">Causes a garbage collection whenever a thread transitions from unmanaged to managed code.</span></span>  
  
## <a name="output"></a><span data-ttu-id="6d2c3-115">Output</span><span class="sxs-lookup"><span data-stu-id="6d2c3-115">Output</span></span>  
 <span data-ttu-id="6d2c3-116">Cet Assistant Débogage managé ne produit aucune sortie.</span><span class="sxs-lookup"><span data-stu-id="6d2c3-116">This MDA produces no output.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="6d2c3-117">Configuration</span><span class="sxs-lookup"><span data-stu-id="6d2c3-117">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <gcUnmanagedToManaged/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="6d2c3-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6d2c3-118">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="6d2c3-119">Diagnostic d’erreurs avec les Assistants Débogage managé</span><span class="sxs-lookup"><span data-stu-id="6d2c3-119">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="6d2c3-120">gcManagedToUnmanaged</span><span class="sxs-lookup"><span data-stu-id="6d2c3-120">gcManagedToUnmanaged</span></span>](gcmanagedtounmanaged-mda.md)
- [<span data-ttu-id="6d2c3-121">Marshaling d’interopérabilité</span><span class="sxs-lookup"><span data-stu-id="6d2c3-121">Interop Marshaling</span></span>](../interop/interop-marshaling.md)
