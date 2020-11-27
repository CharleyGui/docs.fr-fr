---
title: Assistant Débogage managé invalidVariant
description: Passez en revue l’Assistant Débogage managé invalidVariant, qui est appelé en cas de détection d’un VARIANT non valide dans un appel du code natif/non managé au code managé.
ms.date: 03/30/2017
helpviewer_keywords:
- MDAs (managed debugging assistants), invalid variant
- VARIANT type errors
- InvalidVariant MDA
- invalid VARIANT types
- managed debugging assistants (MDAs), invalid variant
ms.assetid: d273e070-d1b1-4a53-a9c7-7af837b04a3d
ms.openlocfilehash: f0667a54e950ead27000eb6b93ebd547dea1cfb0
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96281298"
---
# <a name="invalidvariant-mda"></a>Assistant Débogage managé invalidVariant

L'Assistant Débogage managé (MDA) `invalidVariant` est activé quand une structure `VARIANT` non valide est rencontrée lors d'un appel du code natif ou non managé au code managé.  
  
## <a name="symptoms"></a>Symptômes  

 Comportement inattendu pendant une transition entre du code natif et managé impliquant le marshaling d’une structure `VARIANT` en objet.  
  
## <a name="cause"></a>Cause  

 Le code natif passe une structure `VARIANT` incorrecte au code managé.  Le runtime tente de marshaler cette `VARIANT` en objet et active l'Assistant Débogage managé si la `VARIANT` n'est pas valide. Exemples de structures `VARIANT` non valides : une structure `VARIANT` avec un `VARTYPE` VT_EMPTY &#124; VT_BYREF ou une structure `VARIANT` avec le `VARTYPE` VT_VARIANT.  
  
## <a name="resolution"></a>Résolution  

 Le code natif ou non managé qui passe la structure `VARIANT` doit s'assurer que la `VARIANT` est correcte et bien initialisée.  
  
## <a name="effect-on-the-runtime"></a>Effet sur le runtime  

 Cet Assistant Débogage managé n'a aucun effet sur le comportement du runtime.  
  
## <a name="output"></a>Output  

 Message de l'Assistant Débogage managé indiquant que le runtime a détecté qu'une structure `VARIANT` incorrecte a été passée au code managé par un module non managé.  
  
## <a name="configuration"></a>Configuration  
  
```xml  
<mdaConfig>  
  <assistants>  
    <invalidVariant />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [Diagnostic d'erreurs avec les Assistants de débogage managés](diagnosing-errors-with-managed-debugging-assistants.md)
- [Marshaling d’interopérabilité](../interop/interop-marshaling.md)
