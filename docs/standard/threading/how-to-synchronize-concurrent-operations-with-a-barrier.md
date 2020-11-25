---
title: 'Comment : synchroniser des opérations simultanées avec un objet Barrier'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Barrier, how to use
ms.assetid: e1a253ff-e0fb-4df8-95ff-d01a90d4cb19
ms.openlocfilehash: dc0955ba6194dd936da19c634ada797d6cbd3720
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95716471"
---
# <a name="how-to-synchronize-concurrent-operations-with-a-barrier"></a>Comment : synchroniser des opérations simultanées avec un objet Barrier

L’exemple suivant montre comment synchroniser des tâches simultanées avec un objet <xref:System.Threading.Barrier>.  
  
## <a name="example"></a>Exemple  

 L’objectif du programme suivant est de compter le nombre d’itérations (ou phases) nécessaires pour permettre à deux threads de trouver leur moitié de la solution sur la même phase à l’aide d’un algorithme aléatoire qui remélange les mots. Une fois que chaque thread a mélangé ses mots, l’opération post-phase de cloisonnement compare les deux résultats pour vérifier si la phrase complète a été restituée dans l’ordre correct des mots.  
  
 [!code-csharp[CDS_Barrier#01](../../../samples/snippets/csharp/VS_Snippets_Misc/cds_barrier/cs/barrier.cs#01)]
 [!code-vb[CDS_Barrier#01](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_barrier/vb/barrier_vb.vb#01)]  
  
 Un objet <xref:System.Threading.Barrier> est un objet qui empêche des tâches individuelles d’une opération parallèle de se poursuivre tant que toutes les tâches n’ont pas atteint le cloisonnement. Cela est utile quand une opération parallèle se produit en plusieurs phases, et que chaque phase exige une synchronisation entre les tâches. Dans cet exemple, l’opération est exécutée en deux phases. Durant la première phase, chaque tâche remplit sa section de la mémoire tampon avec des données. Quand chaque tâche a terminé de remplir sa section, elle signale au cloisonnement qu’elle est prête à se poursuivre, puis elle attend. Quand toutes les tâches ont signalé au cloisonnement qu’elles sont prêtes, elles sont débloquées et la deuxième phase démarre. Le cloisonnement est nécessaire, car la deuxième phase requiert que chaque tâche ait accès à toutes les données qui ont été générées à ce stade. Sans le cloisonnement, les premières tâches à effectuer pourraient tenter de lire des mémoires tampons qui n'ont pas encore été remplies par d’autres tâches. Vous pouvez synchroniser ainsi un nombre quelconque de phases.  
  
## <a name="see-also"></a>Voir aussi

- [Structures de données pour la programmation parallèle](../parallel-programming/data-structures-for-parallel-programming.md)
