---
title: Assistant Débogage managé dllMainReturnsFalse
description: En savoir plus sur l’Assistant Débogage managé dllMainReturnsFalse dans .NET. Cet Assistant Débogage managé est activé si l’initialisation de la DLL a échoué.
ms.date: 03/30/2017
helpviewer_keywords:
- managed debugging assistants (MDAs), DllMain returns false
- DllMainReturnsFalse MDA
- DllMain function
- MDAs (managed debugging assistants), DllMain returns false
ms.assetid: e2abdd04-f571-4b97-8c16-2221b8588429
ms.openlocfilehash: 21d5e37d6823876e07cf5b2cbb881c1cf8b47b11
ms.sourcegitcommit: a2c8b19e813a52b91facbb5d7e3c062c7188b457
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/26/2020
ms.locfileid: "85416055"
---
# <a name="dllmainreturnsfalse-mda"></a>Assistant Débogage managé dllMainReturnsFalse
L’Assistant Débogage managé `dllMainReturnsFalse` est activé si la fonction `DllMain` managée d’un assembly utilisateur, appelée avec la raison DLL_PROCESS_ATTACH, retourne FALSE.  
  
## <a name="symptoms"></a>Symptômes  
 La fonction `DllMain` a retourné FALSE, indiquant qu’elle ne s’est pas exécuté correctement. Cela peut entraîner des problèmes indéterminés, car les fonctions `DllMain` contiennent généralement du code d’initialisation important.  
  
## <a name="cause"></a>Cause  
 La fonction `DllMain` est appelée avec la raison DLL_PROCESS_ATTACH pour l’initialisation de DLL lors du chargement. Si elle retourne FALSE, cela signifie que l’initialisation de la DLL a échoué.  
  
## <a name="resolution"></a>Résolution  
 Analysez le code de la fonction `DllMain` de la DLL ayant échoué, et identifiez la cause de l’échec d’initialisation.  
  
## <a name="effect-on-the-runtime"></a>Effet sur le runtime  
 Cet Assistant Débogage managé n'a aucun effet sur le CLR. Il fournit uniquement des données sur la valeur de retour pour `DllMain`.  
  
## <a name="output"></a>Output  
 Un message indiquant qu’une fonction `DllMain`, appelée pour la raison DLL_PROCESS_ATTACH, a retourné FALSE. Notez que cet Assistant Débogage managé est activé uniquement si `DllMain` est implémenté dans le code managé.  
  
## <a name="configuration"></a>Configuration  
  
```xml  
<mdaConfig>  
  <assistants>  
    <dllMainReturnsFalse />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a>Voir aussi

- [Diagnostic d’erreurs avec les Assistants Débogage managé](diagnosing-errors-with-managed-debugging-assistants.md)
