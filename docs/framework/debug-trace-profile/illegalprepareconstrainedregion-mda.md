---
title: Assistant Débogage managé illegalPrepareConstrainedRegion
description: Passez en revue l’Assistant Débogage managé illegalPrepareConstrainedRegion, appelé si un appel PrepareConstrainedRegions n’est pas suivi d’une instruction try.
ms.date: 03/30/2017
helpviewer_keywords:
- PrepareConstrainedRegions method
- managed debugging assistants (MDAs), illegal PrepareConstrainedRegions
- try/catch exception handling, managed debugging assistants
- IllegalPrepareConstrainedRegions MDA
- MDAs (managed debugging assistants), illegal PrepareConstrainedRegions
ms.assetid: 2f9b5031-f910-4e01-a196-f89eab313eaf
ms.openlocfilehash: d6a0d1d95840ebd735806c5547730ae9e0b2aace
ms.sourcegitcommit: 0edbeb66d71b8df10fcb374cfca4d731b58ccdb2
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "86051283"
---
# <a name="illegalprepareconstrainedregion-mda"></a><span data-ttu-id="45400-103">Assistant Débogage managé illegalPrepareConstrainedRegion</span><span class="sxs-lookup"><span data-stu-id="45400-103">illegalPrepareConstrainedRegion MDA</span></span>
<span data-ttu-id="45400-104">L’Assistant Débogage managé `illegalPrepareConstrainedRegion` est activé quand un appel de méthode <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A?displayProperty=nameWithType> ne précède pas immédiatement l’instruction `try` du gestionnaire d’exceptions.</span><span class="sxs-lookup"><span data-stu-id="45400-104">The `illegalPrepareConstrainedRegion` managed debugging assistant (MDA) is activated when a <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A?displayProperty=nameWithType> method call does not immediately precede the `try` statement of the exception handler.</span></span> <span data-ttu-id="45400-105">Cette restriction étant au niveau MSIL, il est permis d’avoir une source générant du non-code entre l’appel et `try`, telle que les commentaires.</span><span class="sxs-lookup"><span data-stu-id="45400-105">This restriction is at the MSIL level, so it is permissible to have non-code-generating source between the call and the `try`, such as comments.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="45400-106">Symptômes</span><span class="sxs-lookup"><span data-stu-id="45400-106">Symptoms</span></span>  
 <span data-ttu-id="45400-107">Une région d’exécution limitée n’est jamais traitée comme telle, mais comme un bloc de gestion des exceptions simple (`finally` ou `catch`).</span><span class="sxs-lookup"><span data-stu-id="45400-107">A constrained execution region (CER) that is never treated as such, but as a simple exception handling block (`finally` or `catch`).</span></span> <span data-ttu-id="45400-108">Par conséquent, la région ne s’exécute pas en cas de mémoire insuffisante ou d’interruption de thread.</span><span class="sxs-lookup"><span data-stu-id="45400-108">As a consequence, the region does not run in the event of an out-of-memory condition or a thread abort.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="45400-109">Cause</span><span class="sxs-lookup"><span data-stu-id="45400-109">Cause</span></span>  
 <span data-ttu-id="45400-110">Le modèle de préparation pour une région d’exécution limitée n’est pas suivi correctement.</span><span class="sxs-lookup"><span data-stu-id="45400-110">The preparation pattern for a CER is not followed correctly.</span></span>  <span data-ttu-id="45400-111">Il s’agit d’un événement d’erreur.</span><span class="sxs-lookup"><span data-stu-id="45400-111">This is an error event.</span></span> <span data-ttu-id="45400-112">L' <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A> appel de méthode utilisé pour marquer des gestionnaires d’exceptions comme introduisant une CER dans leurs `catch` / `finally` / `fault` / `filter` blocs doit être utilisé immédiatement avant l' `try` instruction.</span><span class="sxs-lookup"><span data-stu-id="45400-112">The <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A> method call used to mark exception handlers as introducing a CER in their `catch`/`finally`/`fault`/`filter` blocks must be used immediately before the `try` statement.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="45400-113">Résolution</span><span class="sxs-lookup"><span data-stu-id="45400-113">Resolution</span></span>  
 <span data-ttu-id="45400-114">Vérifiez que l’appel à <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A> se produit immédiatement avant l’instruction `try`.</span><span class="sxs-lookup"><span data-stu-id="45400-114">Ensure that the call to <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A> happens immediately before the `try` statement.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="45400-115">Effet sur le runtime</span><span class="sxs-lookup"><span data-stu-id="45400-115">Effect on the Runtime</span></span>  
 <span data-ttu-id="45400-116">Cet Assistant Débogage managé n'a aucun effet sur le CLR.</span><span class="sxs-lookup"><span data-stu-id="45400-116">This MDA has no effect on the CLR.</span></span>  
  
## <a name="output"></a><span data-ttu-id="45400-117">Sortie</span><span class="sxs-lookup"><span data-stu-id="45400-117">Output</span></span>  
 <span data-ttu-id="45400-118">L’Assistant Débogage managé affiche le nom de la méthode qui appelle la méthode <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A>, l’offset MSIL et un message indiquant que l’appel ne précède pas immédiatement le début du bloc try.</span><span class="sxs-lookup"><span data-stu-id="45400-118">The MDA displays the name of the method calling the <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A> method, the MSIL offset, and a message indicating the call does not immediately precede the beginning of the try block.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="45400-119">Configuration</span><span class="sxs-lookup"><span data-stu-id="45400-119">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <illegalPrepareConstrainedRegion/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="example"></a><span data-ttu-id="45400-120">Exemple</span><span class="sxs-lookup"><span data-stu-id="45400-120">Example</span></span>  
 <span data-ttu-id="45400-121">L’exemple de code suivant illustre le modèle qui provoque l’activation de cet Assistant Débogage managé.</span><span class="sxs-lookup"><span data-stu-id="45400-121">The following code example demonstrates the pattern that causes this MDA to be activated.</span></span>  
  
```csharp
void MethodWithInvalidPCR()  
{  
    RuntimeHelpers.PrepareConstrainedRegions();  
    Object o = new Object();  
    try  
    {  
        …  
    }  
    finally  
    {  
        …  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="45400-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="45400-122">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A>
- [<span data-ttu-id="45400-123">Diagnostic d’erreurs avec les Assistants Débogage managé</span><span class="sxs-lookup"><span data-stu-id="45400-123">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="45400-124">Marshaling d’interopérabilité</span><span class="sxs-lookup"><span data-stu-id="45400-124">Interop Marshaling</span></span>](../interop/interop-marshaling.md)
