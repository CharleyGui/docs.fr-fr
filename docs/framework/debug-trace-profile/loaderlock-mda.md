---
title: Assistant Débogage managé loaderLock
description: Passez en revue l’Assistant Débogage managé (MDA) loaderLock dans .NET, qui détecte les tentatives d’exécution du code managé sur un thread détenant le verrou du chargeur du système d’exploitation Windows.
ms.date: 03/30/2017
helpviewer_keywords:
- deadlocks [.NET Framework]
- LoaderLock MDA
- MDAs (managed debugging assistants), loader locks
- managed debugging assistants (MDAs), loader locks
- operating system loader locks
- loader locks
- locks, threads
ms.assetid: 8c10fa02-1b9c-4be5-ab03-451d943ac1ee
ms.openlocfilehash: 055b07a805c5f0b613519d6019950a9b249a4b38
ms.sourcegitcommit: 0edbeb66d71b8df10fcb374cfca4d731b58ccdb2
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "86051620"
---
# <a name="loaderlock-mda"></a>Assistant Débogage managé loaderLock
L’Assistant Débogage managé `loaderLock` détecte les tentatives d’exécution de code managé sur un thread qui détient le verrou du chargeur du système d’exploitation Microsoft Windows.  Toute exécution de ce type est interdite, car elle peut entraîner des interblocages et l’utilisation de DLL avant leur initialisation par le chargeur du système d’exploitation.  
  
## <a name="symptoms"></a>Symptômes  
 L’échec le plus courant lors de l’exécution de code à l’intérieur du verrou du chargeur du système d’exploitation est l’interblocage des threads quand vous tentez d’appeler d’autres fonctions Win32 qui nécessitent également le verrou du chargeur.  `LoadLibrary`, `GetProcAddress`, `FreeLibrary` et `GetModuleHandle` sont des exemples de ces fonctions.  L’application ne devrait pas appeler directement ces fonctions ; le common language runtime devrait appeler ces fonctions à la suite d’un appel de niveau supérieur, comme <xref:System.Reflection.Assembly.Load%2A>, ou comme premier appel à une méthode d’appel de code non managé.  
  
 Des interblocages peuvent également se produire si un thread attend le début ou la fin d’un autre thread.  Quand l’exécution d’un thread démarre ou se termine, celui-ci doit acquérir le verrou du chargeur du système d’exploitation pour délivrer des événements aux DLL concernées.  
  
 Enfin, il existe des cas où les appels dans des DLL peuvent se produire avant que ces DLL aient été correctement initialisées par le chargeur du système d’exploitation.  Contrairement aux échecs d’interblocage, qui peuvent être diagnostiqués en examinant les piles de tous les threads impliqués dans l’interblocage, il est très difficile de diagnostiquer l’utilisation de DLL non initialisées sans utiliser cet Assistant Débogage managé.  
  
## <a name="cause"></a>Cause  
 Les assemblys C++ mixtes managés/non managés conçus pour le .NET Framework 1.0 ou 1.1 tentent généralement d’exécuter le code au sein du verrou du chargeur, sauf s’ils ont fait l’objet d’une attention particulière, par exemple dans le cas où les liaisons ont été effectuées avec **/NOENTRY**.
  
 Les assemblys C++ mixtes managés/non managés conçus pour le .NET Framework version 2.0 sont moins sujets à ces problèmes, car ils ont le même niveau de risque limité que les applications utilisant des DLL non managées qui ne respectent pas les règles du système d’exploitation.  Par exemple, si un point d’entrée `DllMain` d’une DLL non managée appelle `CoCreateInstance` pour obtenir un objet managé qui a été exposé à COM, le résultat est une tentative d’exécution de code managé au sein du verrou du chargeur. Pour plus d’informations sur les problèmes de verrou du chargeur dans le .NET Framework 2.0 et ultérieur, consultez [Initialisation des assemblys mixtes](/cpp/dotnet/initialization-of-mixed-assemblies).  
  
## <a name="resolution"></a>Résolution  
 Dans Visual C++ .NET 2002 et Visual C++ .NET 2003, les DLL compilées avec l’option de compilateur `/clr` pouvaient faire l’objet d’un interblocage non déterministe lors du chargement. On parlait dans ce cas de « problème de chargement de DLL mixtes » ou de « problème de verrou du chargeur ». Dans Visual C++ 2005, le non-déterminisme a été pratiquement supprimé du processus de chargement des DLL mixtes. Toutefois, il reste quelques scénarios dans lesquels le verrouillage du chargeur peut se produire (de façon déterministe). Pour une liste détaillée des causes résiduelles et des solutions des problèmes de verrou du chargeur, consultez [Initialisation des assemblys mixtes](/cpp/dotnet/initialization-of-mixed-assemblies). Si cette rubrique ne référence pas votre problème de verrouillage du chargeur, vous devez examiner la pile du thread pour déterminer la raison pour laquelle le verrouillage du chargeur se produit et comment résoudre le problème. Examinez l’arborescence des appels de procédure pour le thread qui a activé cet Assistant Débogage managé.  Le thread tente d’effectuer des appels interdits dans du code managé tout en maintenant le verrou du chargeur du système d’exploitation.  Vous verrez probablement `DllMain` ou un point d’entrée équivalent de la DLL dans la pile.  Les règles du système d’exploitation quant ce que vous êtes autorisé à faire depuis l’intérieur d’un point d’entrée de ce type sont assez limitées.  Ces règles interdisent toute exécution managée.  
  
## <a name="effect-on-the-runtime"></a>Effet sur le runtime  
 En règle générale, plusieurs threads au sein du processus s’interbloquent.  Un de ces threads est probablement un thread chargé d’effectuer une garbage collection : ce blocage peut donc avoir un impact considérable sur l’ensemble du processus.  De plus, il empêche toutes les autres opérations qui nécessitent le verrouillage du chargeur du système d’exploitation, comme le chargement et le déchargement d’assemblys ou de DLL, et le démarrage ou l’arrêt de threads.  
  
 Dans certains cas inhabituels, il est également possible que des violations d’accès ou des problèmes similaires soient déclenchés dans les DLL qui sont appelées avant d’avoir été initialisées.  
  
## <a name="output"></a>Sortie  
 Cet Assistant Débogage managé signale qu’une exécution managée interdite est tentée.  Vous devez examiner la pile du thread pour déterminer la raison pour laquelle le verrouillage du chargeur se produit et comment résoudre le problème.  
  
## <a name="configuration"></a>Configuration  
  
```xml  
<mdaConfig>  
  <assistants>  
    <loaderLock/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a>Voir aussi

- [Diagnostic d’erreurs avec les Assistants Débogage managé](diagnosing-errors-with-managed-debugging-assistants.md)
