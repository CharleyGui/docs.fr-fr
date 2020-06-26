---
title: Assistant Débogage managé gcUnmanagedToManaged
description: Passez en revue l’Assistant Débogage managé gcManagedToUnmanaged dans .NET. Cet Assistant Débogage managé peut s’activer en raison d’une altération du tas de mémoire pendant la transition vers du code managé.
ms.date: 03/30/2017
helpviewer_keywords:
- MDAs (managed debugging assistants), garbage collection
- GC unmanaged to managed
- transitioning threads unmanaged to managed code
- GcUnmanagedToManaged MDA
- threading [.NET Framework], garbage collection
- managed debugging assistants (MDAs), garbage collection
- threading [.NET Framework], managed debugging assistants
- garbage collection, run-time errors
- unmanaged to managed garbage collection
ms.assetid: 103eb3a3-1cf0-4406-8a9a-a7798fdc22d1
ms.openlocfilehash: 320d55224e6a204d330447d6c68eabe0fa6cf892
ms.sourcegitcommit: a2c8b19e813a52b91facbb5d7e3c062c7188b457
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/26/2020
ms.locfileid: "85415899"
---
# <a name="gcunmanagedtomanaged-mda"></a>Assistant Débogage managé gcUnmanagedToManaged
L'Assistant Débogage managé (MDA) `gcUnmanagedToManaged` déclenche une opération garbage collection chaque fois qu'un thread effectue la transition du code non managé au code managé.  
  
## <a name="symptoms"></a>Symptômes  
 Une application exécutant des composants utilisateur non managés à l'aide de COM et d'appels de code non managé provoque une violation d'accès non déterministe dans le CLR.  
  
## <a name="cause"></a>Cause  
 Si une application exécute des composants utilisateur non managés, il se peut que ces composants aient endommagé le tas obtenu à l'issue d'une opération garbage collection. Cela provoque une violation d'accès dans le CLR quand le garbage collector tente de parcourir le graphique d'objet.  
  
## <a name="resolution"></a>Résolution  
 L'activation de cet assistant réduit la durée entre le moment où le composant non managé endommage le tas obtenu à l'issue d'une opération garbage collection et le moment de la violation d'accès en obligeant l'exécution d'une opération garbage collection avant chaque transition managée.  
  
## <a name="effect-on-the-runtime"></a>Effet sur le runtime  
 Provoque une opération garbage collection chaque fois qu’un thread effectue la transition du code non managé au code managé.  
  
## <a name="output"></a>Output  
 Cet Assistant Débogage managé ne produit aucune sortie.  
  
## <a name="configuration"></a>Configuration  
  
```xml  
<mdaConfig>  
  <assistants>  
    <gcUnmanagedToManaged/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [Diagnostic d’erreurs avec les Assistants Débogage managé](diagnosing-errors-with-managed-debugging-assistants.md)
- [gcManagedToUnmanaged](gcmanagedtounmanaged-mda.md)
- [Marshaling d’interopérabilité](../interop/interop-marshaling.md)
