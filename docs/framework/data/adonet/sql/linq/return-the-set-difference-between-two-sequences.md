---
title: 'Comment : retourner la différence définie entre deux séquences'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 62efb546-c898-408f-af21-36e7c6fed217
ms.openlocfilehash: 5bb7d797ad2adc4374f7a10c11d66be69feeb7a1
ms.sourcegitcommit: 4735bb7741555bcb870d7b42964d3774f4897a6e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/30/2019
ms.locfileid: "66380049"
---
# <a name="return-the-set-difference-between-two-sequences"></a>Comment : retourner la différence définie entre deux séquences
Utilisez l'opérateur <xref:System.Linq.Queryable.Except%2A> pour retourner la différence définie entre deux séquences.  
  
## <a name="example"></a>Exemple  
 Cet exemple utilise <xref:System.Linq.Queryable.Except%2A> pour retourner une séquence de tous les pays/régions dans lesquels `Customers` active, mais dans lesquels aucun `Employees` live.  
  
 [!code-csharp[DLinqQueryExamples#41](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#41)]
 [!code-vb[DLinqQueryExamples#41](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#41)]  
  
 Dans [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], l'opération <xref:System.Linq.Queryable.Except%2A> est correctement définie sur les jeux uniquement. La sémantique pour les multijeux n'est pas définie.  
  
## <a name="see-also"></a>Voir aussi

- [Exemples de requêtes](../../../../../../docs/framework/data/adonet/sql/linq/query-examples.md)
- [Traduction des opérateurs de requête standard](../../../../../../docs/framework/data/adonet/sql/linq/standard-query-operator-translation.md)
