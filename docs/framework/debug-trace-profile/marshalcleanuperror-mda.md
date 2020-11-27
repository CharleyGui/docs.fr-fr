---
title: Assistant Débogage managé marshalCleanupError
description: Passez en revue l’Assistant Débogage managé (MDA) marshalCleanupError, qui est appelé car une erreur inattendue s’est produite lors du nettoyage des structures temporaires.
ms.date: 03/30/2017
helpviewer_keywords:
- cleanup operations
- marshaling, run-time errors
- managed debugging assistants (MDAs), marshaling
- MDAs (managed debugging assistants), marshaling
- marshaling cleanup error
- MarshalCleanupError MDA
- memory, cleanup errors
ms.assetid: 2f5d9e7c-ae51-4155-a435-54347aa1f091
ms.openlocfilehash: e65136f022caa7b1e18a27f7b97a4ef4c27f42d3
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96271187"
---
# <a name="marshalcleanuperror-mda"></a>Assistant Débogage managé marshalCleanupError

L’Assistant Débogage managé `marshalCleanupError` est activé quand le Common Language Runtime (CLR) rencontre une erreur pendant une tentative de nettoyage de la mémoire et des structures temporaires utilisées pour le marshaling de types de données entre des limites de code native et managé.  
  
## <a name="symptoms"></a>Symptômes  

 Une fuite de mémoire se produit en cas de transitions de code natif et managé, de non-restauration d'état d'exécution tel que la culture de thread ou d'erreurs de nettoyage <xref:System.Runtime.InteropServices.SafeHandle>.  
  
## <a name="cause"></a>Cause  

 Une erreur inattendue s'est produite pendant le nettoyage des structures temporaires.  
  
## <a name="resolution"></a>Résolution  

 Examinez toutes les implémentations de marshaleur personnalisé, de finaliseur et de destructeur <xref:System.Runtime.InteropServices.SafeHandle> pour déterminer si elles contiennent des erreurs.  
  
## <a name="effect-on-the-runtime"></a>Effet sur le runtime  

 Cet Assistant Débogage managé n'a aucun effet sur le CLR.  
  
## <a name="output"></a>Output  

 Message indiquant l'opération ayant échoué pendant le nettoyage.  
  
## <a name="configuration"></a>Configuration  
  
```xml  
<mdaConfig>  
  <assistants>  
    <marshalCleanupError />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [Diagnostic d'erreurs avec les Assistants de débogage managés](diagnosing-errors-with-managed-debugging-assistants.md)
- [Marshaling d’interopérabilité](../interop/interop-marshaling.md)
