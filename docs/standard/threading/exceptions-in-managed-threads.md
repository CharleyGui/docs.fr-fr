---
title: Exceptions dans les threads managés
description: Découvrez comment les exceptions non gérées sont gérées dans .NET. La plupart des exceptions de thread non gérées se poursuivent naturellement et mènent à l’arrêt de l’application.
ms.date: 03/30/2017
helpviewer_keywords:
- unhandled exceptions,in managed threads
- threading [.NET],unhandled exceptions
- threading [.NET],exceptions in managed threads
- managed threading
ms.assetid: 11294769-2e89-43cb-890e-ad4ad79cfbee
ms.openlocfilehash: e5acda4137d020d35d3144e9cc61e174024e165a
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94826467"
---
# <a name="exceptions-in-managed-threads"></a>Exceptions dans les threads managés

Le common language runtime permet à la plupart des exceptions non gérées dans les threads de continuer naturellement. Dans la plupart des cas, cela signifie que l’exception non prise en charge provoque l’arrêt de l’application.
  
Le common language runtime représente une protection pour certaines exceptions non prises en charge qui sont utilisées pour contrôler le flux du programme :  
  
- Une <xref:System.Threading.ThreadAbortException> est levée dans un thread, car <xref:System.Threading.Thread.Abort%2A> a été appelé.  
  
- Une <xref:System.AppDomainUnloadedException> est levée dans un thread, car le domaine d’application dans lequel le thread s’exécute est en cours de déchargement.  
  
- Le common language runtime ou un processus hôte met fin au thread en levant une exception interne.  
  
 Si l’une de ces exceptions n’est pas prise en charge dans les threads créés par le common language runtime, elle arrête le thread, mais le common language runtime n’autorise pas l’exception à poursuivre.  
  
 Si ces exceptions ne sont pas prises en charge dans le thread principal ou dans les threads qui sont entrés dans le runtime à partir de code non managé, elles se poursuivent normalement, ce qui entraîne l’arrêt de l’application.  
  
> [!NOTE]
> Il est possible que le runtime lève une exception non prise en charge avant que du code managé ait pu installer un gestionnaire d’exceptions. Bien que le code managé n’ait pas eu la possibilité de traiter cette exception, elle est autorisée à poursuivre naturellement.  
  
## <a name="exposing-threading-problems-during-development"></a>Mettre en lumière des problèmes de threads au cours du développement  
 Lorsque les threads sont autorisés à s’interrompre de façon silencieuse, sans arrêter l’application, de graves problèmes de programmation risquent de passer inaperçus. Il s’agit d’un problème particulier pour les services et d’autres applications qui s’exécutent pendant des périodes prolongées. Au fur et à mesure des échecs de threads, le programme s’endommage progressivement. L’application risque de voir ses performances se dégrader ou de ne plus répondre.  
  
 Le fait d’autoriser les exceptions non prises en charge dans les threads à poursuivre naturellement, jusqu’à ce que le système d’exploitation arrête le programme, expose à de tels problèmes lors du développement et des tests. Les rapports d’erreurs sur les arrêts du programme prennent en charge le débogage.  
  
## <a name="change-from-previous-versions"></a>Modification par rapport aux versions précédentes

Dans les versions 1,0 et 1,1 de .NET Framework, le common language runtime fournit un arrêt pour les exceptions non gérées dans les situations suivantes :  
  
- Il n’existe pas d’exceptions non prises en charge sur un thread de pool de threads. Lorsqu’une tâche lève une exception qu’elle ne prend pas en charge, le runtime imprime l’arborescence des appels de procédure de l’exception dans la console, puis renvoie le thread au pool de threads.  
  
- Il n’existe pas d’exceptions non prises en charge sur un thread créé avec la méthode <xref:System.Threading.Thread.Start%2A> de la classe <xref:System.Threading.Thread>. Lorsque le code qui s’exécute sur un tel thread lève une exception qu’elle ne prend pas en charge, le runtime imprime l’arborescence des appels de procédure de l’exception dans la console, puis arrête correctement le thread.  
  
- Il n’existe pas d’exceptions non prises en charge sur le thread du finaliseur. Lorsqu’un finaliseur lève une exception qu’elle ne prend pas en charge, le runtime imprime l’arborescence des appels de procédure de l’exception dans la console, puis permet au thread du finaliseur de reprendre l’exécution des finaliseurs.  
  
 L’état au premier plan ou en arrière-plan d’un thread managé n’affecte pas ce comportement.  
  
 Dans le cas des exceptions non prises en charge sur les threads provenant de code non managé, la différence est plus subtile. La boîte de dialogue à liaison JIT du runtime prévaut sur la boîte de dialogue du système d’exploitation pour les exceptions managées ou les exceptions natives sur les threads qui sont passés à travers du code natif. Le processus s’arrête dans tous les cas.

### <a name="migration"></a>Migration

Si vous effectuez une migration à partir de .NET Framework 1,0 ou 1,1 et que vous avez tiré parti de l’arrêt du runtime, par exemple pour arrêter des threads, envisagez l’une des stratégies de migration suivantes :  
  
- Restructurer le code de façon que le thread s’arrête normalement à la réception d’un signal.  
  
- Utilisez la méthode <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> pour abandonner le thread.  
  
- Si un thread doit être arrêté pour permettre l’arrêt du processus, faire du thread un thread d’arrière-plan afin qu’il s’arrête automatiquement à la sortie du processus.  
  
Dans tous les cas, la stratégie doit respecter les instructions de conception des exceptions. Consultez la page [Instructions de conception des exceptions](../design-guidelines/exceptions.md).  
  
À titre de mesure de compatibilité temporaire, les administrateurs peuvent placer un indicateur de compatibilité dans la section `<runtime>` du fichier de configuration de l’application. Cela entraîne le retour du common language runtime au comportement des versions 1.0 et 1.1.  
  
```xml  
<legacyUnhandledExceptionPolicy enabled="1"/>  
```  
  
## <a name="host-override"></a>Remplacement de l’hôte

Un hôte non managé peut utiliser l’interface [ICLRPolicyManager](../../framework/unmanaged-api/hosting/iclrpolicymanager-interface.md) dans l’API d’hébergement pour remplacer la stratégie d’exception non gérée par défaut de l’Common Language Runtime. La fonction [ICLRPolicyManager::SetUnhandledExceptionPolicy](../../framework/unmanaged-api/hosting/iclrpolicymanager-setunhandledexceptionpolicy-method.md) est utilisée pour définir la stratégie des exceptions non prises en charge .  
  
## <a name="see-also"></a>Voir aussi

- [Éléments fondamentaux du threading managé](managed-threading-basics.md)
