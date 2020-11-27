---
title: Assistant Débogage managé raceOnRCWCleanup
description: Passez en revue l’Assistant Débogage managé (MDA) raceOnRCWCleanup, qui est activé si le wrapper RCW est en cours d’utilisation sur un autre thread ou sur la pile de threads de libération dans .NET.
ms.date: 03/30/2017
helpviewer_keywords:
- RCW
- managed debugging assistants (MDAs), RCWs
- race on RCW cleanup
- MDAs (managed debugging assistants), RCWs
- RaceOnRCWCleanup MDA
- runtime callable wrappers
ms.assetid: bee1e9b1-50a8-4c89-9cd9-7dd6b2458187
ms.openlocfilehash: 393c5ea44108445a9a1a9d16e7d1d192eced5740
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96271445"
---
# <a name="raceonrcwcleanup-mda"></a><span data-ttu-id="7de19-103">Assistant Débogage managé raceOnRCWCleanup</span><span class="sxs-lookup"><span data-stu-id="7de19-103">raceOnRCWCleanup MDA</span></span>

<span data-ttu-id="7de19-104">L’Assistant Débogage managé (MDA) `raceOnRCWCleanup` est activé quand le Common Language Runtime (CLR) détecte qu’un [wrapper RCW](../../standard/native-interop/runtime-callable-wrapper.md) est en cours d’utilisation au moment où un appel visant à le libérer est effectué à l’aide d’une commande telle que la méthode <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="7de19-104">The `raceOnRCWCleanup` managed debugging assistant (MDA) is activated when the common language runtime (CLR) detects that a [Runtime Callable Wrapper](../../standard/native-interop/runtime-callable-wrapper.md) (RCW) is in use when a call to release it is made using a command such as the <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A?displayProperty=nameWithType> method.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="7de19-105">Symptômes</span><span class="sxs-lookup"><span data-stu-id="7de19-105">Symptoms</span></span>  

 <span data-ttu-id="7de19-106">Violations d'accès ou altération de la mémoire pendant ou après la libération d'un RCW à l'aide de <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A> ou d'une méthode similaire.</span><span class="sxs-lookup"><span data-stu-id="7de19-106">Access violations or memory corruption during or after freeing an RCW using <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A> or a similar method.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="7de19-107">Cause</span><span class="sxs-lookup"><span data-stu-id="7de19-107">Cause</span></span>  

 <span data-ttu-id="7de19-108">Le RCW est en cours d'utilisation sur un autre thread ou sur la pile des threads de libération,</span><span class="sxs-lookup"><span data-stu-id="7de19-108">The RCW is in use on another thread or on the freeing thread stack.</span></span>  <span data-ttu-id="7de19-109">et ne peut donc pas être libéré.</span><span class="sxs-lookup"><span data-stu-id="7de19-109">An RCW that is in use cannot be released.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="7de19-110">Résolution</span><span class="sxs-lookup"><span data-stu-id="7de19-110">Resolution</span></span>  

 <span data-ttu-id="7de19-111">Ne libérez pas un RCW qui pourrait être utilisé dans le thread actuel ou dans d'autres threads.</span><span class="sxs-lookup"><span data-stu-id="7de19-111">Do not free an RCW that could be in use either in the current or in other threads.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="7de19-112">Effet sur le runtime</span><span class="sxs-lookup"><span data-stu-id="7de19-112">Effect on the Runtime</span></span>  

 <span data-ttu-id="7de19-113">Cet Assistant Débogage managé n'a aucun effet sur le CLR.</span><span class="sxs-lookup"><span data-stu-id="7de19-113">This MDA has no effect on the CLR.</span></span>  
  
## <a name="output"></a><span data-ttu-id="7de19-114">Output</span><span class="sxs-lookup"><span data-stu-id="7de19-114">Output</span></span>  

 <span data-ttu-id="7de19-115">Message décrivant l'erreur.</span><span class="sxs-lookup"><span data-stu-id="7de19-115">A message describing the error.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="7de19-116">Configuration</span><span class="sxs-lookup"><span data-stu-id="7de19-116">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <raceOnRCWCleanup/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="7de19-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7de19-117">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="7de19-118">Diagnostic d'erreurs avec les Assistants de débogage managés</span><span class="sxs-lookup"><span data-stu-id="7de19-118">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="7de19-119">Marshaling d’interopérabilité</span><span class="sxs-lookup"><span data-stu-id="7de19-119">Interop Marshaling</span></span>](../interop/interop-marshaling.md)
