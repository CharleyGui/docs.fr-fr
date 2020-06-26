---
title: Assistant Débogage managé gcManagedToUnmanaged
description: Passez en revue l’Assistant Débogage managé gcManagedToUnmanaged. Cet Assistant Débogage managé peut s’activer en raison d’une garbage collection prématurée pendant la transition vers du code non managé.
ms.date: 03/30/2017
helpviewer_keywords:
- MDAs (managed debugging assistants), garbage collection
- GcManagedToUnmanaged MDA
- GC managed to unmanaged
- transitioning threads managed to unmanaged code
- threading [.NET Framework], garbage collection
- managed to unmanaged garbage collection
- managed debugging assistants (MDAs), garbage collection
- threading [.NET Framework], managed debugging assistants
- garbage collection, run-time errors
ms.assetid: 7417f837-805e-4fed-a430-ca919c8421dc
ms.openlocfilehash: 76c621a1f2bb780d38228f2a84d4c77441774770
ms.sourcegitcommit: a2c8b19e813a52b91facbb5d7e3c062c7188b457
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/26/2020
ms.locfileid: "85415912"
---
# <a name="gcmanagedtounmanaged-mda"></a><span data-ttu-id="d7cfc-104">Assistant Débogage managé gcManagedToUnmanaged</span><span class="sxs-lookup"><span data-stu-id="d7cfc-104">gcManagedToUnmanaged MDA</span></span>
<span data-ttu-id="d7cfc-105">L'Assistant Débogage managé (MDA) `gcManagedToUnmanaged` déclenche une opération garbage collection chaque fois qu'un thread effectue la transition du code managé au code non managé.</span><span class="sxs-lookup"><span data-stu-id="d7cfc-105">The `gcManagedToUnmanaged` managed debugging assistant (MDA) causes a garbage collection whenever a thread transitions from managed to unmanaged code.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="d7cfc-106">Symptômes</span><span class="sxs-lookup"><span data-stu-id="d7cfc-106">Symptoms</span></span>  
 <span data-ttu-id="d7cfc-107">Un composant utilisateur non managé lève une violation d'accès lors de la tentative d'utilisation d'un objet managé qui avait été exposé à COM.</span><span class="sxs-lookup"><span data-stu-id="d7cfc-107">An unmanaged user component throws an access violation when trying to use a managed object that had been exposed to COM.</span></span> <span data-ttu-id="d7cfc-108">L’objet COM semble avoir été libéré.</span><span class="sxs-lookup"><span data-stu-id="d7cfc-108">The COM object appears to have been released.</span></span> <span data-ttu-id="d7cfc-109">La violation d'accès est non déterministe.</span><span class="sxs-lookup"><span data-stu-id="d7cfc-109">The access violation is nondeterministic.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="d7cfc-110">Cause</span><span class="sxs-lookup"><span data-stu-id="d7cfc-110">Cause</span></span>  
 <span data-ttu-id="d7cfc-111">Si un composant non managé n'effectue pas correctement le décompte de références d'un objet COM managé, le runtime peut collecter un objet managé exposé à COM lorsque le composant non managé détient encore une référence à l'objet.</span><span class="sxs-lookup"><span data-stu-id="d7cfc-111">If an unmanaged component is not reference counting a managed COM object correctly, then the runtime could collect a managed object exposed to COM when the unmanaged component still holds a reference to the object.</span></span> <span data-ttu-id="d7cfc-112">Le runtime appelle <xref:System.Runtime.InteropServices.Marshal.Release%2A> pendant les opérations garbage collection. Par conséquent, si le composant utilisateur a recours à l’objet avant l’opération garbage collection, il n’aura pas encore été collecté.</span><span class="sxs-lookup"><span data-stu-id="d7cfc-112">The runtime calls <xref:System.Runtime.InteropServices.Marshal.Release%2A> during garbage collections, so if the user component uses the object before the garbage collection occurs, then it will not yet have been collected.</span></span> <span data-ttu-id="d7cfc-113">Cela explique le non-déterminisme.</span><span class="sxs-lookup"><span data-stu-id="d7cfc-113">This is the source of the nondeterminism.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="d7cfc-114">Résolution</span><span class="sxs-lookup"><span data-stu-id="d7cfc-114">Resolution</span></span>  
 <span data-ttu-id="d7cfc-115">L’activation de cet assistant réduit le laps de temps entre le moment où l’objet peut participer à une collection et le moment où <xref:System.Runtime.InteropServices.Marshal.Release%2A> est appelé, ce qui facilite la localisation du composant non managé qui tente en premier d’accéder à l’objet récupéré par le garbage collector.</span><span class="sxs-lookup"><span data-stu-id="d7cfc-115">Enabling this assistant reduces the time between when the object is eligible for collection and <xref:System.Runtime.InteropServices.Marshal.Release%2A> is called, helping to track down which unmanaged component first tries to access the collected object.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="d7cfc-116">Effet sur le runtime</span><span class="sxs-lookup"><span data-stu-id="d7cfc-116">Effect on the Runtime</span></span>  
 <span data-ttu-id="d7cfc-117">Provoque une opération garbage collection chaque fois qu'un thread effectue la transition du code managé au code non managé.</span><span class="sxs-lookup"><span data-stu-id="d7cfc-117">Causes a garbage collection whenever a thread transitions from managed to unmanaged code.</span></span>  
  
## <a name="output"></a><span data-ttu-id="d7cfc-118">Output</span><span class="sxs-lookup"><span data-stu-id="d7cfc-118">Output</span></span>  
 <span data-ttu-id="d7cfc-119">Cet Assistant Débogage managé ne produit aucune sortie.</span><span class="sxs-lookup"><span data-stu-id="d7cfc-119">This MDA produces no output.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="d7cfc-120">Configuration</span><span class="sxs-lookup"><span data-stu-id="d7cfc-120">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <gcManagedToUnmanaged/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="d7cfc-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d7cfc-121">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="d7cfc-122">Diagnostic d’erreurs avec les Assistants Débogage managé</span><span class="sxs-lookup"><span data-stu-id="d7cfc-122">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="d7cfc-123">Marshaling d’interopérabilité</span><span class="sxs-lookup"><span data-stu-id="d7cfc-123">Interop Marshaling</span></span>](../interop/interop-marshaling.md)
- [<span data-ttu-id="d7cfc-124">gcUnmanagedToManaged</span><span class="sxs-lookup"><span data-stu-id="d7cfc-124">gcUnmanagedToManaged</span></span>](gcunmanagedtomanaged-mda.md)
