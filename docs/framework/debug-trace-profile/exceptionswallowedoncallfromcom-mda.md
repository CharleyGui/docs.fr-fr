---
title: Assistant Débogage managé exceptionSwallowedOnCallFromCom
description: Passez en revue l’Assistant Débogage managé exceptionSwallowedOnCallFromCOM dans .NET. Cet Assistant Débogage managé se produit si une exception a été levée, mais qu’il n’existe aucun moyen de le signaler.
ms.date: 03/30/2017
helpviewer_keywords:
- messages, informational
- informational messages
- managed debugging assistants (MDAs), exceptions
- exception handling, managed debugging assistants
- MDAs (managed debugging assistants), exceptions
- ExceptionSwallowedOnCallFromCOM MDA
ms.assetid: 55d6ab12-f251-4aab-aa64-aacbe9d9f974
ms.openlocfilehash: 11daccb4d1e757bf2fae25858d706eee5921c509
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96244351"
---
# <a name="exceptionswallowedoncallfromcom-mda"></a>Assistant Débogage managé exceptionSwallowedOnCallFromCom

L'Assistant Débogage managé `exceptionSwallowedOnCallFromCOM` est activé quand une exception est levée à partir d'un code CLR (Common Language Runtime) appelé depuis COM via une méthode dépourvue de type de retour HRESULT non managé.  
  
## <a name="symptoms"></a>Symptômes  

 Un appel à un composant managé depuis COM retourne la valeur FALSE ou 0. Par ailleurs, si la méthode possède un type de retour void, la levée d'une exception pendant l'exécution de la méthode peut passer inaperçue. Dans ce cas, l'exception est interceptée discrètement et l'appelant COM reprend la main.  
  
## <a name="cause"></a>Cause  

 Une exception a été levée, mais aucune procédure valide ne permet de la signaler.  
  
## <a name="resolution"></a>Résolution  

 Le message est purement informatif, et n'indique pas nécessairement la présence d'un bogue.  
  
## <a name="effect-on-the-runtime"></a>Effet sur le runtime  

 Cet Assistant Débogage managé n'a aucun effet sur le CLR. Il indique uniquement des informations sur les exceptions interceptées discrètement.  
  
## <a name="output"></a>Output  

 Message d'information contenant le nom de la méthode, le nom du type et le message de l'exception.  
  
## <a name="configuration"></a>Configuration  
  
```xml  
<mdaConfig>  
  <assistants>  
    <exceptionSwallowedOnCallFromCom />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [Diagnostic d'erreurs avec les Assistants de débogage managés](diagnosing-errors-with-managed-debugging-assistants.md)
- [Marshaling d’interopérabilité](../interop/interop-marshaling.md)
