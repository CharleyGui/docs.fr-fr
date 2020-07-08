---
title: Assistant Débogage managé invalidIUnknown
description: Passez en revue l’Assistant Débogage managé invalidIUnknown (MDA) qui est activé quand un pointeur IUnknown non valide est passé au code managé à partir du code natif.
ms.date: 03/30/2017
helpviewer_keywords:
- MDAs (managed debugging assistants), invalid IUnknown pointer
- InvalidIUnknown MDA
- invalid IUnknown pointers
- IUnknown pointers
- managed debugging assistants (MDAs), invalid IUnknown pointer
ms.assetid: c7924771-a16b-40fe-b337-ce51dcdf6a12
ms.openlocfilehash: 65d704463ed746390ff1710b590bf080013bf53d
ms.sourcegitcommit: 0edbeb66d71b8df10fcb374cfca4d731b58ccdb2
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "86051725"
---
# <a name="invalidiunknown-mda"></a>Assistant Débogage managé invalidIUnknown
L'Assistant Débogage managé (MDA) `invalidIUnknown` est activé quand un pointeur `IUnknown` non valide est passé au code managé à partir du code natif. Le pointeur `IUnknown` ne peut pas retourner un succès quand il est interrogé sur l'interface `IUnknown`.  
  
## <a name="symptoms"></a>Symptômes  
 Une erreur inattendue se produit quand un pointeur d'interface COM est marshalé pendant le marshaling d'argument.  
  
## <a name="cause"></a>Cause  
 Une implémentation incorrecte de `QueryInterface` sur l'interface COM a été passée au CLR.  
  
## <a name="resolution"></a>Résolution  
 Corrigez l'implémentation de `QueryInterface`.  
  
## <a name="effect-on-the-runtime"></a>Effet sur le runtime  
 Cet Assistant Débogage managé n'a aucun effet sur le CLR.  
  
## <a name="output"></a>Sortie  
 Description de l'erreur.  
  
## <a name="configuration"></a>Configuration  
  
```xml  
<mdaConfig>  
  <assistants>  
    <invalidIUnknown />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [Diagnostic d’erreurs avec les Assistants Débogage managé](diagnosing-errors-with-managed-debugging-assistants.md)
- [Marshaling d’interopérabilité](../interop/interop-marshaling.md)
