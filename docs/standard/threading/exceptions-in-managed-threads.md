---
title: Exceptions dans les threads managés
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- unhandled exceptions,in managed threads
- threading [.NET Framework],unhandled exceptions
- threading [.NET Framework],exceptions in managed threads
- managed threading
ms.assetid: 11294769-2e89-43cb-890e-ad4ad79cfbee
ms.openlocfilehash: 6c14c60b30f8f70aa5e888ed45d6f867154e18d8
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/28/2020
ms.locfileid: "78159648"
---
# <a name="exceptions-in-managed-threads"></a>Exceptions dans les threads managés
À partir du .NET Framework version 2.0, le common language runtime permet à la plupart des exceptions non prises en charge dans les threads de poursuivre naturellement. Dans la plupart des cas, cela signifie que l’exception non prise en charge provoque l’arrêt de l’application.  
  
> [!NOTE]
> Il s’agit d’un changement important par rapport au .NET Framework versions 1.0 et 1.1, qui assurent une protection pour nombreuses exceptions non prises en charge, par exemple les exceptions non prises en charge dans les threads des pools de threads. Consultez la section [Changements par rapport aux versions précédentes](#ChangeFromPreviousVersions) plus loin dans cette rubrique.  
  
 Le common language runtime représente une protection pour certaines exceptions non prises en charge qui sont utilisées pour contrôler le flux du programme :  
  
- Une <xref:System.Threading.ThreadAbortException> est levée dans un thread, car <xref:System.Threading.Thread.Abort%2A> a été appelé.  
  
- Une <xref:System.AppDomainUnloadedException> est levée dans un thread, car le domaine d’application dans lequel le thread s’exécute est en cours de déchargement.  
  
- Le common language runtime ou un processus hôte met fin au thread en levant une exception interne.  
  
 Si l’une de ces exceptions n’est pas prise en charge dans les threads créés par le common language runtime, elle arrête le thread, mais le common language runtime n’autorise pas l’exception à poursuivre.  
  
 Si ces exceptions ne sont pas prises en charge dans le thread principal ou dans les threads qui sont entrés dans le runtime à partir de code non managé, elles se poursuivent normalement, ce qui entraîne l’arrêt de l’application.  
  
> [!NOTE]
> Il est possible que le runtime lève une exception non prise en charge avant que du code managé ait pu installer un gestionnaire d’exceptions. Bien que le code managé n’ait pas eu la possibilité de traiter cette exception, elle est autorisée à poursuivre naturellement.  
  
## <a name="exposing-threading-problems-during-development"></a>Mettre en lumière des problèmes de threads au cours du développement  
 Lorsque les threads sont autorisés à s’interrompre de façon silencieuse, sans arrêter l’application, de graves problèmes de programmation risquent de passer inaperçus. Il s’agit d’un problème particulier pour les services et autres applications qui s’exécutent sur de longues périodes. Au fur et à mesure des échecs de threads, le programme s’endommage progressivement. L’application risque de voir ses performances se dégrader ou de ne plus répondre.  
  
 Le fait d’autoriser les exceptions non prises en charge dans les threads à poursuivre naturellement, jusqu’à ce que le système d’exploitation arrête le programme, expose à de tels problèmes lors du développement et des tests. Les rapports d’erreurs sur les arrêts du programme prennent en charge le débogage.  
  
<a name="ChangeFromPreviousVersions"></a>
## <a name="change-from-previous-versions"></a>Changements par rapport aux versions antérieures  
 La modification la plus importante concerne les threads managés. Dans les versions 1.0 et 1.1 du .NET Framework, le common language runtime représente une protection pour les exceptions non prises en charge dans les situations suivantes :  
  
- Il n’existe pas d’exceptions non prises en charge sur un thread de pool de threads. Lorsqu’une tâche lève une exception qu’elle ne prend pas en charge, le runtime imprime l’arborescence des appels de procédure de l’exception dans la console, puis renvoie le thread au pool de threads.  
  
- Il n’existe pas d’exceptions non prises en charge sur un thread créé avec la méthode <xref:System.Threading.Thread.Start%2A> de la classe <xref:System.Threading.Thread>. Lorsque le code qui s’exécute sur un tel thread lève une exception qu’elle ne prend pas en charge, le runtime imprime l’arborescence des appels de procédure de l’exception dans la console, puis arrête correctement le thread.  
  
- Il n’existe pas d’exceptions non prises en charge sur le thread du finaliseur. Lorsqu’un finaliseur lève une exception qu’elle ne prend pas en charge, le runtime imprime l’arborescence des appels de procédure de l’exception dans la console, puis permet au thread du finaliseur de reprendre l’exécution des finaliseurs.  
  
 L’état au premier plan ou en arrière-plan d’un thread managé n’affecte pas ce comportement.  
  
 Dans le cas des exceptions non prises en charge sur les threads provenant de code non managé, la différence est plus subtile. La boîte de dialogue à liaison JIT du runtime prévaut sur la boîte de dialogue du système d’exploitation pour les exceptions managées ou les exceptions natives sur les threads qui sont passés à travers du code natif. Le processus s’arrête dans tous les cas.  
  
### <a name="migrating-code"></a>Migrer du code  
 En général, la modification permet de mettre en lumière des problèmes de programmation auparavant non reconnus afin de les résoudre. Dans certains cas, toutefois, les programmeurs pouvaient tirer parti de la protection du runtime, par exemple pour arrêter des threads. Selon la situation, ils doivent envisager l’une des stratégies de migration suivantes :  
  
- Restructurer le code de façon que le thread s’arrête normalement à la réception d’un signal.  
  
- Utilisez la méthode <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> pour abandonner le thread.  
  
- Si un thread doit être arrêté pour permettre l’arrêt du processus, faire du thread un thread d’arrière-plan afin qu’il s’arrête automatiquement à la sortie du processus.  
  
 Dans tous les cas, la stratégie doit respecter les instructions de conception des exceptions. Consultez la page [Instructions de conception des exceptions](../../../docs/standard/design-guidelines/exceptions.md).  
  
### <a name="application-compatibility-flag"></a>Indicateur de compatibilité des applications  
 À titre de mesure de compatibilité temporaire, les administrateurs peuvent placer un indicateur de compatibilité dans la section `<runtime>` du fichier de configuration de l’application. Cela entraîne le retour du common language runtime au comportement des versions 1.0 et 1.1.  
  
```xml  
<legacyUnhandledExceptionPolicy enabled="1"/>  
```  
  
## <a name="host-override"></a>Remplacement de l’hôte  
 Dans le .NET Framework version 2.0, un hôte non managé peut utiliser l’interface [ICLRPolicyManager](../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md) dans l’API d’hébergement pour remplacer la stratégie d’exceptions non prises en charge par défaut du common language runtime. La fonction [ICLRPolicyManager::SetUnhandledExceptionPolicy](../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setunhandledexceptionpolicy-method.md) est utilisée pour définir la stratégie des exceptions non prises en charge .  
  
## <a name="see-also"></a>Voir aussi

- [Éléments fondamentaux du threading managé](../../../docs/standard/threading/managed-threading-basics.md)
