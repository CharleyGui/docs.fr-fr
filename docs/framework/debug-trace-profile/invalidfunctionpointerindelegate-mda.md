---
title: invalidFunctionPointerInDelegate (MDA)
description: Passez en revue l’Assistant Débogage managé (MDA) invalidFunctionPointerInDelegate, qui est appelé si un pointeur fonction non valide est passé pour créer un délégué.
ms.date: 03/30/2017
helpviewer_keywords:
- invalidFunctionPointerInDelegate MDA
- managed debugging assistants (MDAs), invalid function pointer to delegates
- MDAs (managed debugging assistants), invalid function pointer to delegates
- function pointers, invalid
- marshaling, run-time errors
- managed debugging assistants (MDAs), marshaling
- MDAs (managed debugging assistants), marshaling
- invalid function pointers
ms.assetid: 99ae44f1-783e-49a9-9009-24f54bbd0f09
ms.openlocfilehash: a17427d117c62ba782af3c9549c84623a3013b06
ms.sourcegitcommit: 0edbeb66d71b8df10fcb374cfca4d731b58ccdb2
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "86051738"
---
# <a name="invalidfunctionpointerindelegate-mda"></a>invalidFunctionPointerInDelegate (MDA)
L'Assistant Débogage managé `invalidFunctionPointerInDelegate` est activé quand un pointeur de fonction non valide est transmis pour créer un délégué sur un pointeur de fonction natif.  
  
## <a name="symptoms"></a>Symptômes  
 Violations d'accès ou endommagement de mémoire inattendu pendant l'utilisation d'un délégué sur un pointeur de fonction.  
  
## <a name="cause"></a>Cause  
 Un pointeur de fonction non valide a été spécifié.  
  
## <a name="resolution"></a>Résolution  
 Spécifiez un pointeur de fonction valide.  
  
## <a name="effect-on-the-runtime"></a>Effet sur le runtime  
 Cet Assistant Débogage managé n'a aucun effet sur le CLR.  
  
## <a name="output"></a>Sortie  
 Pointeur de fonction non valide.  
  
## <a name="configuration"></a>Configuration  
  
```xml  
<mdaConfig>  
  <assistants>  
    <invalidFunctionPointerInDelegate />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [Diagnostic d’erreurs avec les Assistants Débogage managé](diagnosing-errors-with-managed-debugging-assistants.md)
- [Marshaling d’interopérabilité](../interop/interop-marshaling.md)
