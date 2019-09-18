---
title: Assistant Débogage managé illegalPrepareConstrainedRegion
ms.date: 03/30/2017
helpviewer_keywords:
- PrepareConstrainedRegions method
- managed debugging assistants (MDAs), illegal PrepareConstrainedRegions
- try/catch exception handling, managed debugging assistants
- IllegalPrepareConstrainedRegions MDA
- MDAs (managed debugging assistants), illegal PrepareConstrainedRegions
ms.assetid: 2f9b5031-f910-4e01-a196-f89eab313eaf
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 623aff91eb801b4b32fc180bd97ed3822ad7f163
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71052673"
---
# <a name="illegalprepareconstrainedregion-mda"></a><span data-ttu-id="0aee2-102">Assistant Débogage managé illegalPrepareConstrainedRegion</span><span class="sxs-lookup"><span data-stu-id="0aee2-102">illegalPrepareConstrainedRegion MDA</span></span>
<span data-ttu-id="0aee2-103">L’Assistant Débogage managé `illegalPrepareConstrainedRegion` est activé quand un appel de méthode <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A?displayProperty=nameWithType> ne précède pas immédiatement l’instruction `try` du gestionnaire d’exceptions.</span><span class="sxs-lookup"><span data-stu-id="0aee2-103">The `illegalPrepareConstrainedRegion` managed debugging assistant (MDA) is activated when a <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A?displayProperty=nameWithType> method call does not immediately precede the `try` statement of the exception handler.</span></span> <span data-ttu-id="0aee2-104">Cette restriction étant au niveau MSIL, il est permis d’avoir une source générant du non-code entre l’appel et `try`, telle que les commentaires.</span><span class="sxs-lookup"><span data-stu-id="0aee2-104">This restriction is at the MSIL level, so it is permissible to have non-code-generating source between the call and the `try`, such as comments.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="0aee2-105">Symptômes</span><span class="sxs-lookup"><span data-stu-id="0aee2-105">Symptoms</span></span>  
 <span data-ttu-id="0aee2-106">Une région d’exécution limitée n’est jamais traitée comme telle, mais comme un bloc de gestion des exceptions simple (`finally` ou `catch`).</span><span class="sxs-lookup"><span data-stu-id="0aee2-106">A constrained execution region (CER) that is never treated as such, but as a simple exception handling block (`finally` or `catch`).</span></span> <span data-ttu-id="0aee2-107">Par conséquent, la région ne s’exécute pas en cas de mémoire insuffisante ou d’interruption de thread.</span><span class="sxs-lookup"><span data-stu-id="0aee2-107">As a consequence, the region does not run in the event of an out-of-memory condition or a thread abort.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="0aee2-108">Cause</span><span class="sxs-lookup"><span data-stu-id="0aee2-108">Cause</span></span>  
 <span data-ttu-id="0aee2-109">Le modèle de préparation pour une région d’exécution limitée n’est pas suivi correctement.</span><span class="sxs-lookup"><span data-stu-id="0aee2-109">The preparation pattern for a CER is not followed correctly.</span></span>  <span data-ttu-id="0aee2-110">Il s’agit d’un événement d’erreur.</span><span class="sxs-lookup"><span data-stu-id="0aee2-110">This is an error event.</span></span> <span data-ttu-id="0aee2-111">L' <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A> appel de méthode utilisé pour marquer des gestionnaires d’exceptions comme introduisant une `catch` CER dans leurs `fault` `filter` / `finally` / / blocs doit être utilisé immédiatement avant le `try` instruction.</span><span class="sxs-lookup"><span data-stu-id="0aee2-111">The <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A> method call used to mark exception handlers as introducing a CER in their `catch`/`finally`/`fault`/`filter` blocks must be used immediately before the `try` statement.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="0aee2-112">Résolution :</span><span class="sxs-lookup"><span data-stu-id="0aee2-112">Resolution</span></span>  
 <span data-ttu-id="0aee2-113">Vérifiez que l’appel à <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A> se produit immédiatement avant l’instruction `try`.</span><span class="sxs-lookup"><span data-stu-id="0aee2-113">Ensure that the call to <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A> happens immediately before the `try` statement.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="0aee2-114">Effet sur le runtime</span><span class="sxs-lookup"><span data-stu-id="0aee2-114">Effect on the Runtime</span></span>  
 <span data-ttu-id="0aee2-115">Cet Assistant Débogage managé n'a aucun effet sur le CLR.</span><span class="sxs-lookup"><span data-stu-id="0aee2-115">This MDA has no effect on the CLR.</span></span>  
  
## <a name="output"></a><span data-ttu-id="0aee2-116">Sortie</span><span class="sxs-lookup"><span data-stu-id="0aee2-116">Output</span></span>  
 <span data-ttu-id="0aee2-117">L’Assistant Débogage managé affiche le nom de la méthode qui appelle la méthode <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A>, l’offset MSIL et un message indiquant que l’appel ne précède pas immédiatement le début du bloc try.</span><span class="sxs-lookup"><span data-stu-id="0aee2-117">The MDA displays the name of the method calling the <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A> method, the MSIL offset, and a message indicating the call does not immediately precede the beginning of the try block.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="0aee2-118">Configuration</span><span class="sxs-lookup"><span data-stu-id="0aee2-118">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <illegalPrepareConstrainedRegion/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="example"></a><span data-ttu-id="0aee2-119">Exemple</span><span class="sxs-lookup"><span data-stu-id="0aee2-119">Example</span></span>  
 <span data-ttu-id="0aee2-120">L’exemple de code suivant illustre le modèle qui provoque l’activation de cet Assistant Débogage managé.</span><span class="sxs-lookup"><span data-stu-id="0aee2-120">The following code example demonstrates the pattern that causes this MDA to be activated.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="0aee2-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0aee2-121">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A>
- [<span data-ttu-id="0aee2-122">Diagnostic d’erreurs avec les Assistants Débogage managé</span><span class="sxs-lookup"><span data-stu-id="0aee2-122">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="0aee2-123">Marshaling d'interopérabilité</span><span class="sxs-lookup"><span data-stu-id="0aee2-123">Interop Marshaling</span></span>](../interop/interop-marshaling.md)
