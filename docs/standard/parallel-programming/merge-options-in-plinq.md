---
title: Options de fusion en PLINQ
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- PLINQ queries, merge options
ms.assetid: e8f7be3b-88de-4f33-ab14-dc008e76c1ba
ms.openlocfilehash: 18f233ac4c5afa63ec31e83d5fff8f0a57f9146f
ms.sourcegitcommit: 81ad1f09b93f3b3e6706a7f2e4ddf50ef229ea3d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/20/2019
ms.locfileid: "74203998"
---
# <a name="merge-options-in-plinq"></a>Options de fusion en PLINQ
Quand une requête s’exécute en parallèle, PLINQ partitionne la séquence source pour que plusieurs threads puissent fonctionner simultanément sur différentes parties, généralement sur des threads distincts. Si les résultats doivent être utilisés sur un thread, par exemple, dans une boucle `foreach` (`For Each` en Visual Basic), les résultats de chaque thread doivent être fusionnés de nouveau en une séquence. Le type de fusion que PLINQ exécute dépend des opérateurs présents dans la requête. Par exemple, les opérateurs qui imposent un nouvel ordre des résultats doivent mettre en mémoire tampon tous les éléments de tous les threads. Du point de vue du thread utilisateur (qui est également celui de l’utilisateur de l’application), une requête entièrement mise en mémoire tampon peut s’exécuter pendant un certain temps avant qu’elle ne génère son premier résultat. D’autres opérateurs, par défaut, sont partiellement mis en mémoire tampon. Ils transmettent leurs résultats par lots. L’opérateur <xref:System.Linq.ParallelEnumerable.ForAll%2A> n’est pas mis en mémoire tampon par défaut. Il transmet immédiatement tous les éléments à partir de tous les threads.  
  
 À l’aide de la méthode <xref:System.Linq.ParallelEnumerable.WithMergeOptions%2A>, comme indiqué dans l’exemple suivant, vous pouvez fournir un indicateur à PLINQ spécifiant le type de fusion à exécuter.  
  
 [!code-csharp[PLINQ#26](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#26)]
 [!code-vb[PLINQ#26](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinq2_vb.vb#26)]  
  
 Pour obtenir un exemple complet, consultez [Comment : spécifier des options de fusion en PLINQ](../../../docs/standard/parallel-programming/how-to-specify-merge-options-in-plinq.md).  
  
 Si la requête ne peut pas prendre en charge l’option demandée, cette dernière sera simplement ignorée. Dans la plupart des cas, il n’est pas nécessaire de spécifier une option de fusion pour une requête PLINQ. Toutefois, dans certains cas, après avoir effectué des tests et des mesures, vous pouvez trouver qu’une requête s’exécute mieux dans un mode non défini par défaut. Cette option est souvent utilisée pour forcer un opérateur de fusion de blocs à diffuser ses résultats en continu afin de fournir une interface utilisateur plus réactive.  
  
## <a name="parallelmergeoptions"></a>ParallelMergeOptions  
 L’énumération <xref:System.Linq.ParallelMergeOptions> inclut les options suivantes qui spécifient, pour les formes de requête prises en charge, la manière dont la sortie finale de la requête est transmise quand les résultats sont utilisés sur un thread :  
  
- `Not Buffered`  
  
     Avec l’option <xref:System.Linq.ParallelMergeOptions.NotBuffered>, chaque élément traité est retourné à partir de chaque thread dès qu’il est généré. Ce comportement revient à « diffuser en continu » la sortie. Si l’opérateur <xref:System.Linq.ParallelEnumerable.AsOrdered%2A> est présent dans la requête, `NotBuffered` conserve l’ordre des éléments sources. Although `NotBuffered` starts yielding results as soon as they're available, the total time to produce all the results might still be longer than using one of the other merge options.  
  
- `Auto Buffered`  
  
     Avec l’option <xref:System.Linq.ParallelMergeOptions.AutoBuffered>, la requête regroupe des éléments dans une mémoire tampon, puis transmet régulièrement tout le contenu de cette mémoire simultanément au thread utilisateur. Cette option revient à transmettre les données sources dans des « blocs » au lieu d’utiliser le comportement de « diffusion en continu » de `NotBuffered`. `AutoBuffered` peut nécessiter plus de temps que `NotBuffered` pour rendre le premier élément disponible sur le thread utilisateur. La taille de la mémoire tampon et le comportement exact de transmission ne sont pas configurables et peuvent varier en fonction de différents facteurs liés à la requête.  
  
- `FullyBuffered`  
  
     Avec l’option <xref:System.Linq.ParallelMergeOptions.FullyBuffered>, la sortie de la requête entière est mise en mémoire tampon avant que l’un des éléments ne soit transmis. Cette option peut nécessiter plus de temps pour que le premier élément soit disponible sur le thread utilisateur, mais les résultats complets peuvent toujours être générés plus rapidement qu’avec les autres options.  
  
## <a name="query-operators-that-support-merge-options"></a>Opérateurs de requête prenant en charge les options de fusion  
 Le tableau suivant répertorie les opérateurs qui prennent en charge tous les modes d’options de fusion, qui sont soumis aux restrictions spécifiées.  
  
|opérateur|Restrictions|  
|--------------|------------------|  
|<xref:System.Linq.ParallelEnumerable.AsEnumerable%2A>|aucune.|  
|<xref:System.Linq.ParallelEnumerable.Cast%2A>|aucune.|  
|<xref:System.Linq.ParallelEnumerable.Concat%2A>|Requêtes non ordonnées qui ont uniquement une source de type Tableau ou Liste.|  
|<xref:System.Linq.ParallelEnumerable.DefaultIfEmpty%2A>|aucune.|  
|<xref:System.Linq.ParallelEnumerable.OfType%2A>|aucune.|  
|<xref:System.Linq.ParallelEnumerable.Reverse%2A>|Requêtes non ordonnées qui ont uniquement une source de type Tableau ou Liste.|  
|<xref:System.Linq.ParallelEnumerable.Select%2A>|aucune.|  
|<xref:System.Linq.ParallelEnumerable.SelectMany%2A>|aucune.|  
|<xref:System.Linq.ParallelEnumerable.Skip%2A>|aucune.|  
|<xref:System.Linq.ParallelEnumerable.Take%2A>|aucune.|  
|<xref:System.Linq.ParallelEnumerable.Where%2A>|aucune.|  
  
 Tous les autres opérateurs de requête PLINQ peuvent ignorer les options de fusion fournis par l’utilisateur. Certains opérateurs de requête, tels que <xref:System.Linq.ParallelEnumerable.Reverse%2A> et <xref:System.Linq.ParallelEnumerable.OrderBy%2A>, ne peuvent pas transmettre d’éléments tant qu’ils n’ont pas tous été générés et réorganisés. Par conséquent, si vous utilisez <xref:System.Linq.ParallelMergeOptions> dans une requête qui contient également un opérateur tel que <xref:System.Linq.ParallelEnumerable.Reverse%2A>, le comportement de fusion ne sera appliqué dans la requête qu’une fois que l’opérateur aura généré ses résultats.  
  
 La capacité de certains opérateurs à gérer les options de fusion varie selon le type de la séquence source et selon que l’opérateur <xref:System.Linq.ParallelEnumerable.AsOrdered%2A> a été utilisé antérieurement dans la requête ou non. <xref:System.Linq.ParallelEnumerable.ForAll%2A> est toujours <xref:System.Linq.ParallelMergeOptions.NotBuffered> ; il transmet immédiatement ses éléments. <xref:System.Linq.ParallelEnumerable.OrderBy%2A> est toujours <xref:System.Linq.ParallelMergeOptions.FullyBuffered> ; il doit trier l’intégralité de la liste avant toute transmission.  
  
## <a name="see-also"></a>Voir aussi

- [Parallel LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
- [Comment : spécifier des options de fusion en PLINQ](../../../docs/standard/parallel-programming/how-to-specify-merge-options-in-plinq.md)
