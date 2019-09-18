---
title: Assistant Débogage managé exceptionSwallowedOnCallFromCom
ms.date: 03/30/2017
helpviewer_keywords:
- messages, informational
- informational messages
- managed debugging assistants (MDAs), exceptions
- exception handling, managed debugging assistants
- MDAs (managed debugging assistants), exceptions
- ExceptionSwallowedOnCallFromCOM MDA
ms.assetid: 55d6ab12-f251-4aab-aa64-aacbe9d9f974
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 3a49bdce78c1445cd25de8755ded0f27a4902937
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71052818"
---
# <a name="exceptionswallowedoncallfromcom-mda"></a>Assistant Débogage managé exceptionSwallowedOnCallFromCom
L'Assistant Débogage managé `exceptionSwallowedOnCallFromCOM` est activé quand une exception est levée à partir d'un code CLR (Common Language Runtime) appelé depuis COM via une méthode dépourvue de type de retour HRESULT non managé.  
  
## <a name="symptoms"></a>Symptômes  
 Un appel à un composant managé depuis COM retourne la valeur FALSE ou 0. Par ailleurs, si la méthode possède un type de retour void, la levée d'une exception pendant l'exécution de la méthode peut passer inaperçue. Dans ce cas, l'exception est interceptée discrètement et l'appelant COM reprend la main.  
  
## <a name="cause"></a>Cause  
 Une exception a été levée, mais aucune procédure valide ne permet de la signaler.  
  
## <a name="resolution"></a>Résolution :  
 Le message est purement informatif, et n'indique pas nécessairement la présence d'un bogue.  
  
## <a name="effect-on-the-runtime"></a>Effet sur le runtime  
 Cet Assistant Débogage managé n'a aucun effet sur le CLR. Il indique uniquement des informations sur les exceptions interceptées discrètement.  
  
## <a name="output"></a>Sortie  
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
- [Diagnostic d’erreurs avec les Assistants Débogage managé](diagnosing-errors-with-managed-debugging-assistants.md)
- [Marshaling d'interopérabilité](../interop/interop-marshaling.md)
