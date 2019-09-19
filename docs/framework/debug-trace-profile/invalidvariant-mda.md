---
title: Assistant Débogage managé invalidVariant
ms.date: 03/30/2017
helpviewer_keywords:
- MDAs (managed debugging assistants), invalid variant
- VARIANT type errors
- InvalidVariant MDA
- invalid VARIANT types
- managed debugging assistants (MDAs), invalid variant
ms.assetid: d273e070-d1b1-4a53-a9c7-7af837b04a3d
author: mairaw
ms.author: mairaw
ms.openlocfilehash: c34f160b643a0431168097d3832357b4ac6e4557
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71052574"
---
# <a name="invalidvariant-mda"></a>Assistant Débogage managé invalidVariant
L'Assistant Débogage managé (MDA) `invalidVariant` est activé quand une structure `VARIANT` non valide est rencontrée lors d'un appel du code natif ou non managé au code managé.  
  
## <a name="symptoms"></a>Symptômes  
 Comportement inattendu pendant une transition entre du code natif et managé impliquant le marshaling d’une structure `VARIANT` en objet.  
  
## <a name="cause"></a>Cause  
 Le code natif passe une structure `VARIANT` incorrecte au code managé.  Le runtime tente de marshaler cette `VARIANT` en objet et active l'Assistant Débogage managé si la `VARIANT` n'est pas valide. Exemples de structures `VARIANT` non valides : une structure `VARIANT` avec un `VARTYPE` VT_EMPTY &#124; VT_BYREF ou une structure `VARIANT` avec le `VARTYPE` VT_VARIANT.  
  
## <a name="resolution"></a>Résolution :  
 Le code natif ou non managé qui passe la structure `VARIANT` doit s'assurer que la `VARIANT` est correcte et bien initialisée.  
  
## <a name="effect-on-the-runtime"></a>Effet sur le runtime  
 Cet Assistant Débogage managé n'a aucun effet sur le comportement du runtime.  
  
## <a name="output"></a>Sortie  
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
- [Diagnostic d’erreurs avec les Assistants Débogage managé](diagnosing-errors-with-managed-debugging-assistants.md)
- [Marshaling d'interopérabilité](../interop/interop-marshaling.md)
