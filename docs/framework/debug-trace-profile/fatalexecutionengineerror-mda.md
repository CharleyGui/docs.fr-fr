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
# <a name="fatalexecutionengineerror-mda"></a>Assistant Débogage managé fatalExecutionEngineError

L’Assistant Débogage managé `fatalExecutionEngineError` est activé quand une erreur irrécupérable dans le common language runtime a été détectée. Le processus se termine.  
  
## <a name="symptoms"></a>Symptômes  

 Arrêt inattendu du processus. D’autres symptômes ne peuvent pas être déterminés, car une défaillance du common language runtime peut se produire pour différentes raisons.  
  
## <a name="cause"></a>Cause  

 Le common language runtime a été endommagé de façon irréversible. Ceci est dû le plus souvent à une altération des données, qui peut être provoquée par un certain nombre de problèmes, comme des fonctions d’appel de code non managé incorrectement formées et au passage de données non valides au CLR.  
  
## <a name="resolution"></a>Résolution  

 L’activation d’Assistants Débogage managé supplémentaires peut aider à identifier le problème. Les Assistants Débogage managé suivants peuvent être particulièrement utiles pour diagnostiquer le problème :  
  
- [invalidOverlappedToPinvoke](invalidoverlappedtopinvoke-mda.md)  
  
- [overlappedFreeError](overlappedfreeerror-mda.md)  
  
- [pInvokeStackImbalance](pinvokestackimbalance-mda.md)  
  
- [gcUnmanagedToManaged](gcunmanagedtomanaged-mda.md)  
  
- [gcManagedToUnmanaged](gcmanagedtounmanaged-mda.md)  
  
- [callbackOnCollectedDelegate](callbackoncollecteddelegate-mda.md)  
  
- [reportAvOnComRelease](reportavoncomrelease-mda.md)  
  
- [invalidVariant](invalidvariant-mda.md)  
  
- [invalidIUnknown](invalidiunknown-mda.md)  
  
- [raceOnRCWCleanup](raceonrcwcleanup-mda.md)  
  
- [invalidFunctionPointerInDelegate](invalidfunctionpointerindelegate-mda.md)  
  
- [invalidGCHandleCookie](invalidgchandlecookie-mda.md)  
  
## <a name="effect-on-the-runtime"></a>Effet sur le runtime  

 Cet Assistant Débogage managé n’a aucun effet sur le comportement du runtime.  
  
## <a name="output"></a>Output  

 L’adresse de la fonction CLR qui a provoqué l’erreur irrécupérable, l’ID du thread où l’erreur s’est produite et le code d’erreur.  
  
## <a name="configuration"></a>Configuration  
  
```xml  
<mdaConfig>  
  <assistants>  
    <fatalExecutionEngineError />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareMethod%2A>
- <xref:System.Runtime.ConstrainedExecution.Cer>
- [Diagnostic d'erreurs avec les Assistants de débogage managés](diagnosing-errors-with-managed-debugging-assistants.md)
