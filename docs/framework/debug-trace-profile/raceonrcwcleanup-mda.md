---
title: Assistant Débogage managé raceOnRCWCleanup
ms.date: 03/30/2017
helpviewer_keywords:
- RCW
- managed debugging assistants (MDAs), RCWs
- race on RCW cleanup
- MDAs (managed debugging assistants), RCWs
- RaceOnRCWCleanup MDA
- runtime callable wrappers
ms.assetid: bee1e9b1-50a8-4c89-9cd9-7dd6b2458187
author: mairaw
ms.author: mairaw
ms.openlocfilehash: ca3b28d0d27af0a752de894f5856b76939b01e09
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69967242"
---
# <a name="raceonrcwcleanup-mda"></a><span data-ttu-id="c2c17-102">Assistant Débogage managé raceOnRCWCleanup</span><span class="sxs-lookup"><span data-stu-id="c2c17-102">raceOnRCWCleanup MDA</span></span>
<span data-ttu-id="c2c17-103">L’Assistant Débogage managé (MDA) `raceOnRCWCleanup` est activé quand le Common Language Runtime (CLR) détecte qu’un [wrapper RCW](../../standard/native-interop/runtime-callable-wrapper.md) est en cours d’utilisation au moment où un appel visant à le libérer est effectué à l’aide d’une commande telle que la méthode <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="c2c17-103">The `raceOnRCWCleanup` managed debugging assistant (MDA) is activated when the common language runtime (CLR) detects that a [Runtime Callable Wrapper](../../standard/native-interop/runtime-callable-wrapper.md) (RCW) is in use when a call to release it is made using a command such as the <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A?displayProperty=nameWithType> method.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="c2c17-104">Symptômes</span><span class="sxs-lookup"><span data-stu-id="c2c17-104">Symptoms</span></span>  
 <span data-ttu-id="c2c17-105">Violations d'accès ou altération de la mémoire pendant ou après la libération d'un RCW à l'aide de <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A> ou d'une méthode similaire.</span><span class="sxs-lookup"><span data-stu-id="c2c17-105">Access violations or memory corruption during or after freeing an RCW using <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A> or a similar method.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="c2c17-106">Cause</span><span class="sxs-lookup"><span data-stu-id="c2c17-106">Cause</span></span>  
 <span data-ttu-id="c2c17-107">Le RCW est en cours d'utilisation sur un autre thread ou sur la pile des threads de libération,</span><span class="sxs-lookup"><span data-stu-id="c2c17-107">The RCW is in use on another thread or on the freeing thread stack.</span></span>  <span data-ttu-id="c2c17-108">et ne peut donc pas être libéré.</span><span class="sxs-lookup"><span data-stu-id="c2c17-108">An RCW that is in use cannot be released.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="c2c17-109">Résolution :</span><span class="sxs-lookup"><span data-stu-id="c2c17-109">Resolution</span></span>  
 <span data-ttu-id="c2c17-110">Ne libérez pas un RCW qui pourrait être utilisé dans le thread actuel ou dans d'autres threads.</span><span class="sxs-lookup"><span data-stu-id="c2c17-110">Do not free an RCW that could be in use either in the current or in other threads.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="c2c17-111">Effet sur le runtime</span><span class="sxs-lookup"><span data-stu-id="c2c17-111">Effect on the Runtime</span></span>  
 <span data-ttu-id="c2c17-112">Cet Assistant Débogage managé n'a aucun effet sur le CLR.</span><span class="sxs-lookup"><span data-stu-id="c2c17-112">This MDA has no effect on the CLR.</span></span>  
  
## <a name="output"></a><span data-ttu-id="c2c17-113">Sortie</span><span class="sxs-lookup"><span data-stu-id="c2c17-113">Output</span></span>  
 <span data-ttu-id="c2c17-114">Message décrivant l'erreur.</span><span class="sxs-lookup"><span data-stu-id="c2c17-114">A message describing the error.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="c2c17-115">Configuration</span><span class="sxs-lookup"><span data-stu-id="c2c17-115">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <raceOnRCWCleanup/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="c2c17-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c2c17-116">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="c2c17-117">Diagnostic d’erreurs avec les Assistants Débogage managé</span><span class="sxs-lookup"><span data-stu-id="c2c17-117">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="c2c17-118">Marshaling d'interopérabilité</span><span class="sxs-lookup"><span data-stu-id="c2c17-118">Interop Marshaling</span></span>](../../../docs/framework/interop/interop-marshaling.md)
