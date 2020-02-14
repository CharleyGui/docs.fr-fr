---
title: Assistant Débogage managé gcManagedToUnmanaged
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
ms.openlocfilehash: f7e6334e20a6e0db1d52307a833de0ecd0d74cc4
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/14/2020
ms.locfileid: "77217478"
---
# <a name="gcmanagedtounmanaged-mda"></a><span data-ttu-id="8ac53-102">Assistant Débogage managé gcManagedToUnmanaged</span><span class="sxs-lookup"><span data-stu-id="8ac53-102">gcManagedToUnmanaged MDA</span></span>
<span data-ttu-id="8ac53-103">L'Assistant Débogage managé (MDA) `gcManagedToUnmanaged` déclenche une opération garbage collection chaque fois qu'un thread effectue la transition du code managé au code non managé.</span><span class="sxs-lookup"><span data-stu-id="8ac53-103">The `gcManagedToUnmanaged` managed debugging assistant (MDA) causes a garbage collection whenever a thread transitions from managed to unmanaged code.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="8ac53-104">Symptômes</span><span class="sxs-lookup"><span data-stu-id="8ac53-104">Symptoms</span></span>  
 <span data-ttu-id="8ac53-105">Un composant utilisateur non managé lève une violation d'accès lors de la tentative d'utilisation d'un objet managé qui avait été exposé à COM.</span><span class="sxs-lookup"><span data-stu-id="8ac53-105">An unmanaged user component throws an access violation when trying to use a managed object that had been exposed to COM.</span></span> <span data-ttu-id="8ac53-106">L’objet COM semble avoir été libéré.</span><span class="sxs-lookup"><span data-stu-id="8ac53-106">The COM object appears to have been released.</span></span> <span data-ttu-id="8ac53-107">La violation d'accès est non déterministe.</span><span class="sxs-lookup"><span data-stu-id="8ac53-107">The access violation is nondeterministic.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="8ac53-108">Cause :</span><span class="sxs-lookup"><span data-stu-id="8ac53-108">Cause</span></span>  
 <span data-ttu-id="8ac53-109">Si un composant non managé n'effectue pas correctement le décompte de références d'un objet COM managé, le runtime peut collecter un objet managé exposé à COM lorsque le composant non managé détient encore une référence à l'objet.</span><span class="sxs-lookup"><span data-stu-id="8ac53-109">If an unmanaged component is not reference counting a managed COM object correctly, then the runtime could collect a managed object exposed to COM when the unmanaged component still holds a reference to the object.</span></span> <span data-ttu-id="8ac53-110">Le runtime appelle <xref:System.Runtime.InteropServices.Marshal.Release%2A> pendant les opérations garbage collection. Par conséquent, si le composant utilisateur a recours à l’objet avant l’opération garbage collection, il n’aura pas encore été collecté.</span><span class="sxs-lookup"><span data-stu-id="8ac53-110">The runtime calls <xref:System.Runtime.InteropServices.Marshal.Release%2A> during garbage collections, so if the user component uses the object before the garbage collection occurs, then it will not yet have been collected.</span></span> <span data-ttu-id="8ac53-111">Cela explique le non-déterminisme.</span><span class="sxs-lookup"><span data-stu-id="8ac53-111">This is the source of the nondeterminism.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="8ac53-112">Résolution</span><span class="sxs-lookup"><span data-stu-id="8ac53-112">Resolution</span></span>  
 <span data-ttu-id="8ac53-113">L’activation de cet assistant réduit le laps de temps entre le moment où l’objet peut participer à une collection et le moment où <xref:System.Runtime.InteropServices.Marshal.Release%2A> est appelé, ce qui facilite la localisation du composant non managé qui tente en premier d’accéder à l’objet récupéré par le garbage collector.</span><span class="sxs-lookup"><span data-stu-id="8ac53-113">Enabling this assistant reduces the time between when the object is eligible for collection and <xref:System.Runtime.InteropServices.Marshal.Release%2A> is called, helping to track down which unmanaged component first tries to access the collected object.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="8ac53-114">Effet sur le runtime</span><span class="sxs-lookup"><span data-stu-id="8ac53-114">Effect on the Runtime</span></span>  
 <span data-ttu-id="8ac53-115">Provoque une opération garbage collection chaque fois qu'un thread effectue la transition du code managé au code non managé.</span><span class="sxs-lookup"><span data-stu-id="8ac53-115">Causes a garbage collection whenever a thread transitions from managed to unmanaged code.</span></span>  
  
## <a name="output"></a><span data-ttu-id="8ac53-116">Output</span><span class="sxs-lookup"><span data-stu-id="8ac53-116">Output</span></span>  
 <span data-ttu-id="8ac53-117">Cet Assistant Débogage managé ne produit aucune sortie.</span><span class="sxs-lookup"><span data-stu-id="8ac53-117">This MDA produces no output.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="8ac53-118">Configuration</span><span class="sxs-lookup"><span data-stu-id="8ac53-118">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <gcManagedToUnmanaged/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="8ac53-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8ac53-119">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="8ac53-120">Diagnostic d’erreurs avec les Assistants Débogage managé</span><span class="sxs-lookup"><span data-stu-id="8ac53-120">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="8ac53-121">Marshaling d'interopérabilité</span><span class="sxs-lookup"><span data-stu-id="8ac53-121">Interop Marshaling</span></span>](../interop/interop-marshaling.md)
- [<span data-ttu-id="8ac53-122">gcUnmanagedToManaged</span><span class="sxs-lookup"><span data-stu-id="8ac53-122">gcUnmanagedToManaged</span></span>](gcunmanagedtomanaged-mda.md)
