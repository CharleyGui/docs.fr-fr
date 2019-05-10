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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 5f5d529451f30a6785547410f5121dbb6f91fe01
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64660386"
---
# <a name="fatalexecutionengineerror-mda"></a>Assistant Débogage managé fatalExecutionEngineError
L’Assistant Débogage managé `fatalExecutionEngineError` est activé quand une erreur irrécupérable dans le common language runtime a été détectée. Le processus se termine.  
  
## <a name="symptoms"></a>Symptômes  
 Arrêt inattendu du processus. D’autres symptômes ne peuvent pas être déterminés, car une défaillance du common language runtime peut se produire pour différentes raisons.  
  
## <a name="cause"></a>Cause  
 Le common language runtime a été endommagé de façon irréversible. Ceci est dû le plus souvent à une altération des données, qui peut être provoquée par un certain nombre de problèmes, comme des fonctions d’appel de code non managé incorrectement formées et au passage de données non valides au CLR.  
  
## <a name="resolution"></a>Résolution  
 L’activation d’Assistants Débogage managé supplémentaires peut aider à identifier le problème. Les Assistants Débogage managé suivants peuvent être particulièrement utiles pour diagnostiquer le problème :  
  
- [invalidOverlappedToPinvoke](../../../docs/framework/debug-trace-profile/invalidoverlappedtopinvoke-mda.md)  
  
- [overlappedFreeError](../../../docs/framework/debug-trace-profile/overlappedfreeerror-mda.md)  
  
- [pInvokeStackImbalance](../../../docs/framework/debug-trace-profile/pinvokestackimbalance-mda.md)  
  
- [gcUnmanagedToManaged](../../../docs/framework/debug-trace-profile/gcunmanagedtomanaged-mda.md)  
  
- [gcManagedToUnmanaged](../../../docs/framework/debug-trace-profile/gcmanagedtounmanaged-mda.md)  
  
- [callbackOnCollectedDelegate](../../../docs/framework/debug-trace-profile/callbackoncollecteddelegate-mda.md)  
  
- [reportAvOnComRelease](../../../docs/framework/debug-trace-profile/reportavoncomrelease-mda.md)  
  
- [invalidVariant](../../../docs/framework/debug-trace-profile/invalidvariant-mda.md)  
  
- [invalidIUnknown](../../../docs/framework/debug-trace-profile/invalidiunknown-mda.md)  
  
- [raceOnRCWCleanup](../../../docs/framework/debug-trace-profile/raceonrcwcleanup-mda.md)  
  
- [invalidFunctionPointerInDelegate](../../../docs/framework/debug-trace-profile/invalidfunctionpointerindelegate-mda.md)  
  
- [invalidGCHandleCookie](../../../docs/framework/debug-trace-profile/invalidgchandlecookie-mda.md)  
  
## <a name="effect-on-the-runtime"></a>Effet sur le runtime  
 Cet Assistant Débogage managé n’a aucun effet sur le comportement du runtime.  
  
## <a name="output"></a>Sortie  
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
- [Diagnostic d’erreurs avec les Assistants Débogage managé](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
