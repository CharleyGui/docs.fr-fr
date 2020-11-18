---
title: 'Procédure : implémenter des partitions dynamiques'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- tasks, how to create a dynamic partitioner
ms.assetid: c875ad12-a161-43e6-ad1c-3d6927c536a7
ms.openlocfilehash: 1120d846743ac3b89d2d110b4d1abdd0083f9eab
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94825739"
---
# <a name="how-to-implement-dynamic-partitions"></a>Procédure : implémenter des partitions dynamiques

L’exemple suivant montre comment implémenter un <xref:System.Collections.Concurrent.OrderablePartitioner%601?displayProperty=nameWithType> personnalisé qui implémente le partitionnement dynamique et peut être utilisée à partir de certaines surcharges <xref:System.Threading.Tasks.Parallel.ForEach%2A> et à partir de PLINQ.  
  
## <a name="example"></a>Exemple

À chaque fois qu’une partition appelle <xref:System.Collections.IEnumerator.MoveNext%2A> sur l’énumérateur, celui-ci fournit à la partition un élément de liste. Dans le cas de PLINQ et <xref:System.Threading.Tasks.Parallel.ForEach%2A>, la partition est une instance <xref:System.Threading.Tasks.Task>. Étant donné que les requêtes arrivent simultanément sur plusieurs threads, l’accès à l’index actuel est synchronisé.  

[!code-csharp[TPL_Partitioners#04](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_partitioners/cs/partitioner02.cs#OrderableListPartitioner)]
[!code-vb[TPL_Partitioners#04](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_partitioners/vb/dynamicpartitioner.vb#04)]  

Il s’agit d’un exemple de partitionnement par segments, chaque segment se composant d’un seul élément. En fournissant plus d’éléments à la fois, vous pourriez réduire le conflit sur le verrou et atteindre, en théorie, des performances plus rapides. Toutefois, à un moment donné, des segments plus volumineux pourraient nécessiter une logique supplémentaire d’équilibrage de charge afin de conserver tous les threads occupés jusqu'à ce que tout le travail soit effectué.  
  
## <a name="see-also"></a>Voir aussi

* [Partitionneurs personnalisés pour PLINQ et la bibliothèque parallèle de tâches (TPL)](custom-partitioners-for-plinq-and-tpl.md)
* [Procédure : implémenter un partitionneur pour un partitionnement statique](how-to-implement-a-partitioner-for-static-partitioning.md)
