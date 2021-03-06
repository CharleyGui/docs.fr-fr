---
title: 'Procédure : accélérer les petits corps de boucles'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- parallel loops, how to speed up
ms.assetid: c7a66677-cb59-4cbf-969a-d2e8fc61a6ce
ms.openlocfilehash: 2597e37ed5901d704c94ff960bcb4b2c97633392
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95722387"
---
# <a name="how-to-speed-up-small-loop-bodies"></a>Procédure : accélérer les petits corps de boucles

Une boucle <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> dont le corps est court risque de s'exécuter plus lentement que la boucle séquentielle équivalente, notamment la boucle [for](../../csharp/language-reference/keywords/for.md) en C# et la boucle [For](/previous-versions/visualstudio/visual-studio-2008/44kykk21(v=vs.90)) en Visual Basic. La baisse des performances est provoquée par les surcharges impliquées dans le partitionnement des données et par le coût de l'appel d'un délégué sur chaque itération de boucle. Pour résoudre ces scénarios, la classe <xref:System.Collections.Concurrent.Partitioner> offre la méthode <xref:System.Collections.Concurrent.Partitioner.Create%2A?displayProperty=nameWithType>, ce qui vous permet de fournir une boucle séquentielle pour le corps du délégué, afin que celui-ci soit appelé une seule fois par partition, au lieu d'une fois par itération. Pour plus d’informations, consultez [Partitionneurs personnalisés pour PLINQ et la bibliothèque parallèle de tâches (TPL)](custom-partitioners-for-plinq-and-tpl.md).  
  
## <a name="example"></a>Exemple  

 [!code-csharp[TPL_Partitioners#01](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_partitioners/cs/partitioner01.cs#01)]
 [!code-vb[TPL_Partitioners#01](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_partitioners/vb/partitionercreate01.vb#01)]  
  
 L'approche illustrée dans cet exemple est utile quand la boucle exécute une quantité minimale de travail. À mesure que le travail devient de plus en plus gourmand en ressources informatiques, vous obtiendrez probablement des performances identiques ou meilleures en utilisant une boucle <xref:System.Threading.Tasks.Parallel.For%2A> ou <xref:System.Threading.Tasks.Parallel.ForEach%2A> avec le partitionneur par défaut.  
  
## <a name="see-also"></a>Voir aussi

- [Parallélisme des données](data-parallelism-task-parallel-library.md)
- [Partitionneurs personnalisés pour PLINQ et TPL](custom-partitioners-for-plinq-and-tpl.md)
- [Itérateurs (C#)](../../csharp/programming-guide/concepts/iterators.md)
- [Itérateurs (Visual Basic)](../../visual-basic/programming-guide/concepts/iterators.md)
- [Expressions lambda dans PLINQ et TPL](lambda-expressions-in-plinq-and-tpl.md)
