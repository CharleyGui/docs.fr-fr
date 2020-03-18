---
title: 'Comment : implémenter des partitions dynamiques'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- tasks, how to create a dynamic partitioner
ms.assetid: c875ad12-a161-43e6-ad1c-3d6927c536a7
ms.openlocfilehash: 3970566b4e3f51ce538c328d4e69b20ec22ec09b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73091418"
---
# <a name="how-to-implement-dynamic-partitions"></a><span data-ttu-id="7b555-102">Comment : implémenter des partitions dynamiques</span><span class="sxs-lookup"><span data-stu-id="7b555-102">How to: Implement Dynamic Partitions</span></span>

<span data-ttu-id="7b555-103">L’exemple suivant montre comment implémenter un <xref:System.Collections.Concurrent.OrderablePartitioner%601?displayProperty=nameWithType> personnalisé qui implémente le partitionnement dynamique et peut être utilisée à partir de certaines surcharges <xref:System.Threading.Tasks.Parallel.ForEach%2A> et à partir de PLINQ.</span><span class="sxs-lookup"><span data-stu-id="7b555-103">The following example shows how to implement a custom <xref:System.Collections.Concurrent.OrderablePartitioner%601?displayProperty=nameWithType> that implements dynamic partitioning and can be used from certain overloads <xref:System.Threading.Tasks.Parallel.ForEach%2A> and from PLINQ.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7b555-104"> Exemple</span><span class="sxs-lookup"><span data-stu-id="7b555-104">Example</span></span>

<span data-ttu-id="7b555-105">À chaque fois qu’une partition appelle <xref:System.Collections.IEnumerator.MoveNext%2A> sur l’énumérateur, celui-ci fournit à la partition un élément de liste.</span><span class="sxs-lookup"><span data-stu-id="7b555-105">Each time a partition calls <xref:System.Collections.IEnumerator.MoveNext%2A> on the enumerator, the enumerator provides the partition with one list element.</span></span> <span data-ttu-id="7b555-106">Dans le cas de PLINQ et <xref:System.Threading.Tasks.Parallel.ForEach%2A>, la partition est une instance <xref:System.Threading.Tasks.Task>.</span><span class="sxs-lookup"><span data-stu-id="7b555-106">In the case of PLINQ and <xref:System.Threading.Tasks.Parallel.ForEach%2A>, the partition is a <xref:System.Threading.Tasks.Task> instance.</span></span> <span data-ttu-id="7b555-107">Étant donné que les requêtes arrivent simultanément sur plusieurs threads, l’accès à l’index actuel est synchronisé.</span><span class="sxs-lookup"><span data-stu-id="7b555-107">Because requests are happening concurrently on multiple threads, access to the current index is synchronized.</span></span>  

[!code-csharp[TPL_Partitioners#04](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_partitioners/cs/partitioner02.cs#OrderableListPartitioner)]
[!code-vb[TPL_Partitioners#04](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_partitioners/vb/dynamicpartitioner.vb#04)]  

<span data-ttu-id="7b555-108">Il s’agit d’un exemple de partitionnement par segments, chaque segment se composant d’un seul élément.</span><span class="sxs-lookup"><span data-stu-id="7b555-108">This is an example of chunk partitioning, with each chunk consisting of one element.</span></span> <span data-ttu-id="7b555-109">En fournissant plus d’éléments à la fois, vous pourriez réduire le conflit sur le verrou et atteindre, en théorie, des performances plus rapides.</span><span class="sxs-lookup"><span data-stu-id="7b555-109">By providing more elements at a time, you could reduce the contention over the lock and theoretically achieve faster performance.</span></span> <span data-ttu-id="7b555-110">Toutefois, à un moment donné, des segments plus volumineux pourraient nécessiter une logique supplémentaire d’équilibrage de charge afin de conserver tous les threads occupés jusqu'à ce que tout le travail soit effectué.</span><span class="sxs-lookup"><span data-stu-id="7b555-110">However, at some point, larger chunks might require additional load-balancing logic in order to keep all threads busy until all the work is done.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7b555-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7b555-111">See also</span></span>

* [<span data-ttu-id="7b555-112">Partitionneurs personnalisés pour PLINQ et la bibliothèque parallèle de tâches (TPL)</span><span class="sxs-lookup"><span data-stu-id="7b555-112">Custom Partitioners for PLINQ and TPL</span></span>](../../../docs/standard/parallel-programming/custom-partitioners-for-plinq-and-tpl.md)
* [<span data-ttu-id="7b555-113">Comment : implémenter un partitionneur pour un partitionnement statique</span><span class="sxs-lookup"><span data-stu-id="7b555-113">How to: Implement a Partitioner for Static Partitioning</span></span>](../../../docs/standard/parallel-programming/how-to-implement-a-partitioner-for-static-partitioning.md)
