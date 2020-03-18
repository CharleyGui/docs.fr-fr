---
title: 'Comment : implémenter un partitionneur pour un partitionnement statique'
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- tasks, how to create a static partitioner
ms.assetid: f4410508-cac6-4ba7-bef1-c5e68b2794f3
ms.openlocfilehash: 94fbb681b20b9c920c20df2a9017f75a9aa9a6ea
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73091531"
---
# <a name="how-to-implement-a-partitioner-for-static-partitioning"></a>Comment : implémenter un partitionneur pour un partitionnement statique
L’exemple suivant montre une façon d’implémenter un partitionneur personnalisé simple pour PLINQ qui exécute le partitionnement statique. Étant donné que le partitionneur ne prend pas en charge les partitions dynamiques, il n’est pas utilisable à partir de <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType>. Ce partitionneur particulier peut fournir une accélération par rapport au partitionneur de plage par défaut pour les sources de données pour lequel chaque élément requiert une quantité croissante de temps de traitement.  
  
## <a name="example"></a> Exemple  
 [!code-csharp[TPL_Partitioners#05](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_partitioners/cs/partitioners.cs#05)]  
  
 Les partitions dans cet exemple sont basées sur l’hypothèse d’une augmentation linéaire du temps de traitement pour chaque élément. Dans le monde réel, il peut être difficile de prédire le temps de traitement de cette façon. Si vous utilisez un partitionneur statique avec une source de données spécifique, vous pouvez optimiser la formule de partitionnement pour la source, ajouter une logique d’équilibrage de charge ou utiliser une méthode de partitionnement par segments, comme illustré dans [Guide pratique pour implémenter des partitions dynamiques](../../../docs/standard/parallel-programming/how-to-implement-dynamic-partitions.md).  
  
## <a name="see-also"></a>Voir aussi

- [Partitionneurs personnalisés pour PLINQ et la bibliothèque parallèle de tâches (TPL)](../../../docs/standard/parallel-programming/custom-partitioners-for-plinq-and-tpl.md)
