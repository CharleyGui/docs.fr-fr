---
title: Assistant Débogage managé fatalExecutionEngineError
description: Passez en revue l’Assistant Débogage managé (MDA) fatalExecutionEngineError dans .NET, qui peut être activé en raison d’un arrêt inattendu du processus.
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
ms.openlocfilehash: a9347338d53755b74b3ff291f75cb6b221134130
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96244273"
---
# <a name="fatalexecutionengineerror-mda"></a><span data-ttu-id="21988-103">Assistant Débogage managé fatalExecutionEngineError</span><span class="sxs-lookup"><span data-stu-id="21988-103">fatalExecutionEngineError MDA</span></span>

<span data-ttu-id="21988-104">L’Assistant Débogage managé `fatalExecutionEngineError` est activé quand une erreur irrécupérable dans le common language runtime a été détectée.</span><span class="sxs-lookup"><span data-stu-id="21988-104">The `fatalExecutionEngineError` managed debugging assistant (MDA) is activated when a fatal error in the common language runtime (CLR) has been detected.</span></span> <span data-ttu-id="21988-105">Le processus se termine.</span><span class="sxs-lookup"><span data-stu-id="21988-105">The process will be terminated.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="21988-106">Symptômes</span><span class="sxs-lookup"><span data-stu-id="21988-106">Symptoms</span></span>  

 <span data-ttu-id="21988-107">Arrêt inattendu du processus.</span><span class="sxs-lookup"><span data-stu-id="21988-107">Unexpected process termination.</span></span> <span data-ttu-id="21988-108">D’autres symptômes ne peuvent pas être déterminés, car une défaillance du common language runtime peut se produire pour différentes raisons.</span><span class="sxs-lookup"><span data-stu-id="21988-108">Other symptoms cannot be determined because a CLR failure can occur for a variety of reasons.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="21988-109">Cause</span><span class="sxs-lookup"><span data-stu-id="21988-109">Cause</span></span>  

 <span data-ttu-id="21988-110">Le common language runtime a été endommagé de façon irréversible.</span><span class="sxs-lookup"><span data-stu-id="21988-110">The CLR has been fatally corrupted.</span></span> <span data-ttu-id="21988-111">Ceci est dû le plus souvent à une altération des données, qui peut être provoquée par un certain nombre de problèmes, comme des fonctions d’appel de code non managé incorrectement formées et au passage de données non valides au CLR.</span><span class="sxs-lookup"><span data-stu-id="21988-111">This is most often caused by data corruption, which can be caused by a number of problems, such as calls to malformed platform invoke functions and passing invalid data to the CLR.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="21988-112">Résolution</span><span class="sxs-lookup"><span data-stu-id="21988-112">Resolution</span></span>  

 <span data-ttu-id="21988-113">L’activation d’Assistants Débogage managé supplémentaires peut aider à identifier le problème.</span><span class="sxs-lookup"><span data-stu-id="21988-113">Enabling additional MDAs might help identify the problem.</span></span> <span data-ttu-id="21988-114">Les Assistants Débogage managé suivants peuvent être particulièrement utiles pour diagnostiquer le problème :</span><span class="sxs-lookup"><span data-stu-id="21988-114">The following MDAs can be particularly helpful in diagnosing the issue:</span></span>  
  
- [<span data-ttu-id="21988-115">invalidOverlappedToPinvoke</span><span class="sxs-lookup"><span data-stu-id="21988-115">invalidOverlappedToPinvoke</span></span>](invalidoverlappedtopinvoke-mda.md)  
  
- [<span data-ttu-id="21988-116">overlappedFreeError</span><span class="sxs-lookup"><span data-stu-id="21988-116">overlappedFreeError</span></span>](overlappedfreeerror-mda.md)  
  
- [<span data-ttu-id="21988-117">pInvokeStackImbalance</span><span class="sxs-lookup"><span data-stu-id="21988-117">pInvokeStackImbalance</span></span>](pinvokestackimbalance-mda.md)  
  
- [<span data-ttu-id="21988-118">gcUnmanagedToManaged</span><span class="sxs-lookup"><span data-stu-id="21988-118">gcUnmanagedToManaged</span></span>](gcunmanagedtomanaged-mda.md)  
  
- [<span data-ttu-id="21988-119">gcManagedToUnmanaged</span><span class="sxs-lookup"><span data-stu-id="21988-119">gcManagedToUnmanaged</span></span>](gcmanagedtounmanaged-mda.md)  
  
- [<span data-ttu-id="21988-120">callbackOnCollectedDelegate</span><span class="sxs-lookup"><span data-stu-id="21988-120">callbackOnCollectedDelegate</span></span>](callbackoncollecteddelegate-mda.md)  
  
- [<span data-ttu-id="21988-121">reportAvOnComRelease</span><span class="sxs-lookup"><span data-stu-id="21988-121">reportAvOnComRelease</span></span>](reportavoncomrelease-mda.md)  
  
- [<span data-ttu-id="21988-122">invalidVariant</span><span class="sxs-lookup"><span data-stu-id="21988-122">invalidVariant</span></span>](invalidvariant-mda.md)  
  
- [<span data-ttu-id="21988-123">invalidIUnknown</span><span class="sxs-lookup"><span data-stu-id="21988-123">invalidIUnknown</span></span>](invalidiunknown-mda.md)  
  
- [<span data-ttu-id="21988-124">raceOnRCWCleanup</span><span class="sxs-lookup"><span data-stu-id="21988-124">raceOnRCWCleanup</span></span>](raceonrcwcleanup-mda.md)  
  
- [<span data-ttu-id="21988-125">invalidFunctionPointerInDelegate</span><span class="sxs-lookup"><span data-stu-id="21988-125">invalidFunctionPointerInDelegate</span></span>](invalidfunctionpointerindelegate-mda.md)  
  
- [<span data-ttu-id="21988-126">invalidGCHandleCookie</span><span class="sxs-lookup"><span data-stu-id="21988-126">invalidGCHandleCookie</span></span>](invalidgchandlecookie-mda.md)  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="21988-127">Effet sur le runtime</span><span class="sxs-lookup"><span data-stu-id="21988-127">Effect on the Runtime</span></span>  

 <span data-ttu-id="21988-128">Cet Assistant Débogage managé n’a aucun effet sur le comportement du runtime.</span><span class="sxs-lookup"><span data-stu-id="21988-128">This MDA has no effect on the runtime's behavior.</span></span>  
  
## <a name="output"></a><span data-ttu-id="21988-129">Output</span><span class="sxs-lookup"><span data-stu-id="21988-129">Output</span></span>  

 <span data-ttu-id="21988-130">L’adresse de la fonction CLR qui a provoqué l’erreur irrécupérable, l’ID du thread où l’erreur s’est produite et le code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="21988-130">The address of the CLR function that caused the fatal error, the ID of the thread where the error occurred, and the error code.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="21988-131">Configuration</span><span class="sxs-lookup"><span data-stu-id="21988-131">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <fatalExecutionEngineError />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="21988-132">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="21988-132">See also</span></span>

- <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareMethod%2A>
- <xref:System.Runtime.ConstrainedExecution.Cer>
- [<span data-ttu-id="21988-133">Diagnostic d'erreurs avec les Assistants de débogage managés</span><span class="sxs-lookup"><span data-stu-id="21988-133">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
