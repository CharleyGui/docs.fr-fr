---
title: Assistant Débogage managé disconnectedContext
ms.date: 03/30/2017
helpviewer_keywords:
- DisconnectedContext MDA
- MDAs (managed debugging assistants), disconnected context
- dead context
- transitioning disconnected apartment or context
- context disconnections
- managed debugging assistants (MDAs), disconnected context
ms.assetid: 1887d31d-7006-4491-93b3-68fd5b05f71d
ms.openlocfilehash: 3d04e304a6b30fe6fd4deeda5a97007f11ee7b13
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/14/2020
ms.locfileid: "77216550"
---
# <a name="disconnectedcontext-mda"></a><span data-ttu-id="1fb6f-102">Assistant Débogage managé disconnectedContext</span><span class="sxs-lookup"><span data-stu-id="1fb6f-102">disconnectedContext MDA</span></span>
<span data-ttu-id="1fb6f-103">L'Assistant Débogage managé `disconnectedContext` est activé quand le CLR essaie d'effectuer une transition vers un contexte ou un cloisonnement déconnecté pendant le traitement d'une demande concernant un objet COM.</span><span class="sxs-lookup"><span data-stu-id="1fb6f-103">The `disconnectedContext` managed debugging assistant (MDA) is activated when the CLR attempts to transition into a disconnected apartment or context while servicing a request concerning a COM object.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="1fb6f-104">Symptômes</span><span class="sxs-lookup"><span data-stu-id="1fb6f-104">Symptoms</span></span>  
 <span data-ttu-id="1fb6f-105">Les appels effectués sur un [wrapper RCW](../../standard/native-interop/runtime-callable-wrapper.md) (Runtime Callable Wrapper) sont fournis au composant COM sous-jacent dans le contexte ou cloisonnement actuel plutôt que celui où ils se trouvent.</span><span class="sxs-lookup"><span data-stu-id="1fb6f-105">Calls made on a [Runtime Callable Wrapper](../../standard/native-interop/runtime-callable-wrapper.md) (RCW) are delivered to the underlying COM component in the current apartment or context instead of the one in which they exist.</span></span> <span data-ttu-id="1fb6f-106">Cela peut entraîner une altération et/ou une perte de données si le composant COM n'est pas multithread, comme dans le cas de composants de thread cloisonné.</span><span class="sxs-lookup"><span data-stu-id="1fb6f-106">This can cause corruption and or data loss if the COM component is not multithreaded, as in the case of single-threaded apartment (STA) components.</span></span> <span data-ttu-id="1fb6f-107">Par ailleurs, si le wrapper RCW est lui-même un proxy, l'appel peut se traduire par la levée d'une <xref:System.Runtime.InteropServices.COMException> avec un HRESULT de valeur RPC_E_WRONG_THREAD.</span><span class="sxs-lookup"><span data-stu-id="1fb6f-107">Alternatively, if the RCW is itself a proxy, the call might result in the throwing of a <xref:System.Runtime.InteropServices.COMException> with an HRESULT of RPC_E_WRONG_THREAD.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="1fb6f-108">Cause :</span><span class="sxs-lookup"><span data-stu-id="1fb6f-108">Cause</span></span>  
 <span data-ttu-id="1fb6f-109">Le contexte ou cloisonnement OLE a été arrêté au moment où le CLR a essayé d'effectuer une transition vers ce contexte ou cloisonnement.</span><span class="sxs-lookup"><span data-stu-id="1fb6f-109">The OLE apartment or context has been shut down when the CLR attempts to transition into it.</span></span> <span data-ttu-id="1fb6f-110">En règle générale, cela se produit quand les threads cloisonnés sont arrêtés avant que tous les composants COM détenus par le cloisonnement ne soient complètement libérés. Cela peut être dû à un appel explicite à partir du code utilisateur sur un wrapper RCW ou à la manipulation du composant COM par le CLR lui-même, par exemple quand le CLR libère le composant COM alors que le wrapper RCW associé a été récupéré par le Garbage Collector.</span><span class="sxs-lookup"><span data-stu-id="1fb6f-110">This is most commonly caused by STA apartments being shut down before all the COM components owned by the apartment were completely released This can occur as a result of an explicit call from user code on an RCW or while the CLR itself is manipulating the COM component, for example when the CLR is releasing the COM component when the associated RCW has been garbage collected.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="1fb6f-111">Résolution</span><span class="sxs-lookup"><span data-stu-id="1fb6f-111">Resolution</span></span>  
 <span data-ttu-id="1fb6f-112">Pour éviter ce problème, assurez-vous que le thread qui détient le thread cloisonné ne prend pas fin tant que l'application n'a pas terminé de traiter tous les objets qui se trouvent dans le cloisonnement.</span><span class="sxs-lookup"><span data-stu-id="1fb6f-112">To avoid this problem, ensure the thread that owns the STA does not terminate before the application has finished with all the objects that live in the apartment.</span></span> <span data-ttu-id="1fb6f-113">Il en va de même pour les contextes ; assurez-vous qu'un contexte n'est pas arrêté tant que l'application n'a pas complètement terminé de traiter tous les composants COM qui appartiennent à ce contexte.</span><span class="sxs-lookup"><span data-stu-id="1fb6f-113">The same applies to contexts; ensure contexts are not shut down before the application is completely finished with any COM components that live inside the context.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="1fb6f-114">Effet sur le runtime</span><span class="sxs-lookup"><span data-stu-id="1fb6f-114">Effect on the Runtime</span></span>  
 <span data-ttu-id="1fb6f-115">Cet Assistant Débogage managé n'a aucun effet sur le CLR.</span><span class="sxs-lookup"><span data-stu-id="1fb6f-115">This MDA has no effect on the CLR.</span></span> <span data-ttu-id="1fb6f-116">Il fournit uniquement des informations sur le contexte déconnecté.</span><span class="sxs-lookup"><span data-stu-id="1fb6f-116">It only reports data about the disconnected context.</span></span>  
  
## <a name="output"></a><span data-ttu-id="1fb6f-117">Output</span><span class="sxs-lookup"><span data-stu-id="1fb6f-117">Output</span></span>  
 <span data-ttu-id="1fb6f-118">Indique le cookie de contexte du contexte ou du cloisonnement déconnecté.</span><span class="sxs-lookup"><span data-stu-id="1fb6f-118">Reports the context cookie of the disconnected apartment or context.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="1fb6f-119">Configuration</span><span class="sxs-lookup"><span data-stu-id="1fb6f-119">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <disconnectedContext />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="1fb6f-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1fb6f-120">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="1fb6f-121">Diagnostic d’erreurs avec les Assistants Débogage managé</span><span class="sxs-lookup"><span data-stu-id="1fb6f-121">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="1fb6f-122">Marshaling d'interopérabilité</span><span class="sxs-lookup"><span data-stu-id="1fb6f-122">Interop Marshaling</span></span>](../interop/interop-marshaling.md)
