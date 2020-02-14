---
title: Assistant Débogage managé fatalExecutionEngineError
ms.date: 03/30/2017
helpviewer_keywords:
- corrupted CLR
- fatal execution error
- terminated processes
- unexpected terminations
- fatal errors
- MDAs (managed debugging assistants), fatal errors
- process termination
- FatalExecutionEngineError MDA
- managed debugging assistants (MDAs), fatal errors
ms.assetid: 8b559e44-2393-4e4e-8160-7558d37a4a89
ms.openlocfilehash: e25c9ef6ec43089f1d85479d1afe301232ed1d4f
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/14/2020
ms.locfileid: "77217487"
---
# <a name="fatalexecutionengineerror-mda"></a><span data-ttu-id="b3020-102">Assistant Débogage managé fatalExecutionEngineError</span><span class="sxs-lookup"><span data-stu-id="b3020-102">fatalExecutionEngineError MDA</span></span>
<span data-ttu-id="b3020-103">L’Assistant Débogage managé `fatalExecutionEngineError` est activé quand une erreur irrécupérable dans le common language runtime a été détectée.</span><span class="sxs-lookup"><span data-stu-id="b3020-103">The `fatalExecutionEngineError` managed debugging assistant (MDA) is activated when a fatal error in the common language runtime (CLR) has been detected.</span></span> <span data-ttu-id="b3020-104">Le processus se termine.</span><span class="sxs-lookup"><span data-stu-id="b3020-104">The process will be terminated.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="b3020-105">Symptômes</span><span class="sxs-lookup"><span data-stu-id="b3020-105">Symptoms</span></span>  
 <span data-ttu-id="b3020-106">Arrêt inattendu du processus.</span><span class="sxs-lookup"><span data-stu-id="b3020-106">Unexpected process termination.</span></span> <span data-ttu-id="b3020-107">D’autres symptômes ne peuvent pas être déterminés, car une défaillance du common language runtime peut se produire pour différentes raisons.</span><span class="sxs-lookup"><span data-stu-id="b3020-107">Other symptoms cannot be determined because a CLR failure can occur for a variety of reasons.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="b3020-108">Cause :</span><span class="sxs-lookup"><span data-stu-id="b3020-108">Cause</span></span>  
 <span data-ttu-id="b3020-109">Le common language runtime a été endommagé de façon irréversible.</span><span class="sxs-lookup"><span data-stu-id="b3020-109">The CLR has been fatally corrupted.</span></span> <span data-ttu-id="b3020-110">Ceci est dû le plus souvent à une altération des données, qui peut être provoquée par un certain nombre de problèmes, comme des fonctions d’appel de code non managé incorrectement formées et au passage de données non valides au CLR.</span><span class="sxs-lookup"><span data-stu-id="b3020-110">This is most often caused by data corruption, which can be caused by a number of problems, such as calls to malformed platform invoke functions and passing invalid data to the CLR.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="b3020-111">Résolution</span><span class="sxs-lookup"><span data-stu-id="b3020-111">Resolution</span></span>  
 <span data-ttu-id="b3020-112">L’activation d’Assistants Débogage managé supplémentaires peut aider à identifier le problème.</span><span class="sxs-lookup"><span data-stu-id="b3020-112">Enabling additional MDAs might help identify the problem.</span></span> <span data-ttu-id="b3020-113">Les Assistants Débogage managé suivants peuvent être particulièrement utiles pour diagnostiquer le problème :</span><span class="sxs-lookup"><span data-stu-id="b3020-113">The following MDAs can be particularly helpful in diagnosing the issue:</span></span>  
  
- [<span data-ttu-id="b3020-114">invalidOverlappedToPinvoke</span><span class="sxs-lookup"><span data-stu-id="b3020-114">invalidOverlappedToPinvoke</span></span>](invalidoverlappedtopinvoke-mda.md)  
  
- [<span data-ttu-id="b3020-115">overlappedFreeError</span><span class="sxs-lookup"><span data-stu-id="b3020-115">overlappedFreeError</span></span>](overlappedfreeerror-mda.md)  
  
- [<span data-ttu-id="b3020-116">pInvokeStackImbalance</span><span class="sxs-lookup"><span data-stu-id="b3020-116">pInvokeStackImbalance</span></span>](pinvokestackimbalance-mda.md)  
  
- [<span data-ttu-id="b3020-117">gcUnmanagedToManaged</span><span class="sxs-lookup"><span data-stu-id="b3020-117">gcUnmanagedToManaged</span></span>](gcunmanagedtomanaged-mda.md)  
  
- [<span data-ttu-id="b3020-118">gcManagedToUnmanaged</span><span class="sxs-lookup"><span data-stu-id="b3020-118">gcManagedToUnmanaged</span></span>](gcmanagedtounmanaged-mda.md)  
  
- [<span data-ttu-id="b3020-119">callbackOnCollectedDelegate</span><span class="sxs-lookup"><span data-stu-id="b3020-119">callbackOnCollectedDelegate</span></span>](callbackoncollecteddelegate-mda.md)  
  
- [<span data-ttu-id="b3020-120">reportAvOnComRelease</span><span class="sxs-lookup"><span data-stu-id="b3020-120">reportAvOnComRelease</span></span>](reportavoncomrelease-mda.md)  
  
- [<span data-ttu-id="b3020-121">invalidVariant</span><span class="sxs-lookup"><span data-stu-id="b3020-121">invalidVariant</span></span>](invalidvariant-mda.md)  
  
- [<span data-ttu-id="b3020-122">invalidIUnknown</span><span class="sxs-lookup"><span data-stu-id="b3020-122">invalidIUnknown</span></span>](invalidiunknown-mda.md)  
  
- [<span data-ttu-id="b3020-123">raceOnRCWCleanup</span><span class="sxs-lookup"><span data-stu-id="b3020-123">raceOnRCWCleanup</span></span>](raceonrcwcleanup-mda.md)  
  
- [<span data-ttu-id="b3020-124">invalidFunctionPointerInDelegate</span><span class="sxs-lookup"><span data-stu-id="b3020-124">invalidFunctionPointerInDelegate</span></span>](invalidfunctionpointerindelegate-mda.md)  
  
- [<span data-ttu-id="b3020-125">invalidGCHandleCookie</span><span class="sxs-lookup"><span data-stu-id="b3020-125">invalidGCHandleCookie</span></span>](invalidgchandlecookie-mda.md)  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="b3020-126">Effet sur le runtime</span><span class="sxs-lookup"><span data-stu-id="b3020-126">Effect on the Runtime</span></span>  
 <span data-ttu-id="b3020-127">Cet Assistant Débogage managé n’a aucun effet sur le comportement du runtime.</span><span class="sxs-lookup"><span data-stu-id="b3020-127">This MDA has no effect on the runtime's behavior.</span></span>  
  
## <a name="output"></a><span data-ttu-id="b3020-128">Output</span><span class="sxs-lookup"><span data-stu-id="b3020-128">Output</span></span>  
 <span data-ttu-id="b3020-129">L’adresse de la fonction CLR qui a provoqué l’erreur irrécupérable, l’ID du thread où l’erreur s’est produite et le code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="b3020-129">The address of the CLR function that caused the fatal error, the ID of the thread where the error occurred, and the error code.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="b3020-130">Configuration</span><span class="sxs-lookup"><span data-stu-id="b3020-130">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <fatalExecutionEngineError />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="b3020-131">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b3020-131">See also</span></span>

- <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareMethod%2A>
- <xref:System.Runtime.ConstrainedExecution.Cer>
- [<span data-ttu-id="b3020-132">Diagnostic d’erreurs avec les Assistants Débogage managé</span><span class="sxs-lookup"><span data-stu-id="b3020-132">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
