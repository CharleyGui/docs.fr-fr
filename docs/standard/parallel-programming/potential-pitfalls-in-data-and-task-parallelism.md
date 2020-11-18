---
title: Pièges potentiels dans le parallélisme des données et des tâches
description: Découvrez les pièges potentiels dans le parallélisme des données et des tâches, car le parallélisme augmente la complexité qui n’est pas rencontrée dans le code séquentiel.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- parallel programming, pitfalls
ms.assetid: 1e357177-e699-4b8f-9e49-56d3513ed128
ms.openlocfilehash: 61c0ea2360ae347e9d5b5eed6fc490171e028408
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94822254"
---
# <a name="potential-pitfalls-in-data-and-task-parallelism"></a>Pièges potentiels dans le parallélisme des données et des tâches
Dans de nombreux cas, <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> et <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> permettent une amélioration significative des performances par rapport à des boucles séquentielles ordinaires. Toutefois, le travail de la parallélisation de la boucle présente une certaine complexité pouvant entraîner des problèmes qui, dans du code séquentiel, ne sont pas si courants ou ne surviennent pas du tout. Cette rubrique répertorie les pratiques à éviter lorsque vous écrivez des boucles parallèles.  
  
## <a name="do-not-assume-that-parallel-is-always-faster"></a>Ne partez pas du principe qu’une boucle parallèle est toujours plus rapide  
 Dans certains cas, elle peut s’exécuter plus lentement qu’une boucle séquentielle équivalente. La règle empirique de base veut que les boucles parallèles ayant peu d’itérations et des délégués utilisateurs rapides ne soient pas susceptibles d’apporter une grande accélération. Toutefois, étant donné que de nombreux facteurs sont impliqués dans les performances, nous vous recommandons de toujours mesurer les résultats réels.  
  
## <a name="avoid-writing-to-shared-memory-locations"></a>Éviter d’écrire à des emplacements de mémoire partagés  
 Dans du code séquentiel, il n’est pas rare de lire des variables statiques ou d’écrire dans ces dernières ou dans des champs de classe. Toutefois, l’accès simultané de plusieurs threads à de telles variables entraîne un fort risque d’engorgement. Bien que vous puissiez utiliser des verrous pour synchroniser l’accès à la variable, le coût de synchronisation peut nuire aux performances. Par conséquent, nous vous recommandons d’éviter, ou au moins de limiter autant que possible l’accès à un état partagé dans une boucle parallèle. La meilleure façon de procéder consiste à utiliser les surcharges de <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> et <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> qui utilisent une variable <xref:System.Threading.ThreadLocal%601?displayProperty=nameWithType> pour stocker l’état local du thread pendant l’exécution de la boucle. Pour plus d’informations, consultez [Guide pratique pour écrire une boucle Parallel.For avec des variables locales de thread](how-to-write-a-parallel-for-loop-with-thread-local-variables.md) et [Guide pratique pour écrire une boucle Parallel.ForEach avec des variables locales de partition](how-to-write-a-parallel-foreach-loop-with-partition-local-variables.md).  
  
## <a name="avoid-over-parallelization"></a>Éviter la surparallélisation  
 L’utilisation de boucles parallèles entraîne des coûts de surcharge liés au partitionnement de la collection source et à la synchronisation des threads de travail. Les avantages de la parallélisation sont également limités par le nombre de processeurs de l’ordinateur. L’exécution de plusieurs threads liés au calcul sur un seul processeur ne permet aucune accélération. Par conséquent, vous devez veiller à ne pas surparalléliser une boucle.  
  
 Les boucles imbriquées sont le scénario le plus courant dans lequel une surparallélisation peut se produire. Dans la plupart des cas, il est préférable de paralléliser uniquement la boucle externe, sauf si une ou plusieurs conditions suivantes s’appliquent :  
  
- La boucle interne est réputée être très longue.  
  
- Vous effectuez un calcul coûteux sur chaque commande. (l’opération montrée dans l’exemple n’est pas coûteuse)  
  
- Le système cible est connu pour avoir suffisamment de processeurs pour gérer le nombre de threads produits en parallélisant la requête sur `cust.Orders`.  
  
 Dans tous les cas, le test et la mesure sont la meilleure façon de déterminer la forme de requête optimale.  
  
## <a name="avoid-calls-to-non-thread-safe-methods"></a>Éviter de faire appel aux méthodes qui ne sont pas thread-safe  
 L’écriture dans des méthodes d’instance qui ne sont pas thread-safe à partir d’une boucle parallèle peut entraîner une corruption des données qui peut être détectée ou non dans votre programme. Cela peut également entraîner des exceptions. Dans l’exemple suivant, plusieurs threads tenteraient d’appeler simultanément la méthode <xref:System.IO.FileStream.WriteByte%2A?displayProperty=nameWithType>, qui n’est pas prise en charge par la classe.  
  
 [!code-csharp[TPL_Pitfalls#04](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_pitfalls/cs/pitfalls.cs#04)]
 [!code-vb[TPL_Pitfalls#04](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_pitfalls/vb/pitfalls_vb.vb#04)]  
  
## <a name="limit-calls-to-thread-safe-methods"></a>Limiter les appels aux méthodes qui ne sont pas thread-safe  
 La plupart des méthodes statiques dans .NET sont thread-safe et peuvent être appelées à partir de plusieurs threads simultanément. Toutefois, même dans ces cas, la synchronisation impliquée peut entraîner un ralentissement significatif de la requête.  
  
> [!NOTE]
> Vous pouvez le tester vous-même en insérant des appels à <xref:System.Console.WriteLine%2A> dans vos requêtes. Bien que cette méthode soit utilisée dans les exemples de documentation destinés à la démonstration, ne l’utilisez pas dans les boucles parallèles, sauf si nécessaire.  
  
## <a name="be-aware-of-thread-affinity-issues"></a>Tenir compte des problèmes d’affinité de thread  
 Certaines technologies, par exemple, les composants STA (Single-Threaded Apartment), Windows Forms et Windows Presentation Foundation (WPF) imposent des restrictions d’affinité de thread qui requièrent l’exécution de code sur un thread spécifique. Par exemple, dans Windows Forms et WPF, un contrôle est uniquement accessible sur le thread sur lequel il a été créé. Cela signifie, par exemple, que vous ne pouvez pas mettre à jour un contrôle de liste à partir d’une boucle parallèle, sauf si vous configurez le planificateur de threads de sorte qu’il planifie le travail uniquement sur le thread d’interface utilisateur. Pour plus d’informations, consultez [Spécification d’un contexte de synchronisation](xref:System.Threading.Tasks.TaskScheduler#specifying-a-synchronization-context).  
  
## <a name="use-caution-when-waiting-in-delegates-that-are-called-by-parallelinvoke"></a>Être vigilant lors de l’attente dans des délégués appelés par Parallel.Invoke  
 Dans certaines circonstances, la bibliothèque parallèle de tâches intègre une tâche, ce qui signifie qu’elle s’exécute sur la tâche du thread en cours d’exécution. (Pour plus d’informations, consultez [planificateurs de tâches](xref:System.Threading.Tasks.TaskScheduler).) Cette optimisation des performances peut entraîner un blocage dans certains cas. Par exemple, deux tâches peuvent exécuter le même code de délégué, qui signale la survenue d’un événement et attend l’autre tâche à signaler. Si la seconde tâche est incluse sur le même thread que la première et que cette dernière passe à l’état En attente, la seconde tâche ne pourra jamais signaler son événement. Pour éviter une telle situation, vous pouvez spécifier un délai d’expiration sur l’opération d’attente, ou utiliser les constructeurs de thread explicites pour s’assurer qu’une tâche ne peut pas bloquer l’autre.  
  
## <a name="do-not-assume-that-iterations-of-foreach-for-and-forall-always-execute-in-parallel"></a>Ne pas supposer que les itérations de ForEach, For et ForAll s’exécutent toujours en parallèle  
 Il est important de garder à l’esprit que les itérations individuelles dans une boucle <xref:System.Threading.Tasks.Parallel.For%2A>, <xref:System.Threading.Tasks.Parallel.ForEach%2A> ou <xref:System.Linq.ParallelEnumerable.ForAll%2A> peuvent, mais ne doivent pas forcément, s’exécuter en parallèle. Par conséquent, vous devez éviter d’écrire du code dont l’exactitude dépend de l’exécution parallèle d’itérations ou de l’exécution d’itérations dans un ordre particulier. Par exemple, ce code est susceptible d’interbloquer :  
  
 [!code-csharp[TPL_Pitfalls#01](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_pitfalls/cs/pitfalls.cs#01)]
 [!code-vb[TPL_Pitfalls#01](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_pitfalls/vb/pitfalls_vb.vb#01)]  
  
 Dans cet exemple, une itération définit un événement que toutes les autres itérations attendent. Aucune des itérations en attente ne peut s’achever tant que l’itération de définition d’événement n’est pas terminée. Toutefois, il est possible que les itérations en attente bloquent tous les threads utilisés pour exécuter la boucle parallèle, avant que l’itération de définition d’événement ait eu une chance de s’exécuter. Cela provoque un interblocage : l’itération de définition d’événement ne s’exécute jamais et les itérations en attente ne s’activent pas non plus.  
  
 En particulier, une itération de boucle parallèle ne doit jamais attendre une autre itération de la boucle pour progresser. Si la boucle parallèle décide de planifier les itérations de manière séquentielle, mais dans l’ordre inverse, un interblocage se produit.  
  
## <a name="avoid-executing-parallel-loops-on-the-ui-thread"></a>Éviter d’exécuter des boucles parallèles sur le thread d’interface utilisateur  
 Il est important de maintenir la réactivité de l’interface utilisateur de l’application (IU). Si une opération contient suffisamment de travail pour assurer la parallélisation, cette opération ne doit pas être exécutée sur le thread d’interface utilisateur.  Au lieu de cela, elle doit décharger cette opération de sorte qu’elle s’exécute sur un thread d’arrière-plan. Par exemple, si vous souhaitez utiliser une boucle parallèle pour calculer des données qui doivent ensuite être restituées dans un contrôle d’interface utilisateur, vous devez envisager l’exécution de la boucle dans une instance de tâche plutôt que directement dans un gestionnaire d’événements de l’interface utilisateur.  Vous ne devez marshaler la mise à jour de l’interface utilisateur vers le thread de l’interface utilisateur qu’une fois le calcul principal terminé.  
  
 Si vous exécutez des boucles parallèles sur le thread d’interface utilisateur, veillez à éviter la mise à jour des contrôles d’interface utilisateur à partir de la boucle. Toute tentative de mise à jour des contrôles d’interface utilisateur à partir d’une boucle parallèle qui s’exécute sur le thread d’interface utilisateur peut entraîner une altération de l’état, des exceptions, des reports de mise à jour et même des interblocages, selon la manière dont la mise à jour de l’interface utilisateur est appelée. Dans l’exemple suivant, la boucle parallèle bloque le thread d’interface utilisateur sur lequel elle s’exécute jusqu’à ce que toutes les itérations soient terminées. Toutefois, si une itération de la boucle s’exécute sur un thread d’arrière-plan (comme <xref:System.Threading.Tasks.Parallel.For%2A> peut le faire), l’appel à Invoke entraîne l’envoi d’un message au thread d’interface utilisateur et bloque en attendant que ce message soit traité. Étant donné que le thread d’interface utilisateur est bloqué lors de l’exécution de <xref:System.Threading.Tasks.Parallel.For%2A>, le message ne peut jamais être traité et le thread d’interface utilisateur est soumis à des interblocages.  
  
 [!code-csharp[TPL_Pitfalls#02](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_pitfalls/cs/pitfalls.cs#02)]
 [!code-vb[TPL_Pitfalls#02](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_pitfalls/vb/pitfalls_vb.vb#02)]  
  
 L’exemple suivant montre comment éviter l’interblocage, en exécutant la boucle à l’intérieur d’une instance de tâche. Le thread d’interface utilisateur n’est pas bloqué par la boucle, et le message peut être traité.  
  
 [!code-csharp[TPL_Pitfalls#03](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_pitfalls/cs/pitfalls.cs#03)]
 [!code-vb[TPL_Pitfalls#03](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_pitfalls/vb/pitfalls_vb.vb#03)]  
  
## <a name="see-also"></a>Voir aussi

- [Programmation parallèle](index.md)
- [Pièges potentiels avec PLINQ](potential-pitfalls-with-plinq.md)
- [Modèles de programmation parallèle : présentation et application des modèles parallèles avec le .NET Framework 4 (page éventuellement en anglais)](https://www.microsoft.com/download/details.aspx?id=19222)
